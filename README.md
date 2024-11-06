# FawApparel - Mobile Edition

World's best clothing-line >_<

## Tugas 1

### 1. Apa itu _stateless widget_ dan _stateful widget_?
**_Stateless widget_** adalah widget yang sifatnya statis atau tidak berubah. Properti yang ada di dalam widget ini tidak akan bisa berubah setelah dibuat, sehingga cocok untuk bagian UI yang bersifat tetap. Sementara itu, **_stateful widget_** adalah kebalikannya, bersifat dinamis atau berubah-ubah. Properti yang ada di dalam widget ini bisa berubah-ubah, sehingga cocok untuk bagian UI yang harus berubah sesuai _behavior_ pengguna.
**Berikut perbedaan antara stateless dan stateful widget:**
| Sifat  | Stateless | Stateful | 
| ------------- | ------------- | ------------- |
| **Mutable**  | Immutable atau tidak dapat berubah | Mutable atau dapat berubah  |
| **Pengelolaan State**  | Tidak memiliki pengelolaan state  | Memiliki objek State untuk mengelola state  |
| **Rebuild** | Dibangun ulang hanya saat widget parent berubah | Dibangun ulang setiap kali setState dipanggil |
| **Kasus Penggunaan Ideal** | Elemen UI statis | Elemen UI dinamis yang perlu merespons perubahan |

### 2. Widget apa saja yang digunakan dalam proyek ini?
Terdapat berbagai widget yang digunakan dalam penyelesaian Tugas 1 ini, antara lain:
* `MaterialApp`: berfungsi sebagai root aplikasi Flutter yang menerapkan tema dan memfasilitasi navigasi.
* `Scaffold`: Menyediakan struktur dasar untuk halaman.
* `AppBar`: Menampilkan title (FawApparel) di bagian atas layar.
* `Padding`: Memberikan padding terhadap widget child.
* `Column`: Menyusun widget children secara vertikal dari atas ke bawah.
* `Row`: Menyusun widget children secara horizontal
* `Card`: Menampilkan informasi dengan efek bayangan (elevation) untuk memberi tampilan seperti kartu.
* `Text`: Menampilkan teks.
* `SizedBox`: Membuat kotak tidak terlihat yang biasa diposisikan antara widget untuk memberi jarak.
* `InkWell`: Merespon tap user dengan efek ripple.
* `MediaQuery`: Menyesuaikan lebar widget berdasarkan ukuran layar perangkat.
* SnackBar: Memberikan pesan kepada pengguna dalam bentuk _alert_.




### 3. Apa fungsi dari `setState()`? Variabel apa saja yang dapat terdampak?

### 4. Apa itu `const` dan `final`?

### 5. Bagaimana setiap checklist tugas dipenuhi?
