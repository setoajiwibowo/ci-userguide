#############
Smiley Helper
#############

File *Smiley Helper* berisi fungsi yang memungkinkan Anda mengelola *smiley*
(emoticon).

.. important:: *Smiley Helper* sudah ditinggalkan dan tidak boleh digunakan. Saat ini hanya disimpan untuk kompatibilitas mundur.

.. contents::
  :local:

.. raw:: html

  <div class="custom-index container"></div>

Memuat Helper ini
=================

Helper ini dimuat menggunakan kode berikut::

	$this->load->helper('smiley');

Ikhtisar
========

*Smiley Helper* memiliki penyaji yang mengambil smiley teks biasa seperti :-) dan mengubahnya menjadi representasi gambar seperti |smile!|

Hal ini juga memungkinkan Anda menampilkan serangkaian gambar smiley yang ketika diklik akan dimasukkan ke dalam bentuk bidang.  Misalnya jika Anda memiliki blog yang memungkinkan pengguna mengomentari Anda dapat menunjukkan smiley sebelah formulir komentar. Pengguna Anda dapat mengklik smiley yang diinginkan dan dengan bantuan beberapa JavaScript itu akan ditempatkan ke dalam bidang bentuk.

Tutorial Smiley dapat Diklik
============================

Berikut adalah contoh yang menunjukkan bagaimana Anda dapat membuat satu set diklik Smiley di bidang formulir. Contoh ini memerlukan bahwa Anda pertama download dan menginstal gambar smiley, kemudian membuat controller dan view seperti yang dijelaskan.

.. important:: Sebelum Anda mulai, silahkan `mengunduh gambar smiley
	<https://ellislab.com/asset/ci_download_files/smileys.zip>`_
	dan menempatkan mereka di tempat yang dapat diakses publik pada server Anda.  Helper ini juga mengasumsikan Anda memiliki array pengganti smiley terletak di `application/config/smileys.php`

Controller
----------

Di direktori **application/controllers/** anda, buatlah file bernama
Smileys.php dan tempatkan kode di bawah ini di dalamnya.

.. important:: Mengubah URL di fungsi :php:func:`get_clickable_smileys()`
	di bawah sehingga menunjuk ke folder smiley Anda.

Anda akan melihat bahwa selain *smiley helper* kami juga menggunakan :doc:`Table Class <../libraries/table>`::

	<?php

	class Smileys extends CI_Controller {

		public function index()
		{
			$this->load->helper('smiley');
			$this->load->library('table');

			$image_array = get_clickable_smileys('http://example.com/images/smileys/', 'comments');
			$col_array = $this->table->make_columns($image_array, 8);

			$data['smiley_table'] = $this->table->generate($col_array);
			$this->load->view('smiley_view', $data);
		}

	}

Di direktori **application/views/** anda, buatlah file bernama **smiley_view.php**
dan tempatkan kode ini di dalamnya::

	<html>
		<head>
			<title>Smileys</title>
			<?php echo smiley_js(); ?>
		</head>
		<body>
			<form name="blog">
				<textarea name="comments" id="comments" cols="40" rows="4"></textarea>
			</form>
			<p>Klik untuk menyisipkan smiley!</p>
			<?php echo $smiley_table; ?> </body> </html>
			Ketika Anda telah menciptakan controller di atas dan memuatnya dengan mengunjungi http://www.example.com/index.php/smileys/
		</body>
	</html>

Bidang Alias
------------

Ketika membuat perubahan view itu dapat nyaman untuk memiliki bidang id di controller.  Untuk menyiasatinya Anda dapat memberikan smiley Anda menghubungkan nama generik yang akan terikat dengan id tertentu dalam view Anda.

::

	$image_array = get_smiley_links("http://example.com/images/smileys/", "comment_textarea_alias");

Untuk memetakan alias untuk bidang id melewati mereka berdua ke fungsi
:func:`smiley_js()` ::

	$image_array = smiley_js("comment_textarea_alias", "comments");

Fungsi yang Tersedia
====================

.. php:function:: get_clickable_smileys($image_url[, $alias = ''[, $smileys = NULL]])

	:param	string	$image_url: Path URL ke direktori smiley
	:param	string	$alias: Bidang alias
	:returns:	Array siap untuk menggunakan smiley
	:rtype:	array

	Mengembalikan array yang berisi gambar smiley Anda dibungkus link yang dapat diklik.  Anda harus menyediakan URL ke folder smiley dan bidang id atau bidang alias.

	Contoh::

		$image_array = get_clickable_smileys('http://example.com/images/smileys/', 'comment');

.. php:function:: smiley_js([$alias = ''[, $bidang_id = ''[, $inline = TRUE]]])

	:param	string	$alias: Bidang alias
	:param	string	$bidang_id: Bidang ID
	:param	bool	$inline: Apakah kita sedang memasukkan smiley inline
	:returns:	Smiley-enabling JavaScript code
	:rtype:	string

	Menghasilkan JavaScript yang memungkinkan gambar diklik dan dimasukkan ke dalam bidang formulir. Jika Anda berikan alias bukan id ketika menghasilkan link smiley Anda, Anda perlu untuk lulus dan corresponding bentuk id alias ke fungsi. Fungsi ini dirancang untuk ditempatkan ke wilayah <head> halaman web Anda.

	Contoh::

		<?php echo smiley_js(); ?>

.. php:function:: parse_smileys([$str = ''[, $image_url = ''[, $smileys = NULL]]])

	:param	string	$str: Teks yang berisi kode smiley
	:param	string	$image_url: Path URL ke direktori Smiley
	:param	array	$smileys: Array dari Smiley
	:returns:	Smiley yang diparsing
	:rtype:	string

	Mengambil string teks sebagai masukan dan menggantikan yang terdapat smiley teks biasa menjadi setara gambar. Parameter pertama harus berisi string yang kedua harus berisi URL ke folder smiley Anda

	Contoh::

		$str = 'Berikut adalah beberapa smiley: :-)  ;-)';
		$str = parse_smileys($str, 'http://example.com/images/smileys/');
		echo $str;

.. |smile!| image:: ../images/smile.gif