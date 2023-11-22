# flutter_project

**Nama:** Irvan  
**NPM:** 2206083514  
**Kelas:** PBP A

-----------------------------------------------------------------------------------------------------------------------------------------

<details>
<summary><strong>Tugas 7</strong></summary>

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
</details>

<details>
<summary><strong>Tugas 8</strong></summary>

**1. Jelaskan perbedaan antara Navigator.push() dan Navigator.pushReplacement(), disertai dengan contoh mengenai penggunaan kedua metode tersebut yang tepat!**

Di dalam Flutter, Navigator.push() dan Navigator.pushReplacement() merupakan dua metode yang digunakan untuk melakukan transisi antara berbagai layar (screens) dalam aplikasi. Berikut adalah perbedaan antara keduanya:

1. **Navigator.push()**:
- Metode ini digunakan untuk menambahkan layar baru ke dalam tumpukan (stack) navigasi.
- Setelah menggunakan Navigator.push(), pengguna dapat kembali ke layar sebelumnya dengan menekan tombol "Back" atau menggunakan fungsi `Navigator.pop()`.

Contoh penggunaan `Navigator.push()`:
```
// Import modul flutter
import 'package:flutter/material.dart';

// Fungsi untuk membuat layar baru dan menavigasikannya
void navigateToSecondScreen(BuildContext context) {
  Navigator.push(
    context,
    MaterialPageRoute(builder: (context) => SecondScreen()),
  );
}

// Layar pertama
class FirstScreen extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: Text('First Screen')),
      body: Center(
        child: ElevatedButton(
          onPressed: () {
            // Panggil fungsi navigateToSecondScreen untuk menampilkan layar kedua
            navigateToSecondScreen(context);
          },
          child: Text('Go to Second Screen'),
        ),
      ),
    );
  }
}

// Layar kedua
class SecondScreen extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: Text('Second Screen')),
      body: Center(
        child: Text('This is the Second Screen'),
      ),
    );
  }
}
```

2. **Navigator.pushReplacement()**:

- Metode ini juga digunakan untuk menambahkan layar baru ke dalam tumpukan navigasi.
- Namun, perbedaannya adalah bahwa setelah menggunakan Navigator.pushReplacement(), layar sebelumnya dihapus dari tumpukan sehingga pengguna tidak dapat kembali ke layar tersebut.

Contoh penggunaan `Navigator.pushReplacement()`:
```
// Fungsi untuk membuat layar baru dan menggantikan layar saat ini
void navigateToThirdScreen(BuildContext context) {
  Navigator.pushReplacement(
    context,
    MaterialPageRoute(builder: (context) => ThirdScreen()),
  );
}

// ...

// Pada saat tombol ditekan, layar ketiga akan ditampilkan dan menggantikan layar kedua
ElevatedButton(
  onPressed: () {
    navigateToThirdScreen(context);
  },
  child: Text('Go to Third Screen'),
);
```

Dalam contoh di atas, setelah pengguna menekan tombol untuk pindah ke layar ketiga, layar kedua akan dihapus dari tumpukan dan digantikan oleh layar ketiga menggunakan `Navigator.pushReplacement()`.

**2. Jelaskan masing-masing layout widget pada Flutter dan konteks penggunaannya masing-masing!**

1. **Container**
    - **Deskripsi**: Container adalah widget yang dapat digunakan untuk mengatur tata letak dan dekorasi dari widget di dalamnya.
    - **Konteks Penggunaan**: Cocok digunakan untuk mengelola tata letak sederhana, seperti mengatur padding, margin, dan dekorasi untuk widget di dalamnya.

2. **Row dan Column**
    - **Deskripsi**: Row dan Column digunakan untuk mengatur widget secara horizontal (Row) atau vertikal (Column).
    - **Konteks Penggunaan**: Berguna untuk menyusun widget secara berurutan, baik secara horizontal maupun vertikal.

3. **ListView**
    - **Deskripsi**: ListView adalah widget yang digunakan untuk menampilkan daftar item secara terus menerus atau dalam bentuk daftar gulir.
    - **Konteks Penggunaan**: Cocok untuk menampilkan daftar item, seperti daftar kontak, berita, atau item dalam aplikasi.

4. **Stack**
    - **Deskripsi**: Stack adalah widget yang digunakan untuk menempatkan widget di atas satu sama lain.
    - **Konteks Penggunaan**: Berguna ketika Anda ingin menumpuk widget, seperti menempatkan teks di atas gambar atau menyusun elemen-elemen tumpuk lainnya.

5. **Expanded dan Flexible**
    - **Deskripsi**: Expanded dan Flexible digunakan untuk memberikan widget ruang tambahan sesuai dengan kebutuhan.
    - **Konteks Penggunaan**: Cocok digunakan dalam Row atau Column untuk memberikan proporsi ruang yang berbeda kepada widget di dalamnya.

6. **GridView**
    - **Deskripsi**: GridView adalah widget yang digunakan untuk menampilkan item dalam bentuk grid.
    - **Konteks Penggunaan**: Berguna untuk menampilkan data dalam bentuk grid, seperti galeri gambar atau aplikasi e-commerce dengan produk yang disusun dalam grid.

**3. Sebutkan apa saja elemen input pada form yang kamu pakai pada tugas kali ini dan jelaskan mengapa kamu menggunakan elemen input tersebut!**

**Elemen input yang digunakan pada form di tugas kali ini adalah:**

1. **TextFormField untuk Nama Item**
    - **Alasan Penggunaan**: `TextFormField` digunakan untuk mengambil input teks, dalam hal ini untuk nama item. Ini memungkinkan pengguna memasukkan teks dengan keyboard ponsel dan menyediakan validasi menggunakan properti `validator`.

