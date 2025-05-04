# Sistem Rekomendasi Wisata di Indonesia

- **Nama:** Baiq Ega Aulia
- **Email:** baiqusbypkp@gmail.com
- **ID Dicoding:** Baiq Ega Aulia


# Project Overview

Perkembangan teknologi membawa perubahan yang pesat, sehingga memungkinkan akses informasi menjadi lebih mudah. Salah satu sektor yang mengalami dampak dari perkembangan ini adalah pariwisata. Indonesia memiliki potensi wisata yang sangat luas dengan berbagai destinasi menarik yang tersedia. Namun, banyaknya pilihan sering kali membuat wisatawan kesulitan menentukan tujuan yang paling sesuai untuk dikunjungi. Oleh karena itu, diperlukan sistem rekomendasi yang dapat membantu wisatawan menemukan destinasi yang selaras dengan preferensi mereka. Proyek ini bertujuan untuk mengembangkan sistem rekomendasi destinasi wisata di Indonesia dengan menggunakan dataset yang memuat informasi rinci mengenai berbagai tempat wisata di negara ini.

Referensi: [Jurnal rekomendasi wisata](https://ejournal.unama.ac.id/index.php/jurnalmsi/article/download/1262/1071).


# Business Understanding

## Problem Statement

Berdasarkan latar belakang yang dijelaskan di atas, rumusan masalah yang didapatkan sebagai berikut:
1. Bagaimana sistem dapat merekomendasikan destinasi wisata di Indonesia berdasarkan deskripsi, kategori, dan fasilitas yang tersedia di dataset?
2. Bagaimana sistem dapat menyederhanakan proses pencarian informasi dan memberikan rekomendasi yang relevan secara efisien?

## Goals
Berdasarkan rumusan masalah yang dijelaskan di atas, tujuan dari projek ini adalah sebagai berikut:
1. Membangun sistem rekomendasi yang efektif menggunakan informasi deskripsi, kategori, dan fasilitas destinasi.
2. Membangun sistem rekomendasi yang efisien dan efektif menggunakan rating destinasi wisata.

## Solution 
Berdasarkan tujuan di atas, ada beberapa solusi yang bisa dilakukan, yaitu:
1. Menerapkan Content-Based Filtering untuk merekomendasikan destinasi yang serupa dengan destinasi yang sebelumnya disukai oleh pengguna, berdasarkan deskripsi dan fitur destinasi tersebut (misalnya, kategori, fasilitas).
2. Menerapkan Collaborative Filtering untuk merekomendasikan destinasi berdasarkan preferensi pengguna lain yang memiliki selera yang mirip. Dalam konteks ini, gunakan user-item interaction untuk memprediksi rating yang mungkin diberikan user ke suatu destinasi.


# Data Understanding

## Deskripsi Dataset
Dataset pada projek ini diambil dari kaggle, yaitu [Sistem Rekomendasi Wisata](https://www.kaggle.com/datasets/aprabowo/indonesia-tourism-destination?select=tourism_with_id.csv). Pada dataset ini berisi 4 *file* dengan nama `package_tourism`, `tourism_rating`, `tourism_with_id`, dan `user` dengan ekstensi `csv` `(*Comma Separated Values*)`,dengan masing-masing banyaknya data yaitu 100 data dan 7 variabel untuk `package_tourism(package)`, 10000 data dan 3 variabel untuk `tourism_rating(rating)`, 437 data dan 13 variabel untuk `tourism_with_id(location)`, serta 300 data dan 3 variabel untuk `user`.
Berikut adalah penjelasan variabel dari masing-masing dataset:
### package_tourism(package)
Berikut merupakan deskripsi variabel dari dataset `package_tourism(package)`:
- Package: ID unik untuk setiap paket wisata.
- City: Kota di mana tempat wisata berada.
- Place_Tourism1 : Destinasi wisata pertama yang termasuk dalam paket
- Place_Tourism2 : Destinasi wisata kedua yang termasuk dalam paket
- Place_Tourism3 : Destinasi wisata ketiga yang termasuk dalam paket
- Place_Tourism4 : Destinasi wisata keempat yang termasuk dalam paket
- Place_Tourism5 : Destinasi wisata kelima yang termasuk dalam paket
### tourism_rating(rating)
Berikut merupakan deskripsi variabel dari dataset `tourism_rating(rating)`:
- User_Id       : ID unik untuk setiap user.
- Place_Id      : ID unik untuk setiap tempat wisata.
- Place_Ratings : Rating untuk setiap tempat wisata dari user.
### tourism_with_id(location)
- Place_Id      : ID unik untuk setiap tempat wisata.
- Place_Name    : Nama tempat wisata.
- Description   : Deskripsi singkat mengenai tempat wisata.
- Category      : Kategori tempat wisata (misalnya, Budaya, Taman Hiburan, Cagar Alam).
- City          : Kota di mana tempat wisata berada.
- Price         : Harga tiket masuk ke tempat wisata (dalam rupiah).
- Rating        : Penilaian rata-rata dari pengunjung (skala 1-5).
- Time_Minutes  : Waktu yang diperlukan untuk mengunjungi tempat wisata (dalam menit).
- Coordinate    : Koordinat geografis tempat wisata.
- Lat           : Garis lintang lokasi tempat wisata.
- Long          : Garis bujur lokasi tempat wisata.
- Unnamed: 11   : Tidak diketahui.
- Unnamed: 12   : Tidak diketahui.
### user
- User_Id       : ID unik untuk setiap pengguna.
- Location      : Kota atau lokasi asal pengguna.
- Age           : Usia pengguna.

## Import Libraray
Pada tahap ini, dilakukan import seluruh library python yang diperlukan dalam pengembangan projek

## Data Loading
Pada tahap, dilakukan pengabilan dataset. Dataset yang digunakan adalah Dataset Sistem Rekomendasi Wisata

Dataset destinasi wisata Indonesia terdiri dari empat sub-dataset, yaitu paket wisata, penilaian, lokasi, dan pengguna. Masing-masing sub-dataset memiliki jumlah data yang berbeda, yaitu 100 data untuk paket wisata, 10.000 data untuk penilaian, 437 data untuk lokasi, dan 300 data untuk pengguna.

## Exploratory Data Analysis
Pada tahap ini, akan dilakukan identifikasi jumlah data serta pemeriksaan beberapa kolom di seluruh dataset yang tersedia. Sebagai langkah awal, pengecekan akan difokuskan pada empat dataset untuk memastikan kualitas dan kesesuaian data sebelum proses analisis lebih lanjut.

### package

![2]()


![3]()

Berikut adalah hasil variabel dalam dataset **package**:

- **Package**: Nomor identifikasi unik untuk setiap paket wisata.  
- **City**: Kota tempat destinasi wisata berada.  
- **Place_Tourism1**: Destinasi wisata pertama dalam paket.  
- **Place_Tourism2**: Destinasi wisata kedua dalam paket.  
- **Place_Tourism3**: Destinasi wisata ketiga dalam paket.  
- **Place_Tourism4**: Destinasi wisata keempat dalam paket.  
- **Place_Tourism5**: Destinasi wisata kelima dalam paket.  

Dataset **package** terdiri dari 100 entri dengan 7 variabel, di mana variabel **Place_tourism4** dan **Place_tourism5** mengandung nilai **null**. Selain itu, dataset ini mencakup 5 nilai unik pada variabel **City**, yaitu **Jakarta, Yogyakarta, Bandung, Semarang, dan Surabaya**, dengan masing-masing kota memiliki **20 paket wisata**.

### rating

![4]()


![5]()

Berikut adalah variabel dalam dataset **rating**:

- **User_Id**: Nomor identifikasi unik yang diberikan kepada setiap pengguna.  
- **Place_Id**: Nomor identifikasi unik yang digunakan untuk setiap destinasi wisata.  
- **Place_Ratings**: Penilaian yang diberikan oleh pengguna untuk setiap tempat wisata.  

Dataset **rating** terdiri dari **10.000 data** dengan **3 variabel**. Dalam dataset ini, terdapat **300 nilai unik** pada variabel **User_Id** serta **5 nilai unik** pada variabel **Place_Ratings**, yaitu **1, 2, 3, 4, dan 5**. Dari kelima nilai rating tersebut, rating **4** memiliki jumlah data tertinggi dibandingkan yang lain, meskipun selisihnya relatif kecil.

### location

![6]()


![7]()

Berikut adalah variabel dalam dataset **location**:

- **Place_Id**: Identifikasi unik untuk setiap destinasi wisata.  
- **Place_Name**: Nama dari tempat wisata tersebut.  
- **Description**: Ringkasan singkat yang menjelaskan tempat wisata.  
- **Category**: Jenis kategori destinasi wisata (contoh: Budaya, Taman Hiburan, Cagar Alam).  
- **City**: Kota tempat wisata berada.  
- **Price**: Biaya tiket masuk ke destinasi wisata (dalam rupiah).  
- **Rating**: Rata-rata penilaian dari pengunjung, dengan skala 1 hingga 5.  
- **Time_Minutes**: Perkiraan durasi kunjungan ke tempat wisata (dalam menit).  
- **Coordinate**: Koordinat geografis lokasi wisata.  
- **Lat**: Garis lintang dari lokasi wisata.  
- **Long**: Garis bujur dari lokasi wisata.  
- **Unnamed: 11**: Informasi tidak diketahui.  
- **Unnamed: 12**: Informasi tidak diketahui.  

Dataset **location** memiliki **437 data** dan terdiri dari **13 variabel**, mencerminkan jumlah unik destinasi wisata yang dicakup. Terdapat beberapa nilai **null** pada kolom **Time_Minutes** dan **Unnamed: 11**. Selain itu, dalam variabel **Category** terdapat **6 nilai unik**, yaitu **Budaya, Taman Hiburan, Cagar Alam, Bahari, Pusat Perbelanjaan, dan Tempat Ibadah**. Dari kategori tersebut, **Taman Hiburan** memiliki jumlah data tertinggi, yaitu **135 entri**.

### user

![8]()


![9]()


![10]()

Berikut adalah variabel dalam dataset **user**:

- **User_Id**: Identifikasi unik untuk setiap pengguna.  
- **Location**: Kota atau daerah asal pengguna.  
- **Age**: Usia pengguna.  

Dataset **user** terdiri dari **300 data** dengan **3 variabel**, mencerminkan jumlah unik pengguna yang tercatat. Variabel **Location** memiliki **28 nilai unik**, menunjukkan beragam daerah asal pengguna. Selain itu, variabel **Age** mencakup rentang usia antara **24 hingga 40 tahun**. Sementara itu, **5 pengguna dengan jumlah rating terbanyak** berasal dari **Bekasi, Semarang, Yogyakarta, Lampung, dan Bogor**.


# Data Preparation
Pada tahap ini akan dibuat dataframe yang siap untuk EDA lanjutan, *content based filtering* dan *Collaborative Filtering*. Hal ini penting dilakukan karena untuk memastikan data bersih, terhindar dari *error*, dan memastikan model bekerja lebih efektif. 

## Data Preprocessing untuk EDA
Pada tahap ini akan dilakukan langkah-langkah berikut:
1. Mengetahui jumlah *user* dan *location*
2. Mengetahui jumlah rating

Berikut merupakan penjelasan dari masing-masing tahap:

### Mengecek total user dan location
Pada tahap ini, empat dataset dibagi menjadi dua kelompok, yaitu **user** dan **location** (tempat wisata). Selanjutnya, dataset **rating_df** dan **user_df** digabungkan untuk memperoleh total jumlah pengguna, sedangkan dataset **location_df** dan **rating_df** digabungkan untuk menentukan total destinasi wisata.  

Selain itu, penggabungan dataset **user** dilakukan untuk menghitung jumlah keseluruhan pengguna yang terdaftar.  

![11]()

Jumlah total pengguna tercatat sebanyak 300 user.

Selanjutnya, dilakukan penggabungan dataset location untuk menentukan jumlah keseluruhan destinasi wisata yang ada.

![12]()

Jumlah total destinasi wisata yang tercatat dalam dataset location adalah 437 data.

### Mengecek jumlah rating
Selanjutnya, akan dibuat variabel baru, yaitu place, dengan menggabungkan data rating dan place untuk melihat banyaknya rating dari gabungan data yang ada, pada kasus ini data rating_df dan location_df. Setelah itu, akan dicoba mengecek variabel setelah penggabungan data. Terlihat bahwa variabel memiliki 10000 data rating dari gabungan dataset rating_df dan location_df, serta data ini memiliki nilai null pada kolom time_minutes dan Unnamed: 11. Setelah itu  akan diambil fitur numerik terlebih dahulu, kemudian akan dicari jumlah dari fitur numerik tersebut berdasarkan Place-Id. Berikut adalah hasil dari proses ini, yaitu melihat total rating:

![13]()


## Data Preprocessing untuk *Content Based Filtering*
Pada tahap ini akan dilakukan langkah-langkah berikut:
1. Membuat dataframe untuk Modeling *Content Based Filtering* 
2. Mengecek nilai null
3. Mengecek nilai duplikat
4. Mengecek deskripsi analisis dan banyaknya data unik
5. Mengecek kembali data untuk *Content Based Filtering*
6. Mengecek nilai unik dari kolom Category
7. Menghapus duplikat pada Place_Id
8. Membuat data dictionary untuk modeling
9. TF-IDF

Berikut merupakan penjelasan dari masing-masing tahap:
### Membuat dataframe untuk Modeling *Content Based Filtering*
Pada tahap ini, akan dibuat dataframe untuk pembuatan sistem dengan metode *Content Based Filtering*. Langkah pertama akan dibuat dataframe bernama `all_place_name` dengan data dari `rating_df`. Setelah itu, gabungkan dataframe ini dengan kolom `place_name`, `category`, dan `city` dari tabel *location_df* dengan kunci `Place_Id`. Setelah itu akan digabungkan lagi dengan kolom `age` dari tabel *user_df* dengan kunci `User_Id`. Hasil akhir 4 data pertama dataframe ini yaitu:

![14]()


### Memeriksa Nilai Null
Langkah selanjutnya adalah melakukan pengecekan terhadap nilai null, kemudian menganalisis deskripsi fitur numerik. Selain itu, dilakukan pemeriksaan terhadap jumlah data unik dalam kolom Place_Id, Place_Name, dan Category.

![15]()

Terlihat bahwa data tidak memiliki nilai null, sehingga bisa lanjut ke tahap berikutnya. 

### Memeriksa Data Duplikat
Langkah selanjutnya adalah melakukan pengecekan terhadap nilai duplikat dalam dataset untuk memastikan integritas dan keakuratan data yang digunakan.

![24]()


Terlihat bahwa data tidak memiliki nilai null, sehingga perlu untuk menghapus nilai duplikat tersebut dengan fungsi `drop_duplicated()`

### Memeriksa Deskripsi Analisis dan Jumlah Data Unik
Pada tahap ini, dilakukan analisis deskriptif terhadap dataset serta pengecekan jumlah data unik pada kolom Place_Id, Place_Name, dan Location untuk memahami distribusi dan karakteristik data yang tersedia.
Berikut merupakan deskripsi analisis dari data numerik ini:

![16]()

Berikut merupakan deskripsi analisis dari data numerik ini:

![17]()

Hasilnya, data telah dipastikan bersih dari **nilai null** dan memiliki **437 nilai unik** pada kolom **Place_Id** serta **Place_Name**. Selain itu, terdapat **6 nilai unik** pada **Category**. Dataset ini juga mencakup **300 pengguna** dengan rentang **rating** antara **1 hingga 5**.  

### Memeriksa Kembali Data untuk Content-Based Filtering
Pada tahap ini, dilakukan pengecekan ulang terhadap data yang telah melalui proses preprocessing sebelumnya. Setelah itu, data akan diurutkan berdasarkan Place_Id untuk memastikan struktur yang sesuai dengan kebutuhan analisis lebih lanjut.
 Berikut adalah 5 data pertama data tersebut:

![18]()

### Memeriksa Nilai Unik pada Kolom Category
Langkah berikutnya adalah melakukan pengecekan terhadap nilai unik dalam kolom Category untuk memastikan keberagaman dan keberadaan berbagai kategori tempat wisata yang tersedia dalam dataset.

![19]()

Data dalam dataset memiliki berbagai kategori tempat wisata, yaitu Budaya, Taman Hiburan, Cagar Alam, Pusat Perbelanjaan, dan Tempat Ibadah.

### Menghapus Duplikasi pada Place_Id
Langkah berikutnya adalah membuat variabel preparation yang akan berisi data dari all_place_name. Setelah itu, data diurutkan berdasarkan Place_Id untuk memastikan struktur yang lebih terorganisir dan siap untuk analisis lebih lanjut.

### Membuat data dictionary untuk modeling
Pada tahap ini akan dikonversi data series menjadi list, sehingga akan menggunakan fungsi tolist untuk konversi data. Setelah itu membuat data dictionary untuk data place_id, place_name, dan place_cat(place_category). Lalu akan dicek data yang telah dibuat. Berikut merupakan 5 data pertama untuk modeling. 

![20]()

Dataframe ini telah siap untuk Langkah selanjutnya. 

### Ekstraksi TF-IDF
Ekstraksi TF-IDF (Term Frequency-Inverse Document Frequency) adalah teknik yang digunakan untuk mengubah teks menjadi representasi numerik dengan mempertimbangkan seberapa sering suatu kata muncul dalam suatu dokumen dibandingkan dengan keseluruhan dokumen.
 Berikut merupakan hasil TF-IDF yang berhasil dibuat:

![21]()

Sebagai contoh, **Museum Nike Ardilla** memiliki nilai **1** pada kategori **Budaya**, yang menandakan bahwa museum tersebut termasuk dalam kategori **Budaya**, dan konsep ini berlaku untuk destinasi lainnya. 

## Data Preprocessing untuk *Collaborative Filtering*
Pada tahap ini akan dilakukan langkah-langkah berikut:
1. Membuat dataframe untuk Modeling *Collaborative Filtering* 
2. Acak data
3. Membagi data menjadi data train dan data test

### Membuat Dataframe untuk Modeling Collaborative Filtering
Langkah pertama dalam proses ini adalah membuat variabel df yang berisi dataset rating_df, yang akan digunakan sebagai dasar dalam penerapan metode Collaborative Filtering.Berikut merupakan hasil encode User_Id:

![26]()

Setelah itu, dilakukan persiapan data untuk menyandikan (encode) fitur Place_Id ke dalam indeks integer. Berikutnya dilakukan pemetaan userID dan placeID ke dataframe yang berkaitan. Setelah itu mengecek beberapa hal dalam data seperti jumlah user, jumlah tempat wisata, dan mengubah nilai rating menjadi float. Berikut merupakan hasil pengecekan banyaknya *user* dan *place*:

![27]()

Terlihat bahwa dataframe memiliki data *user* sebanyak 300 data, data *place* sebanyak 437 data, serta data rating dari 1.0 sampai 5.0.

### Mengacak Data
Langkah berikutnya adalah mengacak data untuk memastikan distribusinya menjadi random, sehingga model dapat belajar dari berbagai pola tanpa bias terhadap urutan asli data. Berikut adalah hasil 5 data pertama dari acak data:

![28]()

### Membagi Data Train dan Data Validation
Langkah berikutnya adalah membagi data train dan data validasi dengan komposisi 80:20 dari data yang telah melalui tahap data preparation.
Sebelum melakukan pembagian, lakukan pemetaan (mapping) data user dan place agar setiap nilai pengguna dan tempat wisata direpresentasikan sebagai satu value. Selain itu, ubah rating ke dalam skala 0 sampai 1 untuk mempermudah proses training model.

# Modeling and Result
Pada tahap ini akan digunakan metode *Content Based Filtering* dan *Collaborative Filtering* untuk menjawab problem statement dari tahap business understanding

## *Content-Based Filtering* Menggunakan *Cosine Similarity*

*Content-Based Filtering* merupakan metode yang digunakan dalam sistem rekomendasi dengan menitikberatkan pada karakteristik dari item yang akan direkomendasikan. Teknik ini memanfaatkan atribut atau fitur dari item tersebut untuk mengukur kemiripan dengan preferensi pengguna. Tahapan prosesnya meliputi:

### 1. *Cosine Similarity*

*Cosine Similarity* adalah teknik pengukuran kemiripan antar dua vektor berdimensi tinggi yang umum digunakan dalam pembelajaran mesin dan analisis data. Ukuran ini mengkalkulasi nilai kosinus dari sudut antara dua vektor, untuk mengetahui sejauh mana arah keduanya serupa, tanpa memperhatikan besarannya. Pada tahap ini, dilakukan penghitungan tingkat kemiripan antar tempat wisata menggunakan metode *cosine similarity*. Kemudian, ditampilkan matriks kemiripan antara objek wisata, dengan 5 kolom (axis = 1) dan 10 baris (axis = 0). Berikut hasil visualisasinya:

![22]()

Sebagai contoh, Curug Cipanas memiliki tingkat kemiripan sebesar 1 dengan Bumi Perkemahan Batu Kuda dan Umbul Sidomukti, yang mengindikasikan bahwa ketiganya memiliki kategori yang sama.

### 2. Pembuatan Fungsi Rekomendasi dan Hasilnya

Selanjutnya dibuat fungsi untuk menghasilkan rekomendasi berdasarkan input nama tempat wisata. Fungsi ini akan menampilkan lima tempat wisata yang paling relevan. Berikut adalah contoh input rekomendasi:

![23]()

Dan berikut adalah hasil rekomendasi yang diberikan oleh sistem:

![25]()

Hasil menunjukkan bahwa sistem merekomendasikan tempat wisata yang berada dalam kategori serupa, yaitu cagar alam.

### Kelebihan dan Kekurangan

Kelebihan utama dari *content-based filtering* adalah kemampuannya dalam memberikan rekomendasi yang bersifat personal dan dapat dijelaskan. Namun, metode ini memiliki kelemahan dalam hal keberagaman, yakni kurang efektif dalam menyarankan item yang sangat berbeda dari preferensi pengguna sebelumnya.

## *Collaborative Filtering*

*Collaborative Filtering* adalah pendekatan dalam sistem rekomendasi yang mengandalkan interaksi historis pengguna terhadap sejumlah item. Pendekatan ini tidak memerlukan atribut produk secara eksplisit, melainkan menggunakan representasi vektor dari pengguna dan item dalam ruang laten yang sama. Proses pengembangan model dilakukan melalui beberapa tahapan sebagai berikut:

### 1. Proses Pelatihan Model

Langkah awal adalah membangun model *RecommenderNet* menggunakan class `Model` dari pustaka Keras. Model kemudian dikompilasi menggunakan fungsi kerugian `binary_crossentropy`, optimasi `adam`, dan metrik evaluasi berupa RMSE. Setelah itu, dilakukan pelatihan menggunakan data yang telah disiapkan.

### 2. Visualisasi Proses Pelatihan

Untuk memantau performa model selama pelatihan, dibuat grafik visualisasi menggunakan *matplotlib* yang menampilkan metrik evaluasi. Berikut adalah hasil visualisasinya:

![29]()

### 3. Proses Rekomendasi

Sebelum menghasilkan rekomendasi, disiapkan terlebih dahulu daftar tempat wisata yang belum dikunjungi oleh pengguna, karena item inilah yang akan direkomendasikan. Kemudian dilakukan prediksi untuk menghasilkan 10 tempat wisata dengan skor tertinggi. Berikut adalah hasil rekomendasinya:

![30]()
### Kelebihan dan Kekurangan

Dibandingkan *content-based filtering*, metode *collaborative filtering* lebih unggul dalam memberikan rekomendasi yang lebih beragam karena memanfaatkan pola interaksi dari pengguna lain dengan minat serupa. Namun, metode ini memiliki kelemahan yaitu *cold start problem*, yang terjadi ketika ada pengguna atau item baru yang belum memiliki riwayat interaksi, sehingga sistem kesulitan dalam memberikan rekomendasi yang relevan.


# Evaluation

Tahapan ini digunakan untuk mengukur seberapa baik kinerja dari sistem rekomendasi yang dikembangkan. Dalam proyek ini, evaluasi dilakukan pada dua pendekatan, yaitu *Content-Based Filtering* yang dinilai menggunakan metrik *Precision*, dan *Collaborative Filtering* yang dievaluasi melalui nilai RMSE.

## Evaluasi Model *Content-Based Filtering* dengan *Precision*

Sebelum membahas *Precision*, perlu dipahami terlebih dahulu mengenai *Confusion Matrix*. *Confusion Matrix* merupakan alat ukur performa dalam permasalahan klasifikasi pada machine learning, khususnya ketika hasil keluaran terdiri dari dua atau lebih kelas. Matriks ini berbentuk tabel yang terdiri atas empat kombinasi antara nilai prediksi dan nilai aktual, yang direpresentasikan dengan istilah berikut:

* **True Positive (TP):**
  Prediksi positif dan memang benar.
* **True Negative (TN):**
  Prediksi negatif dan sesuai kenyataan.
* **False Positive (FP)** (*Kesalahan Tipe 1*):
  Prediksi menunjukkan positif, namun kenyataannya salah.
* **False Negative (FN)** (*Kesalahan Tipe 2*, yang tergolong serius):
  Prediksi menunjukkan negatif, namun sebenarnya salah.

Salah satu metrik yang dapat diperoleh dari *Confusion Matrix* adalah *Precision*. *Precision* merupakan metrik penting dalam menilai sistem pencarian informasi karena mengukur tingkat ketepatan model dalam merekomendasikan item yang relevan dengan kebutuhan pengguna. Oleh karena itu, *Precision* menjadi metrik yang tepat untuk mengevaluasi pendekatan *Content-Based Filtering*. Rumus *Precision* untuk sistem rekomendasi dapat dilihat pada gambar berikut:

![31]()

Dalam konteks sistem rekomendasi, *Precision\@K* dihitung sebagai rasio antara jumlah item relevan yang berhasil direkomendasikan dengan total item yang disarankan dalam daftar sepanjang K. Artinya, metrik ini menunjukkan seberapa banyak item yang direkomendasikan ternyata benar-benar relevan. Rumus lengkapnya dapat dilihat di bawah ini:

![32]()

Mengacu pada rumus tersebut, dilakukan penghitungan *Precision* pada sistem rekomendasi berbasis *Content-Based Filtering*. Berikut adalah data input yang digunakan:

![23]()

Data tersebut menggunakan tempat wisata "Kebun Binatang Ragunan" yang memiliki kategori *Cagar Alam*. Berdasarkan data input ini, sistem memberikan lima rekomendasi seperti yang terlihat berikut:

![25]()

Dari hasil di atas, dapat dilihat bahwa kelima rekomendasi memiliki kategori yang sama, yaitu *Cagar Alam*. Maka, berdasarkan rumus sebelumnya:

```
precision = jumlah item relevan dalam K / total item dalam K
precision = 5 / 5
precision = 1
```

Artinya, sistem rekomendasi berbasis *Content-Based Filtering* menghasilkan nilai *Precision* sebesar **1**, yang menunjukkan bahwa seluruh item yang direkomendasikan benar-benar relevan. Ini menandakan bahwa model bekerja dengan sangat baik.

## Evaluasi Model *Collaborative Filtering* dengan RMSE

Untuk mengevaluasi model *Collaborative Filtering*, digunakan metrik RMSE (*Root Mean Square Error*) karena RMSE cocok dalam mengevaluasi prediksi numerik seperti prediksi rating pengguna. RMSE sendiri merupakan ukuran deviasi standar dari selisih antara nilai prediksi dan nilai aktual. Karena formula RMSE sejatinya merupakan bentuk standar dari deviasi residual, maka rumus ini umumnya sudah dikenal dalam analisis statistik. Rumus tersebut menghitung seberapa besar penyimpangan antara nilai observasi dan prediksi. Berikut adalah rumus dari RMSE:

![33]()

Keterangan:

* *yi* adalah nilai aktual untuk observasi ke-i
* *ŷi* adalah nilai prediksi dari observasi ke-i
* *P* merupakan jumlah parameter yang diestimasi (termasuk konstanta)
* *N* adalah jumlah total observasi

RMSE digunakan untuk menilai performa model berdasarkan seberapa besar kesalahan saat proses pelatihan berlangsung. Di bawah ini ditampilkan visualisasi hasil pelatihan model pada proyek ini:

![29]()

Berdasarkan grafik di atas, diperoleh nilai RMSE pada data pelatihan sebesar **0.3144**, dan nilai RMSE pada data validasi sebesar **0.3661**. Ini menunjukkan bahwa model *Collaborative Filtering* yang dibangun telah menunjukkan kinerja yang baik dalam menghasilkan prediksi rating yang akurat.


# Kesimpulan 

Proyek ini berhasil mengembangkan **sistem rekomendasi tempat wisata** menggunakan dua pendekatan utama: *Content-Based Filtering* dan *Collaborative Filtering*.  
Selama proses pengerjaan, berbagai tahapan telah dilakukan, termasuk **Data Understanding, Data Preparation, Modeling**, serta **Evaluasi Model** untuk memastikan sistem bekerja secara optimal.  
Pada pendekatan **Content-Based Filtering**, hasil evaluasi menunjukkan performa yang sangat baik, sehingga sistem berhasil memberikan rekomendasi yang akurat berdasarkan informasi **deskripsi, kategori, dan fasilitas destinasi wisata**.  
Sementara itu, dalam **Collaborative Filtering**, hasil evaluasi juga cukup baik, sehingga sistem rekomendasi dapat bekerja secara efisien dengan memanfaatkan **rating destinasi wisata** untuk memberikan rekomendasi yang relevan.  
Namun, proyek ini masih memiliki keterbatasan karena ukuran dataset yang terbatas. Hal ini menyebabkan kemungkinan model memberikan rekomendasi yang kurang sesuai dengan input yang diberikan pengguna.  


# Reference
- Raysa Puteri Ardhiyani, Herry Mulyono. 2018. ANALISIS DAN PERANCANGAN SISTEM INFORMASI PARIWISATA BERBASIS WEB SEBAGAI MEDIA PROMOSI PADA KABUPATEN TEBO . Jurnal Manajemen Sistem Informasi. Vol.3, No.1, Maret 2018
- Dwi Septiani, Ica Isabela. 2022. ANALISIS TERM FREQUENCY INVERSE DOCUMENT FREQUENCY(TF-IDF) DALAM TEMU KEMBALI INFORMASI PADA DOKUMEN TEKS. SINTESIA: Jurnal Sistem dan Teknologi Informasi Indonesia. Vol. 01, No. 2, Maret 2022.
- geeksforgeeks.org. (2024, 10 Oktober). Cosine Similarity. Diakses pada 15 Januari 2025, dari https://www.geeksforgeeks.org/cosine-similarity/
- Sadesty Rahmadhani, LutfiHakim, GalihHendra Wibowo, Sepyan Purnama Kristanto, Eka Mistiko Rini. 2024. SISTEM REKOMENDASI PENELUSURAN BUKU BERBASIS CONTENT-BASED FILTERINGDENGAN PEMBOBOTAN TF-RF. Volume 10, Edisi 4, Agustus 2024.
- dqlab.id. (2023, 28 November). Content Based Filtering dalam Algoritma Data Science. Diakses pada 15 Januari 2025. dari https://dqlab.id/content-based-filtering-dalam-algoritma-data-science
- dqlab.id. (2022, 16 November). Pendekatan Machine Learning Collaborative Filtering. Diakses pada 15 Januari 2025. dari https://dqlab.id/pendekatan-machine-learning-collaborative-filtering
- ibm.com. (2024, 21 Maret). Apa itu penyaringan kolaboratif?. Diakses pada 15 Januari 2025. dari https://www.ibm.com/id-id/topics/collaborative-filtering
- socs.binus.ac.id. (2020). Confusion Matrix. Diakses pada 15 Januari 2025. dari https://socs.binus.ac.id/2020/11/01/confusion-matrix/
- evidentlyai.com. (2025, 9 Januari). Precision and recall at K in ranking and recommendations. Diakses pada 15 Januari 2025. dari https://www.evidentlyai.com/ranking-metrics/precision-recall-at-k
- arize.com/. (2023, 8 Agustus). Root Mean Square Error (RMSE) In AI: What You Need To Know. Diakses pada 15 Januari 2025. dari https://arize.com/blog-course/root-mean-square-error-rmse-what-you-need-to-know/






   



   
















# recomendation_analitycs
