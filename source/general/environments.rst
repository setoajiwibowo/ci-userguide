###############################
Penanganan Beberapa Environment
###############################

Pengembang sering menginginkan sistem perilaku yang berbeda tergantung pada apakah 
aplikasi berjalan dalam pengembangan atau produksi lingkungan. Sebagai contoh, 
keluaran kesalahan *verbose* adalah sesuatu yang akan berguna ketika mengembangkan 
sebuah aplikasi, tetapi juga dapat menimbulkan masalah keamanan ketika "live".

Konstan ENVIRONMENT
===================

Secara default, CodeIgniter dilengkapi dengan set konstan *environment* 
untuk menggunakan nilai yang diberikan di ``$_SERVER['CI_ENV']``, Jika tidak default menjadi 
'development'. Pada bagian atas **index.php**, Anda akan lihat::

	define('ENVIRONMENT', isset($_SERVER['CI_ENV']) ? $_SERVER['CI_ENV'] : 'development');

Variabel server ini dapat diatur dalam file .htaccess, atau Apache config menggunakan `SetEnv <https://httpd.apache.org/docs/2.2/mod/mod_env.html#setenv>`_. 
Metode alternatif tersedia untuk nginx dan server lain, atau Anda dapat menghilangkan 
logika ini sepenuhnya dan mengatur konstan berdasarkan alamat IP server.

Selain mempengaruhi beberapa perilaku framework (Lihat bagian berikutnya), 
Anda dapat menggunakan konstan ini dalam pengembangan Anda sendiri untuk 
membedakan antara lingkungan yang Anda jalankan.

Efek pada Perilaku Default Framework
====================================

Ada beberapa tempat di sistem CodeIgniter di mana konstan *ENVIRONMENT* digunakan. 
Bagian ini menjelaskan bagaimana perilaku default *framework* terpengaruh.

Pelaporan Kesalahan
-------------------

Mengatur konstan ENVIRONMENT untuk nilai 'development' akan menyebabkan semua kesalahan 
PHP yang akan diberikan ke browser ketika mereka terjadi.  Sebaliknya, pengaturan 
konstan untuk 'production' akan menonaktifkan semua keluaran kesalahan.
Menonaktifkan pelaporan kesalahan dalam produksi adalah sebuah :doc:`good security practice <security>`.

File Konfigurasi
-------------------

Opsional, Anda dapat memiliki file konfigurasi lingkungan spesifik CodeIgniter. Ini mungkin 
berguna untuk mengelola hal-hal seperti perbedaan kunci API di beberapa lingkungan.
Hal ini dijelaskan secara lebih rinci di bagian lingkungan dari dokumentasi :doc:`Konfigurasi Kelas
<../libraries/config>`.