2. **TextFormField untuk Harga**
    - **Alasan Penggunaan**: `TextFormField` juga digunakan untuk mengambil input teks, tetapi pada bagian ini untuk harga item. Pada kasus ini, nilai harga kemudian diubah menjadi tipe data integer untuk keperluan pemrosesan lebih lanjut.

3. **TextFormField untuk Deskripsi**
    - Alasan Penggunaan: Seperti sebelumnya, `TextFormField` digunakan untuk mengambil input teks, kali ini untuk deskripsi item. Sama seperti nama item, pengguna dapat memasukkan teks dan validasi dapat diterapkan.

4. **ElevatedButton untuk Tombol Simpan**
    - Alasan Penggunaan: `ElevatedButton` digunakan sebagai tombol untuk menyimpan item setelah pengguna mengisi formulir dengan benar. Saat tombol ditekan, validasi akan diperiksa, dan jika valid, data item akan disimpan atau ditampilkan dalam dialog.

Setiap elemen input dipilih berdasarkan kebutuhan formulir dan kemampuannya untuk menyediakan pengalaman pengguna yang baik, validasi input, dan kemudahan integrasi dengan Flutter.

**4. Bagaimana penerapan clean architecture pada aplikasi Flutter?**

**Struktur Proyek**:
Atur proyek Flutter Anda menjadi modul yang merepresentasikan lapisan-lapisan dari Clean Architecture.
```bash
`lib/`: Kode UI Flutter.
`data/`: Logika akses data.
`domain/`: Logika bisnis.
`presentation/`: Logika tampilan dan UI.
```

**Lapisan Domain**:
Berisi definisi model entitas, objek nilai, serta aturan bisnis dan logika.

**Lapisan Data**:
Di sini, implementasikan repositori dan sumber data untuk berinteraksi dengan lapisan domain. Pastikan lapisan data tetap independen dari lapisan presentasi dan domain.

**Lapisan Presentation**:
Fokus pada antarmuka pengguna, logika presentasi, dan manajemen state menggunakan pola arsitektur seperti Bloc, Provider, atau MobX.

**Aturan Dependensi**:
Terapkan aturan dependensi di mana lapisan yang lebih dalam tidak bergantung pada lapisan yang lebih tinggi. Lapisan domain harus mandiri tanpa bergantung pada implementasi teknis dari lapisan data atau presentasi.

**Dependency Injection**:
Manfaatkan Dependency Injection (DI) untuk menyediakan dependensi ke lapisan tertentu. Contoh framework DI di Flutter termasuk `get_it` atau `provider`.

**Pengujian**:
Tulis uji unit untuk setiap lapisan secara terpisah. Pastikan uji unit lapisan presentasi tidak bergantung pada infrastruktur atau sumber daya eksternal.

**Penggunaan Repositori**:
Lapisan presentasi mengakses data melalui repositori yang diimplementasikan di lapisan data. Repositori menyatukan sumber daya data dan menyediakan antarmuka untuk lapisan domain.

**Penanganan Error**:
Tangani error dan pengecualian secara efektif, terutama di lapisan data dan domain. Kembalikan error yang relevan dan jelas di lapisan presentasi.

**Dependensi Eksternal**:
Pisahkan dependensi eksternal seperti database, panggilan API, dan plugin Flutter untuk memudahkan pengujian dan penggantian implementasi.

**5. Jelaskan bagaimana cara kamu mengimplementasikan checklist di atas secara step-by-step! (bukan hanya sekadar mengikuti tutorial)**

__PERTAMA MENAMBAHKAN DRAWER MENU UNTUK NAVIGASI__
- Buka proyek yang sebelumnya telah dibuat pada IDE favoritmu.
- Buat berkas baru di dalam direktori baru widgets dengan nama `left_drawer.dart`. Dan Tambahkan kode dibawah ini
```
import 'package:flutter/material.dart';
import 'package:flutter_project/screens/menu.dart';
import 'package:flutter_project/screens/shoplist_form.dart';

class LeftDrawer extends StatelessWidget {
  const LeftDrawer({super.key});

  @override
  Widget build(BuildContext context) {
    return Drawer(
      child: ListView(
        children: [
          const DrawerHeader(
            decoration: BoxDecoration(
              color: Colors.indigo,
            ),
            child: Column(
              children: [
                Text(
                  'Shopping List',
                  textAlign: TextAlign.center,
                  style: TextStyle(
                    fontSize: 30,
                    fontWeight: FontWeight.bold,
                    color: Colors.white,
                  ),
                ),
                Padding(padding: EdgeInsets.all(10)),
                Text("Catat seluruh keperluan belanjamu di sini!",
                    style: TextStyle(
                    fontSize: 15, // Ukuran font 15
                    color: Colors.white, // Warna teks putih
                    fontWeight: FontWeight.normal, // Weight biasa
                    ),
                    textAlign: TextAlign.center, // Center alignment
                ),
              ],
            ),
          ),
          ListTile(
            leading: const Icon(Icons.home_outlined),
            title: const Text('Halaman Utama'),
            // Bagian redirection ke MyHomePage
            onTap: () {
              Navigator.pushReplacement(
                  context,
                  MaterialPageRoute(
                    builder: (context) => MyHomePage(),
                  ));
            },
          ),
          ListTile(
            leading: const Icon(Icons.add_shopping_cart),
            title: const Text('Tambah Item'),
            // Bagian redirection ke ShopFormPage
            onTap: () {
              Navigator.pushReplacement(
              context,
              MaterialPageRoute(
                  builder: (context) => ShopFormPage(),
              ));
            },
          ),
        ],
      ),
    );
  }
}
```
Kode diatas saya gunakan untuk membuat drawer menu, kode diatas mencakupi bagian header dari drawer, dan bagian routing ke page lain.
- Selanjutnya adalah memasukkan drawer ke halaman yang diinginkan, saya menggunakan halaman `menu.dart`.
```
// Impor drawer widget
import 'package:flutter_project/widgets/left_drawer.dart';
...
return Scaffold(
  appBar: AppBar(
    title: const Text(
      'Shopping List',
    ),
    backgroundColor: Colors.indigo,
    foregroundColor: Colors.white,
  ),
  // Masukkan drawer sebagai parameter nilai drawer dari widget Scaffold
  drawer: const LeftDrawer(),
```

