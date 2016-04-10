###################################
Memulai Cepat Database: Contoh Kode
###################################

Halaman berikut berisi contoh kode yang menunjukkan bagaimana kelas basis data digunakan.
Untuk rincian lengkap silahkan baca halaman individual yang menjelaskan 
fungsi masing-masing.

Menginisialisasi Kelas Basis Data
=================================

Berikut kode untuk me-load dan menginisialisasi kelas basis data berdasarkan 
pengaturan :doc:`konfigurasi <configuration>` anda::

	$this->load->database();

Setelah dimuat kelas siap untuk digunakan seperti yang dijelaskan di bawah.

Catatan: Jika semua halaman Anda memerlukan akses basis data Anda dapat terhubung secara otomatis. Lihat halaman :doc:`menghubungkan <connecting>` untuk rinciannya.

Kueri standar Dengan Beberapa Hasil (Versi Objek)
=================================================

::

	$query = $this->db->query('SELECT name, title, email FROM my_table');
	
	foreach ($query->result() as $row)
	{
		echo $row->title;
		echo $row->name;
		echo $row->email;
	}
	
	echo 'Total Hasil: ' . $query->num_rows();

Fungsi result() di atas mengembalikan sebuah array dari **objek**. Contoh:
$row->title

Kueri standar Dengan Beberapa Hasil (Versi Array)
=================================================

::

	$query = $this->db->query('SELECT name, title, email FROM my_table');
	
	foreach ($query->result_array() as $row)
	{
		echo $row['title'];
		echo $row['name'];
		echo $row['email'];
	}

Fungsi result_array() di atas mengembalikan sebuah array dari indeks array standar. 
Contoh: $row['title']

Kueri Standar Dengan Hasil Tunggal
==================================

::

	$query = $this->db->query('SELECT name FROM my_table LIMIT 1'); 
	$row = $query->row();
	echo $row->name;

Fungsi row() di atas mengembalikan sebuah **objek**. Contoh: $row->name

Kueri Standar Dengan Hasil Tunggal (Versi Array)
================================================

::

	$query = $this->db->query('SELECT name FROM my_table LIMIT 1');
	$row = $query->row_array();
	echo $row['name'];

Fungsi row_array() di atas mengembalikan sebuah **array**. Contoh:
$row['name']

Standard Masukan
=================

::

	$sql = "INSERT INTO mytable (title, name) VALUES (".$this->db->escape($title).", ".$this->db->escape($name).")";
	$this->db->query($sql);
	echo $this->db->affected_rows();

Kueri Pembangun Kueri
=====================

Sebuah :doc:`Pola Pembangun Kueri <query_builder>` memberi Anda cara sederhana 
mengambil data::

	$query = $this->db->get('table_name');
	
	foreach ($query->result() as $row)
	{
		echo $row->title;
	}

Fungsi get() di atas mengambil semua hasil dari tabel yang disediakan. 
Sebuah kelas :doc:`Pembangun Kueri <query_builder>` berisi pujian penuh fungsi 
untuk bekerja dengan data.

Pembangun Kueri Masukan
=======================

::

	$data = array(
		'title' => $title,
		'name' => $name,
		'date' => $date
	);
	
	$this->db->insert('mytable', $data);  // Produces: INSERT INTO mytable (title, name, date) VALUES ('{$title}', '{$name}', '{$date}')

