#####################
Model-View-Controller
#####################

CodeIgniter didasarkan pada pola pengembangan MVC. MVC adalah pendekatan perangkat lunak yang memisahkan logika aplikasi dari presentasi. Dalam prakteknya, itu memungkinkan halaman web Anda mengandung scripting minimal karena presentasi terpisah dari scripting PHP.

-  **Model** mewakili struktur data Anda. Biasanya kelas model Anda akan 
   berisi fungsi yang membantu Anda mengambil, memasukkan, dan memperbarui 
   informasi dalam database Anda.
-  **View** adalah informasi yang sedang disajikan kepada pengguna.  
   Sebuah *View* biasanya akan menjadi halaman web, tetapi dalam CodeIgniter, 
   view juga bisa menjadi fragmen halaman seperti header atau footer.  
   Hal ini juga dapat menjadi halaman RSS, atau jenis lain dari "halaman".
-  **Controller** berfungsi sebagai *perantara* antara *Model*, *View*, dan 
   sumber daya lain yang diperlukan untuk memproses permintaan HTTP 
   dan menghasilkan halaman web.

CodeIgniter memiliki pendekatan yang cukup longgar untuk MVC sejak *Model* yang tidak diperlukan.  Jika Anda tidak perlu pemisahan menambahkan, atau menemukan bahwa mempertahankan model memerlukan kompleksitas dari yang Anda inginkan, Anda dapat mengabaikan mereka dan membangun aplikasi Anda minimal menggunakan *Controller* dan *Views*. CodeIgniter juga memungkinkan Anda untuk memasukkan script Anda sendiri, atau bahkan mengembangkan *library* inti untuk sistem, yang memungkinkan Anda untuk bekerja dengan cara yang paling masuk akal untuk Anda.