__KEDUA MENAMBAHKAN FORM DAN ELEMEN INPUT__
- Buat berkas baru pada direktori `lib` dengan nama `shoplist_form.dart`, dan tambahkan kode dibawah ke dalam berkas `shoplist_form.dart`.
```
import 'package:flutter/material.dart';
import 'package:flutter_project/widgets/left_drawer.dart';

class ShopFormPage extends StatefulWidget {
    const ShopFormPage({super.key});

    @override
    State<ShopFormPage> createState() => _ShopFormPageState();
}

class _ShopFormPageState extends State<ShopFormPage> {
  final _formKey = GlobalKey<FormState>();
  String _name = "";
  int _price = 0;
  String _description = "";

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: const Center(
          child: Text(
            'Form Tambah Item',
          ),
        ),
        backgroundColor: Colors.indigo,
        foregroundColor: Colors.white,
      ),
      drawer: const LeftDrawer(),
      body: Form(
        key: _formKey,
        child: SingleChildScrollView(
          child: Column(
            crossAxisAlignment: CrossAxisAlignment.start,
            children: [
              Padding(
                padding: const EdgeInsets.all(8.0),
                child: TextFormField(
                  decoration: InputDecoration(
                    hintText: "Nama Item",
                    labelText: "Nama Item",
                    border: OutlineInputBorder(
                      borderRadius: BorderRadius.circular(5.0),
                    ),
                  ),
                  onChanged: (String? value) {
                    setState(() {
                      _name = value!;
                    });
                  },
                  validator: (String? value) {
                    if (value == null || value.isEmpty) {
                      return "Nama Item tidak boleh kosong!";
                    } 
                    if (value.runtimeType != String) {
                      return "Nama Item harus berupa string!";
                    }
                    return null;
                  },
                ),
              ),
              Padding(
                padding: const EdgeInsets.all(8.0),
                child: TextFormField(
                  decoration: InputDecoration(
                    hintText: "Harga",
                    labelText: "Harga",
                    border: OutlineInputBorder(
                      borderRadius: BorderRadius.circular(5.0),
                    ),
                  ),
                  onChanged: (String? value) {
                    setState(() {
                      _price = int.parse(value!);
                    });
                  },
                  validator: (String? value) {
                    if (value == null || value.isEmpty) {
                      return "Harga tidak boleh kosong!";
                    }
                    if (int.tryParse(value) == null) {
                      return "Harga harus berupa angka!";
                    }
                    return null;
                  },
                ),
              ),
              Padding(
                padding: const EdgeInsets.all(8.0),
                child: TextFormField(
                  decoration: InputDecoration(
                    hintText: "Deskripsi",
                    labelText: "Deskripsi",
                    border: OutlineInputBorder(
                      borderRadius: BorderRadius.circular(5.0),
                    ),
                  ),
                  onChanged: (String? value) {
                    setState(() {
                      _description = value!;
                    });
                  },
                  validator: (String? value) {
                    if (value == null || value.isEmpty) {
                      return "Deskripsi tidak boleh kosong!";
                    } 
                    if (value.runtimeType != String) {
                      return "Deskripsi harus berupa string!";
                    }
                    return null;
                  },
                ),
              ),
              Align(
                alignment: Alignment.bottomCenter,
                child: Padding(
                  padding: const EdgeInsets.all(8.0),
                  child: ElevatedButton(
                    style: ButtonStyle(
                      backgroundColor:
                          MaterialStateProperty.all(Colors.indigo),
                    ),
                    onPressed: () {
                      if (_formKey.currentState!.validate()) {
                        _formKey.currentState!.reset(); // Ditempatkan di sini
                        showDialog(
                          context: context,
                          builder: (context) {
                            return AlertDialog(
                              title: const Text('Produk berhasil tersimpan'),
                              content: SingleChildScrollView(
                                child: Column(
                                  crossAxisAlignment: CrossAxisAlignment.start,
                                  children: [
                                    Text('Name: $_name'),
                                    Text('Amount: $_price'),
                                    Text('Description: $_description'),
                                  ],
                                ),
                              ),
                              actions: [
                                TextButton(
                                  child: const Text('OK'),
                                  onPressed: () {
                                    Navigator.pop(context);
                                  },
                                ),
                              ],
                            );
                          },
                        );
                      }
                    },
                    child: const Text(
                      "Save",
                      style: TextStyle(color: Colors.white),
                    ),
                  ),
                ),
              ),
            ]
          )
        ),
      ),
    );
  }
}
```
kode diatas berfungsi dalam membuat page shoplist_form, dimana didalamnya berupa form input, tombol save, dan card untuk barang baru yang ditambah kedalam shopping list.

