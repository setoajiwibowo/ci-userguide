###############
Language Helper
###############

File *Language Helper* berisi fungsi yang membantu dalam bekerja dengan
file bahasa.

.. contents::
  :local:

.. raw:: html

  <div class="custom-index container"></div>

Memuat Helper ini
=================

Helper ini dimuat menggunakan kode berikut::

	$this->load->helper('language');

Fungsi yang Tersedia
====================

Fungsi yang tersedia sebagai berikut:


.. php:function:: lang($line[, $for = ''[, $attributes = array()]])

 	:param	string	$line: Kunci garis Bahasa
 	:param	string	$for: Atribut HTML "for" (ID dari elemen yang kita menciptakan label)
 	:param	array	$attributes: Atribut HTML tambahan
 	:returns:	Label baris bahasa berformat HTML
	:rtype:	string

	Fungsi ini mengembalikan baris teks dari file bahasa dengan sintaks sederhana 
	yang mungkin lebih diinginkan untuk file *view* dari
	``CI_Lang::line()``.

	Contoh::

		echo lang('language_key', 'form_item_id', array('class' => 'myClass'));
		// Outputs: <label for="form_item_id" class="myClass">Garis bahasa</label>