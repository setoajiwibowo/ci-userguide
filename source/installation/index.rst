###################
Instruksi Instalasi
###################

CodeIgniter diinstal dalam empat langkah

#. Unzip paket.
#. Unggah folder CodeIgniter dan berkas ke server Anda. Biasanya File **index.php** akan berada di *root server* Anda.
#. Buka berkas **application/config/config.php** dengan editor teks dan aturlah *base URL* Anda. Jika Anda berniat untuk menggunakan enkripsi atau sesi, aturlah *encryption key* Anda.
#. Jika Anda berniat untuk menggunakan database, buka berkas **application/config/database.php** dengan editor teks dan aturlah pengaturan *database* Anda.

Jika Anda ingin meningkatkan keamanan dengan menyembunyikan lokasi 
file CodeIgniter Anda, Anda dapat mengubah nama folder *system* dan 
*application* menjadi sesuatu yang lebih pribadi. Jika Anda mengubah folder tersebut, 
Anda harus membuka file utama **index.php** Anda dan aturlah variabel **$system_path** 
dan **$application_folder** di atas file dengan nama baru yang Anda pilih.

Untuk keamanan terbaik, baik folder *system* dan *application*
harus ditempatkan di atas *web root* sehingga mereka tidak langsung dapat diakses
melalui *browser*. Secara default, file **.htaccess** yang termasuk dalam setiap folder
untuk membantu mencegah akses langsung, tapi yang terbaik adalah untuk menghapus mereka dari publik
Akses sepenuhnya dalam hal perubahan konfigurasi web server atau tidak dipatuhi oleh **.htaccess**.

Jika Anda ingin menjaga *views public* Anda, hal ini juga memungkinkan untuk memindahkan folder *views* dari folder *application* Anda.

Setelah memindah folder tersebut, bukalah file **index.php** utama Anda dan atur variabel
**$system_path**, **$application_folder** dan **$view_folder**,
sebaiknya dengan path lengkap, misalnya **/www/MyUser/system**.

Salah satu tolak ukur tambahan untuk berada di lingkungan produksi adalah untuk menonaktifkan
Pelaporan kesalahan PHP dan setiap fungsi pengembangan lainnya.  Di
CodeIgniter, ini dapat dilakukan dengan menetapkan konstan *ENVIRONMENT*, yang
lebih lengkap dijelaskan pada halaman :doc:`Keamanan
<../general/security>`.

Itu dia!

Jika Anda baru di CodeIgniter, silakan baca :doc:`Memulai <../overview/getting_started>` bagian dari Panduan Pengguna
untuk mulai belajar bagaimana membangun aplikasi PHP yang dinamis. Nikmatilah!

.. toctree::
	:hidden:
	:titlesonly:

	downloads
	self
	upgrading
	troubleshooting

