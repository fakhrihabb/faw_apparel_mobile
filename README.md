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
* `SnackBar`: Memberikan pesan kepada pengguna dalam bentuk _alert_.

### 3. Apa fungsi dari `setState()`? Variabel apa saja yang dapat terdampak?
Fungsi dari `setState()` dalam Flutter adalah untuk memberitahu framework bahwa ada perubahan pada state yang membutuhkan pembaruan tampilan (rebuild). Ketika `setState()` dipanggil, Flutter akan memicu proses rebuild sehingga tampilan dapat disesuaikan dengan perubahan yang terjadi pada state. Dalam proyek ini, tidak ada _stateful widget_, sehingga tidak ada variabel apapun yang terdampak. Akan tetapi, dalam _general case_, variabel yang terdampak dapat berupa integer, boolean, list, map, dan string.

### 4. Apa perbedaan `const` dan `final`?
Berikut perbedaan antara `const` dan `final`:
| Perbedaan | `final` | `const` |
| ------------- | ------------- | ------------- |
| Penetapan Nilai | Ditentukan saat runtime | Ditentukan saat compile |
| Sifat Nilai | Nilainya tetap setelah ditetapkan | Nilainya harus konstan dan tidak berubah sama sekali |
| Kapan Digunakan | Ketika nilai hanya diketahui saat runtime | Ketika nilai sudah pasti sejak awal (compile-time) |
| Penggunaan pada Objek | Bisa pada objek yang nilainya tidak berubah setelah dibuat | Hanya bisa digunakan untuk objek yang nilainya sudah pasti sejak awal |


### 5. Bagaimana setiap checklist tugas dipenuhi?
#### a.  Membuat sebuah program Flutter baru dengan tema E-Commerce yang sesuai dengan tugas-tugas sebelumnya.
Demi mempermudah proses pembuatan program, saya menggunakan fitur **_New flutter project_** dalam Android Studio. Setelah itu, kode _default_ dimodifikasi sehingga terpisah dalam 2 file, `main.dart` dan `menu.dart`. Adapun isi `main.dart`, yakni `main()` yang meng-run `MyApp` dan `MyApp` yang me-return `MaterialApp` dengan home `MyHomePage`. Sementara itu, isi `menu.dart` adalah `MyHomePage` yang mendukung `MaterialApp` dan cards, seperti `InfoCard` dan `ItemCard`.

#### b. Membuat tiga tombol sederhana dengan ikon dan teks untuk: Melihat daftar produk (Lihat Daftar Produk), Menambah produk (Tambah Produk), Logout (Logout)
Mengimplementasikan `ItemCard` sebagai tombol yang dapat diklik. Agar interaktif dan memunculkan `SnackBar`, diimplementasikan `InkWell`.
```
...
      child: InkWell(
        // Aksi ketika kartu ditekan.
        onTap: () {
          // Menampilkan pesan SnackBar saat kartu ditekan.
          ScaffoldMessenger.of(context)
            ..hideCurrentSnackBar()
            ..showSnackBar(SnackBar(
                content: Text("Kamu telah menekan tombol ${item.name}!")));
        },
        // Container untuk menyimpan Icon dan Text
        child: Container(
          padding: const EdgeInsets.all(8),
          child: Center(
            child: Column(
              // Menyusun ikon dan teks di tengah kartu.
              mainAxisAlignment: MainAxisAlignment.center,
              children: [
                Icon(
                  item.icon,
                  color: Colors.white,
                  size: 30.0,
                ),
                const Padding(padding: EdgeInsets.all(3)),
                Text(
                  item.name,
                  textAlign: TextAlign.center,
                  style: const TextStyle(color: Colors.white),
                ),
              ],
            ),
          ),
        ),
      ),
      ...
```
Kustomisasi warna dan ikon dilakukan dalam `MyHomePage`, ketika meng-construct `ItemHomePage` (yang kemudian digunakan ketika app meng-construct `ItemCard`).
```
...
  final List<ItemHomepage> items = [
    ItemHomepage(
        "Lihat Daftar Produk", Icons.shopping_bag, Colors.grey.shade500),
    ItemHomepage("Tambah Produk", Icons.add, Colors.grey.shade700),
    ItemHomepage("Logout", Icons.logout, Colors.grey.shade900),
  ];
  ...
```

#### c. Mengimplementasikan warna-warna yang berbeda untuk setiap tombol (Lihat Daftar Produk, Tambah Produk, dan Logout).
Jika kita melihat section sebelumnya, telah jelas bahwa kustomisasi warna dan ikon dilakukan dalam `MyHomePage`, ketika meng-construct `ItemHomePage` (yang kemudian digunakan ketika app meng-construct `ItemCard`).
```
...
  final List<ItemHomepage> items = [
    ItemHomepage(
        "Lihat Daftar Produk", Icons.shopping_bag, Colors.grey.shade500),
    ItemHomepage("Tambah Produk", Icons.add, Colors.grey.shade700),
    ItemHomepage("Logout", Icons.logout, Colors.grey.shade900),
  ];
...
```
`ItemCard` kemudian akan menerima argumen color dari `ItemHomePage` dan menggunakannya dalam atribut `color`.
```
...
  Widget build(BuildContext context) {
    return Material(
      color: item.color,
      ...
```

#### d. Memunculkan Snackbar dengan tulisan
Memanfaatkan `InkWell` dengan properti `onTap` yang akan menampilkan `SnackBar` dengan tulisan yang sesuai.
```
...
      child: InkWell(
        // Aksi ketika kartu ditekan.
        onTap: () {
          // Menampilkan pesan SnackBar saat kartu ditekan.
          ScaffoldMessenger.of(context)
            ..hideCurrentSnackBar()
            ..showSnackBar(SnackBar(
                content: Text("Kamu telah menekan tombol ${item.name}!")));
        },
        ...
```
