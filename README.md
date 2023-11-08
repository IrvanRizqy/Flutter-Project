# flutter_project

**Nama:** Irvan  
**NPM:** 2206083514  
**Kelas:** PBP A

## Tugas 7

**1. Apa perbedaan utama antara stateless dan stateful widget dalam konteks pengembangan aplikasi Flutter?**

Dalam konteks pengembangan aplikasi Flutter, perbedaan utama antara **Stateless** dan **Stateful** widget adalah bagaimana mereka menangani perubahan data dan pembaruan antarmuka pengguna:

**Stateless Widget:**
- Stateless widget adalah widget yang tidak memiliki internal state (keadaan internal).
- Mereka digunakan untuk bagian-bagian tampilan yang tidak perlu diubah saat data atau kondisi berubah.
- Stateless widget hanya akan dirender sekali saat dibuat, dan setelah itu tidak akan mengalami perubahan. Mereka berguna untuk tampilan statis.
- Contoh penggunaan stateless widget adalah untuk menampilkan teks, ikon, gambar, atau tampilan yang tidak berubah dalam siklus hidup aplikasi.

**Stateful Widget:**
- Stateful widget adalah widget yang memiliki internal state (keadaan internal).
- Mereka digunakan untuk bagian-bagian tampilan yang perlu diperbarui ketika data atau kondisi berubah.
- Stateful widget memiliki metode `setState` yang memungkinkan Anda untuk memperbarui tampilan ketika ada perubahan dalam state widget tersebut.
- Contoh penggunaan stateful widget adalah untuk membuat formulir, daftar yang dapat digulir, atau tampilan yang perlu berinteraksi dengan data atau pengguna.

Jadi, dalam rangka memutuskan antara Stateless dan Stateful widget, Anda harus mempertimbangkan apakah bagian tampilan yang Anda buat memerlukan pembaruan saat data berubah atau tidak. Jika tampilan tersebut statis, Anda dapat menggunakan Stateless widget. Jika tampilan tersebut memerlukan pembaruan, Anda perlu menggunakan Stateful widget dan mengelola state internalnya.

**2. Sebutkan seluruh widget yang kamu gunakan untuk menyelesaikan tugas ini dan jelaskan fungsinya masing-masing.**

Dalam kode `menu.dart`, kami menggunakan berbagai widget untuk mengatur tampilan dan perilaku aplikasi. Berikut adalah daftar widget yang digunakan dan penjelasan singkat tentang fungsinya:

1. **Scaffold**: Widget ini adalah kerangka dasar untuk mengatur tampilan aplikasi Flutter. Ini mencakup AppBar, body, dan berbagai fitur lainnya.

2. **AppBar**: Digunakan untuk menampilkan bilah atas (app bar) dalam aplikasi. Ini termasuk judul aplikasi dan berbagai tindakan seperti tombol kembali.

3. **Column**: Widget ini digunakan untuk mengatur anak-anaknya secara vertikal. Ini adalah wadah untuk menampilkan elemen-elemen di dalamnya dalam satu kolom.

4. **GridView.count**: Digunakan untuk menampilkan grid dari widget lain, seperti `ShopCard` dalam kasus ini. Ini memungkinkan Anda untuk mengatur widget dalam bentuk grid dengan jumlah kolom yang ditentukan.

5. **ShopCard**: Ini adalah widget kustom yang digunakan untuk menampilkan item dalam grid. Ini memiliki ikon, teks, dan latar belakang dengan warna yang berbeda sesuai dengan item yang dipilih.

6. **Material**: Digunakan untuk memberikan latar belakang dengan warna dan efek material design ke widget `ShopCard`. Ini menciptakan lapisan material di atasnya.

7. **InkWell**: Widget ini digunakan untuk membuat area yang responsif terhadap sentuhan. Ketika pengguna menyentuhnya, `InkWell` menghasilkan efek sentuhan yang indah dan dapat memicu tindakan tertentu.

8. **Text**: Digunakan untuk menampilkan teks di dalam `ShopCard`. Ini menampilkan nama item.

9. **Icon**: Digunakan untuk menampilkan ikon di dalam `ShopCard`. Ini menampilkan ikon yang sesuai dengan setiap item.

Setiap widget memiliki peran dan fungsinya masing-masing dalam mengatur tampilan dan perilaku tampilan aplikasi. Dalam kode ini, mereka digunakan untuk membuat tampilan beranda (home) yang menampilkan daftar item toko dengan berbagai tindakan yang dapat dilakukan oleh pengguna saat item tersebut diklik.

**3. Jelaskan bagaimana cara kamu mengimplementasikan checklist di atas secara step-by-step (bukan hanya sekadar mengikuti tutorial)**

__PERTAMA MEMBUAT DIREKTORI BARU UNTUK MENYIMPAN PROJECT FLUTTER__
- Jalankan command dibawah ini di dalam Command Prompt untuk membuat flutter project
```
flutter create <APP_NAME>
cd <APP_NAME>
```
sebelumnya pastikan sudah memasuki ke direktori yang ingin disimpan project flutter.

