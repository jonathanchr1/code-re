# Speculative Generality

`Speculative Generality` merupakan code smell yang mengacu pada kecenderungan untuk membuat class, method, field, atau parameter yang tidak digunakan atau tidak diperlukan, dengan anggapan bahwa mereka mungkin akan digunakan di masa depan. Hal ini dapat memunculkan kompleksitas yang tidak perlu dalam code dan dapat menyulitkan pemahaman serta pemeliharaan code.

### Contoh

Berikut adalah contoh dari `Speculative Generality` :

```java
interface Vehicle {
    void accelerate();
    void brake();
}

abstract class Car implements Vehicle {
    // Implementation...
}

abstract class Truck implements Vehicle {
    // Implementation...
}

class Sedan extends Car {
    // Implementation...
}

class SUV extends Car {
    // Implementation...
}

class Pickup extends Truck {
    // Implementation...
}

class SemiTruck extends Truck {
    // Implementation...
}

// More classes...
```

Dalam contoh ini, terdapat smell speculative generality karena antarmuka Vehicle dan kelas abstrak Car dan Truck mungkin terlalu umum dan tidak memberikan nilai tambah yang jelas dalam konteks aplikasi yang sebenarnya.

Antarmuka Vehicle menentukan metode umum accelerate() dan brake(), yang mungkin tidak relevan untuk semua jenis kendaraan. Misalnya, truk mungkin memiliki perilaku pengereman yang berbeda dari sedan, atau mungkin memerlukan metode tambahan seperti loadCargo(). Demikian pula, kelas abstrak Car dan Truck mungkin terlalu umum dan tidak memfasilitasi implementasi yang berguna bagi kelas-kelas turunannya.

Jika hierarki kelas ini tidak memberikan nilai tambah yang jelas atau relevan dalam konteks aplikasi yang sebenarnya, itu bisa menjadi contoh smell speculative generality. Dalam kasus seperti itu, lebih baik untuk merancang hierarki kelas yang lebih spesifik dan relevan dengan kebutuhan aktual aplikasi.

### Perbaikan

Dalam refaktorisasi ini, kita mempertahankan struktur umum dengan antarmuka Vehicle dan kelas abstrak Car dan Truck, tetapi menghindari smell speculative generality dengan menyediakan implementasi yang lebih spesifik untuk masing-masing kelas turunan.

Kita juga dapat mempertimbangkan untuk menambahkan perilaku yang lebih spesifik untuk kelas-kelas tersebut sesuai dengan kebutuhan aplikasi yang sebenarnya. Misalnya, Anda dapat menambahkan metode loadCargo() untuk kelas Truck, atau metode openTrunk() untuk kelas SUV, untuk menunjukkan perilaku yang berbeda di antara jenis kendaraan.

Berikut adalah hasil code setelah dilakukan perbaikan/refactoring :

```java
interface Vehicle {
    void accelerate();
    void brake();
}

abstract class Car implements Vehicle {
    // Implementation...
}

abstract class Truck implements Vehicle {
    // Implementation...
}

class Sedan extends Car {
    // Implementation...
}

class SUV extends Car {
    // Implementation...
}

class Pickup extends Truck {
    // Implementation...
}

class SemiTruck extends Truck {
    // Implementation...
}

// More specific classes...
```

[Back to Home Page](https://jonathanchr1.github.io/code-re/)
