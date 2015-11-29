#############
Cookie Helper
#############

File *Cookie Helper* berisi fungsi yang membantu dalam bekerja dengan cookie.

.. contents::
  :local:

.. raw:: html

  <div class="custom-index container"></div>

Memuat Helper ini
=================

Helper ini dimuat menggunakan kode berikut::

	$this->load->helper('cookie');

Fungsi yang Tersedia
====================

Fungsi yang tersedia sebagai berikut:


.. php:function:: set_cookie($name[, $value = ''[, $expire = ''[, $domain = ''[, $path = '/'[, $prefix = ''[, $secure = FALSE[, $httponly = FALSE]]]]]]]])

	:param	mixed	$name: Nama Cookie *atau* array asosiatif semua parameter yang tersedia untuk fungsi ini
	:param	string	$value: Nilai cookie
	:param	int	$expire: Jumlah detik sampai berakhirnya
	:param	string	$domain: Cookie domain (biasanya: .yourdomain.com)
	:param	string	$path: Jalur Cookie
	:param	string	$prefix: Nama Cookie prefix
	:param	bool	$secure: Apakah hanya mengirim cookie melalui HTTPS
	:param	bool	$httponly: Apakah menyembunyikan cookie dari JavaScript
	:rtype:	void

	Fungsi *helper* ini memberikan sintaks ramah untuk mengatur cookie browser. 
	Mengacu pada :doc:`Input Library <../libraries/input>` untuk penjelasan penggunaannya, 
	seperti fungsi ini adalah alias untuk ``CI_Input::set_cookie()``.

.. php:function:: get_cookie($index[, $xss_clean = NULL]])

	:param	string	$index: Nama Cookie
	:param	bool	$xss_clean: Apakah akan menerapkan XSS filtering untuk nilai yang dikembalikan
	:returns:	Nilai cookie atau NULL jika tidak ditemukan
	:rtype:	mixed

	Fungsi *helper* ini memberikan sintaks ramah untuk mengatur cookie browser. 
	Mengacu pada :doc:`Input Library <../libraries/input>` untuk penjelasan rinci tentang penggunaannya, 
	karena fungsi ini bertindak sangat mirip dengan ``CI_Input::cookie()``, kecuali itu juga akan tambahkan ``$config['cookie_prefix']`` yang mungkin telah diatur di dalam file
	*application/config/config.php* anda.

.. php:function:: delete_cookie($name[, $domain = ''[, $path = '/'[, $prefix = '']]]])

	:param	string	$name: Nama Cookie
	:param	string	$domain: Cookie domain (biasanya: .yourdomain.com)
	:param	string	$path: Jalur Cookie
	:param	string	$prefix: Nama Cookie prefix
	:rtype:	void

	Memungkinkan Anda menghapus cookie. Kecuali Anda sudah menetapkan jalur khusus atau nilai-nilai lain, 
	hanya nama cookie yang dibutuhkan.
	::

		delete_cookie('name');

	Fungsi ini jika tidak identik dengan ``set_cookie()``, kecuali bahwa ia tidak memiliki nilai dan 
	parameter kadaluarsa.  Anda bisa mengirimkan sebuah nilai array dalam parameter pertama atau Anda 
	dapat mengatur parameter diskrit.
	::

		delete_cookie($name, $domain, $path, $prefix);
