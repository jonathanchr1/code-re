# Duplicate Code

![duplicate-code-01](https://github.com/jonathanchr1/code-re/assets/113973058/9f51001e-09d6-42bb-b4cc-9a7e11de7595)

`Duplicate Code` merupakan code smell yang terjadi dimana ada dua atau lebih bagian dari code yang terlihat identik atau mirip. Hal ini bisa terjadi karena adanya pengulangan kode (copy-paste) atau karena adanya beberapa bagian dari kode yang melakukan fungsi yang serupa secara konseptual tetapi memiliki detail yang sedikit berbeda.

### Contoh

Berikut adalah contoh dari `Duplicate Code` :

```java
public class printBehavior {
	public static void pigeon() {
		System.out.println("Pigeons can fly");
	}

	public static void eagle() {
		System.out.println("Eagles can fly");
	}

	public static void lion() {
		System.out.println("Lions can run");
	}

	public static void cheetah() {
		System.out.println("Cheetahs can run");
	}
}
```

Pada code tersebut, ada beberapa method yang memiliki struktur code yang serupa `(Duplicate Code)`, meski memiliki perilaku yang berbeda. Method-method tersebut adalah `pigeon`, `eagle`, `lion`, dan `cheetah`.

### Perbaikan

Untuk menghilangkan `Duplicate Code` pada code tersebut, kita dapat membuat suatu method yang dapat menjadi wadah untuk implementasi method-method yang ada (`pigeon`, `eagle`, `lion`, dan `cheetah`). Pada code tersebut, kita dapat melihat bahwa `pigeon` dan `eagle` memiliki perilaku yang sama, yaitu terbang (fly). Selain itu, `lion` dan `cheetah` memiliki perilaku yang sama, yakni berlari (run). Berdasarkan hal ini, kita dapat membuat method `fly` dan `run` yang dapat menjadi wadah untuk implementasi `pigeon`, `eagle`, `lion`, dan `cheetah`.

Berikut adalah hasil code setelah dilakukan perbaikan/refactoring :

```java
public class printBehavior {
	public static void pigeon() {
		fly("Pigeons");
	}

	public static void eagle() {
		fly("Eagles");
	}

	public static void lion() {
		run("Lions");
	}

	public static void cheetah() {
		run("Cheetahs");
	}

	public static void fly(String str) {
		System.out.println(str + " can fly");
	}

	public static void run(String str) {
		System.out.println(str + " can run");
	}
}
```

[Back to Home Page](https://jonathanchr1.github.io/code-re/)
