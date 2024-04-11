# Shotgun Surgery

`Shotgun Surgery` merupakan code smell yang terjadi dimana perubahan yang dilakukan pada satu bagian kecil dari code memerlukan perubahan yang tersebar luas di berbagai bagian lainnya dari. Dengan kata lain, code smell ini terjadi ketika kita ingin menubah atau menambahkan suatu fitur ke dalam code, maka kita perlu mengganti bagian code lain yang tersebar di banyak class lain. Hal ini dapat diibaratkan seperti menembak peluru dengan senapan shotgun, di mana perubahan yang dilakukan bisa menyebar secara luas.

### Contoh

Berikut adalah contoh dari `Shotgun Surgery` :

```java
public class Account {
       private String type;
       private int amount;

       public Account(String type, int amount){
              this.amount=amount;
              this.type=type;
       }
       public void debit(int debit) throws Exception{
              if(amount <= 500){
                     throw new Exception("Transaction Failed");
              }
              amount = amount-debit;
              System.out.println("Now amount is" + amount);
       }
       public void transfer(Account to,int cerditAmount) throws Exception{
              if(from.amount <= 500){
                     throw new Exception("Money Transfer Failed");
              }
              to.amount = amount+cerditAmount;
       }
}
```

Penjelasan

### Perbaikan

Penjelasan

Berikut adalah hasil refactor

```java
public class AcountRefactored {
       private String type;
       private int amount;

       public AcountRefactored(String type, int amount){
              this.amount=amount;
              this.type=type;
       }
       private boolean isAccountUnderflow(){
             return amount<=500;
       }
       public void debit(int debit) throws Exception{
              if(isAccountUnderflow()) {
                     throw new Exception("Transaction Failed");
              }
              amount = amount-debit;
              System.out.println("Now amount is" + amount);
       }
       public void transfer(AcountRefactored from,AcountRefactored to,int cerditAmount) throws Exception{
              if(isAccountUnderflow()){
                     throw new Exception("Money Transfer Failed");
              }
              to.amount = amount+cerditAmount;
       }
}
```

[Back to Home Page](https://jonathanchr1.github.io/code-re/)
