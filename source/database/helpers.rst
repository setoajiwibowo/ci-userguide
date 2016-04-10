###################
Metode Kueri Helper
###################

Informasi Dari Mengeksekusi sebuah Kueri
========================================

**$this->db->insert_id()**

Nomor ID masukan saat melakukan sisipan basis data.

.. note:: Jika menggunakan driver PDO dengan PostgreSQL atau menggunakan driver Interbase fungsi ini memerlukan parameter *$name* yang menentukan urutan yang tepat untuk memeriksa *insert id*.

**$this->db->affected_rows()**

Menampilkan jumlah baris yang terkena dampak ketika melakukan "write" 
jenis kueri(insert, update dll).

.. note:: Di dalam MySQL "DELETE FROM TABLE" mengembalikan 0 baris yang terkena. Kelas basis data memiliki *hack* kecil yang memungkinkan untuk mengembalikan jumlah yang benar baris yang terkena dampak. Secara default *hack* ini diaktifkan tetapi dapat dimatikan dalam berkas driver basis data.

**$this->db->last_query()**

Mengembalikan kueri terakhir yang dijalankan (string bukan hasilnya).
Contoh::

	$str = $this->db->last_query();
	
	// Menghasilkan:  SELECT * FROM sometable....


.. note:: Menonaktifkan **save_queries** pengaturan dalam konfigurasi basis data Anda yang akan membuat fungsi ini tidak berguna.

Informasi Tentang Basis Data Anda
=================================

**$this->db->count_all()**

Memungkinkan Anda untuk menentukan jumlah baris dalam tabel tertentu.
Kirim nama tabel di parameter pertama. Contoh::

	echo $this->db->count_all('my_table');
	
	// Menghasilkan sebuah integer, seperti 25

**$this->db->platform()**

Keluaran platform basis data yang Anda jalankan (MySQL, MS SQL, Postgres,
dll...)::

	echo $this->db->platform();

**$this->db->version()**

Keluaran versi basis data yang Anda jalankan::

	echo $this->db->version();

Membuat Kueri Anda Lebih Mudah
==============================

**$this->db->insert_string()**

Fungsi ini menyederhanakan proses menulis sisipan basis data. Itu
mengembalikan string SQL insert yang diformat dengan benar. Contoh::

	$data = array('name' => $name, 'email' => $email, 'url' => $url);
	
	$str = $this->db->insert_string('table_name', $data);

Parameter pertama adalah nama tabel, yang kedua adalah asosiatif
array dengan data yang dimasukkan. Contoh di atas menghasilkan::

	INSERT INTO table_name (name, email, url) VALUES ('Rick', 'rick@example.com', 'example.com')

.. note:: Nilai-nilai secara otomatis lolos, memproduksi kueri lebih aman.

**$this->db->update_string()**

Fungsi ini menyederhanakan proses menulis update basis data. Itu
mengembalikan sebuah string update SQL yang diformat dengan benar. Contoh::

	$data = array('name' => $name, 'email' => $email, 'url' => $url);
	
	$where = "author_id = 1 AND status = 'active'";
	
	$str = $this->db->update_string('table_name', $data, $where);

Parameter pertama adalah nama tabel, yang kedua adalah asosiatif
array dengan data yang akan diperbarui, dan parameter ketiga klausa
"where". Contoh di atas menghasilkan::

	 UPDATE table_name SET name = 'Rick', email = 'rick@example.com', url = 'example.com' WHERE author_id = 1 AND status = 'active'

.. note:: Nilai-nilai secara otomatis lolos, memproduksi kueri lebih aman.