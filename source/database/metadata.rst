########################
Metadata dari Basis Data
########################

**************
Tabel MetaData
**************

Fungsi-fungsi ini memungkinkan Anda mengambil informasi tabel.

Daftar Tabel dalam Basis Data Anda
==================================

**$this->db->list_tables();**

Mengembalikan array yang berisi nama-nama dari semua tabel dalam database yang 
sedang Anda hubungkan. Contoh::

	$tables = $this->db->list_tables();
	
	foreach ($tables as $table)
	{
		echo $table;
	}


Menentukan apakah tabel ada
===========================

**$this->db->table_exists();**

Kadang-kadang membantu untuk mengetahui apakah tabel tertentu ada sebelum menjalankan operasi di atasnya.  Mengembalikan *boolean TRUE/FALSE*. Contoh penggunaan::

	if ($this->db->table_exists('table_name'))
	{
		// beberapa kode...
	}

.. note:: Ganti *table_name* dengan nama tabel yang Anda cari.


***************
Bidang metadata
***************

Daftar Bidang di Tabel
======================

**$this->db->list_fields()**

Mengembalikan array yang berisi nama field. Kueri ini bisa dipanggil dua cara:

1. Anda dapat menyediakan nama tabel dan menyebutnya dari obyek $this->db->::

	$fields = $this->db->list_fields('table_name');
	
	foreach ($fields as $field)
	{
		echo $field;
	}

2. Anda dapat mengumpulkan nama bidang yang terkait dengan kueri yang Anda jalankan 
dengan memanggil fungsi dari hasil objek kueri Anda::

	$query = $this->db->query('SELECT * FROM some_table');
	
	foreach ($query->list_fields() as $field)
	{
		echo $field;
	}


Menentukan Jika sebuah Bidang ada dalam Tabel
=============================================

**$this->db->field_exists()**

Kadang-kadang ini membantu untuk mengetahui apakah bidang tertentu ada sebelum 
melakukan suatu tindakan.  Mengembalikan *boolean TRUE/FALSE*. Contoh penggunaan::

	if ($this->db->field_exists('field_name', 'table_name'))
	{
		// beberapa kode...
	}

.. note:: Ganti *field_name* dengan nama kolom yang Anda cari, dan ganti *table_name* 
dengan nama tabel yang Anda cari.


Mengambil Bidang Metadata
=========================

**$this->db->field_data()**

Mengembalikan array objek yang berisi informasi bidang.

Kadang-kadang ini membantu untuk mengumpulkan nama bidang atau metadata lainnya, seperti jenis kolom, panjang maksimal, dll.

.. note:: Tidak semua database menyediakan metadata.

Contoh Penggunaan::

	$fields = $this->db->field_data('table_name');
	
	foreach ($fields as $field)
	{
		echo $field->name;
		echo $field->type;
		echo $field->max_length;
		echo $field->primary_key;
	}

Jika Anda telah menjalankan kueri Anda dapat menggunakan obyek hasil bukannya 
memasok nama tabel::

	$query = $this->db->query("YOUR QUERY");
	$fields = $query->field_data();

Data berikut tersedia dari fungsi ini yang didukung oleh basis data Anda:

-  name - nama kolom
-  max_length - panjang maksimum kolom
-  primary_key - 1 jika kolom adalah kunci utama
-  type - jenis kolom