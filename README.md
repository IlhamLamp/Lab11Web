# LAB11

<table border="2" cellpading="10">
  <tr>
    <td><b>Nama</b></td>
    <td>Ilham Nur Utomo</td>
  </tr>
  <tr>
    <td><b>NIM</b></td>
    <td>312010129</td>
  </tr>
  <tr>
    <td><b>Kelas</b></td>
    <td>TI.20.A1</td>
  </tr>
  <tr>
    <td><b>MataKuliah</b></td>
    <td>Pemrograman Web</td>
  </tr>
  <tr>
    <td><b>Praktikum</b></td>
    <td><a href="#p11">11</a>,<a href="#p12">12</a>,<a href="#p13">13</a></td>
</table>

<div id="p11">

# <spaan style="color: blue">Praktikum 11 | PHP Framework (Codeigniter)</span>

## 1. Konfigurasi Webserver
- Mengaktifkan ekstensi melalui Xampp, bagian ``Apache > Config > PHP(php.ini)``, Hilangkan `;`.<br>
![img1](img-git/1-ekstensi.png)

## 2. Installasi Codeigniter 
- Unduh, ekstrak, ubah nama menjadi `ci4`, pindahkan ke direktori ``htdocs/lab11_ci``, Buka browser dengan alamat ``http://localhost/lab11_ci/ci4/public``.<br>
![img2](img-git/2-public.PNG)

## 3. Memanggil CLI
- Melalui ``Xampp > Shell``, kemudian pindah ke direktori ci4. Ketik ``php spark`` untuk melihat info.<br>
![img3](img-git/3-spark.PNG)

## 4. Debugging Mode
- Ketik ``php spark serve`` pada CLI, untuk menjalankan.<br>
![img4](img-git/4-sparks.png)
<br>

- Menampilkan pesan error, untuk mencobanya ubah kode file ``app/Controllers/home.php``, hapus `;`nya.<br>
![img5](img-git/5-error-t.png)
<br>

- Ketik ``http://localhost:8080`` pada browser. Berikut tampilan error nya.<br>
![img6](img-git/6-woop.PNG)
<br>

- Kemudian, ubah nama file ``env`` menjadi ``.env``. Masuk ke dalam filenya, hapus tanda `#` pada ``CI_ENVIRONMENT = ``<br>
![img7](img-git/7-env.png)
<br>

- Refresh url sebelumnya, Berikut tampilan error nya.<br>
![img8](img-git/8-parse.PNG)
<br>

## 5. Struktur Direktori
- ![img9](img-git/9-structure.png)

## 6. Membuat Route Baru
- Terletak pada ``app/Config/Routes.php``.<br>
![img10](img-git/10-routes.png)
<br>

- Tampilannya, ketika mengetik ``php spark routes`` pada CLI.<br>
![img11](img-git/11-sparkr.png)
<br>

- Mencoba akses ``http://localhost:8080/about``.<br>
![img12](img-git/12-fnf.PNG)

## 7. Membuat Controller
- Buat ``page.php`` pada folder Controllers.
    ```php
    <?php
    namespace App\Controllers;
    class Page extends BaseController
    {
        public function about()
        {
            echo "Ini halaman About";
        }

        public function contact()
        {
            echo "Ini halaman Contact";
        }

        public function faqs()
        {
            echo "Ini halaman FAQ";
        }
    }
    ```
    <br>
- Refresh browser. <br>
![img13](img-git/13-about-page.png)

- Tambah method baru, 
    ```php
    public function tos()
    {
        echo "ini halaman Term of Services";
    }
    ```

- Karena belum ada pada routing, sehingga mengaksesnya menggunakan ``http://localhost:8080/page/tos``.<br>
![img13-2](img-git/13-page-tos.png)
<br>

