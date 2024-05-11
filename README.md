
LAPORAN PROJEK UTS PRAKTIKUM PCD

1. Deteksi warna pada citra. 

*  Deteksi Warna Biru:
- Dilakukan dengan mengubah citra asli dari ruang warna BGR (Blue, Green, Red) ke ruang warna HSV.
- Tentukan batas atas dan batas bawah untuk warna biru dalam ruang warna HSV.
- Buat mask untuk warna biru dengan menggunakan fungsi cv2.inRange() yang akan menghasilkan citra biner dengan piksel yang sesuai dengan rentang warna biru diatur menjadi putih dan yang lainnya menjadi hitam.
- Terapkan mask biru pada citra asli dengan menggunakan operasi bitwise AND.
- Hasilnya adalah citra yang hanya menampilkan bagian yang memiliki warna biru.

* Deteksi Warna Merah-Biru:
- Proses ini mirip dengan deteksi warna biru, namun juga memperhitungkan rentang warna merah.
- Rentang warna merah kadang melintasi nilai 180 dalam ruang warna HSV, sehingga diperlukan dua rentang untuk menangkap semua warna merah.
- Mask biru dan mask merah digabungkan menggunakan operasi bitwise OR.
- Mask ini kemudian diterapkan pada citra asli untuk menampilkan hanya bagian yang memiliki warna biru atau merah.

* Deteksi Warna Merah-Hijau-Biru:
- Langkah-langkahnya mirip dengan deteksi warna merah-biru, namun juga memperhitungkan rentang warna hijau.
- Mask biru, merah, dan hijau digabungkan menggunakan operasi bitwise OR.
- Mask ini diterapkan pada citra asli untuk menampilkan hanya bagian yang memiliki warna biru, merah, atau hijau.

* Deteksi Tanpa Warna Tertentu (None):
- Dalam proses ini, dilakukan pencarian untuk bagian citra yang bukan biru, merah, atau hijau.
- Rentang warna untuk setiap warna (biru, merah, hijau) ditentukan.
- Mask untuk setiap warna dibuat dan digabungkan menggunakan operasi bitwise OR.
- Mask ini diterapkan pada citra asli untuk menampilkan bagian yang tidak termasuk dalam ketiga kategori warna (biru, merah, hijau).

Setelah deteksi warna, histogram ditampilkan untuk masing-masing saluran warna (merah, hijau, biru) pada citra asli. Histogram memberikan representasi visual dari distribusi intensitas piksel di setiap saluran warna. 

2. Menganalisis Histogram
Analisis Histogram:

* Histogram Asli:
- Histogram ini merepresentasikan distribusi intensitas piksel dalam citra asli. Pada sumbu x, terdapat rentang intensitas piksel dari 0 hingga 255, sementara sumbu y menunjukkan jumlah piksel dengan intensitas tersebut.
- Terlihat bahwa distribusi intensitas pikselnya cukup merata di seluruh rentang intensitas. Ini menandakan bahwa citra memiliki variasi warna dan kecerahan yang cukup baik.

* Histogram Merah:
- Histogram merah menunjukkan distribusi intensitas piksel pada saluran warna merah dari citra.
- Jumlah piksel dengan intensitas rendah (dekat dengan 0) terlihat sedikit, yang menandakan bahwa ada sedikit area dalam citra yang sangat gelap di saluran merah.
- Distribusi intensitas piksel terutama terpusat di sekitar nilai intensitas 100-200, menunjukkan dominasi warna merah dalam citra.

* Histogram Hijau:
- Histogram hijau menggambarkan distribusi intensitas piksel pada saluran warna hijau dari citra.
- Terdapat sedikit piksel dengan intensitas rendah, namun sebagian besar distribusi terpusat di sekitar nilai intensitas 100-200, menandakan dominasi warna hijau dalam citra.
- Terdapat beberapa piksel dengan intensitas tinggi, yang mungkin mengindikasikan kehadiran area yang sangat terang atau sangat terang dalam saluran hijau.

* Histogram Biru:
- Histogram biru menampilkan distribusi intensitas piksel pada saluran warna biru dari citra.
- Seperti histogram merah dan hijau, sebagian besar distribusi terpusat di sekitar nilai intensitas 100-200, yang mengindikasikan dominasi warna biru dalam citra.
- Terdapat sedikit piksel dengan intensitas rendah, dan distribusi intensitas piksel cenderung menurun ke arah intensitas tinggi.

