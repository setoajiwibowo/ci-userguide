###############
Download Helper
###############

*Download Helper* memungkinkan Anda mengunduh data ke desktop Anda.

.. contents::
  :local:

.. raw:: html

  <div class="custom-index container"></div>

Memuat Helper ini
=================

Helper ini dimuat menggunakan kode berikut::

	$this->load->helper('download');

Fungsi yang Tersedia
====================

Fungsi yang tersedia sebagai berikut:


.. php:function:: force_download([$filename = ''[, $data = ''[, $set_mime = FALSE]]])

	:param	string	$filename: Nama file
	:param	mixed	$data: Isi file
	:param	bool	$set_mime: Apakah akan mencoba untuk mengirimkan jenis MIME aktual
	:rtype:	void

	Menghasilkan *header server* yang memaksa data yang akan didownload ke desktop Anda.  
	Berguna dengan file download.  Parameter pertama adalah **nama yang Anda inginkan 
	file yang didownload diberi nama**, parameterkedua adalah file data.

	Jika Anda menetapkan parameter kedua ke NULL dan ``$filename`` adalah path file 
	yang dapat dibaca yang ada, maka isinya akan dibaca sebagai gantinya.

	Jika Anda menetapkan parameter ketiga ke boolean TRUE, maka jenis file MIME yang 
	sebenarnya (berdasarkan ekstensi nama file) yang akan dikirim, sehingga jika browser
	Anda memiliki handler untuk jenis itu - browser dapat menggunakannya.

	Contoh::

		$data = 'Berikut adalah beberapa teks!';
		$name = 'mytext.txt';
		force_download($name, $data);

	Jika Anda ingin mengunduh file yang ada dari server Anda, Anda akan perlu melakukan hal berikut::

		// Isi dari photo.jpg akan otomatis dibaca
		force_download('/path/to/photo.jpg', NULL);