__KETIGA MENAMBAHKAN FITUR NAVIGASI PADA TOMBOL__
- Pada widget `ShopItem` di dalam berkas `menu.dart` yang telah kita buat dalam tutorial sebelumnya, kita akan memperbarui kode di atribut `onTap` dari `InkWell` agar dapat mengarahkan pengguna ke route lain. Tambahkan kode tambahan setelah blok `ScaffoldMessenger` yang menampilkan snackbar.
```
  // Area responsif terhadap sentuhan
  onTap: () {
    // Memunculkan SnackBar ketika diklik
    ScaffoldMessenger.of(context)
      ..hideCurrentSnackBar()
      ..showSnackBar(SnackBar(
          content: Text("Kamu telah menekan tombol ${item.name}!")));

    // Navigate ke route yang sesuai (tergantung jenis tombol)
    if (item.name == "Tambah Item") {
      Navigator.push(context,
      MaterialPageRoute(builder: (context) => const ShopFormPage()));
    }

  },
```

__KEEMPAT REFRACTORING FILE__
- Pastikan ekstensi Flutter terpasang di IDE atau text editor yang digunakan.
- Buat berkas baru dengan nama shop_card.dart dalam direktori widgets.
- Pindahkan kode dari widget ShopItem di menu.dart ke dalam berkas widgets/shop_card.dart.
- Jangan lupa untuk mengimpor halaman shoplist_form.dart ke dalam berkas shop_card.dart, dan mengimpor shop_card.dart ke dalam berkas menu.dart.
- Buat folder baru bernama screens di direktori lib.
- Alihkan file menu.dart dan shoplist_form.dart ke dalam folder screens. Pastikan pemindahan file dilakukan melalui IDE atau text editor yang mendukung Flutter extension, bukan melalui file manager konvensional seperti File Explorer atau Finder. Dengan cara ini, IDE atau text editor dapat melakukan refactoring secara otomatis.

__TERAKHIR__
- Lakukan add, commit dan push untuk memperbarui repositori GitHub.
```bash
git add .
git commit -m "<pesan_commit>"
git push -u origin <branch_utama>
```
</details>


<details>
<summary><strong>Tugas 9</strong></summary>

**1. Apakah bisa kita melakukan pengambilan data JSON tanpa membuat model terlebih dahulu? Jika iya, apakah hal tersebut lebih baik daripada membuat model sebelum melakukan pengambilan data JSON?**

Tentu saja, Anda dapat mengambil data JSON tanpa membuat model terlebih dahulu. Namun, membuat model terlebih dahulu akan memudahkan Anda dalam membaca dan mengidentifikasi bug. Hal ini karena model dapat membantu Anda memahami struktur data dan memastikan bahwa data yang diambil sesuai dengan struktur tersebut. Selain itu, model juga dapat membantu Anda dalam melakukan validasi data dan memastikan bahwa data yang diambil memiliki tipe data yang benar.

**2. Jelaskan fungsi dari CookieRequest dan jelaskan mengapa instance CookieRequest perlu untuk dibagikan ke semua komponen di aplikasi Flutter.**

`CookieRequest` adalah fungsi yang digunakan untuk mengirim permintaan HTTP dengan cookie di Flutter. Anda dapat menggunakan paket http dan mengatur header cookie dalam permintaan untuk mengirim cookie. Berikut adalah contoh bagaimana Anda dapat membuat permintaan GET dan mengirim cookie di Flutter:
```
import 'package:http/http.dart' as http;

Future<void> main() async {
  final response = await http.get(
    Uri.parse('https://example.com/'),
    headers: <String, String>{
      'cookie': 'name=value; name2=value2'
    },
  );
  print(response.body);
}
```
Instance `CookieRequest` perlu dibagikan ke semua komponen di aplikasi Flutter karena instance ini menyimpan informasi cookie yang diperlukan untuk mengirim permintaan HTTP dengan cookie. Dengan membagikan instance ini ke semua komponen, Anda dapat memastikan bahwa setiap permintaan HTTP yang dikirim oleh aplikasi menggunakan cookie yang sama. Ini sangat penting jika Anda ingin memastikan bahwa pengguna tetap masuk ke aplikasi Anda dan tidak perlu masuk ulang setiap kali mereka membuka aplikasi.

**3. Jelaskan mekanisme pengambilan data dari JSON hingga dapat ditampilkan pada Flutter.**

Mekanisme pengambilan data dari JSON hingga dapat ditampilkan pada Flutter adalah sebagai berikut:
- Pertama, Anda perlu membuat sebuah model yang dapat merepresentasikan struktur data JSON yang ingin Anda ambil. Model ini harus memiliki konstruktor yang sesuai dengan parameter yang ada di JSON, dan juga harus memiliki metode untuk mengembalikan objek dari JSON. Anda dapat menggunakan paket `json_annotation` untuk mendukung fitur ini.
- Kedua, Anda perlu membuat sebuah fungsi HTTP yang dapat mengirim permintaan GET ke URL yang menyediakan data JSON. Anda dapat menggunakan paket http dan mengatur header cookie dalam permintaan untuk mengirim cookie. Anda juga perlu menangani respons dari server dengan menggunakan metode `jsonDecode` untuk mengubah data JSON menjadi objek model.
- Ketiga, Anda perlu membuat sebuah widget yang dapat menampilkan data model tersebut dengan cara yang sesuai dengan kebutuhan Anda. Misalnya, jika Anda ingin menampilkan data dalam bentuk tabel, Anda dapat menggunakan widget `Table`. Jika Anda ingin menampilkan data dalam bentuk grafik, Anda dapat menggunakan widget `Chart`. Jika Anda ingin menampilkan data dalam bentuk teks, Anda dapat menggunakan widget `Text`.