* Kesimpulan:
- Dari analisis histogram, dapat disimpulkan bahwa citra ini memiliki dominasi warna merah, hijau, dan biru yang seimbang, dengan sedikit kecenderungan ke warna merah.
- Distribusi intensitas piksel yang merata di seluruh rentang intensitas menunjukkan bahwa citra memiliki kontras yang baik dan tidak terlalu cenderung ke arah kegelapan atau kecerahan yang ekstrem.
- Namun, adanya sedikit piksel dengan intensitas tinggi atau rendah dalam masing-masing saluran warna menandakan adanya area-area dengan warna yang sangat terang atau sangat gelap dalam citra tersebut.

3. Mencari dan mengurutkan ambang batas terkecil sampai dengan terbesar. 

ada beberapa nilai ambang yang berbeda untuk melihat efeknya terhadap citra. Dalam kode yang diberikan, terdapat empat jenis ambang batas yang diaplikasikan pada citra:

* Ambang Batas Tanpa Penyaringan (NONE):
Dalam ambang batas ini, semua piksel dengan intensitas nilai di bawah ambang batas diatur menjadi hitam, sedangkan yang di atasnya diatur menjadi putih. Nilai ambang batas yang digunakan adalah 0, yang artinya semua piksel dengan intensitas apapun akan dianggap sebagai "di atas" ambang batas dan diatur menjadi putih. Oleh karena itu, hasilnya adalah citra biner yang menampilkan semua detail citra.

* Ambang Batas untuk Warna Biru (BLUE): 
Nilai ambang batas yang digunakan adalah 120. Hal ini berarti bahwa piksel dengan nilai kecerahan di bawah 120 akan dianggap sebagai "di bawah" ambang batas dan diatur menjadi hitam, sedangkan yang di atasnya akan diatur menjadi putih. Ini memungkinkan kita untuk menyorot bagian-bagian dari citra yang memiliki tingkat kecerahan lebih tinggi daripada 120, yang kemungkinan besar mencakup warna biru dan warna lain yang lebih terang.

* Ambang Batas untuk Warna Merah-Biru (RED-BLUE):
Dalam ambang batas ini, kita menggunakan nilai ambang batas 145. Hal ini menghasilkan citra biner yang menyoroti piksel-piksel dengan nilai kecerahan di atas 145, yang mungkin mencakup warna merah dan biru, karena kedua warna tersebut memiliki nilai kecerahan yang relatif tinggi dalam citra.

* Ambang Batas untuk Warna Merah-Hijau-Biru (RED-GREEN-BLUE):
Dalam ambang batas ini, nilai ambang batas yang digunakan adalah 180. Ini berarti bahwa piksel dengan nilai kecerahan di atas 180 akan dianggap sebagai "di atas" ambang batas dan diatur menjadi putih, sedangkan yang di bawahnya diatur menjadi hitam. Hasilnya adalah citra biner yang menyoroti piksel-piksel dengan nilai kecerahan yang tinggi, yang mungkin mencakup warna merah, hijau, dan biru.

Dalam konteks deteksi warna, pemilihan nilai ambang batas didasarkan pada kecerahan relatif dari warna yang ingin dideteksi. Misal, untuk warna yang lebih terang seperti biru langit atau baju berwarna terang, nilai ambang batas yang lebih rendah mungkin lebih sesuai karena kecerahan mereka cenderung lebih tinggi. Sebaliknya, untuk warna yang lebih gelap atau lembut seperti merah gelap atau hijau daun, nilai ambang batas yang lebih tinggi mungkin diperlukan untuk memisahkan warna tersebut dari latar belakang yang lebih gelap.

Karena itu, dalam konteks deteksi warna, pemilihan nilai ambang batas harus memperhitungkan kecerahan relatif dari warna yang ingin dideteksi dan kontrasnya dengan latar belakang. Pemilihan yang tepat dari nilai ambang batas akan memungkinkan untuk menyoroti warna yang diinginkan.


Teori yang mendukung mengenai projek.

Projek ini berfokus pada pemrosesan citra, terutama pada deteksi warna dan analisis histogram dari citra. berikut beberapa teori yang mendasarinya:

