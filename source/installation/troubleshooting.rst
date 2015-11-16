#################
Pemecahan Masalah
#################

Jika Anda menemukan bahwa apapun yang Anda masukkan ke dalam URL Anda hanya halaman default
Anda sedang loading, itu mungkin bahwa server Anda tidak mendukung variabel *REQUEST_URI* 
yang diperlukan untuk melayani *search-engine friendly URLs*. Sebagai langkah pertama, buka file
**application/config/config.php** Anda dan cari *URI Protocol information*. Itu akan merekomendasikan
bahwa Anda mencoba beberapa alternatif pengaturan. Jika masih tidak bekerja setelah Anda sudah
mencoba ini Anda akan perlu untuk memaksa CodeIgniter untuk menambahkan tanda tanya ke URL Anda. 
Untuk melakukan ini buka file **application/config/config.php** anda dan ubah ini::

	$config['index_page'] = "index.php";

Menjadi::

	$config['index_page'] = "index.php?";
