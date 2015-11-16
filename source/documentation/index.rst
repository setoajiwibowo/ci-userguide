###############################
Menulis Dokumentasi CodeIgniter
###############################

CodeIgniter menggunakan *Sphinx* untuk menghasilkan dokumentasi dalam berbagai format, 
menggunakan *reStructuredText* untuk menangani format. Jika Anda sudah familiar 
dengan *Markdown* atau *Textile*, Anda akan segera memahami *reStructuredText*. 
Fokusnya adalah pada pembacaan dan ramah pengguna. Sementara mereka bisa sangat teknis, 
kami selalu menulis untuk manusia!

Sebuah daftar isi harus selalu disertakan, seperti di bawah.  Daftar isi dibuat secara otomatis dengan memasukkan berikut

::

	.. contents::
		:local:

	.. raw:: html

  	<div class="custom-index container"></div>

.. contents::
  :local:

.. raw:: html

  <div class="custom-index container"></div>

<div> yang dimasukkan sebagai *raw HTML* adalah sebuah *hook* untuk *JavaScript* 
dokumentasi ini untuk secara dinamis menambahkan link ke setiap fungsi dan 
definisi metode yang terdapat dalam halaman saat ini.

********************
Alat yang dibutuhkan
********************

Untuk melihat HTML, ePub, PDF, dll yang dihasilkan, Anda akan perlu menginstal 
*Sphinx* bersama dengan ekstensi domain PHP untuk *Sphinx*. Persyaratan mendasar 
adalah *Python* harus diinstal. Terakhir, Anda akan menginstal *CI Lexer* 
untuk *Pygments*, sehingga blok kode dapat disorot dengan baik.

.. code-block:: bash

	easy_install "sphinx==1.2.3"
	easy_install sphinxcontrib-phpdomain

Kemudian ikuti petunjuk di file README di folder :samp:`cilexer` 
dalam repositori dokumentasi untuk menginstal *CI Lexer*.



******************************************
Halaman dan Bagian Heading dan Sub Heading
******************************************

Judul tidak hanya memberikan order dan bagian dalam halaman, tetapi mereka juga 
digunakan untuk secara otomatis membangun halaman dan daftar isi dokumen. 
Judul dibentuk dengan menggunakan karakter tertentu sebagai garis bawah untuk sedikit teks.  
Judul utama, seperti halaman judul dan judul bagian juga menggunakan *overlines*.  
Judul lain hanya menggunakan garis bawah, dengan hirarki berikut::

	# dengan overline untuk judul halaman
	* dengan overline untuk bagian utama
	= untuk subsections
	- untuk subsubsections
	^ untuk subsubsubsections
	" untuk subsubsubsubsections (!)

File :download:`TextMate ELDocs Bundle <./ELDocs.tmbundle.zip>` dapat membantu Anda membuat *tab triggers* berikut::

	title->

		#############
		Judul Halaman
		#############

	sec->

		************
		Bagian Utama
		************

	sub->

		Subsection
		==========

	sss->

		SubSubSection
		-------------

	ssss->

		SubSubSubSection
		^^^^^^^^^^^^^^^^

	sssss->

		SubSubSubSubSection (!)
		"""""""""""""""""""""""




******************
Metode Dokumentasi
******************

Ketika mendokumentasikan metode kelas untuk pengembang pihak ketiga, *Sphinx* memberikan arahan untuk membantu dan menjaga hal-hal sederhana.  Sebagai contoh, perhatikan *ReST* berikut

.. code-block:: rst

	.. php:class:: Some_class

		.. php:method:: some_method ( $foo [, $bar [, $bat]])

			Fungsi ini akan melakukan beberapa tindakan.  Array ``$bar`` harus 
			mengandung sesuatu dan sesuatu yang lain, dan bersama dengan ``$bat`` 
			merupakan parameter opsional.

			:param int $foo: id *foo* untuk melakukan sesuatu
			:param mixed $bar: Sebuah array data yang harus berisi sesuatu dan sesuatu yang lain
			:param bool $bat: iya atau tidak untuk melakukan sesuatu
			:returns: *FALSE* pada kegagalan, *TRUE* jika berhasil
			:rtype: bool

			::

				$this->load->library('some_class');

				$bar = array(
					'something'		=> 'Berikut adalah parameter ini!',
					'something_else'	=> 42
				);

				$bat = $this->some_class->should_do_something();

				if ($this->some_class->some_method(4, $bar, $bat) === FALSE)
				{
					show_error('Sebuah Kesalahan Terjadi Saat Melakukan Beberapa Metode');
				}

			.. note:: Berikut ini adalah sesuatu yang Anda harus sadari ketika menggunakan some_method().
					untuk Nyata.

			Lihat juga :meth:`Some_class::should_do_something`


		.. php:method:: should_do_something()

			:returns: iya atau tidak sesuatu yang harus dilakukan
			:rtype: bool


Kode ini menciptakan tampilan berikut:

.. php:class:: Some_class

		.. php:method:: some_method ( $foo [, $bar [, $bat]])

			Fungsi ini akan melakukan beberapa tindakan.  Array ``$bar`` harus 
			mengandung sesuatu dan sesuatu yang lain, dan bersama dengan ``$bat`` 
			merupakan parameter opsional.

			:param int $foo: id *foo* untuk melakukan sesuatu
			:param mixed $bar: Sebuah array data yang harus berisi sesuatu dan sesuatu yang lain
			:param bool $bat: iya atau tidak untuk melakukan sesuatu
			:returns: *FALSE* pada kegagalan, *TRUE* jika berhasil
			:rtype: bool

			::

				$this->load->library('some_class');

				$bar = array(
					'something'		=> 'Berikut adalah parameter ini!',
					'something_else'	=> 42
				);

				$bat = $this->some_class->should_do_something();

				if ($this->some_class->some_method(4, $bar, $bat) === FALSE)
				{
					show_error('Sebuah Kesalahan Terjadi Saat Melakukan Beberapa Metode');
				}

			.. note:: Berikut ini adalah sesuatu yang Anda harus sadari ketika menggunakan some_method().
					untuk Nyata.

			Lihat juga :meth:`Some_class::should_do_something`


		.. php:method:: should_do_something()

			:returns: iya atau tidak sesuatu yang harus dilakukan
			:rtype: bool