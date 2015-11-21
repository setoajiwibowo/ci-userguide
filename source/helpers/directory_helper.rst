################
Directory Helper
################

File *Directory Helper* berisi fungsi yang membantu dalam bekerja dengan direktori.

.. contents::
  :local:

.. raw:: html

  <div class="custom-index container"></div>

Memuat Helper ini
=================

Helper ini dimuat menggunakan kode berikut::

	$this->load->helper('directory');

Fungsi yang Tersedia
====================

Fungsi yang tersedia sebagai berikut:


.. php:function:: directory_map($source_dir[, $directory_depth = 0[, $hidden = FALSE]])

	:param	string	$source_dir: Path ke sumber direktori
	:param	int	$directory_depth: Kedalaman direktori untuk melintasi (0 = sepenuhnya rekursif, 1 = direktori saat ini, dll)
	:param	bool	$hidden: Apakah akan menyertakan direktori tersembunyi
	:returns:	Sebuah array file
	:rtype:	array

	Contoh::

		$map = directory_map('./mydirectory/');

	.. note:: *Paths* hampir selalu relatif terhadap file **index.php** utama Anda.


	Sub-folder yang ada di direktori akan dipetakan juga. Jika Anda ingin mengontrol 
	kedalaman rekursi, Anda dapat melakukannya dengan menggunakan parameter kedua (integer).
	Sebuah kedalaman 1 hanya akan memetakan direktori tingkat atas::

		$map = directory_map('./mydirectory/', 1);

	Secara default, file yang tersembunyi tidak akan dimasukkan dalam array kembali.
	Untuk mengubah perilaku ini, Anda dapat menetapkan parameter ketiga ke *true* (boolean)::

		$map = directory_map('./mydirectory/', FALSE, TRUE);

	Setiap nama folder akan menjadi indeks array, sementara file yang terkandung yang akan 
	diindeks secara numerik. Berikut adalah contoh dari array khas::

		Array (
			[libraries] => Array
				(
					[0] => benchmark.html
					[1] => config.html
					["database/"] => Array
						(
							[0] => query_builder.html
							[1] => binds.html
							[2] => configuration.html
							[3] => connecting.html
							[4] => examples.html
							[5] => fields.html
							[6] => index.html
							[7] => queries.html
						)
					[2] => email.html
					[3] => file_uploading.html
					[4] => image_lib.html
					[5] => input.html
					[6] => language.html
					[7] => loader.html
					[8] => pagination.html
					[9] => uri.html
				)