__KEDUA RAPIKAN STRUKTUR PROJEK__
- Setelah membuat flutter project di direktori lokal, buka VSC atau IDE pilihan kamu dan menambahkan kode dibawah pada file baru bernama `menu.dart` pada direktori `flutter_project/lib`.
    ```
    import 'package:flutter/material.dart';
    ```
- Pada direktori yang sama dalam file main.dart, pindahkan (cut) kode baris ke-39 hingga akhir yang berisi kedua class di bawah ini ke file `menu.dart`.
```
class MyHomePage ... {
    ...
}

class _MyHomePageState ... {
    ...
}
```
- Untuk mengoreksi error pada file `main.dart` tambahkan kode dibawah. 
```
import 'package:flutter_project/menu.dart';
```

__KETIGA MEMBUAT WIDGET SEDERHANA__
- Lanjut dengan mengubah sifat widget halaman menu menjadi stateless dengan menghapus `MyHomePage(title: 'Flutter Demo Home Page')` pada file `main.dart`, sehingga menjadi.
```
MyHomePage()
```
- Pada file menu.dart, kamu akan mengubah sifat widget halaman dari stateful menjadi stateless. Lakukan perubahan pada bagian `({super.key, required this.title})` menjadi `({Key? key}) : super(key: key);`. Hapus final String title; sampai bawah serta tambahkan Widget build sehingga kode terlihat seperti di bawah.
```
class MyHomePage extends StatelessWidget {
    MyHomePage({Key? key}) : super(key: key);

    @override
    Widget build(BuildContext context) {
        return Scaffold(
            ...
        );
    }
}
```
Jangan lupa untuk hapus fungsi State yang ada dibawah bagian stateless widget ini.
- Lanjut dengan menambahkan teks dan card untuk memperlihatkan barang yang dijual.
```
class ShopItem {
  final String name;
  final IconData icon;
  final Color color;

  ShopItem(this.name, this.icon, this.color);
}
```
- Lalu dibawah kode `MyHomePage({Key? key}) : super(key: key);`, kamu dapat menambahkan barang-barang yang dijual (nama, harga, dan icon barang tersebut).
```
final List<ShopItem> items = [
    ShopItem("Lihat Item", Icons.checklist, Colors.blue),
    ShopItem("Tambah Item", Icons.add_shopping_cart, Colors.green),
    ShopItem("Logout", Icons.logout, Colors.red),
];
```
- Tambahkan kode dibawah kedalam Widget build.
```
return Scaffold(
      appBar: AppBar(
        title: const Text(
          'Shopping List',
        ),
      ),
      body: SingleChildScrollView(
        // Widget wrapper yang dapat discroll
        child: Padding(
          padding: const EdgeInsets.all(10.0), // Set padding dari halaman
          child: Column(
            // Widget untuk menampilkan children secara vertikal
            children: <Widget>[
              const Padding(
                padding: EdgeInsets.only(top: 10.0, bottom: 10.0),
                // Widget Text untuk menampilkan tulisan dengan alignment center dan style yang sesuai
                child: Text(
                  'Grand Shop', // Text yang menandakan toko
                  textAlign: TextAlign.center,
                  style: TextStyle(
                    fontSize: 30,
                    fontWeight: FontWeight.bold,
                  ),
                ),
              ),
              // Grid layout
              GridView.count(
                // Container pada card kita.
                primary: true,
                padding: const EdgeInsets.all(20),
                crossAxisSpacing: 10,
                mainAxisSpacing: 10,
                crossAxisCount: 3,
                shrinkWrap: true,
                children: items.map((ShopItem item) {
                  // Iterasi untuk setiap item
                  return ShopCard(item);
                }).toList(),
              ),
            ],
          ),
        ),
      ),
    );
```
- dan terakhir membuat widget stateless baru untuk menampilkan card.
```
class ShopCard extends StatelessWidget {
  final ShopItem item;

  const ShopCard(this.item, {Key? key}) : super(key: key);

  @override
  Widget build(BuildContext context) {
    return Material(
      color: item.color, // Set the background color based on the ShopItem's color
      child: InkWell(
        // Area responsive terhadap sentuhan
        onTap: () {
          // Memunculkan SnackBar ketika diklik
          ScaffoldMessenger.of(context)
            ..hideCurrentSnackBar()
            ..showSnackBar(SnackBar(
                content: Text("Kamu telah menekan tombol ${item.name}!")));
        },
        child: Container(
          // Container untuk menyimpan Icon dan Text
          padding: const EdgeInsets.all(8),
          child: Center(
            child: Column(
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
    );
  }
}
```
__TERAKHIR__
- Lakukan add, commit dan push untuk memperbarui repositori GitHub.
```bash
git add .
git commit -m "<pesan_commit>"
git push -u origin <branch_utama>
```