# Parallel Inheritance Hierarchies

![shotgun-surgery-01](https://github.com/jonathanchr1/code-re/assets/113973058/cc228ee1-18c3-4fea-8fe1-9a52bad4fbb0)

`Parallel Inheritance Hierarchies` merupakan code smell yang terjadi ketika ada hierarki kelas yang sejajar dan terpisah yang seringkali ditambah/dikembangkan secara bersamaan. Dalam konteks ini, `parallel` merujuk pada hierarki yang sejajar satu sama lain, sementara `inheritance` menunjukkan bahwa hierarki tersebut dibangun melalui pewarisan kelas.

### Contoh

Berikut adalah contoh dari `Parallel Inheritance Hierarchies` :

```java
package com.example.codesmell.parallelinheritence;
public interface Engineer {
    int getSalary();
    void setSalary(int salary);
    MileStone getMileStone();
    void setMileStone(MileStone mileStone);
}
```
```java
package com.example.codesmell.parallelinheritence;
public interface MileStone {
    public String target();
}
```
```java
package com.example.codesmell.parallelinheritence;
public class ComputerEngineer implements Engineer {
    private int salary;
    private MileStone mileStone;
    public void setSalary(int salary) {
        this.salary = salary;
    }
    public void setMileStone(MileStone mileStone) {
        this.mileStone = mileStone;
    }
    @Override
    public String toString() {
        return "ComputerEngineer [salary=" + salary + ", mileStone=" + mileStone + "]";
    }
}
```
```java
package com.example.codesmell.parallelinheritence;
public class ComputerMileStone implements MileStone {
    @Override
    public String target() {
        return"Build a Billing MicroService";
    }
    @Override
    public String toString() {
        return "ComputerMileStone [target()=" + target()"]";
    }
}
```
```java
package com.example.codesmell.parallelinheritence;
public class CivilEngineer implements Engineer {
    private int salary;
    private MileStone mileStone;
    public void setSalary(int salary) {
        this.salary = salary;
    }
    public void setMileStone(MileStone mileStone) {
        this.mileStone = mileStone;
    }
    @Override
    public String toString() {
        return "CivilEngineer [salary=" + salary + ", mileStone=" + mileStone + "]";
    }
}
```
```java
package com.example.codesmell.parallelinheritence;
public class CivilMileStone implements MileStone {
    @Override
    public String target() {
        // TODO Auto-generated method stub
        return "Create  Twin Towers";
    }
    @Override
    public String toString() {
        return "CivilMileStone [target()=" + target()"]";
    }
}
```

Pada contoh code ini, sebuah company memiliki dua macam pekerja engineer -- civil dan computer engineer. Kedua objek tersebut memiliki atribut serta method yang sama. Andaikan mereka ingin menambahkan data baru, contohnya seperti departemen, maka harus dilakukan pengembangan class dan method baru kemudian atribut di dalamnya harus masing-masing diwariskan pada computer dan civil engineer.

### Perbaikan

Perbaikan dilakukan dengan `Move Method` kepada `MileStone`, yang digabungkan dengan `Engineer` menjadi interface yang sama. Karena pada sebelumnya, bagian-bagian tersebut memiliki code yang mirip. Dengan itu, untuk menghindari terjadinya paralel inheritance terjadinya deduplicate.

Berikut adalah hasil refactor

```java
public interface EngineerMileStone {
    int getSalary();
    void setSalary(int salary);
    public String target();
}
```
```java
package com.example.codesmell.parallelinheritence;
public class RefactorComputerEngineer implements EngineerMileStone {
    private int salary; 
    @Override
    public int getSalary() {
        return salary;
    }
    @Override
    public void setSalary(int salary) {
        this.salary=salary;
    }
    @Override
    public String target() {
        return"Build a Billing MicroService";
    }
    @Override
    public String toString() {
        return "RefactorComputerEngineer [salary=" + salary + ", target()=" + target() + "]";
    }
}
```
```java
package com.example.codesmell.parallelinheritence;
public class ReFactorCivilEngineer implements EngineerMileStone {
    private int salary; 
    @Override
    public int getSalary() {
        return salary;
    }
    @Override
    public void setSalary(int salary) {
        this.salary=salary;
    }
    @Override
    public String target() {
        return "Create  Twin Towers";
    }
    @Override
    public String toString() {
        return "ReFactorCivilEngineer [salary=" + salary + ", target()=" + target() + "]";
    }
}
```

[Back to Home Page](https://jonathanchr1.github.io/code-re/)