Berikut adalah contoh kode untuk melakukan pengambilan data dari JSON hingga dapat ditampilkan pada Flutter:
```
import 'package:http/http.dart' as http;
import 'package:json_annotation/json_annotation.dart';

// Membuat model untuk menyimpan data JSON
class DataModel {
  final String name;
  final int age;

  DataModel({required this.name, required this.age});

  // Membuat konstruktor dari model
  factory DataModel.fromJson(Map<String, dynamic> json) {
    return DataModel(
      name: json['name'],
      age: json['age'],
    );
  }
}

// Membuat fungsi HTTP untuk mengambil data JSON
Future<DataModel> getDataFromJson(String url) async {
  // Mengirim permintaan GET dengan header cookie
  final response = await http.get(
    Uri.parse(url),
    headers: {'cookie': 'name=value; name2=value2'},
  );

  // Mengubah respons menjadi objek model
  final data = jsonDecode(response.body);

  // Mengembalikan objek model
  return DataModel.fromJson(data);
}

// Membuat widget untuk menampilkan data model
class DataWidget extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    // Mendapatkan data dari URL
    final url = 'https://example.com/data.json';
    final data = getDataFromJson(url);

    // Menampilkan data dalam bentuk tabel
    return Table(
      children: [
        Text(data.name),
        Text(data.age.toString()),
      ],
    );
  }
}
```

**4. Jelaskan mekanisme autentikasi dari input data akun pada Flutter ke Django hingga selesainya proses autentikasi oleh Django dan tampilnya menu pada Flutter.**

Untuk melakukan autentikasi dari input data akun pada Flutter ke Django, Anda dapat menggunakan JSON Web Token (JWT) untuk mengamankan permintaan HTTP. Berikut adalah mekanisme autentikasi yang dapat Anda gunakan:

1. Pengguna memasukkan data akun mereka pada aplikasi Flutter.
2. Aplikasi Flutter mengirim permintaan HTTP ke server Django dengan data akun pengguna.
3. Server Django memeriksa data akun pengguna dan menghasilkan token JWT.
4. Server Django mengirim token JWT kembali ke aplikasi Flutter.
5. Aplikasi Flutter menyimpan token JWT dan menggunakannya untuk mengamankan permintaan HTTP selanjutnya.
6. Server Django memeriksa token JWT pada setiap permintaan HTTP dan memberikan akses ke data yang sesuai.

Untuk membagikan instance CookieRequest ke semua komponen di aplikasi Flutter, Anda dapat menggunakan Provider atau InheritedWidget. Dengan menggunakan salah satu dari kedua opsi ini, Anda dapat memastikan bahwa setiap komponen di aplikasi menggunakan instance yang sama dan bahwa data cookie yang diperlukan untuk mengirim permintaan HTTP dengan cookie tetap sama.

**5. Sebutkan seluruh widget yang kamu pakai pada tugas ini dan jelaskan fungsinya masing-masing.**

Pada kedua file `login.dart` dan `list_product.dart`, terdapat beberapa widget yang digunakan. Berikut adalah penjelasan singkat mengenai setiap widget yang digunakan:

__login.dart__
1. **MaterialApp**: Ini adalah widget utama yang menyediakan beberapa konfigurasi aplikasi, seperti judul dan tema.
    - Fungsi: Mengatur konfigurasi dasar aplikasi.
2. **Scaffold**: Ini adalah kerangka dasar halaman yang berisi elemen-elemen dasar seperti AppBar dan body.
    - Fungsi: Menyediakan struktur dasar untuk tata letak halaman.
3. **AppBar**: Ini adalah bilah atas halaman yang menampilkan judul.
    - Fungsi: Menampilkan judul halaman.
4. **Container**: Ini adalah wadah yang dapat disesuaikan dengan ukuran dan tata letak tertentu.
    - Fungsi: Menyediakan padding untuk elemen-elemen di dalamnya.
5. **Column**: Ini adalah widget yang mengatur elemen-elemen anak secara vertikal.
    - Fungsi: Menyusun elemen-elemen anak secara vertikal di dalam Container.
6. **TextField**: Ini adalah input teks yang memungkinkan pengguna memasukkan teks.
    - Fungsi: Mengambil input teks untuk username dan password.
7. **SizedBox**: Ini adalah kotak berukuran yang dapat disesuaikan.
    - Fungsi: Menyediakan ruang kosong antara elemen-elemen.
8. **ElevatedButton**: Ini adalah tombol dengan latar belakang yang meninggi ketika ditekan.
    - Fungsi: Menjalankan aksi login ketika tombol ditekan.
9. **SnackBar**: Ini adalah pop-up kecil yang menampilkan pesan.
    - Fungsi: Menampilkan pesan sambutan atau pesan kesalahan setelah login.
10. **AlertDialog**: Ini adalah dialog yang menampilkan pesan dan tombol aksi.
    - Fungsi: Menampilkan pesan kesalahan jika login gagal.

__list_product.dart__
1. **Scaffold**: Sama seperti pada login.dart, ini adalah kerangka dasar halaman.
    - Fungsi: Menyediakan struktur dasar untuk tata letak halaman.
2. **AppBar**: Bilah atas halaman yang menampilkan judul.
    - Fungsi: Menampilkan judul halaman.
3. **Drawer**: Ini adalah menu samping yang dapat digeser dari kiri ke kanan.
    - Fungsi: Menyediakan navigasi menu samping.
4. **FutureBuilder**: Ini adalah widget yang membangun tampilan berdasarkan hasil dari Future.
    - Fungsi: Menampilkan indikator loading ketika data masih diambil, atau menampilkan daftar produk setelah data diambil.
