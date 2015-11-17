###############################
Menggunakan Library CodeIgniter
###############################

Semua *library* yang tersedia berada dalam direktori *system/libraries/* Anda.  
Dalam kebanyakan kasus, untuk menggunakan salah satu dari kelas-kelas ini 
melibatkan menginisialisasinya dalam :doc:`controller <controllers>` 
menggunakan metode inisialisasi berikut::

	$this->load->library('class_name');

Dimana 'class_name' adalah nama dari kelas yang Anda ingin memohon. Sebagai contoh, 
untuk memuat :doc:`Library Form Validation 
<../libraries/form_validation>` Anda akan melakukan ini::

	$this->load->library('form_validation');

Setelah diinisialisasi Anda dapat menggunakannya seperti yang ditunjukkan 
di halaman buku petunjuk yang sesuai dengan kelas itu.

Selain itu, beberapa *library* dapat dimuat pada saat yang sama dengan melewati 
sebuah *array library* dengan metode *load*.

Contoh::

	$this->load->library(array('email', 'table'));

Membuat Library Anda Sendiri
============================

Silakan baca bagian dari panduan pengguna yang membahas bagaimana
:doc:`membuat library anda sendiri <creating_libraries>`.