###############
Security Helper
###############

File *Security Helper* berisi fungsi keamanan terkait.

.. contents::
  :local:

.. raw:: html

  <div class="custom-index container"></div>

Memuat Helper ini
=================

Helper ini dimuat menggunakan kode berikut::

	$this->load->helper('security');

Fungsi yang Tersedia
====================

Fungsi yang tersedia sebagai berikut:


.. php:function:: xss_clean($str[, $is_image = FALSE])

	:param	string	$str: Masukan data
	:param	bool	$is_image: Apakah kita sedang berhadapan dengan gambar
	:returns:	XSS-clean string
	:rtype:	string

	Memberikan penyaringan *Cross Site Script Hack*.

	Fungsi ini adalah alias untuk ``CI_Input::xss_clean()``. Untuk info lebih lanjut, 
	silakan lihat dokumentasi :doc:`Input Library <../libraries/input>`.

.. php:function:: sanitize_filename($filename)

	:param	string	$filename: Nama file
	:returns:	Nama file yang dibersihkan
	:rtype:	string

	Memberikan perlindungan terhadap direktori traversal.

	Fungsi ini adalah alias untuk ``CI_Security::sanitize_filename()``.
	Untuk info lebih lanjut, silakan lihat dokumentasi :doc:`Security Library <../libraries/security>`.


.. php:function:: do_hash($str[, $type = 'sha1'])

	:param	string	$str: Masukan
	:param	string	$type: Algoritma
	:returns:	Hex-formatted hash
	:rtype:	string

	Memungkinkan Anda untuk membuat salah satu cara *hash* yang cocok untuk mengenkripsi password. 
	Akan menggunakan SHA1 secara default.

	Lihat `hash_algos() <http://php.net/function.hash_algos>`_
	untuk daftar lengkap dari algoritma yang didukung.

	Contoh::

		$str = do_hash($str); // SHA1
		$str = do_hash($str, 'md5'); // MD5

	.. note:: Fungsi ini sebelumnya bernama ``dohash()``, yang telah dihapus dalam mendukung ``do_hash()``.

	.. note:: Fungsi ini sudah ditinggalkan. Gunakan native ``hash()``


.. php:function:: strip_image_tags($str)

	:param	string	$str: Masukan string
	:returns:	Input string dengan tidak ada tag gambar
	:rtype:	string

	Ini adalah fungsi keamanan yang akan men-strip tag gambar dari string.  
	Ia meninggalkan URL gambar sebagai teks biasa.

	Contoh::

		$string = strip_image_tags($string);

	Fungsi ini adalah alias untuk ``CI_Security::strip_image_tags()``. 
	Untuk info lebih lanjut, silakan lihat dokumentasi :doc:`Security Library <../libraries/security>`.


.. php:function:: encode_php_tags($str)

	:param	string	$str: Masukan string
	:returns:	Safely formatted string
	:rtype:	string

	Ini adalah fungsi keamanan yang mengubah tag PHP untuk entitas.

	.. note:: :php:func:`xss_clean()` melakukan ini secara otomatis, jika Anda menggunakannya.

	Contoh::

		$string = encode_php_tags($string);