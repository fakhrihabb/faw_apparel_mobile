# FawApparel - Mobile Edition

World's best clothing-line >_<

## Tugas 7

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

## Tugas 8

### 1. Kegunaan `const` di Flutter
Penggunaan `const` dalam Flutter sangat berguna untuk membuat widget dan nilai-nilai yang tidak berubah (immutable) atau konstan. `const` memberitahu Flutter bahwa nilai dari widget atau objek tersebut akan selalu sama sepanjang siklus hidupnya, sehingga dapat dioptimalkan oleh sistem untuk menghemat penggunaan memori dan mempercepat performa aplikasi. Adapun keuntungan menggunakan `const`, antara lain: efisiensi memori, performa cepat, dan menghindari bug dari perubahan objek tanpa sengaja.

**Kapan menggunakan `const`?**
* **Widget yang Tidak Berubah:** Saat widget tidak akan berubah selama siklus hidup aplikasi, seperti Text, Container, atau Icon yang memiliki nilai tetap.
* **Widget dalam Widget Tree:** Saat sebuah widget berada di dalam widget tree dan nilainya tidak berubah. Ini akan meringankan kerja Flutter dalam rendering ulang widget tersebut.
* **Nilai atau List Konstan:** Untuk list, map, atau objek yang nilainya tidak berubah setelah didefinisikan, misalnya daftar item statis atau properti tetap dari aplikasi.

### 2. Perbandingan Column dan Row
#### a. Column
Column adalah widget yang menata childrennya secara vertikal (dari atas ke bawah). Widget ini sangat berguna ketika Anda ingin menampilkan elemen-elemen UI secara berurutan dari atas ke bawah. Contoh implementasi: list follower pada Instagram
#### b. Row
Row adalah widget yang menata anak-anaknya secara horizontal (dari kiri ke kanan). Widget ini sering digunakan ketika Anda ingin menyusun elemen-elemen UI secara berdampingan. Contoh implementasi: tombol kategori dalam explore page Instagram

### 3. Elemen input yang digunakan dalam proyek
Pada halaman form yang dibuat di kode tersebut, terdapat beberapa elemen input berikut:
#### a. `TextFormField`:
* `Name`: mengisi nama produk
* `Price`: mengisi harga produk. Menggunakan validasi untuk memastikan input berupa angka.
* `Description`: mengisi deskripsi produk.
#### b. `ElevatedButton`:
* `Save`: tombol berfungsi untuk menampilkan data yang diisi pengguna dalam dialog box setelah validasi berhasil.
Flutter memiliki banyak elemen input selain yang disebutkan di atas, beberapa di antaranya adalah: `Checkbox`, `Radio`, `Switch`, `DropdownButton`, `Slider`, `DatePicker`, dan `TimePicker`.

### 4. Pengaturan tema:
Tema ditentukan dalam `main.dart`. Lebih tepatnya, saat melakukan build `MaterialApp`, atribut theme diisi dengan `ThemeData` dengan `primarySwatch` berisi `Colors.grey`, menandakan tema aplikasi berwarna abu-abu beserta semua variasi shade-nya. Akan tetapi, karena sebagian besar aplikasi ini hitam-putih, theme ini sering di-_override_ dengan `Colors.black`.

### 5. Menangani navigasi dengan banyak halaman
Navigasi secara utama akan dilakukan dengan `left_drawer.dart`. Jika ditekan, `drawer` akan menampilkan semua opsi halaman yang ada. Jika ditekan, maka aplikasi akan pindah halaman. Perpindahan halaman ini dilakukan dengan `push`, yang berarti page saat ini akan 'ditimpa' dengan page baru. Jika user menekan back, page teratas akan tertutup dan page di bawahnya (homepage) akan muncul. Akan tetapi, tombol yang mengarah ke homepage menggunakan `pushReplacement`, yang berarti page saat ini digantikan dengan homepage dan jika ditekan tombol back aplikasi akan tertutup.
