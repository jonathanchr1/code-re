# Shotgun Surgery

![shotgun-surgery-01](https://github.com/jonathanchr1/code-re/assets/113973058/cc228ee1-18c3-4fea-8fe1-9a52bad4fbb0)

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
       public void transfer(Account to, int cerditAmount) throws Exception{
              if(from.amount <= 500){
                     throw new Exception("Money Transfer Failed");
              }
              to.amount = amount+cerditAmount;
       }
}
```

Dapat snippet code ini, bagian yang dapat menyebabkan terjadinya smell shotgun surgery adalah bagian valiadasi balanace akun yang harus lebih dari 500. Anadaikan developer ingin bertujuan untuk merubah minimal user balance, maka harus dicari setiap instance dari code tersebut dan harus dimodifikasi secara satu-per-satu juga.

### Perbaikan

Untuk memperbaiki snippet code sebelumnya, dapat melakukan `extract method` pada bagian validasi `ammount`. Dibuatlah method sendiri untuk pengecekan `ammount`. Karena telah dikumpulkan code duplikat, sekarang kita hanya melakukan perubahan pada `isAccountUnder()` jika ada sesuatu yang perlu diubah mengenai perhitungan saldo minimum.

Berikut adalah hasil refactor

```java
public class AcountRefactored {
       private String type;
       private int amount;

       public AcountRefactored(String type, int amount){
              this.amount=amount;
              this.type=type;
       }
       private boolean isAccountUnder(){
             return amount<=500;
       }
       public void debit(int debit) throws Exception{
              if(isAccountUnder()) {
                     throw new Exception("Transaction Failed");
              }
              amount = amount-debit;
              System.out.println("Now amount is" + amount);
       }
       public void transfer(AcountRefactored to, int cerditAmount) throws Exception{
              if(isAccountUnder()){
                     throw new Exception("Money Transfer Failed");
              }
              to.amount = amount+cerditAmount;
       }
}
```

[Back to Home Page](https://jonathanchr1.github.io/code-re/)
