# Penjelasan Source Code dan File Java (Praktikum 8)

Dokumen ini berisi penjelasan detail mengenai setiap file Java dan kode program yang terdapat dalam package `praktikum8`.

---

## 1. Interface & Multiple Implementation

### 📄 `AlatElektronik.java`
**Fungsi:** Merupakan sebuah **Interface** yang menjadi kontrak dasar operasi untuk semua perangkat elektronik.

```java
package praktikum8;

public interface AlatElektronik {
    void nyalakan();
    void matikan();
}
Penjelasan Kode:public interface AlatElektronik: Mendeklarasikan sebuah interface.void nyalakan(); dan void matikan();: Method abstrak tanpa bodi/implementasi. Setiap class yang mengimplementasikan interface ini wajib menyediakan implementasi untuk kedua method ini.📄 Kamera.javaFungsi: Merupakan sebuah Interface yang mendefinisikan kemampuan atau perilaku pengambilan foto.Javapackage praktikum8;

public interface Kamera {
    void ambilFoto();
}
Penjelasan Kode:void ambilFoto();: Method abstrak yang harus diimplementasikan oleh class mana pun yang bertindak sebagai kamera.📄 Smartphone.javaFungsi: Class konkret yang menerapkan Multiple Interface Implementation dengan mengimplementasikan dua interface sekaligus, yaitu AlatElektronik dan Kamera.Javapackage praktikum8;

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
Penjelasan Kode:implements AlatElektronik, Kamera: Menyatakan bahwa class Smartphone memenuhi kontrak dari dua interface sekaligus.private String merk;: Variabel instans yang dienkapsulasi untuk menyimpan nama merek.@Override: Anotasi penanda bahwa method nyalakan(), matikan(), dan ambilFoto() meng-override method abstrak dari interface yang diimplementasikannya.2. Polimorfisme & Method Overriding📄 Hewan.javaFungsi: Class induk (Superclass) yang menjadi dasar hierarki pewarisan (inheritance) untuk class hewan.Javapackage praktikum8;

public class Hewan {
    public void bersuara() {
        System.out.println("Hewan ini mengeluarkan suara yang tidak spesifik.");
    }
}
Penjelasan Kode:public void bersuara(): Method umum yang memberikan perilaku bawaan (default) untuk semua jenis hewan.📄 Kucing.javaFungsi: Class turunan (Subclass) dari Hewan yang merepresentasikan objek Kucing.Javapackage praktikum8;

public class Kucing extends Hewan {
    @Override
    public void bersuara() {
        System.out.println("Kucing: Meow meow!");
    }
}
Penjelasan Kode:extends Hewan: Mewarisi seluruh atribut dan method dari class Hewan.@Override: Mengganti isi logika method bersuara() milik class induk agar mengeluarkan suara khas kucing ("Kucing: Meow meow!").📄 Anjing.javaFungsi: Class turunan (Subclass) dari Hewan yang merepresentasikan objek Anjing.Javapackage praktikum8;

public class Anjing extends Hewan {
    @Override
    public void bersuara() {
        System.out.println("Anjing: Guk guk!");
    }
}
Penjelasan Kode:extends Hewan: Mewarisi class Hewan.@Override: Meng-override method bersuara() untuk menghasilkan respon suara spesifik anjing ("Anjing: Guk guk!").📄 PoliTester.javaFungsi: Class utama (Main Class) yang mendemonstrasikan konsep Polimorfisme dan Upcasting.Javapackage praktikum8;

public class PoliTester {
    public static void main(String[] args) {
        Hewan[] daftarHewan = new Hewan[3];
        daftarHewan[0] = new Hewan();
        daftarHewan[1] = new Kucing(); // Upcasting
        daftarHewan[2] = new Anjing(); // Upcasting

        for (Hewan h : daftarHewan) {
            h.bersuara();
        }
    }
}
Penjelasan Kode:Hewan[] daftarHewan = new Hewan[3];: Mendeklarasikan array berkapasitas 3 dengan tipe superclass Hewan.daftarHewan[1] = new Kucing(); & daftarHewan[2] = new Anjing();: Praktik Upcasting, di mana objek subclass disimpan ke dalam variabel bertipe superclass.for (Hewan h : daftarHewan) { h.bersuara(); }: Penerapan Polimorfisme (Dynamic Method Dispatch). Meskipun method yang dipanggil sama (h.bersuara()), output yang keluar berbeda-beda menyesuaikan dengan tipe objek asli yang disimpan di memory saat runtime.3. Abstract Class & Inheritance📄 BangunDatar.javaFungsi: Class abstrak (Abstract Class) yang digunakan sebagai cetak biru dasar untuk bentuk bangun datar.Javapackage praktikum8;

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
Penjelasan Kode:public abstract class BangunDatar: Mencegah class diinstansiasi secara langsung (new BangunDatar()).public abstract double hitungLuas();: Method abstrak tanpa bodi. Mengharuskan setiap subclass untuk mengimplementasikan rumus perhitungan luas spesifiknya.public void cetakWarna(): Concrete method yang sudah memiliki implementasi dan dapat digunakan langsung oleh subclass.📄 Lingkaran.javaFungsi: Class konkret turunan dari BangunDatar yang mewakili bangun datar Lingkaran.Javapackage praktikum8;

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
Penjelasan Kode:extends BangunDatar: Mewarisi class abstrak BangunDatar.super(warna);: Memanggil konstruktor class induk untuk mengisi atribut warna.@Override public double hitungLuas(): Mengimplementasikan method abstrak hitungLuas() dengan rumus luas lingkaran ($\pi \times r^2$) menggunakan Math.PI.
