UNIVERSITAS PERSATUAN ISLAM
             UNIPI     PSDKU CISURUPAN


Dokumentasi Pemeliharaan Aplikasi "Simple Inventory"

Nama: AKRAM MULLOH
NIM			: 2305024
Prodi			: Informatika
Semester		: 4 (Empat)
Mata Kuliah		: Maintenance Software
Dosen Pengampu	: Dede Alamsyah, S.Kom., M.Pd.
Tahun Ajaran		: 2024/2025

         

   DAFTAR ISI   

1. Deskripsi Umum Aplikasi
2. Struktur Folder dan File
3. Instruksi Instalasi dan Konfigurasi
4. Dependency yang Digunakan
5. Instruksi Build dan Deployment
6. Panduan Debugging dan Logging
7. Catatan Perubahan (Change Log)
8. Daftar Bug Dikenal
9. Saran Pengembangan / Peningkatan
10. Lampiran

         

          1. Deskripsi Umum Aplikasi   

   Simple Inventory    adalah aplikasi manajemen inventaris berbasis web yang memungkinkan pengguna mencatat barang masuk, keluar, dan memantau stok. Aplikasi ini dirancang untuk kemudahan penggunaan dan efisiensi pelacakan inventaris.

 Fitur Utama:

    Login (Admin dan User)
    CRUD Data Barang
    Input Barang Masuk dan Keluar
    Laporan Stok Barang
    Manajemen Pengguna

   
 Teknologi Digunakan:

    PHP 7.4 (native)
    MySQL
    Bootstrap 4, jQuery
    Apache Server (XAMPP atau Laragon)

         

    




2. Struktur Folder dan File   


simple   inventory/
├── config/              Koneksi database (db.php)
├── controllers/         Proses logika bisnis (login.php, barang.php)
├── views/               Tampilan halaman (login.php, dashboard.php)
├── public/              Aset CSS dan JS
├── assets/              Gambar, file upload
├── index.php            Halaman utama
├── logout.php           Logout user


Penjelasan:

    config/: konfigurasi koneksi database
    controllers/: memproses input dan validasi
    views/: tampilan yang dilihat pengguna
    public/: memuat semua sumber daya visual dan interaktif

         

   3. Instruksi Instalasi dan Konfigurasi  
 Persyaratan:

    PHP 7.4+
    MySQL
    Apache (XAMPP atau Laragon)

        
 Langkah Instalasi:

1. Clone atau salin project ke folder htdocs/
2. Buat database inventory_db di phpMyAdmin
3. Import file .sql dari folder database
4. Edit file config/db.php sesuai koneksi lokal
5. Jalankan http://localhost/simple   inventory/

          Konfigurasi Deployment (Linux Server):

    Upload file ke /var/www/html/
    Ubah permission folder dengan chmod    R 755
    Edit ulang db.php dengan konfigurasi server

         
 4. Dependency yang Digunakan
   

Library                                  Fungsi                                                                                                                                                        

Bootstrap 4    		     UI responsif                      
 jQuery 	                 Interaksi dinamis di browser      	
 FontAwesome		     Menyediakan ikon                  
 Chart.js   		     Menampilkan grafik laporan        
 Mysqli   		     Menjalankan query MySQL di PHP    


Semua dependency ini menggunakan versi stabil dan dapat di   update via CDN atau manual.

          5. Instruksi Build dan Deployment   

Karena menggunakan PHP native, aplikasi ini tidak memerlukan proses build.

 Deployment:

1. Upload semua file ke server
2. Impor database ke server MySQL
3. Edit file koneksi db.php
4. Jalankan aplikasi via browser: http://ip   server/simple   inventory/

         

          6. Panduan Debugging dan Logging   

          Debugging:

•	Gunakan var_dump(), print_r() untuk cek variable
•	Aktifkan error_reporting(E_ALL) dan display_errors = On di php.ini
•	Gunakan console browser (DevTools) untuk melihat request

          Logging:

    Buat file log.txt untuk mencatat aktivitas penting
    Format log: [timestamp] LEVEL     pesan
    Contoh: 2025   06   18 10:00:01 INFO     User admin login berhasil

         

    

 7. Catatan Perubahan (Change Log)   

    Tanggal                     Modul                        Perubahan                               Oleh            
                                                                                                                                                                                                                    
    2025   06   17             Login       Menambahkan validasi form login         Akram Mulloh    
    2025   06   18            Barang      Tambah fitur filter kategori barang          Akram Mulloh    

         

8. Daftar Bug Dikenal   

ID     /      Modul   /   Deskripsi Bug      /                     Tingkat     Status  /       Solusi Sementara                                                                                                                                                                                                                                                                              
1.       / Login    /   Tidak ada alert saat login gagal /    Sedang /     Belum / Tambahkan script alert  /    
2.         Barang  /   Duplikasi data saat refresh   Rendah/      Fixed /     Cek keberadaan kode unik /  

         

   9. Saran Pengembangan / Peningkatan   

•	Tambahkan fitur filter berdasarkan kategori barang
•	Gunakan AJAX agar proses input tanpa reload halaman
•	Refactor struktur folder agar mengikuti pola MVC
•	Tambahkan unit testing (PHPUnit)
•	Siapkan pipeline CI/CD sederhana dengan GitHub Action
•	Dokumentasi tambahan untuk pengguna dan developer baru

         

       


   10. Lampiran   

    login.php
    dashboard.php
    data\_barang.php

          Kode penting:

php
// config/db.php (Koneksi)
$host = "localhost";
$user = "root";
$pass = "";
$db   = "inventory_db";
$conn = mysqli_connect($host, $user, $pass, $db);

// controllers/barang.php (Insert Barang)
if(isset($_POST['tambah'])){
  $nama = $_POST['nama'];
  $kode = $_POST['kode'];
  mysqli_query($conn, "INSERT INTO barang VALUES(NULL, '$kode', '$nama')");
}

// logging aktivitas login
file_put_contents("log.txt", "[".date('Y   m   d H:i:s')."] INFO     Login sukses\n", FILE_APPEND);


         


