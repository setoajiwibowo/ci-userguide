##############
Halaman Statis
##############

**Catatan:** Pengajaran ini mengasumsikan Anda sudah mengunduh CodeIgniter dan
:doc:`menginstall *framework* <../installation/index>` dalam lingkungan pengembangan Anda.

Hal pertama yang Anda akan lakukan adalah membuat **controller** untuk menangani halaman statis.  Sebuah controller hanyalah sebuah kelas yang membantu kerja delegasi. Ini adalah lem aplikasi web Anda.

Sebagai contoh, ketika panggilan dilakukan ke:

	http://example.com/news/latest/10

Kita mungkin membayangkan bahwa ada controller bernama "berita". Metode yang dipanggil pada berita akan "terbaru". Pekerjaan metode berita ini bisa untuk meraih 10 item berita, dan membuat mereka pada halaman. Sangat sering di MVC, Anda akan melihat pola URL yang cocok:

	http://example.com/[controller-class]/[controller-method]/[arguments]

Skema URL menjadi lebih kompleks, hal ini dapat berubah. Tapi untuk saat ini, ini semua yang kita perlu tahu.

Buat sebuah file di application/controllers/Pages.php dengan kode berikut.

::

	<?php 
	class Pages extends CI_Controller { 

		public function view($page = 'home') 
		{
	        }
	}

Anda telah membuat sebuah kelas bernama ``Pages``, dengan metode *view* yang menerima satu argumen bernama ``$page``. Kelas ``Pages`` memperpanjang kelas
``CI_Controller``. Ini berarti bahwa kelas *pages* baru dapat mengakses metode dan variabel yang didefinisikan dalam kelas ``CI_Controller`` (*system/core/Controller.php*).

**Controller adalah hal yang akan menjadi pusat setiap permintaan** untuk aplikasi web Anda.  Dalam diskusi CodeIgniter sangat teknis, mungkin akan disebut sebagai *Super objek*.  Seperti kelas php, Anda melihatnya dalam controller Anda sebagai ``$this``.  Mengacu pada ``$this`` adalah bagaimana Anda akan memuat *library*, *view*, dan perintah yang umum pada framework.

Sekarang Anda telah membuat metode pertama Anda, saatnya untuk membuat beberapa halaman dasar template.  Kami akan menciptakan dua "views" (halaman template) yang bertindak sebagai footer dan header halaman kami.

Buat header di *application/views/templates/header.php* dan tambahkan kode berikut:

::

	<html>
		<head>
			<title>Pengajaran CodeIgniter</title>
		</head>
		<body>

			<h1><?php echo $title; ?></h1>

Header berisi kode HTML dasar yang Anda akan ingin menampilkan sebelum memuat *view* utama,
bersama-sama dengan heading. Ini juga akan mengeluarkan variabel ``$title``, yang kita akan 
menentukan kemudian di controller. Sekarang, buat footer di *application/views/templates/footer.php*
yang mencakup kode berikut:

::

			<em>&copy; 2015</em>
		</body>
	</html>

Menambahkan logika ke controller
--------------------------------

Sebelumnya Anda mengatur controller dengan metode ``view ()``.  Metode ini
menerima satu parameter, yang merupakan nama dari halaman yang akan dimuat. Template halaman statis akan berlokasi di direktori *application/views/pages/*.

Dalam direktori tersebut, buat dua file bernama *home.php* dan *about.php*.  Dalam file-file, ketik beberapa teks - apapun yang Anda ingin - dan menyimpan file tersebut.  Jika Anda ingin menjadi sangat *un-original*, coba "Hello World!".

Dalam rangka untuk memuat halaman tersebut, Anda harus memeriksa apakah halaman yang diminta benar-benar ada

::

	public function view($page = 'home')
	{
	        if ( ! file_exists(APPPATH.'/views/pages/'.$page.'.php'))
		{
			// Whoops, kita tidak memiliki halaman untuk itu!
			show_404();
		}

		$data['title'] = ucfirst($page); // Membuat besar huruf pertama

		$this->load->view('templates/header', $data);
		$this->load->view('pages/'.$page, $data);
		$this->load->view('templates/footer', $data);
	}

Sekarang, ketika halaman tidak ada, halaman dimuat, termasuk header dan
footer, dan ditampilkan kepada pengguna. Jika halaman tidak ada, kesalahan "404
Page not found" ditampilkan.

Baris pertama dalam metode ini memeriksa apakah halaman benar-benar ada.
Fungsi *PHP's native* ``file_exists()`` digunakan untuk memeriksa  
di mana file diharapkan ada.``show_404()`` adalah fungsi *built-in* 
CodeIgniter yang membuat halaman *error default*.

Dalam template header, variabel ``$title`` digunakan untuk menyesuaikan
Judul halaman.  Nilai *title* didefinisikan dalam metode ini, tapi bukannya
menempatkan nilai ke variabel, itu ditugaskan untuk elemen title di *array* ``$data``.

Hal terakhir yang harus dilakukan adalah memuat *view* dalam urutan mereka harus ditampilkan.  
Parameter kedua dalam metode ``view()`` yang digunakan untuk melewati nilai-nilai ke *view*.  
Setiap nilai dalam *array* ``$data`` ditugaskan untuk variabel dengan nama kunci.  
Jadi nilai ``$data[ 'title' ]`` di *controller* setara dengan ``$title`` di *view*.

Routing
-------

*Controller* sekarang berfungsi! Arahkan browser Anda ke
``[your-site-url]index.php/pages/view`` untuk melihat halaman anda. Ketika anda mengunjungi
``index.php/pages/view/about`` Anda akan melihat halaman *tentang*, lagi termasuk header dan footer.

Menggunakan *custom routing rules*, Anda memiliki kekuatan untuk memetakan setiap URI untuk setiap *controller* dan metode, dan membebaskan diri dari konvensi yang normal
``http://example.com/[controller-class]/[controller-method]/[arguments]``

Mari kita melakukan itu. Buka file routing yang terletak di
*application/config/routes.php* dan tambahkan dua baris berikut.
Hapus semua kode lain yang menetapkan setiap elemen dalam array ``$route``.

::

	$route['default_controller'] = 'pages/view';
	$route['(:any)'] = 'pages/view/$1';

CodeIgniter membaca aturan routing dari atas ke bawah dan rute permintaan ke aturan pertama yang
cocok. Setiap aturan adalah sebuah ekspresi reguler (sisi kiri) dipetakan ke controller dan metode
nama dipisahkan oleh garis miring (sisi kanan).  Ketika permintaan datang, CodeIgniter terlihat untuk 
kecocokan pertama, dan panggilan *controller* dan metode yang tepat, mungkin dengan argumen.

Informasi lebih lanjut tentang routing dapat ditemukan dalam
:doc:`Dokumentasi <../general/routing>` *URI Routing*.

Di sini, aturan kedua di ``$routes`` *array* mencocokkan **any** perminaan menggunakan *wildcard string* ``(:any)``. dan melewati parameter ke metode
``view()`` dari kelas ``Pages``.

Sekarang kunjungi ``index.php/about``. Apakah itu bisa disalurkan dengan benar ke metode ``view()``
di halaman *controller*? Mengagumkan!
