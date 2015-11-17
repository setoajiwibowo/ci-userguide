##########
XML Helper
##########

File *XML Helper* berisi fungsi yang membantu dalam bekerja dengan data XML.

.. contents::
  :local:

.. raw:: html

  <div class="custom-index container"></div>

Memuat Helper ini
=================

Helper ini dimuat menggunakan kode berikut

::

	$this->load->helper('xml');

Fungsi yang Tersedia
====================

Fungsi yang tersedia sebagai berikut:

.. php:function:: xml_convert($str[, $protect_all = FALSE])

	:param string $str: teks string untuk mengkonversi
	:param bool $protect_all: Apakah melindungi semua konten yang terlihat seperti sebuah entitas potensial bukan entitas yang hanya nomor, misalnya  &foo;
	:returns: String yang dikonversi ke XML
	:rtype:	string

	Mengambil string sebagai masukan dan ubah karakter *reserved* XML berikut untuk entitas:

	  - Ampersands: &
	  - Karakter kurang dari dan lebih besar dari: < >
	  - Tanda kutip tunggal dan ganda: ' "
	  - Tanda garis: -

	Fungsi ini mengabaikan *ampersands* jika mereka adalah bagian dari 
	entitas karakter bernomor yang ada , misalnya &#123;. Contoh::

		$string = '<p>Di sini adalah sebuah paragraf & entitas (&#123;).</p>';
		$string = xml_convert($string);
		echo $string;

	outputs:

	.. code-block:: html

		&lt;p&gt;Di sini adalah sebuah paragraf &amp; entitas (&#123;).&lt;/p&gt;