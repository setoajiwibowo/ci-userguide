############
Email Helper
############

*Email Helper* menyediakan beberapa fungsi bantu untuk bekerja dengan Email.
Untuk solusi email lebih kuat, lihat :doc:`Email
Class <../libraries/email>` CodeIgniter.

.. important:: *Email helper* sudah ditinggalkan dan saat ini hanya disimpan untuk kompatibilitas versi sebelumnya.

.. contents::
  :local:

.. raw:: html

  <div class="custom-index container"></div>

Memuat Helper ini
=================

Helper ini dimuat menggunakan kode berikut::

	$this->load->helper('email');

Fungsi yang Tersedia
====================

Fungsi yang tersedia sebagai berikut:


.. php:function:: valid_email($email)

	:param	string	$email: Alamat email
	:returns:	TRUE jika email yang disuplai valid, jika tidak FALSE
	:rtype:	bool

	Memeriksa apakah input adalah alamat e-mail diformat dengan benar. Catatan fungsi ini 
	tidak benar-benar membuktikan bahwa alamat akan dapat menerima email, tetapi hanya 
	menyatakan bahwa alamat itu adalah alamat sah.

	Contoh::

		if (valid_email('email@somesite.com'))
		{
			echo 'email valid';
		}
		else
		{
			echo 'email tidak valid';
		}

	.. note:: Semua fungsi ini menggunakan PHP's native ``filter_var()``::

		(bool) filter_var($email, FILTER_VALIDATE_EMAIL);

.. php:function:: send_email($recipient, $subject, $message)

	:param	string	$recipient: Alamat Email
	:param	string	$subject: Judul Email
	:param	string	$message: Pesan
	:returns:	TRUE jika email berhasil dikirim, FALSE jika ada kesalahan
	:rtype:	bool

	Mengirim email menggunakan PHP's native `mail() <http://php.net/function.mail>`_
	function.

	.. note:: Semua fungsi ini menggunakan PHP's native ``mail``

		::

			mail($recipient, $subject, $message);

	Untuk solusi email lebih kuat, lihat :doc:`Email Library
	<../libraries/email>` CodeIgniter.