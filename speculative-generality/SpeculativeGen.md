# Speculative Generality

![speculative-generality-01](https://github.com/jonathanchr1/code-re/assets/113973058/9fd6d98a-baa5-4a2a-8f61-b2ce46642f81)

`Speculative Generality` merupakan code smell yang mengacu pada kecenderungan untuk membuat class, method, field, atau parameter yang tidak digunakan atau tidak diperlukan, dengan anggapan bahwa mereka mungkin akan digunakan di masa depan. Hal ini dapat memunculkan kompleksitas yang tidak perlu dalam code dan dapat menyulitkan pemahaman serta pemeliharaan code.

### Contoh

Berikut adalah contoh dari `Speculative Generality` :

```java
public interface Vehicle {
    void accelerate();
    void brake();
}

public abstract class Car implements Vehicle {
    // Implementation...
}

public abstract class Truck implements Vehicle {
    // Implementation...
}

public class Sedan extends Car {
    // Implementation...
}

public class SUV extends Car {
    // Implementation...
}

public class Pickup extends Truck {
    // Implementation...
}

public class SemiTruck extends Truck {
    // Implementation...
}
```

Pada contoh tersebut, terdapat smell `Speculative Generality` karena antarmuka `Vehicle` dan kelas abstrak `Car` dan `Truck` mungkin terlalu umum dan tidak memberikan nilai tambah yang jelas dalam konteks aplikasi yang sebenarnya.

Antarmuka `Vehicle` memiliki method umum `accelerate` dan `brake`, yang mungkin tidak relevan untuk semua jenis kendaraan. Misalnya, `Truck` mungkin memiliki perilaku pengereman yang berbeda dari `Sedan`, atau mungkin memerlukan method tambahan seperti `loadCargo`. , kelas abstrak `Car` dan `Truck` mungkin terlalu umum dan tidak memfasilitasi implementasi yang berguna bagi kelas-kelas turunannya.

Jika hierarki kelas tidak memberikan nilai tambah yang jelas atau relevan dalam konteks aplikasi yang sebenarnya, hal ini dapat dianggap sebagai smell `Speculative Generality`. Dalam kasus seperti ini, lebih baik untuk merancang hierarki kelas yang lebih spesifik dan relevan dengan kebutuhan aplikasi.

### Perbaikan

Untuk memperbaiki code pada contoh tersebut, kita tetap mempertahankan struktur umum dengan antarmuka `Vehicle` dan kelas abstrak `Car` dan `Truck`, tetapi menghindari smell `Speculative Generality` dengan menyediakan implementasi yang lebih spesifik untuk masing-masing kelas turunan.

Kita juga dapat menambahkan perilaku yang lebih spesifik untuk kelas-kelas tersebut sesuai dengan kebutuhan aplikasi yang sebenarnya. Misalnya, kita dapat menambahkan metode `loadCargo` untuk kelas `Truck`, atau metode `openTrunk` untuk kelas `SUV`, untuk menunjukkan perilaku yang berbeda di antara jenis kendaraan.

Berikut adalah hasil code setelah dilakukan perbaikan/refactoring :

```java
public interface Vehicle {
    void accelerate();
    void brake();
}

public abstract class Car implements Vehicle {
    // Implementation...
}

public abstract class Truck implements Vehicle {
    // Implementation...
}

public class Sedan extends Car {
    // Implementation...
}

public class SUV extends Car {
    // Implementation...
}

public class Pickup extends Truck {
    // Implementation...
}

public class SemiTruck extends Truck {
    // Implementation...
}
```

[Back to Home Page](https://jonathanchr1.github.io/code-re/)