## 8. Membuat View
- Buat file, ``app/Views/about.php``
    ```php
    <!DOCTYPE html>
    <html lang="en">
        <head>
            <meta charset="UTF-8">
            <title><?= $title; ?></title>
        </head>
        <body>
            <h1><?= $title; ?></h1>
            <hr>
            <p><?= $content; ?></p>
        </body>
    </html>
    ```
    <br>

- Ubah method `about` pada Controllers page.<br>
![img14](img-git/14-about.png)
<br>

- Refresh halaman tersebut.<br>
![img15](img-git/15-aboutv.png)
<br>

## 9. Layout dengan CSS
- Terletak di ``public/style.css``<br>
![img16](img-git/16-css-layout.PNG)
<br>

## 10. Template
- Pada direktori Views, Buat foler `template`, isi dengan file

- ``header.php``
![img17](img-git/17-header-t.PNG)
<br>

- ``footer.php``
![img18](img-git/18-footer-t.PNG)
<br>

- Tampilan template.
![img19](img-git/19-about-v.PNG)


# Tugas
- Lengkapi kode program untuk menu lainnya yang ada pada Controller Page, sehingga semua link pada navigasi header dapat menampilkan tampilan dengan layout yang sama.

### Jawaban 
- Ubah isi pada ``Routes.php`` menjadi berikut,<br>
![img20](img-git/20-routes.PNG)
<br>

- Pada ``Controllers/page.php``, menjadi berikut
    ```php
    <?php
    namespace App\Controllers;

    class Page extends BaseController
    {
        public function rumah()
        {
            return view('rumah', [
            'title' => 'Halaman Home',
            'content' => 'Ini adalah halaman home yang menjelaskan tentang isi
            halaman ini.'
            ]);
        }

        public function about()
        {
            return view('about', [
            'title' => 'Halaman About',
            'content' => 'Ini adalah halaman about yang menjelaskan tentang isi 
            halaman ini.'
            ]);
        }

        public function contact()
        {
            return view('contact', [
            'title' => 'Halaman Contact',
            'content' => 'Ini adalah halaman contact yang menjelaskan tentang isi 
            halaman ini.'
            ]);
        }

        public function artikel()
        {
            return view('artikel', [
            'title' => 'Halaman Artikel',
            'content' => 'Ini adalah halaman artikel yang menjelaskan tentang isi 
            halaman ini.'
            ]);
        }

        public function faqs()
        {
            return view('faqs', [
                'title' => 'Halaman FAQ',
                'content' => 'Ini adalah halaman FAQ yang menjelaskan tentang isi 
                halaman ini.'
                ]);
        }

        public function tos()
        {
            return view('tos', [
            'title' => 'Halaman TOS',
            'content' => 'Ini adalah halaman Terms of Service yang menjelaskan tentang isi 
            halaman ini.'
            ]);
        }
    }
    ```
- Pada masing-masing file di dalam Views, buat ``rumah.php``,``about.php``,``artikel.php``,``contact.php``,``faqs.php``, dan ``tos.php``. Isi dengan,
    ```php
        <?= $this->include('template/header'); ?>
        <h1><?= $title; ?></h1>
        <hr>
        <p><?= $content; ?></p>
        <?= $this->include('template/footer'); ?>
    ```

- Berikut Tampilannya,
- ``rumah.php``
![img21](img-git/21-rumah.PNG)
<br>

- ``artikel.php``
![img22](img-git/22-artikel.PNG)
<br>

- ``about.php``
![img23](img-git/23-about.PNG)
<br>

- ``kontak.php``
![img24](img-git/24-kontak.PNG)
<br>

- ``faqs.php``
![img25](img-git/25-FAQ.PNG)
<br>

- ``tos.php``
![img26](img-git/26-TOS.PNG)
<br>
</div>

<div id="p12">

# <span style="color: blue">Praktikum 12 | Framework Lanjutan (CRUD)</span>

