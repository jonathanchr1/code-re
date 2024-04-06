# Divergent Change

`Divergent Change` merupakan code smell yang terjadi ketika setiap kali kita ingin melakukan perubahan pada suatu kelas, kita juga perlu melakukan perubahan pada banyak bagian dari code/method yang tidak terkait dengan perubahan yang dilakukan. Code smell ini melanggar prinsip `Single Responsibility Principle`. 

`Divergent Change` merupakan kebalikan dari `Shotgun Surgery`.

### Contoh

Berikut adalah contoh dari `Divergent Change` :

```java
public class product {
    private String name;
    private double price;
    private int stock;
    
    public product(String name, double price, int stock) {
		super();
		this.name = name;
		this.price = price;
		this.stock = stock;
	}

	public String getName() {
		return name;
	}

	public void setName(String name) {
		this.name = name;
	}

	public double getPrice() {
		return price;
	}

	public void setPrice(double price) {
		this.price = price;
	}

	public int getStock() {
		return stock;
	}

	public void setStock(int stock) {
		this.stock = stock;
	}

  public void restock(int quantity) {
    // Logika untuk menambah stok produk
    this.stock += quantity;
  }
    
  public void productDetails() {
    System.out.println("Name : " + getName());
    System.out.println("Price : " + getPrice());
    System.out.println("Stock : " + getStock());
  }

  public void sell(int quantity) {
    // Logika untuk menjual produk
    if (quantity <= this.stock) {
      this.stock -= quantity;
      System.out.println(quantity + " " + this.name + " telah terjual.");
    } else {
      System.out.println("Stok tidak mencukupi untuk " + quantity + " " + this.name);
    }
  }
}
```

Pada code tersebut, kelas `product` memiliki field-field yang mendeskripsikan suatu produk, yaitu `name`, `price`, dan `stock`. Selain itu, terdapat constructor, setter & getter, dan beberapa method operasi, yaitu `productDetails`, `restock`, dan `sell`. Berdasarkan hal ini, kita dapat menyimpulkan bahwa kelas `product` memiliki tiga tugas, yaitu menampilkan informasi produk, mengelola jumlah stok produk, dan mengatur proses penjualan produk. Namun, banyaknya tugas yang dimiliki oleh suatu kelas dapat menyulitkan kita jika kita ingin melakukan perubahan tertentu pada kelas tersebut.

Dalam konteks code tersebut, jika kita ingin melakukan perubahan terkait cara suatu produk disimpan, diproses, atau dijual, kita harus mengubah banyak bagian dari code yang berbeda secara terpisah, daripada hanya satu bagian code. Misalnya, jika metode untuk menambah stok perlu dimodifikasi untuk menangani situasi tertentu, atau jika logika penjualan perlu disesuaikan untuk menangani permintaan khusus pelanggan, maka perubahan tersebut mungkin memerlukan modifikasi di beberapa bagian dalam code. Hal ini code tersebut memiliki code smell `Divergent Change`.

### Perbaikan

Untuk menghilangkan `Divergent Change` pada code tersebut, kita perlu melakukan `Extract Class` dengan memindahkan method `restock` dan `sell` ke dalam kelas terpisah, `productManager`. Perubahan ini dapat memperjelas tugas dari masing-masing kelas dimana `product` memiliki tugas untuk menampilkan informasi suatu produk dan `productManager` memiliki tugas untuk mengelola jumlah stok dan proses penjualan produk. Hal ini juga dapat mempermudah proses modifikasi dari logika manajemen stok pada kelas `productManager` jika perlu diubah di masa depan, tanpa mempengaruhi kelas `product`.

Berikut adalah hasil refactor dari kelas `product` :

```java
// Kelas 'product'
public class product {
    private String name;
    private double price;
    private int stock;
    
    public product(String name, double price, int stock) {
		super();
		this.name = name;
		this.price = price;
		this.stock = stock;
	}

	public String getName() {
		return name;
	}

	public void setName(String name) {
		this.name = name;
	}

	public double getPrice() {
		return price;
	}

	public void setPrice(double price) {
		this.price = price;
	}

	public int getStock() {
		return stock;
	}

	public void setStock(int stock) {
		this.stock = stock;
	}

  public void restock(int quantity) {
    // Logika untuk menambah stok produk
    this.stock += quantity;
  }
    
  public void productDetails() {
    System.out.println("Name : " + getName());
    System.out.println("Price : " + getPrice());
    System.out.println("Stock : " + getStock());
  }    
}
```

```java
// Kelas 'productManager'
public class productManager {
    public void restock(product product, int quantity) {
        product.setStock(product.getStock() + quantity);
        System.out.println(quantity + " " + product.getName() + " telah ditambahkan ke dalam stok.");
    }

    public void sell(product product, int quantity) {
        // Logika untuk menjual produk
        if (quantity <= product.getStock()) {
            product.setStock(product.getStock() - quantity);
            System.out.println(quantity + " " + product.getName() + " telah terjual.");
        } else {
            System.out.println("Stok tidak mencukupi untuk " + quantity + " " + product.getName());
        }
    }
}
```

[Back to Home Page](https://jonathanchr1.github.io/code-re/)
