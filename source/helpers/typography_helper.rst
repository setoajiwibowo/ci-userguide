#################
Typography Helper
#################

File *Typography Helper* berisi fungsi yang membantu memformat teks Anda dengan cara-cara 
yang relevan secara semantik.

.. contents::
  :local:

.. raw:: html

  <div class="custom-index container"></div>

Memuat Helper ini
=================

Helper ini dimuat menggunakan kode berikut::

	$this->load->helper('typography');

Fungsi yang Tersedia
====================

Fungsi yang tersedia sebagai berikut:


.. php:function:: auto_typography($str[, $reduce_linebreaks = FALSE])

	:param	string	$str: Masukan string
	:param	bool	$reduce_linebreaks: Apakah akan mengurangi beberapa contoh baris ganda menjadi dua
	:returns:	HTML-formatted typography-safe string
	:rtype: string

	Memformat teks sehingga secara semantik dan tipografi adalah HTML yang benar

	Fungsi ini adalah alias untuk ``CI_Typography::auto_typography``.
	Untuk info lebih lanjut, silakan lihat dokumentasi :doc:`Typography Library
	<../libraries/typography>`.

	Contoh penggunaan::

		$string = auto_typography($string);

	.. note:: Format tipografi dapat membuat prosesor intensif, terutama jika Anda memiliki 
		banyak konten yang diformat.  Jika Anda memilih untuk menggunakan fungsi ini 
		Anda mungkin ingin mempertimbangkan `caching <../general/caching>` halaman anda.


.. php:function:: nl2br_except_pre($str)

	:param	string	$str: Masukan string
	:returns:	String with HTML-formatted line breaks
	:rtype:	string

	Mengkonversi baris ke tag <br /> kecuali mereka muncul dalam tag <pre>.
	Fungsi ini identik dengan fungsi *native PHP* ``nl2br()``,
	kecuali bahwa itu mengabaikan tag <pre>.

	Contoh penggunaan::

		$string = nl2br_except_pre($string);

.. php:function:: entity_decode($str, $charset = NULL)

	:param	string	$str: Masukkan string
	:param	string	$charset: Set karakter
	:returns:	String dengan entitas HTML didekode
	:rtype:	string

	Fungsi ini adalah alias untuk ``CI_Security::entity_decode()``.
	Untuk info lebih lanjut, silakan lihat dokumentasi :doc:`Security Library
	<../libraries/security>`.