#############
Bagian Berita
#############

Pada bagian sebelumnya, Kita pergi ke beberapa konsep dasar dari framework dengan menulis sebuah 
kelas yang meliputi halaman statis. Kita membersihkan URI dengan menambahkan *custom routing rules*.
Sekarang saatnya untuk memperkenalkan konten dinamis dan mulai menggunakan database.

Menyiapkan *model* Anda
-----------------------

Alih-alih menulis operasi database yang tepat di *controller*, permintaan harus ditempatkan dalam
model, sehingga mereka dapat dengan mudah digunakan kembali nanti. *Model* adalah tempat di mana Anda 
mengambil, memasukkan, dan memperbarui informasi dalam *database* Anda atau menyimpan data lainnya. 
Mereka mewakili data Anda.

Buka direktori *application/models/* dan buat file baru bernama
*News_model.php* dan tambahkan kode berikut. Pastikan Anda telah mengkonfigurasi database Anda benar seperti yang dijelaskan di :doc:`sini <../database/configuration>`.

::

	<?php
	class News_model extends CI_Model {

		public function __construct()
		{
			$this->load->database();
		}
	}

Kode ini terlihat mirip dengan kode *controller* yang digunakan sebelumnya. Kode ini 
menciptakan *model* baru dengan memperluas ``CI_Model`` dan memuat *libabry database*. Model ini akan membuat
kelas database tersedia objek melalui ``$this->db``.

Sebelum melakukan *query database*, skema database harus dibuat. Terhubung ke database Anda dan jalankan
perintah SQL di bawah ini (MySQL). Juga menambahkan beberapa *records*.

::

	CREATE TABLE news (
		id int(11) NOT NULL AUTO_INCREMENT,
		title varchar(128) NOT NULL,
		slug varchar(128) NOT NULL,
		text text NOT NULL,
		PRIMARY KEY (id),
		KEY slug (slug)
	);

Sekarang database dan model telah diatur, Anda akan memerlukan metode untuk mendapatkan semua postingan kita dari database kita.  Untuk melakukan hal ini, *database abstraction layer* yang disertakan dengan :doc:`Query Builder <../database/query_builder>` — CodeIgniter digunakan. Hal ini memungkinkan Anda untuk menulis sekali  'query' dan membuat mereka bekerja pada :doc:`all supported database systems <../general/requirements>`. Tambahkan kode berikut untuk model Anda.

::

	public function get_news($slug = FALSE)
	{
		if ($slug === FALSE)
		{
			$query = $this->db->get('news');
			return $query->result_array();
		}

		$query = $this->db->get_where('news', array('slug' => $slug));
		return $query->row_array();
	}

Dengan kode ini Anda dapat melakukan dua *query* yang berbeda. Anda bisa mendapatkan semua *records* berita,
atau mendapatkan sebuah berita dari `slug <#>`_. Anda mungkin telah memperhatikan bahwa variabel ``$slug``
tidak dibersihkan sebelum menjalankan query; :doc:`Query Builder <../database/query_builder>` 
melakukan ini untuk Anda.

Menampilkan berita
------------------

Sekarang *query* sudah tertulis, model harus terikat dengan *view*
yang akan menampilkan berita kepada pengguna. Hal ini dapat dilakukan di *controller* ``Pages`` 
yang kita buat sebelumnya, tapi demi kejelasan,
sebuah *controller* baru ``News`` didefinisikan. Buat *controller* baru di
*application/controllers/News.php*.

::

	<?php
	class News extends CI_Controller {

		public function __construct()
		{
			parent::__construct();
			$this->load->model('news_model');
			$this->load->helper('url_helper');
		}

		public function index()
		{
			$data['news'] = $this->news_model->get_news();
		}

		public function view($slug = NULL)
		{
			$data['news_item'] = $this->news_model->get_news($slug);
		}
	}

Lihat kode tersebut, Anda dapat melihat beberapa kesamaan dengan file kita buat sebelumnya. Pertama, metode  ``__construct()``: Kode tersebut memanggil *constructor* kelas induknya (``CI_Controller``) dan memuat *model*,
sehingga dapat digunakan di semua metode lain dalam *controller* ini.
Kode tersebut juga memuat koleksi fungsi :doc:`URL Helper <../helpers/url_helper>`, karena kita akan menggunakan salah satu dari mereka dalam *view* nanti.

Berikutnya, ada dua metode untuk melihat semua berita dan satu untuk sebuah berita tertentu.  Anda dapat melihat bahwa variabel ``$slug`` dilewatkan ke metode model dalam metode kedua.  Model ini menggunakan *slug* ini untuk mengidentifikasi berita ditampilkan.

Sekarang data tersebut diambil oleh *controller* melalui *model* kita, tapi belum ada yang ditampilkan.  Hal berikutnya yang harus dilakukan adalah melewarkan data ini ke *view*.

::

	public function index()
	{
		$data['news'] = $this->news_model->get_news();
		$data['title'] = 'News archive';

		$this->load->view('templates/header', $data);
		$this->load->view('news/index', $data);
		$this->load->view('templates/footer');
	}

Kode di atas mendapat semua *records* berita dari model dan memberikan ke sebuah
variabel.  Nilai untuk judul juga ditugaskan untuk elemen ``$data['title']``
dan semua data akan diteruskan ke *view*. Anda sekarang perlu membuat *view* untuk menampilkan berita. 
Buat file *application/views/news/index.php* dan tambahkan potongan kode yang berikutnya.

::

	<h2><?php echo $title; ?></h2>
	
	<?php foreach ($news as $news_item): ?>

		<h3><?php echo $news_item['title']; ?></h3>
		<div class="main">
			<?php echo $news_item['text']; ?>
		</div>
		<p><a href="<?php echo site_url('news/'.$news_item['slug']); ?>">View article</a></p>

	<?php endforeach; ?>

Di sini, setiap item berita di-*looping* dan ditampilkan kepada pengguna.  Anda dapat melihat kita menulis template kita di PHP dicampur dengan HTML.  Jika Anda memilih untuk menggunakan bahasa template, Anda dapat menggunakan kelas :doc:`Template
Parser <../libraries/parser>` CodeIgniter atau *parser* pihak ketiga.

Halaman ikhtisar berita sekarang selesai, tetapi halaman untuk menampilkan berita individu masih absen.  Model yang dibuat sebelumnya dibuat sedemikian rupa sehingga dapat dengan mudah digunakan untuk fungsi ini.  Anda hanya perlu menambahkan beberapa kode untuk controller dan membuat *view* baru. Kembali ke *controller*
``News`` dan perbarui ``view()`` dengan berikut:

::

	public function view($slug = NULL)
	{
		$data['news_item'] = $this->news_model->get_news($slug);

		if (empty($data['news_item']))
		{
			show_404();
		}

		$data['title'] = $data['news_item']['title'];

		$this->load->view('templates/header', $data);
		$this->load->view('news/view', $data);
		$this->load->view('templates/footer');
	}

Alih-alih memanggil metode ``get_news()`` tanpa sebuah parameter, variabel
``$slug`` dilewatkan, sehingga akan menampilkan berita tertentu.
Satu-satunya hal yang tersisa untuk dilakukan adalah membuat *view* yang sesuai di
*application/views/news/view.php*. Masukan kode berikut dalam file ini.

::

	<?php
	echo '<h2>'.$news_item['title'].'</h2>';
	echo $news_item['text'];

Routing
-------

Karena aturan *wildcard routing* buat sebelumnya, Anda memerlukan *route* tambahan untuk melihat controller yang baru saja Anda buat. Memodifikasi file routing
(*application/config/routes.php*) sehingga terlihat sebagai berikut.
Hal ini memastikan permintaan mencapai *controller* ``News`` bukannya pergi ke *controller* ``Pages``. Baris pertama melakukan *routes* URI dengan *slug* ke metode ``view()`` di *controller* ``News``.

::

	$route['news/(:any)'] = 'news/view/$1';
	$route['news'] = 'news';
	$route['(:any)'] = 'pages/view/$1';
	$route['default_controller'] = 'pages/view';

Arahkan browser Anda ke *document root* Anda, diikuti dengan index.php/news dan
lihat halaman berita Anda.
