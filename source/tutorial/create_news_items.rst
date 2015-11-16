##############
Membuat Berita
##############

Anda sekarang tahu bagaimana Anda dapat membaca data dari database menggunakan CodeIgniter, 
tetapi Anda belum menulis informasi ke database. Pada bagian ini Anda akan memperluas
*controller* berita dan model yang buat sebelumnya untuk menyertakan fungsi ini.

Membuat formulir
----------------

Untuk input data ke dalam database yang Anda butuhkan untuk membuat formulir di mana Anda dapat memasukkan informasi yang akan disimpan. Ini berarti Anda akan membutuhkan formulir dengan dua bidang, satu untuk judul dan satu untuk teks. Anda akan memperoleh *slug* dari judul kami dalam model. Buat view baru di
application/views/news/create.php.

::

    <h2><?php echo $title; ?></h2>

    <?php echo validation_errors(); ?>

    <?php echo form_open('news/create'); ?>

        <label for="title">Judul</label> 
        <input type="input" name="title" /><br />

        <label for="text">Teks</label>
        <textarea name="text"></textarea><br />

        <input type="submit" name="submit" value="Buat Berita" /> 

    </form>

Hanya ada dua hal di sini yang mungkin terlihat asing bagi Anda: fungsi form_open() dan fungsi validation_errors().

Fungsi pertama disediakan oleh :doc:`form
helper <../helpers/form_helper>` dan membuat *form element* dan menambahkan fungsionalitas tambahan, seperti menambahkan :doc:`CSRF prevention
field <../libraries/security>`. Yang terakhir ini digunakan untuk melaporkan kesalahan terkait untuk membentuk validasi.

Kembali ke *controller* berita Anda. Anda akan melakukan dua hal di sini,
memeriksa apakah formulir tersebut diserahkan dan apakah data yang diajukan
melewati aturan validasi. Anda akan menggunakan *library* :doc:`form
validation <../libraries/form_validation>` untuk melakukan ini.

::

    public function create()
    {
        $this->load->helper('form');
        $this->load->library('form_validation');
        
        $data['title'] = 'Create a news item';
        
        $this->form_validation->set_rules('title', 'Title', 'required');
        $this->form_validation->set_rules('text', 'Text', 'required');
        
        if ($this->form_validation->run() === FALSE)
        {
            $this->load->view('templates/header', $data);   
            $this->load->view('news/create');
            $this->load->view('templates/footer');
            
        }
        else
        {
            $this->news_model->set_news();
            $this->load->view('news/success');
        }
    }

Kode di atas menambahkan banyak fungsi. Beberapa baris pertama memuat
bentuk *helper* dan *library form validation*. Setelah itu, aturan untuk
validasi form ditetapkan. Metode set\_rules() mengambil tiga argumen;
nama field input, nama yang akan digunakan dalam pesan kesalahan, dan
peraturan.  Dalam hal ini bidang judul dan teks diperlukan.

CodeIgniter memiliki *library form validation* yang kuat seperti yang ditunjukkan 
di atas. Anda dapat membaca :doc:`lebih tentang library ini di sini <../libraries/form_validation>`.

Terus turun, Anda dapat melihat kondisi yang memeriksa apakah validasi form berhasil.  
Jika tidak, formulir ditampilkan, jika di-*submit* **dan** melewati semua aturan, 
model dipanggil. Setelah ini, *view* dimuat untuk menampilkan pesan sukses. Buat sebuah *view* di
application/views/news/success.php dan tulislah pesan sukses.

Model
-----

Satu-satunya hal yang tersisa adalah menulis sebuah metode yang menulis data ke database. 
Anda akan menggunakan kelas *Query Builder* untuk memasukkan informasi dan menggunakan *library* 
masukan untuk mendapatkan data yang diposting. Buka model yang dibuat sebelumnya dan tambahkan berikut

::

    public function set_news()
    {
        $this->load->helper('url');
        
        $slug = url_title($this->input->post('title'), 'dash', TRUE);
        
        $data = array(
            'title' => $this->input->post('title'),
            'slug' => $slug,
            'text' => $this->input->post('text')
        );
        
        return $this->db->insert('news', $data);
    }

Metode baru ini mengurus memasukkan berita ke dalam database. 
Baris ketiga berisi fungsi baru, url\_title(). Fungsi ini -
disediakan oleh :doc:`URL helper <../helpers/url_helper>` - *strip down string* yang Anda lewati, ganti semua spasi dengan tanda hubung (-) dan memastikan semuanya dalam huruf kecil.  Hal ini membuat Anda dengan *slug* yang bagus, sempurna untuk menciptakan URI.

Mari kita lanjutkan dengan menyiapkan *record* yang akan dimasukkan kemudian, 
di dalam *array* $data. Setiap elemen sesuai dengan kolom dalam tabel database 
yang dibuat sebelumnya. Anda mungkin melihat metode baru di sini,
yaitu metode post() dari :doc:`input
library <../libraries/input>`. Metode ini memastikan data dibersihkan, 
melindungi Anda dari serangan jahat dari orang lain.  
*Library* masukan dimuat secara default. 
Akhirnya, Anda memasukkan *array* $data kita ke dalam database kita.

Routing
-------

Sebelum Anda dapat mulai menambahkan item berita ke dalam aplikasi CodeIgniter 
Anda Anda harus menambahkan aturan tambahan untuk file config/routes.php. 
Pastikan file Anda mengandung berikut. Hal ini akan memastikan CodeIgniter 
melihat 'menciptakan' sebagai metode bukan *slug* berita ini.

::

    $route['news/create'] = 'news/create';
    $route['news/(:any)'] = 'news/view/$1';
    $route['news'] = 'news';
    $route['(:any)'] = 'pages/view/$1';
    $route['default_controller'] = 'pages/view';

Sekarang arahkan browser Anda ke lingkungan pengembangan lokal Anda di mana Anda menginstal 
CodeIgniter dan menambahkan index.php/news/create ke URL. Selamat, Anda baru saja membuat
aplikasi CodeIgniter pertama Anda! Tambahkan beberapa berita dan memeriksa halaman 
yang berbeda yang Anda buat.