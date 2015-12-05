###########
Path Helper
###########

File *Path Helper* berisi fungsi yang memungkinkan Anda untuk bekerja dengan *path* file di server.

.. contents::
  :local:

.. raw:: html

  <div class="custom-index container"></div>

Memuat Helper ini
=================

Helper ini dimuat menggunakan kode berikut::

	$this->load->helper('path');

Fungsi yang Tersedia
====================

Fungsi yang tersedia sebagai berikut:


.. php:function:: set_realpath($path[, $check_existance = FALSE])

	:param	string	$path: Path
	:param	bool	$check_existance: Apakah untuk memeriksa apakah path benar-benar ada
	:returns:	Path absolut
	:rtype:	string

	Fungsi ini akan mengembalikan *path* server tanpa link simbolik atau struktur 
	direktori relatif.  Argumen kedua opsional akan menyebabkan kesalahan yang 
	akan dipicu jika jalan tidak dapat diselesaikan.

	Contoh::

		$file = '/etc/php5/apache2/php.ini';
		echo set_realpath($file); // Mencetak '/etc/php5/apache2/php.ini'

		$non_existent_file = '/path/to/non-exist-file.txt';
		echo set_realpath($non_existent_file, TRUE);	// Menunjukkan kesalahan, sebagai *path* tidak dapat diselesaikan
		echo set_realpath($non_existent_file, FALSE);	// Mencetak '/path/to/non-exist-file.txt'

		$directory = '/etc/php5';
		echo set_realpath($directory);	// Mencetak '/etc/php5/'

		$non_existent_directory = '/path/to/nowhere';
		echo set_realpath($non_existent_directory, TRUE);	// Menunjukkan kesalahan, sebagai *path* tidak dapat diselesaikan
		echo set_realpath($non_existent_directory, FALSE);	// Mencetak '/path/to/nowhere'