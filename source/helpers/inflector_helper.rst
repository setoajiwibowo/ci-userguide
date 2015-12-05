################
Inflector Helper
################

File *Inflector Helper* berisi fungsi yang memungkinkan Anda untuk mengubah kata-kata untuk jamak, tunggal, kasus *camel*, dll.

.. contents::
  :local:

.. raw:: html

  <div class="custom-index container"></div>

Memuat Helper ini
=================

Helper ini dimuat menggunakan kode berikut::

	$this->load->helper('inflector');

Fungsi yang Tersedia
====================

Fungsi yang tersedia sebagai berikut:


.. php:function:: singular($str)

	:param	string	$str: Masukan string
	:returns:	Sebuah kata tunggal
	:rtype:	string

	Perubahan kata jamak untuk tunggal.  Contoh::

		echo singular('dogs'); // Mencetak 'dog'

.. php:function:: plural($str)

	:param	string	$str: Masukan string
	:returns:	Sebuah kata jamak
	:rtype:	string

	Perubahan kata tunggal untuk jamak.  Contoh::

		echo plural('dog'); // Mencetak 'dogs'

.. php:function:: camelize($str)

	:param	string	$str: Masukan string
	:returns:	Camelized string
	:rtype:	string

	Perubahan serangkaian kata-kata yang dipisahkan oleh spasi atau garis 
	bawah untuk kasus *camel*. Contoh::

		echo camelize('my_dog_spot'); // Mencetak 'myDogSpot'

.. php:function:: underscore($str)

	:param	string	$str: Masukan string
	:returns:	String yang berisi garis bawah bukan spasi
	:rtype:	string

	Dibutuhkan beberapa kata yang dipisahkan oleh spasi dan menggarisbawahinya. 
	Contoh::

		echo underscore('my dog spot'); // Mencetak 'my_dog_spot'

.. php:function:: humanize($str[, $separator = '_'])

	:param	string	$str: Masukan string
	:param	string	$separator: Pemisah masukan
	:returns:	String yang manusiawi
	:rtype:	string

	Dibutuhkan beberapa kata yang dipisahkan oleh garis bawah dan menambahkan spasi 
	di antara mereka.  Setiap kata dikapitalisasi.

	Contoh::

		echo humanize('my_dog_spot'); // Mencetak 'My Dog Spot'

	Untuk menggunakan strip bukan garis bawah::

		echo humanize('my-dog-spot', '-'); // Mencetak 'My Dog Spot'

.. php:function:: is_countable($word)

	:param	string	$word: Masukan string
	:returns:	TRUE jika kata tersebut dapat dihitung atau FALSE jika tidak
	:rtype:	bool

	Cek jika kata yang diberikan memiliki versi plural. Contoh::

		is_countable('equipment'); // Kembali FALSE