* Model Warna:
- Model warna digunakan untuk merepresentasikan warna dalam citra. Salah satu model warna yang umum digunakan adalah RGB (Red, Green, Blue), yang mana setiap piksel direpresentasikan sebagai kombinasi intensitas dari ketiga warna tersebut.
- Namun, dalam beberapa kasus seperti deteksi warna, model warna seperti HSV (Hue, Saturation, Value) lebih sering digunakan. Model ini memisahkan informasi warna dari kecerahan dan kejenuhan, yang membuatnya lebih mudah untuk menangani deteksi warna tanpa terpengaruh oleh perubahan kecerahan.

* Pengolahan Citra:
- Pengolahan citra adalah serangkaian teknik yang digunakan untuk memanipulasi citra agar dapat diinterpretasikan atau dianalisis lebih lanjut. Ini mencakup operasi seperti peningkatan kontras, deteksi tepi, pemisahan warna, dan banyak lagi.
- Salah satu teknik yang digunakan dalam proyek ini adalah peningkatan kontras. Peningkatan kontras dapat dilakukan dengan berbagai cara, termasuk penambahan atau pengurangan nilai piksel.

* Deteksi Warna:
- Deteksi warna adalah proses identifikasi dan isolasi area dalam citra yang memiliki warna tertentu.
- Dalam proyek ini, deteksi warna dilakukan dengan menentukan rentang nilai untuk masing-masing komponen warna dalam model HSV, lalu membuat mask untuk setiap rentang warna tersebut.
- Operasi bitwise seperti OR digunakan untuk menggabungkan mask dari warna yang berbeda, sehingga menghasilkan mask yang menunjukkan area di mana salah satu atau lebih dari satu warna yang diinginkan hadir.

* Ambang Batas (Thresholding):
- Ambang batas adalah teknik pemrosesan citra yang digunakan untuk mengubah citra menjadi citra biner, di mana piksel diubah menjadi hitam atau putih berdasarkan apakah mereka melewati ambang tertentu.
- Dalam proyek ini, ambang batas digunakan untuk membuat citra biner dari citra kecerahan yang telah ditingkatkan, serta untuk memisahkan warna berdasarkan ambang tertentu.

* Histogram:
- Histogram adalah representasi visual dari distribusi intensitas piksel dalam citra.
- Histogram membantu untuk memahami sebaran intensitas piksel dalam citra, yang berguna untuk analisis kontras, pencahayaan, dan distribusi warna.
- Dalam proyek ini, histogram digunakan untuk menganalisis distribusi intensitas piksel untuk masing-masing saluran warna (merah, hijau, biru) dalam citra asli.

* Teori Warna:
- Untuk pemahaman yang lebih dalam tentang deteksi warna, penting untuk memahami teori warna, seperti lingkaran warna, konsep warna primer, sekunder, dan tersier, serta bagaimana warna dipersepsikan oleh mata manusia.

* Analisis Citra:
- Analisis citra adalah bidang studi yang luas yang melibatkan pemahaman, pengembangan, dan implementasi algoritma untuk ekstraksi informasi dari citra.
- Proyek ini mencakup beberapa aspek analisis citra, termasuk deteksi warna, ambang batas, dan analisis histogram.

* Pengenalan Objek:
Pengenalan objek adalah proses mendeteksi dan mengidentifikasi objek dalam gambar. Dalam konteks gambar baju, pengenalan objek dapat digunakan untuk mendeteksi logo merek, label ukuran, atau aksesoris pada baju. Algoritma pengenalan objek yang umum digunakan meliputi:

- Template Matching: Algoritma ini membandingkan gambar baru dengan template yang telah disimpan sebelumnya untuk menemukan objek yang sama.
- Deteksi Fitur: Algoritma ini mendeteksi fitur seperti tepi, sudut, dan titik kunci dalam gambar dan menggunakannya untuk mengidentifikasi objek.
- Deep Learning: Algoritma deep learning, seperti CNN, dapat dilatih untuk mendeteksi dan mengidentifikasi objek dalam gambar dengan tingkat akurasi yang tinggi.

* Penerapan Praktis:
- Projek ini juga memiliki aspek praktis yang melibatkan pengujian, penyesuaian parameter, dan interpretasi hasil deteksi warna serta analisis histogram.

