#######################
Panggilan Kustom Fungsi
#######################

$this->db->call_function();
============================

Fungsi ini memungkinkan Anda untuk memanggil fungsi basis data PHP yang tidak 
native termasuk dalam CodeIgniter dengan cara platform independen. 
Sebagai contoh katakanlah Anda ingin memanggil fungsi mysql_get_client_info() 
yang **tidak** native didukung oleh CodeIgniter. 
Anda bisa melakukannya seperti ini::

	$this->db->call_function('get_client_info');

Anda harus menyediakan nama fungsi **tanpa** awalan mysql\_ di parameter pertama. 
Awalan ditambahkan secara otomatis berdasarkan driver basis data saat ini yang 
sedang digunakan. Hal ini memungkinkan Anda untuk menjalankan fungsi yang sama 
pada platform basis data yang berbeda. Tidak semua panggilan fungsi yang 
identik antara platform jadi ada batas untuk berapa berguna fungsi ini bisa 
dalam hal portabilitas.

Parameter yang dibutuhkan oleh fungsi yang Anda panggil akan ditambahkan ke parameter kedua.

::

	$this->db->call_function('some_function', $param1, $param2, dll..);

Seringkali Anda akan perlu untuk menyediakan ID koneksi basis data atau ID hasil
basis data. ID koneksi dapat diakses menggunakan::

	$this->db->conn_id;

Hasil ID dapat diakses dari dalam objek hasil Anda seperti ini::

	$query = $this->db->query("SOME QUERY");
	
	$query->result_id;