## 1. Database
- Jalankan ``Apache, MySql`` pada Xampp, Buat database dengan nama ``lab_ci4`` di http://localhost/phpmyadmin.
- Buat tabel dengan nama ``artikel``.
    ```sql
    CREATE TABLE artikel (
        id INT(11) auto_increment,
        judul VARCHAR(200) NOT NULL,
        isi TEXT,
        gambar VARCHAR(200),
        status TINYINT(1) DEFAULT 0,
        slug VARCHAR(200),
        PRIMARY KEY(id)
    );
    ```
![img27](img-git/27-db.png)
<br>

## 2. Konfigurasi Koneksi Database
- Terletak di folder ``ci4``, file `.env`, Hapus tanda `#`.
![img28](img-git/28-db.png)
<br>

## 3. Membuat Model 
- Terletak di folder `app/Models`, buat file `ArtikelModel.php`.
![img29](img-git/29-artikelm.png)
<br>

## 4. Membuat Controller 
- Terletak di folder `app/Controllers`, buat file `Artikel.php`.
![img30](img-git/30-artikelm.png)
<br>

## 5. Membuat View pada artikel 
- Terletak di folder `app/Views/artikel`, buat file `index.php`.
![img31](img-git/31-index.png)
<br>

- Buka browser, ketik http://localhost:8080/artikel 
![img32](img-git/32-index-nd.PNG)
<br>

- Masukkan data ke tabel artikel,
    ```sql
    INSERT INTO artikel (judul, isi, slug) VALUE
    ('Artikel pertama', 'Lorem Ipsum adalah contoh teks atau dummy dalam industri 
    percetakan dan penataan huruf atau typesetting. Lorem Ipsum telah menjadi 
    standar contoh teks sejak tahun 1500an, saat seorang tukang cetak yang tidak 
    dikenal mengambil sebuah kumpulan teks dan mengacaknya untuk menjadi sebuah 
    buku contoh huruf.', 'artikel-pertama'), 
    ('Artikel kedua', 'Tidak seperti anggapan banyak orang, Lorem Ipsum bukanlah 
    teks-teks yang diacak. Ia berakar dari sebuah naskah sastra latin klasik dari 
    era 45 sebelum masehi, hingga bisa dipastikan usianya telah mencapai lebih 
    dari 2000 tahun.', 'artikel-kedua');
    ``` 
![img33](img-git/33-dbartikel.PNG)
<br>

- Refresh kembali browser.
![img34](img-git/34-artikel.png)
<br>

## 6. Membuat Tampilan detail Artikel
- Terletak di folder `app/Controllers`, edit file `Artikel.php`. Tambah method ``view()``.
![img35](img-git/35-view.png)
<br>

## 7. Membuat View pada Detail
- Terletak di folder `app/Views/artikel`, buat file `detail.php`.
![img36](img-git/36-detail.png)
<br>

## 8. Membuat Routing untuk artikel detail
- Terletak di folder `app/Config`, edit file `Routes.php`.
![img36-2](img-git/36-routes.png)
<br>

- Klik `Artikel Kedua` pada http://localhost:8080/artikel, untuk pindah ke detailnya.
![img37](img-git/37-artikel2.png)
<br>

## 9. Membuat Menu admin
- Terletak di folder `app/Controller`, edit file `Artikel.php`. Tambah method `admin_index()`.
![img38](img-git/38-admin-index.png)
<br>

