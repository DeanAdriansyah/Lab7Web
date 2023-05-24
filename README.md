# **PEMOGRAMAAN WEB**
**Nama :** *Dean Adriansyah Asy'ari* 

**NIM :** *312110286* 

**Kelas :** *TI.21.A2*

**Teknik Informatika - UNIVERSITAS PELITA BANGSA**

---
![gambar](README_img/Codeigniter.png)

# <p align="center">Praktikum 7: PHP Framework (Codeigniter)</p>

### Tujuan
* Mampu memahami konsep dasar _Framework_.
* Mampu memahami konsep dasar _MVC_.
* Mampu membuat program sederhana menggunakan _Framework Codeigniter4_.

### Instruksi Praktikum
* Persiapkan text editor misalnya VSCode.
* Buat folder baru dengan nama lab7_php_ci pada docroot webserver (htdocs)
* Ikuti langkah-langkah praktikum yang akan dijelaskan berikutnya.


---
# <p align="center">Langkah-langkah Praktikum</p>
### Persiapan
Sebelum memulai menggunakan Framework Codeigniter, perlu dilakukan konfigurasi pada webserver.
Beberapa ekstensi PHP perlu diaktifkan untuk kebutuhan pengembangan Codeigniter 4.

Berikut beberapa ekstensi yang perlu diaktifkan:
- php-json ekstension untuk bekerja dengan JSON;
- php-mysqlnd native driver untuk MySQL;
- php-xml ekstension untuk bekerja dengan XML;
- php-intl ekstensi untuk membuat aplikasi multibahasa;
- libcurl (opsional), jika ingin pakai Curl.

Untuk mengaktifkan ekstentsi tersebut, melalu XAMPP Control Panel, pada bagian Apache klik Config
-> PHP.ini

![menambahkan_gambar](README_img/___.png)

Pada bagian extention, hilangkan tanda ; (titik koma) pada ekstensi yang akan diaktifkan. Kemudian
simpan kembali filenya dan restart Apache web server.

![menambahkan_gambar](README_img/___.png)

Instalasi Codeigniter 4

Untuk melakukan instalasi Codeigniter 4 dapat dilakukan dengan dua cara, yaitu cara manual dan
menggunakan composer. Pada praktikum ini kita menggunakan cara manual.

• Unduh Codeigniter dari website https://codeigniter.com/download
• Extrak file zip Codeigniter ke direktori htdocs/lab11_ci.
• Ubah nama direktory framework-4.x.xx menjadi ci4.
• Buka browser dengan alamat http://localhost/lab11_ci/ci4/public/

![menambahkan_gambar](README_img/___.png)

Menjalankan CLI (Command Line Interface)

Codeigniter 4 menyediakan CLI untuk mempermudah proses development. Untuk mengakses CLI buka
terminal/command prompt.

![menambahkan_gambar](README_img/___.png)

Arahkan lokasi direktori sesuai dengan direktori kerja project dibuat (xampp/htdocs/lab11_ci/ci4/)
Perintah yang dapat dijalankan untuk memanggil CLI Codeigniter adalah:

![menambahkan_gambar](README_img/___.png)

![menambahkan_gambar](README_img/___.png)

Mengaktifkan Mode Debugging

Codeigniter 4 menyediakan fitur debugging untuk memudahkan developer untuk mengetahui pesan
error apabila terjadi kesalahan dalam membuat kode program.

Secara default fitur ini belum aktif. Ketika terjadi error pada aplikasi akan ditampilkan pesan
kesalahan seperti berikut.

![menambahkan_gambar](README_img/___.png)

Semua jenis error akan ditampilkan sama. Untuk memudahkan mengetahui jenis errornya, maka perlu
diaktifkan mode debugging dengan mengubah nilai konfigurasi pada environment variable
CI_ENVIRINMENT menjadi development.

![menambahkan_gambar](README_img/___.png)

Ubah nama file env menjadi .env kemudian buka file tersebut dan ubah nilai variable
CI_ENVIRINMENT menjadi development.

