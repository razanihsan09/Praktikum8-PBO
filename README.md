# Dokumentasi Kode Program & Penjelasan Class Praktikum 8 (PBO)

Dokumen ini berisi kode program beserta penjelasan lengkap untuk setiap file Java pada package `praktikum8`.

---

## Kegiatan 1: Polimorfisme & Method Overriding

### Hewan.java

```java
package praktikum8;

public class Hewan {
    public void bersuara() {
        System.out.println("Hewan ini mengeluarkan suara yang tidak spesifik.");
    }
}
```

**Penjelasan Class & Kode:**
Class `Hewan` berfungsi sebagai kelas induk (*superclass*) yang menjadi dasar hirarki pewarisan (*inheritance*). Di dalam kelas ini terdapat method `bersuara()` yang memberikan perilaku umum atau bawaan (*default*) untuk seluruh jenis hewan. Method ini sengaja dirancang agar nantinya dapat di-override oleh kelas-kelas turunannya (*subclass*), sehingga berbagai jenis hewan dapat menggunakan nama method yang sama tetapi menghasilkan respons yang berbeda sesuai karakteristiknya.

---

### Kucing.java

```java
package praktikum8;

public class Kucing extends Hewan {
    @Override
    public void bersuara() {
        System.out.println("Kucing: Meow meow!");
    }
}
```

**Penjelasan Class & Kode:**
Class `Kucing` merupakan kelas turunan (*subclass*) dari `Hewan` yang ditandai dengan penggunaan kata kunci `extends`. Class ini menerapkan konsep *method overriding* menggunakan anotasi `@Override` pada method `bersuara()`. Hal ini bertujuan untuk mengganti isi logika bawaan dari kelas induk sehingga saat method dipanggil, keluaran yang dihasilkan adalah suara khas kucing (`"Kucing: Meow meow!"`).

---

### Anjing.java

```java
package praktikum8;

public class Anjing extends Hewan {
    @Override
    public void bersuara() {
        System.out.println("Anjing: Guk guk!");
    }
}
```

**Penjelasan Class & Kode:**
Class `Anjing` juga merupakan *subclass* dari `Hewan`. Sama seperti class `Kucing`, kelas ini mewarisi struktur dari kelas induk dan menyesuaikan perilaku method `bersuara()` melalui *method overriding*. Logika di dalam method diubah agar menampilkan suara khas anjing (`"Anjing: Guk guk!"`). Hal ini membuktikan bahwa beberapa kelas anak dapat merespons pemanggilan method yang sama dengan cara yang berbeda.

---

### PoliTester.java

```java
package praktikum8;

public class PoliTester {
    public static void main(String[] args) {
        Hewan[] daftarHewan = new Hewan[3];
        daftarHewan[0] = new Hewan();
        daftarHewan[1] = new Kucing();
        daftarHewan[2] = new Anjing();

        for (Hewan h : daftarHewan) {
            h.bersuara();
        }
    }
}
```

**Penjelasan Class & Kode:**
Class `PoliTester` bertindak sebagai kelas utama (*main class*) untuk mendemonstrasikan konsep **Polimorfisme** dan **Upcasting**. 
* `Hewan[] daftarHewan = new Hewan[3];`: Membuat array bertipe *superclass* `Hewan`.
* `daftarHewan[1] = new Kucing();` & `daftarHewan[2] = new Anjing();`: Merupakan bentuk **Upcasting**, di mana objek dari *subclass* disimpan ke dalam variabel bertipe *superclass*.
* `for (Hewan h : daftarHewan) { h.bersuara(); }`: Menunjukkan mekanisme *Dynamic Method Dispatch*. Saat perulangan berjalan, Java secara otomatis mengeksekusi method `bersuara()` sesuai dengan tipe objek aslinya yang tersimpan di memori pada saat *runtime*.

---

## Kegiatan 2: Interface & Multiple Implementation

### AlatElektronik.java

```java
package praktikum8;

public interface AlatElektronik {
    void nyalakan();
    void matikan();
}
```