- Selanjutnya, akses kembali folder `app/Views/artikel`, buat file `admin_index.php`.
    ```php
    <?= $this->include('template/admin_header'); ?>
    <table class="table table-bordered table-hover">
        <thead>
            <tr class="table-primary">
                <th scope="col">ID</th>
                <th scope="col">Judul</th>
                <th scope="col">Status</th>
                <th scope="col">Aksi</th>
            </tr>
        </thead>
        <tbody>
            <?php if($artikel): foreach($artikel as $row): ?>
            <tr>
                <td><?= $row['id']; ?></td>
                <td>
                    <b><?= $row['judul']; ?></b>
                    <p><small><?= substr($row['isi'], 0, 50); ?></small></p>
                </td>
                <td><?= $row['status']; ?></td>
                <td>
                    <a class="btn btn-primary p-1" href="<?= base_url('/admin/artikel/edit/' . 
                    $row['id']);?>">Ubah</a>
                    <a class="btn btn-danger p-1" onclick="return confirm('Yakin menghapus data?');" href="<?= base_url('/admin/artikel/delete/' . 
                    $row['id']);?>">Hapus</a>
                </td>
            </tr>
            <?php endforeach; else: ?>
            <tr>
                <td colspan="4">Belum ada data.</td>
            </tr>
            <?php endif; ?>
        </tbody>
        <tfoot>
            <tr class="table-primary">
                <th scope="col">ID</th>
                <th scope="col">Judul</th>
                <th scope="col">Status</th>
                <th scope="col">Aksi</th>
            </tr>
        </tfoot>
    </table>
    <?= $this->include('template/admin_footer'); ?>
    ```
<br>

- Buka folder yang ada di ``app/Views/artikel/template``, kemudian buat:
- ``admin_header.php``,
![img38-1](img-git/38-admin-header.PNG)
<br>

- ``admin_footer.php``
![img38-2](img-git/38-admin-footer.PNG)
<br>

## 10. Membuat Routing untuk menu admin
- Terletak di folder `app/Config`, edit file `Routes.php`.
![img39](img-git/39-routes.png)
<br>

- Akses browser dengan http://localhost:8080/admin/artikel.
![img40](img-git/40-admin-artikel.png)
<br>

## 11. Menambah data untuk Artikel
- Terletak di folder `app/Controller`, edit file `Artikel.php`. Tambah method `add()`.
![img41](img-git/41-add.png)
<br>

- Akses kembali folder `app/Views/artikel`, buat file `form_add.php`.
![img42](img-git/42-form-add.png)
<br>

- Akses browser dengan http://localhost:8080/admin/artikel/add.
![img43](img-git/43-portal-add.PNG)
<br>

## 12. Mengubah data pada Artikel
- Terletak di folder `app/Controller`, edit file `Artikel.php`. Tambah method `edit()`.
![img44](img-git/44-edit.png)
<br>

- Akses kembali folder `app/Views/artikel`, buat file `form_edit.php`.
![img45](img-git/45-form-edit.png)
<br>

- Akses browser dengan http://localhost:8080/admin/artikel/edit/1 untuk Mengubah artikel pertama.
![img46](img-git/46-portal-edit.PNG)
<br>

## 13. Menghapus data pada Artikel
- Terletak di folder `app/Controller`, edit file `Artikel.php`. Tambah method `delete()`.
![img47](img-git/47-del.png)
<br>

- Akses browser dengan http://localhost:8080/admin/artikel/add untuk membuat artikel ketiga, lalu `kirim`.
![img48](img-git/48-add-3.png)
<br>

- Untuk mengeceknya ketik di url, http://localhost:8080/artikel kemudian enter.
![img49](img-git/49-artikel.PNG)
<br>

- Pergi ke menu admin untuk menghapusnya, http://localhost:8080/admin/artikel, kemudian pilih `hapus`.
![img50](img-git/50-admin-art.PNG)
<br>

- Artikel berhasil dihapus.
![img51](img-git/51-artikel-deleted.PNG)
<br>
</div>

<div id="p13">

# <span style="color: blue">Praktikum 13 | Framework Lanjutan (Modul Login)</span>

## 1. Membuat Table User
- Jalankan ``Apache, MySql`` pada Xampp, Akses browser http://localhost/phpmyadmin.
- Buat tabel dengan nama ``artikel``.
    ```sql
        CREATE TABLE user (
        id INT(11) auto_increment,
        username VARCHAR(200) NOT NULL,
        useremail VARCHAR(200),
        userpassword VARCHAR(200),
        PRIMARY KEY(id)
        );
    ```
