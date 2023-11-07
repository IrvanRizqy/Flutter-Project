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

### Penjelasan Widget

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

3. Jelaskan bagaimana cara kamu mengimplementasikan checklist di atas secara step-by-step (bukan hanya sekadar mengikuti tutorial)
