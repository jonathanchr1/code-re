# Comments

`Comments` merupakan code smell yang terjadi ketika ada suatu method yang memiliki banyak komentar. Komentar dapat digunakan untuk memperjelas serta proses atau logika yang dijalankan dalam suatu method. Akan tetapi, jika digunakan secara berlebihan, hal ini dapat menyebabkan code menjadi terlihat padat dan sulit dibaca. Untuk mengatasi hal ini, kita dapat memberikan nama yang bersifat `self-explain` (mampu menjelaskan proses atau logika secara mandiri tanpa adanya komentar) pada suatu method atau atribut.

### Contoh

Berikut adalah contoh dari `Comments` :

```java
public class kalkulasiUkuran {
	public void kalkulasiUkuranLapangan() {
    // Ukuran lapangan
		int panjangLapangan = 105;
		int lebarLapangan = 68;
		
		// Logika untuk hitung luas lapangan
		int luas = panjangLapangan * lebarLapangan;
		System.out.println(luas);
		
		// Logika untuk hitung keliling lapangan
		int keliling = (panjangLapangan + lebarLapangan) * 2;
		System.out.println(keliling);
	}
}
```

Pada code tersebut, kita dapat melihat bahwa method `kalkulasiUkuranLapangan` kelas `kalkulasiUkuran` memiliki beberapa komentar yang digunakan untuk memperjelas atribut dan method yang ada pada kelas tersebut. Adanya komentar-komentar tersebut membuat code pada kelas `kalkulasiUkuran` menjadi terlihat padat. Untuk mengatasi hal ini, kita perlu melakukan proses refactor pada code tersebut agar terlihat lebih sederhana dan mudah dipahami.

### Perbaikan

Untuk memperbaiki code tersebut, kita perlu melakukan `Extract Method` pada beberapa bagian dari method `kalkulasiUkuranLapangan` menjadi method-method baru dan memberikannya nama yang bersifat `self-explain` atau mampu menjelaskan proses atau logika yang dijalankan dalam method-method tersebut.

Berikut adalah hasil refactor dari kelas `kalkulasiUkuran` :

```java
public class kalkulasiUkuran {
	public void kalkulasiUkuranLapangan() {
		int panjangLapangan = 105;
		int lebarLapangan = 68;
		
		hitungLuasLapangan(panjangLapangan, lebarLapangan);
		hitungKelilingLapangan(panjangLapangan, lebarLapangan);
	}

  public void hitungLuasLapangan(int panjang, int lebar) {
		int luas = panjang * lebar;
		System.out.println(luas);
	}

	public void hitungKelilingLapangan(int panjang, int lebar) {
		int keliling = (panjang + lebar) * 2;
		System.out.println(keliling);
	}
}
```

[Back to Home Page](https://jonathanchr1.github.io/code-re/)