5. **Center**: Ini adalah widget yang mengatur elemen anaknya di tengah halaman.
    - Fungsi: Menempatkan elemen-elemen anak di tengah halaman jika data belum tersedia.
6. **ListView.builder**: Ini adalah widget yang membangun daftar dengan elemen-elemen yang dapat di-scroll.
    - Fungsi: Menampilkan daftar produk yang diambil dari server.
7. **Container**: Ini adalah wadah yang dapat disesuaikan dengan ukuran dan tata letak tertentu.
    - Fungsi: Memberikan margin dan padding pada elemen anaknya.
8. **Column**: Ini adalah widget yang mengatur elemen anak secara vertikal.
    - Fungsi: Menyusun elemen-elemen anak secara vertikal di dalam Container.
9. **Text**: Ini adalah widget untuk menampilkan teks.
    - Fungsi: Menampilkan informasi produk seperti nama, harga, dan deskripsi.
10. **CircularProgressIndicator**: Ini adalah indikator loading berbentuk lingkaran.
    - Fungsi: Menampilkan indikator loading ketika data sedang diambil.

**6. Jelaskan bagaimana cara kamu mengimplementasikan checklist di atas secara step-by-step! (bukan hanya sekadar mengikuti tutorial).**

__PERTAMA INTEGRASI AUTENTIKASI DJANGO-FLUTTER__
- __DJANGO__
  - Pertama, buat `django-app` baru bernama `authentication`, dan tambahkan app-nya ke `INSTALLED_APPS` di file `settings.py` pada folder main project.
  - Lanjutkan dengan mengeksekusi perintah `pip install django-cors-headers` pada Command Prompt untuk menginstal library yang dibutuhkan.
  - Tambahkan `corsheaders` ke `INSTALLED_APPS` dan `corsheaders.middleware.CorsMiddleware` pada main project `settings.py`.
  - Tambahkan variabel dibawah pada main project settings.py aplikasi Django kamu.
  ```
  CORS_ALLOW_ALL_ORIGINS = True
  CORS_ALLOW_CREDENTIALS = True
  CSRF_COOKIE_SECURE = True
  SESSION_COOKIE_SECURE = True
  CSRF_COOKIE_SAMESITE = 'None'
  SESSION_COOKIE_SAMESITE = 'None'
  ```
  - Tambahkan kode dibawah sebagai metode view untuk login pada authentication/views.py.
  ```
  from django.shortcuts import render
  from django.contrib.auth import authenticate, login as auth_login
  from django.http import JsonResponse
  from django.views.decorators.csrf import csrf_exempt

  @csrf_exempt
  def login(request):
      username = request.POST['username']
      password = request.POST['password']
      user = authenticate(username=username, password=password)
      if user is not None:
          if user.is_active:
              auth_login(request, user)
              # Status login sukses.
              return JsonResponse({
                  "username": user.username,
                  "status": True,
                  "message": "Login sukses!"
                  # Tambahkan data lainnya jika ingin mengirim data ke Flutter.
              }, status=200)
          else:
              return JsonResponse({
                  "status": False,
                  "message": "Login gagal, akun dinonaktifkan."
              }, status=401)

      else:
          return JsonResponse({
              "status": False,
              "message": "Login gagal, periksa kembali email atau kata sandi."
          }, status=401)
  ```
  - Buat file urls.py pada folder authentication dan tambahkan URL routing terhadap fungsi yang sudah dibuat dengan endpoint login/.
  ```
  from django.urls import path
  from authentication.views import login

  app_name = 'authentication'

  urlpatterns = [
      path('login/', login, name='login'),
  ]
  ```
  - Terakhir, tambahkan path('auth/', include('authentication.urls')), pada file inventory_project/urls.py.

