# Lazy Class

`Lazy Class` merupakan code smell yang terjadi dimana suatu kelas hanya memiliki sedikit fungsi, sekurang-kurangnya hanya satu fungsi. Kelas ini mungkin hanya berfungsi sebagai wadah untuk beberapa method kecil atau variabel yang tidak terlalu relevan. Dalam kasus tertentu, kelas semacam ini tidak memberikan nilai tambah yang signifikan kepada program dan cenderung membingungkan daripada membantu dalam memahami logika program.

### Contoh

Berikut adalah contoh dari `Lazy Class` :

```java
// Kelas 'Employee'
public class Employee {
  private String name;
	private int age;
	private String address;

	public Employee(String name, int age, String address) {
		this.name = name;
		this.age = age;
		this.address = address;
	}

	public String getName() {
		return name;
	}

	public int getAge() {
		return age;
	}

	public void setAge(int age) {
		this.age = age;
	}

	public String getAddress() {
		return address;
	}

	public void setAddress(String address) {
		this.address = address;
	}
	
	public void getEmployeeInformation() {
		Information.displayInfo(this);
	}
}
```
```java
// Kelas 'Information'
public class Information {
	public static void displayInfo(Employee employee) {
		System.out.println("Name : " + employee.getName());
		System.out.println("Age : " + employee.getAge());
		System.out.println(("Address : " + employee.getAddress()));
	}
}
```

Pada code tersebut, kita dapat melihat bahwa kelas `Information` hanya memiliki satu method/fungsi yang digunakan untuk menampilkan data dari kelas `Employee`. Keberadaan kelas `Information` ini merupakan indikasi adanya `Lazy Class` dalam code tersebut.

### Perbaikan

Untuk menghilangkan `Lazy Class` dalam code tersebut, kita dapat memindahkan method `displayInfo` dari kelas `Information` dan mengintegrasikannya ke dalam method `getEmployeeInformation` yang terdapat pada kelas `Employee`. Dengan melakukan perubahan ini, kelas `Information` sudah tidak memiliki relevansi dalam code tersebut sehingga kelas ini dapat dihapus.

Berikut adalah hasil perbaikan code setelah dilakukan refactoring :

```java
public class Employee {
	private String name;
	private int age;
	private String address;

	public Employee(String name, int age, String address) {
		this.name = name;
		this.age = age;
		this.address = address;
	}

	public String getName() {
		return name;
	}

	public int getAge() {
		return age;
	}

	public void setAge(int age) {
		this.age = age;
	}

	public String getAddress() {
		return address;
	}

	public void setAddress(String address) {
		this.address = address;
	}

	public void getEmployeeInformation() {
		System.out.println("Name : " + this.getName());
		System.out.println("Age : " + this.getAge());
		System.out.println(("Address : " + this.getAddress()));
	}
}
```

[Back to Home Page](https://jonathanchr1.github.io/code-re/)