![menambahkan_gambar](README_img/___.png)

Contoh error yang terjadi. Untuk mencoba error tersebut, ubah kode pada file
app/Controller/Home.php hilangkan titik koma pada akhir kode.

![menambahkan_gambar](README_img/___.png)

Struktur Direktori

Untuk lebih memahami Framework Codeigniter 4 perlu mengetahui struktur direktori dan file yang
ada. Buka pada Windows Explorer atau dari Visual Studio Code -> Open Folder.

Terdapat beberapa direktori dan file yang perlu dipahami fungsi dan kegunaannya.
- .github folder ini kita butuhkan untuk konfigurasi repo github, seperti konfigurasi untuk
build dengan github action;
- app folder ini akan berisi kode dari aplikasi yang kita kembangkan;
- public folder ini berisi file yang bisa diakses oleh publik, seperti file index.php, robots.txt,
favicon.ico, ads.txt, dll;
- tests folder ini berisi kode untuk melakukan testing dengna PHPunit;
- vendor folder ini berisi library yang dibutuhkan oleh aplikasi, isinya juga termasuk kode
core dari system CI.
- writable folder ini berisi file yang ditulis oleh aplikasi. Nantinya, kita bisa pakai untuk
menyimpan file yang di-upload, logs, session, dll.

Sedangkan file-file yang berada pada root direktori CI sebagai berikut.
- .env adalah file yang berisi variabel environment yang dibutuhkan oleh aplikasi.
- .gitignore adalah file yang berisi daftar nama file dan folder yang akan diabaikan oleh Git.
- build adalah script untuk mengubah versi codeigniter yang digunakan. Ada versi release
(stabil) dan development (labil).
- composer.json adalah file JSON yang berisi informasi tentang proyek dan daftar library
yang dibutuhkannya. File ini digunakan oleh Composer sebagai acuan.
- composer.lock adalah file yang berisi informasi versi dari libraray yang digunakan aplikasi.
- license.txt adalah file yang berisi penjelasan tentang lisensi Codeigniter;
- phpunit.xml.dist adalah file XML yang berisi konfigurasi untuk PHPunit.
- README.md adalah file keterangan tentang codebase CI. Ini biasanya akan dibutuhkan
pada repo github atau gitlab.
- spark adalah program atau script yang berfungsi untuk menjalankan server, generate kode,
dll.

![menambahkan_gambar](README_img/___.png)

Fokus kita pada folder app, dimana folder tersebut adalah area kerja kita untuk membuat aplikasi.
Dan folder public untuk menyimpan aset web seperti css, gambar, javascript, dll.

Memahami Konsep MVC

Codeigniter menggunakan konsep MVC. MVC meripakan singkatan dari Model-View-Controller. MVC
merupakan konsep arsitektur yang umum digunakan dalam pengembangan aplikasi. Konsep MVC
adalah memisahkan kode program berdasarkan logic proses, data, dan tampilan. Untuk logic proses
diletakkan pada direktori Contoller, Objek data diletakkan pada direktori Model, dan desain tampilan
diletakkan pada direktori View.

Codeigniter menggunakan konsep pemrograman berorientasi objek dalam mengimplementasikan
konsep MVC.

Model merupakan kode program yang berisi pemodelan data. Data dapat berupa database ataupun
sumber lainnya.

View merupakan kode program yang berisi bagian yang menangani terkait tampilan user interface
sebuah aplikasi. didalam aplikasi web biasanya pasti akan berhubungan dengan html dan css.
Controller merupakaan kode program yang berkaitan dengan logic proses yang menghubungkan
antara view dan model. Controller berfungsi untuk menerima request dan data dari user kemudian
diproses dengan menghubungkan bagian model dan view.

Routing dan Controller

Routing merupakan proses yang mengatur arah atau rute dari request untuk menentukan
fungsi/bagian mana yang akan memproses request tersebut. Pada framework CI4, routing bertujuan
untuk menentukan Controller mana yang harus merespon sebuah request. Controller adalah class atau
script yang bertanggung jawab merespon sebuah request.

