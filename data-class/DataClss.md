# Data Class

![data-class-01](https://github.com/jonathanchr1/code-re/assets/113973058/892a3c06-278b-4337-ab1c-7df730649399)

`Data Class` merupakan code smell yang mengacu pada suatu kelas yang hanya memiliki `atribut/field` dan fungsi `setter & getter`. Kelas-kelas semacam ini biasanya hanya digunakan sebagai wadah untuk data yang digunakan oleh kelas lain dan tidak memiliki fungsionalitas tambahan apa pun serta tidak dapat beroperasi secara independen pada data yang mereka miliki.

### Contoh

Berikut adalah contoh dari `Data Class`:

```java
public class UserBank {
	private String name;
  	private int money;
	public UserBank(String name, int money) {
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
```java
public class UserTransaction extends UserBAnk{
	private int ammount;
	public UserTransaction(String name, int money, int ammount){
		super(name, money);
		this.ammount = ammount;
	}
	public void moneyDeposit() {
		//code...
	}
  	public void moneyWithdrawal() {
		//code...
	}
}
```

Pada contoh diatas, class `UserBank` merupakan smell data class karena hanya berisi setter getter untuk field `name` dan `money`. 

### Perbaikan

Untuk mengeliminasi code smell-nya, class `UserBank` dapat digabungkan dengan class `UserTransaction`. Dengan ini, class tersebut memiliki fungsional lainnya.

Berikut adalah hasil refactor

```java
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
