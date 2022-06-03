# LAB11 PHP Framework (Codeigniter)

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
</table>

# <b>Praktikum</b>

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
![img14](img-git/13-page-tos.png)
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
![img15](img-git/14-about.png)
<br>

- Refresh halaman tersebut.<br>
![img16](img-git/15-aboutv.png)
<br>

## 9. Layout dengan CSS
- Terletak di ``public/style.css``<br>
![img17](img-git/16-css-layout.PNG)
<br>

## 10. Template
- Pada direktori Views, Buat foler `template`, isi dengan file

- ``header.php``
![img18](img-git/17-header-t.PNG)
<br>

- ``footer.php``
![img19](img-git/18-footer-t.PNG)
<br>

- Tampilan template.
![img20](img-git/19-about-v.PNG)


# Tugas
- Lengkapi kode program untuk menu lainnya yang ada pada Controller Page, sehingga semua link pada navigasi header dapat menampilkan tampilan dengan layout yang sama.

### Jawaban 
- Ubah isi pada ``Routes.php`` menjadi berikut,<br>
![img21](img-git/20-routes.PNG)
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
![img22](img-git/21-rumah.PNG)
<br>

- ``artikel.php``
![img23](img-git/22-artikel.PNG)
<br>

- ``about.php``
![img24](img-git/23-about.PNG)
<br>

- ``kontak.php``
![img25](img-git/24-kontak.PNG)
<br>

- ``faqs.php``
![img26](img-git/25-FAQ.PNG)
<br>

- ``tos.php``
![img27](img-git/26-TOS.PNG)
<br>