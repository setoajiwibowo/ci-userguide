########################
Auto-loading Sumber Daya
########################

CodeIgniter dilengkapi dengan fitur "Auto-load" yang mengijinkan *library*, *helper*,
dan *model* diinisialisasi secara otomatis setiap kali sistem berjalan.  
Jika Anda membutuhkan sumber daya tertentu secara global di seluruh aplikasi Anda, 
Anda harus mempertimbangkan fitur *auto-loading* untuk kenyamanan.

Item berikut dapat dimuat secara otomatis:

-  *Classes* ditemukan di direktori *libraries/*
-  File *Helper* ditemukan di direktori *helpers/*
-  File *Custom config* ditemukan di direktori *config/*
-  File *Language* ditemukan di direktori *system/language/*
-  *Models* ditemukan di direktori *models/*

Untuk melakukan *autoload* sumber daya, buka file **application/config/autoload.php**
dan tambahkan item yang ingin dimuat ke *array autoload*.  Anda akan menemukan petunjuk 
dalam file yang sesuai untuk setiap jenis item.

.. note:: Jangan masukkan ekstensi file (.php) ketika menambahkan item ke *array autoload*.

Selain itu, jika Anda ingin CodeIgniter menggunakan sebuah `Composer <https://getcomposer.org/>`_
*auto-loader*, hanya atur ``$config['composer_autoload']`` menjadi ``TRUE`` atau
sebuah *custom path* di **application/config/config.php**.