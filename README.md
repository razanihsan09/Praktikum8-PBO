# Praktikum 8 - Pemrograman Berbasis Objek (Java)

Repositori ini berisi kumpulan kode program Java untuk **Praktikum 8** yang berfokus pada penerapan konsep **Polimorfisme (Polymorphism)**, **Class Abstrak (Abstract Class)**, dan **Interface** dalam Pemrograman Berbasis Objek (PBO).

---

## Struktur Direktori & Penjelasan Kelas

Seluruh kode berada di bawah package `praktikum8`. Berikut adalah rincian peran dari setiap berkas Java:

### 1. Konsep Interface & Multiple Implementation

* **`AlatElektronik.java`**  
  Interface yang mendefinisikan kontrak dasar operasi perangkat elektronik dengan method abstrak `nyalakan()` dan `matikan()`[cite: 1].

* **`Kamera.java`**  
  Interface yang mendefinisikan perilaku pengambilan gambar dengan method abstrak `ambilFoto()`[cite: 5].

* **`Smartphone.java`**  
  Kelas konkret yang mengimplementasikan dua interface sekaligus (`AlatElektronik` dan `Kamera`) untuk menyimulasikan fungsi ponsel pintar[cite: 9].

---

### 2. Konsep Polimorfisme & Method Overriding

* **`Hewan.java`**  
  *Superclass* (kelas induk) yang menyediakan method umum `bersuara()` sebagai dasar hirarki pewarisan[cite: 4].

* **`Kucing.java`**  
  *Subclass* dari `Hewan` yang melakukan *method overriding* pada method `bersuara()` untuk menghasilkan suara kucing ("Meow meow!")[cite: 6].

* **`Anjing.java`**  
  *Subclass* dari `Hewan` yang melakukan *method overriding* pada method `bersuara()` untuk menghasilkan suara anjing ("Guk guk!")[cite: 2].

* **`PoliTester.java`**  
  Kelas utama (*main class*) yang mendemonstrasikan polimorfisme dan *upcasting* menggunakan array bertipe `Hewan[]`.

---

### 3. Konsep Abstract Class

* **`BangunDatar.java`**  
  Kelas abstrak (*abstract class*) yang memiliki atribut `warna`, *concrete method* `cetakWarna()`, serta *abstract method* `hitungLuas()`[cite: 3].

* **`Lingkaran.java`**  
  *Subclass* dari `BangunDatar` yang menyimpan atribut `jariJari` dan mengimplementasikan perhitungan luas lingkaran pada method `hitungLuas()`[cite: 7].

---
