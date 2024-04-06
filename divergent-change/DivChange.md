# Divergent Change

'Divergent Change' merupakan code smell yang terjadi ketika satu kelas sering dimodifikasi untuk alasan tertentu.

'Divergent Change' merupakan kebalikan dari 'Shotgun Surgery'.

Berikut adalah contoh dari Divergent Change :

```java
//test penambahan code langsung
void foo() {
  if(true) {
    return;
  }

  System.out.println("halo");
}
```

Penjelasan code

### Penyelesaian

[Kembali ke halaman utama](code-re/README.md)