![img52](img-git/52-table-user.PNG)
<br>

## 2. Membuat Model User
- Terletak di folder `app/Models`, buat file `UserModel.php`.
![img53](img-git/53-user-model.png)
<br>

## 3. Membuat Controller User
- Terletak di folder `app/Controllers`, buat file `User.php`.
![img54](img-git/54-user-controller.png)
<br>

## 4. Membuat View Login
- Terletak di folder `app/Views`, buat folder baru dengan nama `user`, buat file `login.php` di dalamnya.
![img55](img-git/55-login.png)
<br>

## 5. Membuat Database Seeder
- Untuk keperluan uji coba.
- Masuk ke direktori ci4, kemudian ketikkan kode:
``php spark make:seeder UserSeeder``
![img56](img-git/56-spark-seeder.png)
<br>

- Terletak di folder `app/Database/Seeds`, buka file `UserSeeder.php`, kemudian edit menjadi berikut:
![img57](img-git/57-user-seeder.png)
<br>

- Buka kembali CLI, kemudian ketik perintah berikut:
``php spark db:seed UserSeeder``
![img58](img-git/58-db-seeder.png)
<br>

- Berikut data yang sudah ditambah pada tabel `user`. Dengan mengakses ``http://localhost/phpmyadmin``.
![img59](img-git/59-berhasilditambah.PNG)
<br>

- Akses url ``http://localhost:8080/user/login``, menampilkan error:
![img60](img-git/59-localhost.error.PNG)
<br>

- Buka file `.env`, kemudian hapus `#` pada `app.sessionX`
![img61](img-git/59-env.png)
<br>

- Akses kembali url ``http://localhost:8080/user/login``
![img62](img-git/59-login.PNG)
<br>

## 6. Menambah Auth Filter
- Terletak di folder `app/Filters`, buat file `Auth.php`
![img63](img-git/60-auth.png)
<br>

- Kemudian pada folder `app/Config`, edit isi file `Filters.php` menjadi berikut:
![img64](img-git/61-filters.png)
<br>

- Juga berikut
![img65](img-git/62-routes-filters.png)
<br>

- Untuk mencobanya, akses ``http://localhost:8080/artikel``, kemudian tambah menjadi ``http://localhost:8080/admin/artikel`` lalu tekan enter.
![img66](img-git/62-test-login.png)
<br>

- Otomatis akan dialihkan untuk login terlebih dahulu.
![img67](img-git/62-disable.PNG)
<br>

- Mencoba masuk dengan email `admin@email.com`, dan password `admin123`, kemudian tekan `login`.
![img68](img-git/62-proses-login.PNG)
<br>

- Berhasil masuk sebagai admin, dan semua menu dapat diakses.Untuk mencobanya klik menu `Artikel`.
![img69](img-git/62-admin-user.png)
<br>

- Kemudian klik menu `Login Admin`, untuk diarahkan ke ``http://localhost:8080/admin/artikel``.
![img70](img-git/62-relog.png)
<br>

- Maka akan masuk ke menu admin sebelumnya, tidak login ulang.
![img71](img-git/62-done.png)
<br>

## 7. Membuat Fungsi Logout
- Menambah method logout().
- Terletak di folder `app/Controllers`, buka file `User.php`, kemudian edit menjadi berikut:
![img72](img-git/63-logout.png)
<br>

- Untuk mencobanya, klik menu `Logout`.
![img73](img-git/62-done.png)
<br>

- Maka akan langsung diarahkan untuk login ulang, sebelum bisa mengakses menu admin.
![img74](img-git/63-logout-login.PNG)
<br>

- Namun, untuk ``http://localhost:8080/artikel`` masih dapat diakses.
![img75](img-git/64-artikel.png)
<br>

</div>