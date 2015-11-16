##############
Membuat Driver
##############

Direktori Driver dan Struktur File
==================================

Contoh Direktori *driver* dan *layout* struktur file:

-  /application/libraries/Driver_name

   -  Driver_name.php
   -  drivers

      -  Driver_name_subclass_1.php
      -  Driver_name_subclass_2.php
      -  Driver_name_subclass_3.php

.. note:: Dalam rangka mempertahankan kompatibilitas pada sistem file 
	yang *case-sensitive*, direktori *Driver_name* harus diberi nama 
	dalam format yang dikembalikan oleh ``ucfirst()``.

.. note:: Arsitektur *library Driver* adalah bahwa subclass tidak 
	memperpanjang dan karena itu tidak mewarisi sifat atau metode 
	dari *driver* utama.