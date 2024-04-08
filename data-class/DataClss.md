# Data Class

`Data Class` merupakan code smell yang mengacu pada suatu kelas yang hanya memiliki `atribut/field` dan fungsi `setter & getter`. Kelas-kelas semacam ini biasanya hanya digunakan sebagai wadah untuk data yang digunakan oleh kelas lain dan tidak memiliki fungsionalitas tambahan apa pun serta tidak dapat beroperasi secara independen pada data yang mereka miliki.

### Contoh

Berikut adalah contoh dari `Data Class` :

```java
package fowler.dispensables.data_class.before;
public class UserBank {
	private String name;
  private int money;
	public FullName(String name, int money) {
		super();
		this.name = name;
    this.money = money;
	}
	public String getName() {
		return name;
	}
	public void setName(String name) {
		this.name = name;
	}
  public int getMoney(){
    return money;
  }
  public void setMoney(int money){
    this.money = money;
  }
}
```

Penjelasan

### Perbaikan

Penjelasan

Berikut adalah hasil refactor

```java
package fowler.dispensables.data_class.before;
public class UserBank {
	private String name;
  private int money;
	public FullName(String name, int money) {
		super();
		this.name = name;
    this.money = money;
	}
	public void moneyDeposit(int ammount) {
		//code...
	}
  public void moneyWithdrawal(int ammount) {
		//code...
	}
  public int getMoney(){
    return money;
  }
}

```

[Back to Home Page](https://jonathanchr1.github.io/code-re/)
