############################
Tujuan Desain dan Arsitektur 
############################

Tujuan kami untuk CodeIgniter adalah kinerja maksimum, kemampuan, dan fleksibilitas dalam terkecil, paket teringan ungkin.

Untuk memenuhi tujuan ini kami berkomitmen untuk benchmarking, *re-factoring*, dan menyederhanakan pada setiap langkah dari proses pembangunan, menolak apa-apa
yang tidak melanjutkan tujuan lain.

Dari sudut pandang teknis dan arsitektur, CodeIgniter diciptakan dengan tujuan berikut:

-  **Dynamic Instantiation.** Dalam CodeIgniter, komponen dimuat dan *routines* dijalankan hanya bila 
   diminta, daripada secara global. Tidak ada asumsi yang dibuat oleh sistem mengenai apa yang
   mungkindiperlukan luar inti minimal sumber daya, sehingga sistem ini sangat ringan secara default.
   *Event*, yang dipicu oleh permintaan HTTP, dan *controllers* dan *views* yang Anda desain akan 
   menentukan apa yang dipanggil.
-  **Loose Coupling.** *Coupling* adalah gelar untuk komponen sistem bergantung satu sama lain.
   Komponen kurang bergantung pada satu sama lain yang lebih dapat digunakan kembali dan fleksibel
   sistem. Tujuan kami adalah sistem yang sangat *loosely coupled*.
-  **Component Singularity.** *Singularity* adalah gelar untuk komponen yang memiliki tujuan sempit 
   terfokus. Dalam CodeIgniter, masing-masing kelas dan fungsi-fungsi yang sangat otonom untuk
   memungkinkan kegunaan maksimum .

CodeIgniter adalah sebuah sistem yang *dynamically instantiated*, *loosely coupled system* dengan *component singularity* yang tinggi. CodeIgniter berusaha untuk kesederhanaan, fleksibilitas dan kinerja tinggi dalam paket footprint kecil.
