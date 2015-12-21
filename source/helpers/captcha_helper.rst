##############
CAPTCHA Helper
##############

File *CAPTCHA Helper* berisi fungsi yang membantu dalam menciptakan
gambar CAPTCHA.

.. contents::
  :local:

.. raw:: html

  <div class="custom-index container"></div>

Memuat Helper ini
=================

Helper ini dimuat menggunakan kode berikut::

	$this->load->helper('captcha');

Menggunakan CAPTCHA Helper
==========================

Setelah dimuat Anda dapat menghasilkan sebuah CAPTCHA seperti ini::

	$vals = array(
		'word'		=> 'Kata acak',
		'img_path'	=> './captcha/',
		'img_url'	=> 'http://example.com/captcha/',
		'font_path'	=> './path/to/fonts/texb.ttf',
		'img_width'	=> '150',
		'img_height'	=> 30,
		'expiration'	=> 7200,
		'word_length'	=> 8,
		'font_size'	=> 16,
		'img_id'	=> 'Imageid',
		'pool'		=> '0123456789abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ',

		// Latar belakang dan border berwarna putih, teks hitam dan grid merah
		'colors'	=> array(
			'background' => array(255, 255, 255),
			'border' => array(255, 255, 255),
			'text' => array(0, 0, 0),
			'grid' => array(255, 40, 40)
		)
	);

	$cap = create_captcha($vals);
	echo $cap['image'];

-  Fungsi captcha memerlukan *GD image library*.
-  Hanya **img_path** dan **img_url** yang dibutuhkan.
-  Jika **word** tidak diberikan, fungsi akan menghasilkan string ASCII acak. Anda mungkin mengumpulkan perpustakaan kata Anda sendiri bahwa Anda dapat menggambar secara acak.
-  Jika Anda tidak menentukan path untuk *TRUE TYPE font*, font GD jelek asli akan digunakan.
-  Direktori "captcha" harus dapat ditulis
-  **expiration** (dalam detik) menandakan berapa lama gambar akan tetap berada di captcha folder sebelum akan dihapus. Default adalah dua jam.
-  **word_length** defaultnya 8, **pool** defaultnya '0123456789abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ'
-  **font_size** defaultnya 16, font GD asli memiliki batas ukuran. Tentukan font "true type" untuk ukuran lebih besar.
-  **img_id** akan ditetapkan sebagai "id" dari gambar captcha.
-  Jika salah satu nilai **colors** hilang, itu akan digantikan oleh default.

Menambahkan Database
--------------------

Agar fungsi captcha untuk mencegah seseorang dari mengirimkan, Anda akan perlu menambahkan informasi kembali dari ``create_captcha()`` ke database Anda.  Kemudian, ketika data dari formulir dikirimkan oleh pengguna Anda akan perlu untuk memverifikasi bahwa data yang ada dalam database dan belum kedaluwarsa.

Berikut ini adalah prototipe tabel::

	CREATE TABLE captcha (  
		captcha_id bigint(13) unsigned NOT NULL auto_increment,  
		captcha_time int(10) unsigned NOT NULL,  
		ip_address varchar(45) NOT NULL,  
		word varchar(20) NOT NULL,  
		PRIMARY KEY `captcha_id` (`captcha_id`),  
		KEY `word` (`word`)
	);

Berikut adalah contoh penggunaan dengan database. Pada halaman di mana
CAPTCHA akan ditampilkan Anda akan memiliki sesuatu seperti ini::

	$this->load->helper('captcha');
	$vals = array(     
		'img_path'	=> './captcha/',     
		'img_url'	=> 'http://example.com/captcha/'     
	);

	$cap = create_captcha($vals);
	$data = array(     
		'captcha_time'	=> $cap['time'],     
		'ip_address'	=> $this->input->ip_address(),     
		'word'		=> $cap['word']     
	);

	$query = $this->db->insert_string('captcha', $data);
	$this->db->query($query);

	echo 'Submit kata yang Anda lihat di bawah:';
	echo $cap['image'];
	echo '<input type="text" name="captcha" value="" />';

Kemudian, pada halaman yang menerima pengajuan Anda akan memiliki sesuatu seperti ini::

	// First, delete old captchas
	$expiration = time() - 7200; // Batas dua jam
	$this->db->where('captcha_time < ', $expiration)
		->delete('captcha');

	// Kemudian lihat apakah captcha ada:
	$sql = 'SELECT COUNT(*) AS count FROM captcha WHERE word = ? AND ip_address = ? AND captcha_time > ?';
	$binds = array($_POST['captcha'], $this->input->ip_address(), $expiration);
	$query = $this->db->query($sql, $binds);
	$row = $query->row();

	if ($row->count == 0)
	{     
		echo 'Anda harus men-submit kata yang muncul dalam gambar.';
	}

Fungsi yang Tersedia
====================

Fungsi yang tersedia sebagai berikut:

.. php:function:: create_captcha([$data = ''[, $img_path = ''[, $img_url = ''[, $font_path = '']]]])

	:param	array	$data: Array data untuk CAPTCHA
	:param	string	$img_path: Path untuk membuat gambar
	:param	string	$img_url: URL ke folder gambar CAPTCHA
	:param	string	$font_path: Server path untuk font
	:returns:	array('word' => $word, 'time' => $now, 'image' => $img)
	:rtype:	array

	Mengambil informasi array untuk menghasilkan CAPTCHA sebagai masukan dan menciptakan gambar untuk spesifikasi Anda, kembali data array asosiatif tentang gambar.

	::

		array(
			'image'	=> IMAGE TAG
			'time'	=> TIMESTAMP (in microtime)
			'word'	=> CAPTCHA WORD
		)

	**image** ini sebenarnya gambar tag::

		<img src="http://example.com/captcha/12345.jpg" width="140" height="50" />

	**time** adalah timestamp mikro yang digunakan sebagai nama gambar tanpa ekstensi file.  Ini akan menjadi nomor seperti ini: 1139612155.3422

	**word** adalah kata yang muncul dalam gambar captcha, yang jika tidak diberikan ke fungsi, akan menjadi string acak.