- __FLUTTER__
  - Pertama install package dibawah
  ```
  flutter pub add provider
  flutter pub add pbp_django_auth
  ```
  - Untuk menggunakan package diatas, harus memodifikasi root widget menjadi:
  ```
  class MyApp extends StatelessWidget {
    const MyApp({Key? key}) : super(key: key);

    @override
    Widget build(BuildContext context) {
        return Provider(
            create: (_) {
                CookieRequest request = CookieRequest();
                return request;
            },
            child: MaterialApp(
                title: 'Flutter App',
                theme: ThemeData(
                    colorScheme: ColorScheme.fromSeed(seedColor: Colors.indigo),
                    useMaterial3: true,
                ),
                home: LoginPage()),
        );
    }
  }
  ```
  Hal ini akan membuat objek Provider baru yang akan membagikan instance CookieRequest dengan semua komponen yang ada di aplikasi.
  - Isi file login.dart dengan kode berikut.
  ```
  import 'package:flutter_project/screens/menu.dart';
  import 'package:flutter/material.dart';
  import 'package:pbp_django_auth/pbp_django_auth.dart';
  import 'package:provider/provider.dart';

  void main() {
      runApp(const LoginApp());
  }

  class LoginApp extends StatelessWidget {
  const LoginApp({super.key});

  @override
  Widget build(BuildContext context) {
      return MaterialApp(
          title: 'Login',
          theme: ThemeData(
              primarySwatch: Colors.blue,
      ),
      home: const LoginPage(),
      );
      }
  }

  class LoginPage extends StatefulWidget {
      const LoginPage({super.key});

      @override
      _LoginPageState createState() => _LoginPageState();
  }

  class _LoginPageState extends State<LoginPage> {
      final TextEditingController _usernameController = TextEditingController();
      final TextEditingController _passwordController = TextEditingController();

      @override
      Widget build(BuildContext context) {
          final request = context.watch<CookieRequest>();
          return Scaffold(
              appBar: AppBar(
                  title: const Text('Login'),
              ),
              body: Container(
                  padding: const EdgeInsets.all(16.0),
                  child: Column(
                      mainAxisAlignment: MainAxisAlignment.center,
                      children: [
                          TextField(
                              controller: _usernameController,
                              decoration: const InputDecoration(
                                  labelText: 'Username',
                              ),
                          ),
                          const SizedBox(height: 12.0),
                          TextField(
                              controller: _passwordController,
                              decoration: const InputDecoration(
                                  labelText: 'Password',
                              ),
                              obscureText: true,
                          ),
                          const SizedBox(height: 24.0),
                          ElevatedButton(
                              onPressed: () async {
                                  String username = _usernameController.text;
                                  String password = _passwordController.text;

                                  final response = await request.login("http://127.0.0.1:8000/auth/login/", {
                                  'username': username,
                                  'password': password,
                                  });
                      
                                  if (request.loggedIn) {
                                      String message = response['message'];
                                      String uname = response['username'];
                                      Navigator.pushReplacement(
                                          context,
                                          MaterialPageRoute(builder: (context) => MyHomePage()),
                                      );
                                      ScaffoldMessenger.of(context)
                                          ..hideCurrentSnackBar()
                                          ..showSnackBar(
                                              SnackBar(content: Text("$message Selamat datang, $uname.")));
                                      } else {
                                      showDialog(
                                          context: context,
                                          builder: (context) => AlertDialog(
                                              title: const Text('Login Gagal'),
                                              content:
                                                  Text(response['message']),
                                              actions: [
                                                  TextButton(
                                                      child: const Text('OK'),
                                                      onPressed: () {
                                                          Navigator.pop(context);
                                                      },
                                                  ),
                                              ],
                                          ),
                                      );
                                  }
                              },
                              child: const Text('Login'),
                          ),
                      ],
                  ),
              ),
          );
      }
  }
  ```
  - Terakhir Pada file `main.dart`, pada Widget `MaterialApp(...)`, ubah `home: MyHomePage()` menjadi `home: LoginPage()`.

__KEDUA PEMBUATAN MODEL KUSTOM__
- Pertama buka endpoint `JSON` yang sudah dibuat sebelumnya.
- Salin data `JSON` dan kunjungi situs web `Quicktype`.
- Di situs web `Quicktype`, ubah pengaturan dengan menetapkan setup name menjadi `Product`,  source type menjadi `JSON`, dan language menjadi `Dart`.
- Tempel data `JSON` yang telah disalin sebelumnya ke dalam kotak teks yang tersedia di `Quicktype`.
- Klik opsi `Copy Code` pada `Quicktype`.
- Setelah mendapatkan kode model dari `Quicktype`, kembali ke proyek Flutter. Dan buat file baru di folder `lib/models` dengan nama `product.dart` dan tempel kode yang telah disalin dari `Quicktype` ke file ini.

__KETIGA MENERAPKAN FETCH DATA DARI DJANGO UNTUK DITAMPILKAN KE FLUTTER__
- __Dependensi HTTP__
  - Lakukan `flutter pub add http` pada terminal proyek Flutter untuk menambahkan package `http`.
  - Pada file `android/app/src/main/AndroidManifest.xml`, tambahkan kode berikut untuk memperbolehkan akses Internet pada aplikasi Flutter yang sedang dibuat.
  ```
  <application>
  ...
  </application>
  <!-- Required to fetch data from the Internet. -->
  <uses-permission android:name="android.permission.INTERNET" />
  ```

- __Fetch Data dari Django__
  - Buatlah file baru pada folder `lib/screens` dengan nama list_product.dart dan mengisinya dengan kode dibawah.
  ```
  import 'package:flutter/material.dart';
  import 'package:http/http.dart' as http;
  import 'dart:convert';
  import 'package:flutter_project/models/product.dart';
  import 'package:flutter_project/widgets/left_drawer.dart';

  class ProductPage extends StatefulWidget {
      const ProductPage({Key? key}) : super(key: key);

      @override
      _ProductPageState createState() => _ProductPageState();
  }

  class _ProductPageState extends State<ProductPage> {
  Future<List<Product>> fetchProduct() async {
      // TODO: Ganti URL dan jangan lupa tambahkan trailing slash (/) di akhir URL!
      var url = Uri.parse(
          'http://127.0.0.1:8000/json/');
      var response = await http.get(
          url,
          headers: {"Content-Type": "application/json"},
      );

      // melakukan decode response menjadi bentuk json
      var data = jsonDecode(utf8.decode(response.bodyBytes));

      // melakukan konversi data json menjadi object Product
      List<Product> list_product = [];
      for (var d in data) {
          if (d != null) {
              list_product.add(Product.fromJson(d));
          }
      }
      return list_product;
  }

  @override
  Widget build(BuildContext context) {
      return Scaffold(
          appBar: AppBar(
          title: const Text('Product'),
          ),
          drawer: const LeftDrawer(),
          body: FutureBuilder(
              future: fetchProduct(),
              builder: (context, AsyncSnapshot snapshot) {
                  if (snapshot.data == null) {
                      return const Center(child: CircularProgressIndicator());
                  } else {
                      if (!snapshot.hasData) {
                      return const Column(
                          children: [
                          Text(
                              "Tidak ada data produk.",
                              style:
                                  TextStyle(color: Color(0xff59A5D8), fontSize: 20),
                          ),
                          SizedBox(height: 8),
                          ],
                      );
                  } else {
                      return ListView.builder(
                          itemCount: snapshot.data!.length,
                          itemBuilder: (_, index) => Container(
                                  margin: const EdgeInsets.symmetric(
                                      horizontal: 16, vertical: 12),
                                  padding: const EdgeInsets.all(20.0),
                                  child: Column(
                                  mainAxisAlignment: MainAxisAlignment.start,
                                  crossAxisAlignment: CrossAxisAlignment.start,
                                  children: [
                                      Text(
                                      "${snapshot.data![index].fields.name}",
                                      style: const TextStyle(
                                          fontSize: 18.0,
                                          fontWeight: FontWeight.bold,
                                      ),
                                      ),
                                      const SizedBox(height: 10),
                                      Text("${snapshot.data![index].fields.price}"),
                                      const SizedBox(height: 10),
                                      Text(
                                          "${snapshot.data![index].fields.description}")
                                  ],
                                  ),
                              ));
                      }
                  }
              }));
      }
  }
  ```
  - Tambahkan halaman `list_product.dart` ke `widgets/left_drawer.dart` dengan menambahkan kode berikut.
  ```
  ListTile(
      leading: const Icon(Icons.shopping_basket),
      title: const Text('Daftar Item'),
      onTap: () {
          // Route menu ke halaman produk
          Navigator.push(
          context,
          MaterialPageRoute(builder: (context) => const ProductPage()),
          );
      },
  ),
  ```
  - Ubah fungsi tombol `Lihat Item` pada halaman utama agar mengarahkan ke halaman ProductPage.
  ```
  else if (item.name == "Lihat Item") {
    Navigator.push(context,
      MaterialPageRoute(builder: (context) => const ProductPage()));
  }
  ```
  - Impor file yang dibutuhkan saat menambahkan `ProductPage` ke `left_drawer.dart` dan `shop_card.dart`.

