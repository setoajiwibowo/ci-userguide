#############
Number Helper
#############

File *Number Helper* berisi fungsi yang membantu Anda bekerja dengan data numerik.

.. contents::
  :local:

.. raw:: html

  <div class="custom-index container"></div>

Memuat Helper ini
=================

Helper ini dimuat menggunakan kode berikut::

	$this->load->helper('number');

Fungsi yang Tersedia
====================

Fungsi yang tersedia sebagai berikut:


.. php:function:: byte_format($num[, $precision = 1])

	:param	mixed	$num: Angka byte
	:param	int	$precision: Presisi floating point
	:returns:	Data terformat ukuran string
	:rtype:	string

	Format nomor sebagai byte, berdasarkan ukuran, dan menambahkan akhiran yang sesuai. Contoh::

		echo byte_format(456); // Kembali 456 Bytes
		echo byte_format(4567); // Kembali 4.5 KB
		echo byte_format(45678); // Kembali 44.6 KB
		echo byte_format(456789); // Kembali 447.8 KB
		echo byte_format(3456789); // Kembali 3.3 MB
		echo byte_format(12345678912345); // Kembali 1.8 GB
		echo byte_format(123456789123456789); // Kembali 11,228.3 TB

	Parameter opsional kedua memungkinkan Anda untuk mengatur presisi hasil::

		 echo byte_format(45678, 2); // Kembali 44.61 KB

	.. note:: Teks yang dihasilkan oleh fungsi ini ditemukan dalam file bahasa berikut: *language/<your_lang>/number_lang.php*