Pada Codeigniter, request yang diterima oleh file index.php akan diarahkan ke Router untuk meudian
oleh router tesebut diarahkan ke Controller.

Router terletak pada file app/config/Routes.php

![menambahkan_gambar](README_img/___.png)

Pada file tersebut kita dapat mendefinisikan route untuk aplikasi yang kita buat.
Contoh:

![menambahkan_gambar](README_img/___.png)

Kode tersebut akan mengarahkan rute untuk halaman home.

Membuat Route Baru.

Tambahkan kode berikut di dalam Routes.php

![menambahkan_gambar](README_img/___.png)

Untuk mengetahui route yang ditambahkan sudah benar, buka CLI dan jalankan perintah berikut.

![menambahkan_gambar](README_img/___.png)

![menambahkan_gambar](README_img/___.png)

Selanjutnya coba akses route yang telah dibuat dengan mengakses alamat url
http://localhost:8080/about

![menambahkan_gambar](README_img/___.png)

Ketika diakses akan mucul tampilan error 404 file not found, itu artinya file/page tersebut tidak ada.
Untuk dapat mengakses halaman tersebut, harus dibuat terlebih dahulu Contoller yang sesuai dengan
routing yang dibuat yaitu Contoller Page.

Membuat Controller

Selanjutnya adalah membuat Controller Page. Buat file baru dengan nama page.php pada direktori
Controller kemudian isi kodenya seperti berikut.

![menambahkan_gambar](README_img/___.png)

Selanjutnya refresh Kembali browser, maka akan ditampilkan hasilnya yaotu halaman sudah dapat
diakses.

![menambahkan_gambar](README_img/___.png)

Auto Routing

Secara default fitur autoroute pada Codeiginiter sudah aktif. Untuk mengubah status autoroute dapat
mengubah nilai variabelnya. Untuk menonaktifkan ubah nilai true menjadi false.

![menambahkan_gambar](README_img/___.png)

Tambahkan method baru pada Controller Page seperti berikut.

![menambahkan_gambar](README_img/___.png)

Method ini belum ada pada routing, sehingga cara mengaksesnya dengan menggunakan alamat:
http://localhost:8080/page/tos

![menambahkan_gambar](README_img/___.png)

Membuat View

Selanjutnya adalam membuat view untuk tampilan web agar lebih menarik. Buat file baru dengan
nama about.php pada direktori view (app/view/about.php) kemudian isi kodenya seperti berikut.

![menambahkan_gambar](README_img/___.png)

Ubah method about pada class Controller Page menjadi seperti berikut:

![menambahkan_gambar](README_img/___.png)

Kemudian lakukan refresh pada halaman tersebut.

![menambahkan_gambar](README_img/___.png)

Membuat Layout Web dengan CSS

Pada dasarnya layout web dengan css dapat diimplamentasikan dengan mudah pada codeigniter. Yang
perlu diketahui adalah, pada Codeigniter 4 file yang menyimpan asset css dan javascript terletak pada
direktori public.

Buat file css pada direktori public dengan nama style.css (copy file dari praktikum lab4_layout. Kita
akan gunakan layout yang pernah dibuat pada praktikum 4.

![menambahkan_gambar](README_img/___.png)

Kemudian buat folder template pada direktori view kemudian buat file header.php dan footer.php

File app/view/template/header.php

![menambahkan_gambar](README_img/___.png)

![menambahkan_gambar](README_img/___.png)

File app/view/template/footer.php

![menambahkan_gambar](README_img/___.png)

Kemudian ubah file app/view/about.php seperti berikut.

![menambahkan_gambar](README_img/___.png)

Selanjutnya refresh tampilan pada alamat http://localhost:8080/about

![menambahkan_gambar](README_img/___.png)



---
# <p align="center">Tugas</p>

Pertanyaan dan Tugas

Lengkapi kode program untuk menu lainnya yang ada pada Controller Page, sehingga semua link pada
navigasi header dapat menampilkan tampilan dengan layout yang sama.