__KEEMPAT INTEGRASI FORM FLUTTER DENGAN LAYANAN DJANGO__
- __Django__
  - Buatlah sebuah fungsi view baru pada `main/views.py` aplikasi Django kamu dengan potongan kode berikut.
  ```
  @csrf_exempt
  def create_product_flutter(request):
      if request.method == 'POST':
          
          data = json.loads(request.body)

          new_product = Product.objects.create(
              user = request.user,
              name = data["name"],
              price = int(data["price"]),
              description = data["description"]
          )

          new_product.save()

          return JsonResponse({"status": "success"}, status=200)
      else:
          return JsonResponse({"status": "error"}, status=401)
  ```
  - Tambahkan path baru pada `main/urls.py` dengan kode berikut.
  ```
  path('create-flutter/', create_product_flutter, name='create_product_flutter'),
  ```

- __Flutter__
  - Hubungkan halaman `shoplist_form.dart` dengan `CookieRequest` dengan menambahkan baris kode berikut.
  ```
  @override
  Widget build(BuildContext context) {
      final request = context.watch<CookieRequest>();

      return Scaffold(
  ```
  - Ubahlah perintah pada onPressed: () button tambah menjadi kode berikut.
  ```
  onPressed: () async {
    if (_formKey.currentState!.validate()) {
        final response = await request.postJson(
        "http://127.0.0.1:8000/create-flutter/",
        jsonEncode(<String, String>{
            'name': _name,
            'price': _price.toString(),
            'description': _description,
        }));
        if (response['status'] == 'success') {
            ScaffoldMessenger.of(context)
                .showSnackBar(const SnackBar(
            content: Text("Produk baru berhasil disimpan!"),
            ));
            Navigator.pushReplacement(
                context,
                MaterialPageRoute(builder: (context) => MyHomePage()),
            );
        } else {
            ScaffoldMessenger.of(context)
                .showSnackBar(const SnackBar(
                content:
                    Text("Terdapat kesalahan, silakan coba lagi."),
            ));
        }
    }
  },
  ```
__KELIMA IMPLEMENTASI FITUR LOGOUT__
- __DJANGO__
  - Buatlah sebuah metode view untuk `logout` pada `authentication/views.py`.
  ```
  from django.contrib.auth import logout as auth_logout

  @csrf_exempt
  def logout(request):
      username = request.user.username

      try:
          auth_logout(request)
          return JsonResponse({
              "username": username,
              "status": True,
              "message": "Logout berhasil!"
          }, status=200)
      except:
          return JsonResponse({
          "status": False,
          "message": "Logout gagal."
          }, status=401)
  ```
  - Tambahkan path baru pada `authentication/urls.py` dengan kode berikut.
  ```
  path('logout/', logout, name='logout'),
  ```
- __FLUTTER__
  - Buka file `lib/widgets/shop_card.` dan tambahkan potongan kode berikut. Selesaikan masalah impor library setelah menambahkan potongan kode ke dalam file tersebut.
  ```
  @override
  Widget build(BuildContext context) {
      final request = context.watch<CookieRequest>();
      return Material(
  ```
  - Ubahlah perintah `onTap: () {...}` pada widget `Inkwell` menjadi `onTap: () async {...}` agar widget Inkwell dapat melakukan proses logout secara asinkronus.
  - Tambahkan kode berikut ke dalam `async {...}` di bagian akhir:
  ```
  else if (item.name == "Logout") {
    final response = await request.logout(
        "http://127.0.0.1:8000/auth/logout/");
    String message = response["message"];
    if (response['status']) {
      String uname = response["username"];
      ScaffoldMessenger.of(context).showSnackBar(SnackBar(
        content: Text("$message Sampai jumpa, $uname."),
      ));
      Navigator.pushReplacement(
        context,
        MaterialPageRoute(builder: (context) => const LoginPage()),
      );
    } else {
      ScaffoldMessenger.of(context).showSnackBar(SnackBar(
        content: Text("$message"),
      ));
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
</details>