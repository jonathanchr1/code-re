# Dead Code

![dead-code-01](https://github.com/jonathanchr1/code-re/assets/113973058/7175d7d9-97a8-4b9b-bd62-c879ba1b20e6)

`Dead Code` merupakan code smell yang mengacu pada bagian code dalam sebuah program yang sebenarnya tidak digunakan atau diperlukan lagi, tetapi masih tetap ada dalam basis code tersebut. 

### Contoh

Berikut adalah contoh dari `Dead Code` :

```java
public class Greetings{
  public String Greet(String name){
    if(true){
      return "Hello " + name + " !";
    }else{
      return "error";
    }
  }
}
```

Pada code diatas, dibuat sebuah program yang akan menyapa user ketika mereka run softwarenya. Namun pada snippet code tersebut terdapat line yang tidak terpakai, yaitu bagian `return "error"`. Hal ini karena state akan selalu `true`, dengan itu program pasti akan return sapaan pada user.

### Perbaikan

Untuk memperbaiki code smell yang satu ini sangatlah mudah. Salah satu jalan keluarnya adalah dengan menghapus line of code yang tidak terpakai. Oleh karena itu, bagian `return "error"` dihapus dan class method ini hanya digunakan menyapa user.

Berikut adalah hasil refactor

```java
public class Greetings{
  public String Greet(String name){
    return "Hello " + name + " !";
  }
}
```

[Back to Home Page](https://jonathanchr1.github.io/code-re/)
