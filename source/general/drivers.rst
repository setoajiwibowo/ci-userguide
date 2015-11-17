##############################
Menggunakan Driver CodeIgniter
##############################

Driver adalah tipe khusus dari library yang memiliki kelas induk dan sejumlah 
potensi anak kelas. Anak kelas memiliki akses ke Induk kelas, tetapi tidak 
saudara kandung mereka. Drivers provide an elegant syntax in  :doc:`controllers <controllers>` 
untuk *library* yang memanfaatkan atau memerlukan yang dibagi ke dalam kelas-kelas diskrit.

*Drivers* ditemukan di direktori *system/libraries/*, di sub-direktori mereka sendiri yang 
dinamai identik dengan kelas library induk. Juga di dalam direktori tersebut ada 
subdirektori bernama driver, yang berisi semua file kelas mungkin anak.

Untuk menggunakan driver Anda akan menginisialisasinya di dalam controller 
menggunakan metode inisialisasi berikut::

	$this->load->driver('class_name');

Di mana nama kelas adalah nama dari kelas driver yang Anda ingin memohon.  
Misalnya, untuk memuat driver bernama "Some_parent" Anda akan melakukan ini::

	$this->load->driver('some_parent');

Metode kelas yang kemudian dapat dipanggil dengan::

	$this->some_parent->some_method();

Kelas anak, driver sendiri, maka dapat disebut langsung melalui kelas induk, 
tanpa menginisialisasi mereka::

	$this->some_parent->child_one->some_method();
	$this->some_parent->child_two->another_method();

Membuat Driver Anda Sendiri
===========================

Silakan baca bagian dari panduan pengguna yang membahas bagaimana :doc:`membuat driver anda sendiri <creating_drivers>`.