**Penjelasan Class & Kode:**
`AlatElektronik` adalah sebuah **Interface** yang berfungsi sebagai kontrak dasar operasi bagi semua perangkat elektronik. Di dalamnya terdapat dua method abstrak tanpa bodi, yaitu `nyalakan()` dan `matikan()`. Semua method di dalam interface secara implisit bersifat `public` dan `abstract`, sehingga kelas apa pun yang mengimplementasikan interface ini wajib menyediakan logika konkret untuk kedua method tersebut.

---

### Kamera.java

```java
package praktikum8;

public interface Kamera {
    void ambilFoto();
}
```

**Penjelasan Class & Kode:**
`Kamera` merupakan interface yang menetapkan standar kemampuan pengambilan foto melalui method abstrak `ambilFoto()`. Dengan adanya interface ini, berbagai jenis perangkat (seperti Smartphone, Kamera Digital, atau Webcam) dapat memiliki kemampuan mengambil foto dengan pemanggilan method yang seragam.

---

### Smartphone.java

```java
package praktikum8;

public class Smartphone implements AlatElektronik, Kamera {
    private String merk;

    public Smartphone(String merk) {
        this.merk = merk;
    }

    @Override
    public void nyalakan() {
        System.out.println(merk + " menyala, Booting OS...");
    }

    @Override
    public void matikan() {
        System.out.println(merk + " dimatikan. Goodbye.");
    }

    @Override
    public void ambilFoto() {
        System.out.println("Cekrek! Foto berhasil disimpan di galeri " + merk);
    }
}
```

**Penjelasan Class & Kode:**
Class `Smartphone` mendemonstrasikan fitur **Multiple Interface Implementation** di Java dengan mengimplementasikan dua interface sekaligus (`AlatElektronik` dan `Kamera`) menggunakan kata kunci `implements`. 
* Atribut `private String merk` menerapkan prinsip enkapsulasi.
* Konstruktor `Smartphone(String merk)` digunakan untuk menginisialisasi nama merek saat objek dibuat.
* Menggunakan anotasi `@Override` untuk mendefinisikan seluruh method abstrak dari kedua interface (`nyalakan()`, `matikan()`, dan `ambilFoto()`) sesuai fungsi smartphone.

---

## Kegiatan 3: Abstract Class & Inheritance

### BangunDatar.java

```java
package praktikum8;

public abstract class BangunDatar {
    String warna;

    public BangunDatar(String warna) {
        this.warna = warna;
    }

    public abstract double hitungLuas();

    public void cetakWarna() {
        System.out.println("Warna bangun ini adalah: " + warna);
    }
}
```

**Penjelasan Class & Kode:**
Class `BangunDatar` merupakan sebuah **Abstract Class** yang berfungsi sebagai cetak biru bentuk geometri dua dimensi. 
* Kelas abstrak tidak dapat diinstansiasi langsung menggunakan keyword `new`.
* Memiliki atribut `warna` dan konstruktor untuk inisialisasi warna.
* `public abstract double hitungLuas();`: Merupakan *abstract method* tanpa bodi yang mewajibkan seluruh kelas turunan untuk mengimplementasikan rumus perhitungan luasnya masing-masing.
* `public void cetakWarna()`: Merupakan *concrete method* (method lengkap dengan bodi) yang bisa langsung digunakan atau diwarisi oleh *subclass*.

---

### Lingkaran.java

```java
package praktikum8;

public class Lingkaran extends BangunDatar {
    private double jariJari;

    public Lingkaran(String warna, double jariJari) {
        super(warna);
        this.jariJari = jariJari;
    }

    @Override
    public double hitungLuas() {
        return Math.PI * jariJari * jariJari;
    }
}
```

**Penjelasan Class & Kode:**
Class `Lingkaran` merupakan kelas konkret turunan dari kelas abstrak `BangunDatar`.
* `extends BangunDatar`: Menyatakan hubungan pewarisan.
* `super(warna)`: Memanggil konstruktor *superclass* (`BangunDatar`) untuk mengisi atribut `warna`.
* Atribut `private double jariJari`: Menyimpan nilai jari-jari lingkaran.
* `@Override public double hitungLuas()`: Mengimplementasikan method abstrak dari `BangunDatar` dengan memasukkan rumus matematika luas lingkaran ($\pi \times r^2$) memanfaatkan konstanta `Math.PI`.
