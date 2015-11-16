################
Kebutuhan Server
################

`PHP <http://php.net/>`_ versi 5.4 atau terbaru lebih dianjurkan.

CodeIgniter seharusnya bisa bekerja pada 5.2.4 juga, tapi kami sangat 
menyarankan Anda untuk tidak menjalankan PHP versi lama, karena masalah 
keamanan dan masalah kinerja, serta fitur yang hilang.

Database diperlukan untuk sebagian besar pemrograman aplikasi web.
Saat ini database yang didukung adalah:

  - MySQL (5.1+) melalui driver *mysql* (usang), *mysqli* dan *pdo* 
  - Oracle melalui driver *oci8* dan *pdo* 
  - PostgreSQL melalui driver *postgre* dan *pdo* 
  - MS SQL melalui driver *mssql*, *sqlsrv* (hanya versi 2005 dan diatasnya) dan *pdo* 
  - SQLite melalui driver *sqlite* (versi 2), *sqlite3* (versi 3) dan *pdo* 
  - CUBRID melalui driver *cubrid* dan *pdo* 
  - Interbase/Firebird melalui driver *ibase* dan *pdo* 
  - ODBC melalui driver *odbc* dan *pdo* (Anda harus tahu bahwa ODBC sebenarnya merupakan *abstraction layer*)