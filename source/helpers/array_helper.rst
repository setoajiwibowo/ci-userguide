############
Array Helper
############

File Array Helper berisi fungsi yang membantu dalam bekerja dengan array.

.. contents::
  :local:

.. raw:: html

  <div class="custom-index container"></div>

Memuat Helper ini
=================

Helper ini dimuat menggunakan kode berikut::

	$this->load->helper('array');


Fungsi yang Tersedia
====================

Fungsi yang tersedia sebagai berikut:


.. php:function:: element($item, $array[, $default = NULL])

	:param	string	$item: Item untuk mengambil dari array
	:param	array	$array: Masukan array
	:param	bool	$default: Apa yang harus kembali jika array tidak valid
	:returns:	NULL pada kegagalan array item.
	:rtype:	campur

	Memungkinkan Anda mengambil item dari array.  Fungsi ini melakukan tes apakah 
	indeks array diatur dan apakah itu memiliki nilai. Jika nilai ada itu dikembalikan.  
	Jika nilai tidak ada itu kembali NULL, atau apa pun yang Anda ditetapkan 
	sebagai nilai default melalui parameter ketiga.

	Contoh::

		$array = array(
			'warna'	=> 'merah',
			'bentuk'	=> 'bulat',
			'ukuran'	=> ''
		);

		echo element('warna', $array); // kembali "merah"
		echo element('ukuran', $array, 'foobar'); // kembali "foobar"


.. php:function:: elements($items, $array[, $default = NULL])

	:param	string	$item: Item untuk mengambil dari array
	:param	array	$array: Masukan array
	:param	bool	$default:  Apa yang harus kembali jika array tidak valid
	:returns:	NULL pada kegagalan array item.
	:rtype:	campur

	Memungkinkan Anda mengambil sejumlah item dari array. Fungsi ini melakukan tes 
	apakah masing-masing indeks array sudah diatur. Jika indeks tidak ada diatur ke NULL, 
	atau apa pun yang Anda ditetapkan sebagai nilai default melalui parameter ketiga.

	Contoh::

		$array = array(
			'warna' => 'merah',
			'bentuk' => 'bulat',
			'radius' => '10',
			'diameter' => '20'
		);

		$my_shape = elements(array('warna', 'bentuk', 'tinggi'), $array);

	Di atas akan mengembalikan array berikut::

		array(
			'warna' => 'merah',
			'bentuk' => 'bulat',
			'tinggi' => NULL
		);

	Anda dapat mengatur parameter ketiga untuk setiap nilai default yang Anda suka.
	::

		 $my_shape = elements(array('warna', 'bentuk', 'tinggi'), $array, 'foobar');

	Di atas akan mengembalikan array berikut::

		array(     
			'warna' 	=> 'merah',
			'bentuk' 	=> 'bulat',
			'tinggi'	=> 'foobar'
		);

	Hal ini berguna ketika mengirim ``$_POST`` array ke salah satu Model Anda.  Ini mencegah pengguna mengirimkan data POST tambahan yang akan dimasukkan ke dalam tabel Anda.

	::

		$this->load->model('post_model');
		$this->post_model->update(
			elements(array('id', 'judul', 'isi'), $_POST)
		);

	Hal ini memastikan bahwa hanya id, judul dan isi yang dikirim untuk diperbarui.


.. php:function:: random_element($array)

	:param	array	$array: Masukan array
	:returns:	Unsur acak dari array
	:rtype:	campur

	Membawa sebuah array sebagai masukan dan mengembalikan elemen acak dari itu.

	Contoh penggunaan::

		$quotes = array(
			"Saya menemukan bahwa semakin keras saya bekerja, semakin keberuntungan saya tampaknya memiliki. - Thomas Jefferson",
			"Tidak tinggal di tempat tidur, kecuali Anda dapat membuat uang di tempat tidur. - George Burns",
			"Kami tidak kehilangan permainan, kami hanya kehabisan waktu. - Vince Lombardi",
			"Jika semuanya tampak di bawah kontrol, Anda tidak akan cukup cepat. - Mario Andretti ",
			"Realitas hanyalah ilusi, meskipun yang sangat gigih. - Albert Einstein",
			"Kesempatan nikmat pikiran disiapkan. - Louis Pasteur"
		);

		echo random_element($quotes);