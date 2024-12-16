# **Laporan Proyek Machine Learning - Anak Agung Gde Pradnyana**

## **Project Overview**
![confira-agora-os-25-melhores-animes-que-ja-foram-criados-1](https://github.com/user-attachments/assets/58ccfbb8-e6d8-446b-8ef7-ad5971e85f06)

Industri hiburan global, khususnya film dan TV, telah mengalami transformasi besar dengan kemajuan teknologi digital. Salah satu segmen yang berkembang pesat adalah animasi Jepang, atau anime, yang memiliki daya tarik unik dan basis penggemar internasional yang terus bertumbuh. 
Anime tidak hanya menjadi media hiburan tetapi juga sebuah subkultur yang memiliki pengaruh besar dalam industri kreatif dunia. Namun, dengan semakin banyaknya judul anime yang diproduksi setiap tahun, pengguna sering kali kesulitan menemukan konten yang sesuai dengan preferensi mereka. 
Dalam konteks inilah sistem rekomendasi menjadi alat penting yang mendukung pengalaman pengguna dan keberlanjutan industri anime.

Sistem rekomendasi, atau recommendation system, memungkinkan platform streaming untuk memberikan saran anime yang relevan berdasarkan preferensi, pola tontonan, dan ulasan pengguna. 
Teknologi ini tidak hanya memberikan kenyamanan bagi penonton, tetapi juga membantu perusahaan mengoptimalkan katalog konten mereka. 
Dengan adanya sistem rekomendasi, anime yang relevan dapat lebih mudah ditemukan oleh audiens yang mungkin tidak memiliki akses langsung atau pengetahuan tentang judul tertentu. 
Sebagai contoh, algoritma berbasis pembelajaran mesin dapat mengidentifikasi hubungan antara genre, gaya animasi, atau tema spesifik yang disukai oleh pengguna, sehingga memungkinkan pengalaman yang lebih personal

## Business Understanding
### Problem Statements
Berdasarkan domain proyek yang telah diuraikan, terdapat beberapa permasalahan utama yang menjadi dasar dari pembuatan model ini, yaitu:
- Bagaimana hasil exploratory data analysis pada dataset anime 2023?
- Bagaimana implementasi dan evaluasi dari kedua metode *content based filtering* dan *collaborative filtering* dalam merekomendasikan anime?

### Goals
Berdasarkan problem statement yang dijelaskan pada bagian sebelumnya, maka pembuatan model ini akan memiliki beberapa tujuan diantaranya adalah:
- Menganalisis dataset anime tahun 2023 untuk mengidentifikasi pola, tren, dan karakteristik utama yang mendominasi industri anime pada tahun tersebut.
- Mengevaluasi efektivitas metode content-based filtering dan collaborative filtering dalam memberikan rekomendasi anime yang relevan kepada pengguna.

### Solution statements
Dalam solusi ini, digunakan 2 metode *collaborative filtering* dan *content based filtering*. Prosesnya melibatkan:
**1. Preprocessing Data:**
- Menghapus fitur yang tidak ada hubungan untuk modelling.
- Mengatasi nilai kosong dan duplikasi.
- Merubah tipe data pada beberapa fitur untuk proses EDA atau modelling
- Encoding fitur kategorikal menjadi numerik.
- Normalisasi data numerik untuk *collaborative filtering* agar fitur memiliki skala yang sebanding menggunakan MinMaxScaller.
- Mengubah teks genre menjadi representasi vektor numerik di mana setiap genre diberi bobot menggunakan TFIDF pada metode *content based filtering*.

**2. Training dan Evaluasi Model:**
- Melatih masing-masing metode menggunakan data training yang dimana untuk metode *collaborative filtering* base model yang digunakan DNN sedangkan *content based filtering* menggunakan pendekatan cosine similarity.
- Menggunakan metrik evaluasi MSE dan MAE pada metode *collaborative filtering* sedangkan metode *content based filtering* menggunakan precision.

**4. Testing model**
- Hasil training dari kedua metode dicoba untuk merekomendasikan anime yang sama preferensi pengguna.

## Data Understanding
![data0](https://github.com/user-attachments/assets/7f00b10d-f232-44d2-9469-1518e414748b)

Informasi dataset dapat dilihat pada tabel dibawah ini :
Jenis | Keterangan
--- | ---
Sumber | [Anime Dataset 2023](https://www.kaggle.com/datasets/dbdmobile/myanimelist-dataset)
Lisensi | Database Contents License (DbCL)
Kategori | Arts, Anime, Japan, Tv Shows and Movies
Jenis dan Ukuran Berkas | CSV (7.35 GB)
Konsdisi Dataset | Terdapat missing value dan tidak ada data duplicate
---
Terdapat 6 berkas data yang berformat csv namun, data yang dipakai untuk proses EDA dan Modelling hanya 2 dataset dipakai. Berikut deskrpisi dan detail fitur dari dataset tersebut:
### **A. Dataset Anime**

Dataset ini berisi 24 fitur dengan 24905 baris di dalamnya, data ini menawarkan informasi berharga untuk menganalisis dan memahami karakteristik, peringkat, popularitas, dan jumlah penonton dari berbagai acara anime. Dengan memanfaatkan dataset ini, seseorang dapat melakukan berbagai analisis, termasuk mengidentifikasi anime dengan rating tertinggi, mengeksplorasi genre paling populer, memeriksa distribusi rating, dan mendapatkan wawasan tentang preferensi dan tren. Berikut detail kolom atau fitur yang terdapat pada data ini:
- **anime_id:** ID unik untuk setiap anime.
- **Name:** Nama anime dalam bahasa aslinya.
- **English name:** Nama anime dalam bahasa Inggris.
- **Other name:** Nama lain atau judul anime (bisa dalam bahasa Jepang, Mandarin, atau Korea).
- **Score:** Skor atau penilaian yang diberikan untuk anime tersebut.
- **Genres:** Genre atau kategori dari anime, dipisahkan dengan koma.
- **Synopsis:** Deskripsi singkat atau ringkasan alur cerita anime.
- **Type:** Jenis anime (contoh: seri TV, film, OVA, dll.).
- **Episodes:** Jumlah episode dalam anime tersebut.
- **Aired:** Tanggal tayangnya anime tersebut.
- **Premiered:** Musim dan tahun ketika anime pertama kali ditayangkan.
- **Status:** Status anime (contoh: Selesai Tayang, Sedang Tayang, dll.).
- **Producers:** Perusahaan produksi atau produser yang membuat anime.
- **Licensors:** Pihak lisensor dari anime (contoh: platform streaming).
- **Studios:** Studio animasi yang mengerjakan anime.
- **Source:** Sumber materi anime (contoh: manga, novel ringan, orisinal).
- **Duration:** Durasi setiap episodenya.
- **Rating:** Klasifikasi umur untuk anime tersebut.
- **Rank:** Peringkat anime berdasarkan popularitas atau kriteria lain.
- **Popularity:** Peringkat popularitas anime.
- **Favorites:** Jumlah pengguna yang menandai anime ini sebagai favorit.
- **Scored By:** Jumlah pengguna yang memberikan skor untuk anime ini.
- **Members:** Jumlah anggota yang telah menambahkan anime ini ke daftar mereka di - platform.
- **Image URL:** URL dari gambar atau poster anime tersebut.

### **B. Dataset Skor Pengguna**

Dataset Skor Pengguna memungkinkan berbagai analisis dan wawasan tentang interaksi pengguna dengan anime. Dengan memeriksa peringkat pengguna untuk berbagai judul anime, dapat mengidentifikasi anime dengan peringkat tinggi dan populer di kalangan pengguna. Selain itu, Anda dapat menjelajahi preferensi pengguna dan pola menonton untuk judul anime tertentu. Berikut detail fitur dari dataset ini:
- **user_id:** ID unik untuk setiap pengguna.
- **Username:** Nama pengguna (username) dari pengguna.
- **anime_id:** ID unik untuk setiap anime.
- **Anime Title:** Judul dari anime.
- **rating:** Penilaian atau skor yang diberikan oleh pengguna untuk anime tersebut.

### **C. EDA (Exploratory Data Anlysis)**
**Analisis Jumlah Anime Berdasarkan Tipenya**

![eda1](https://github.com/user-attachments/assets/2bc1f5fc-c601-486e-89e5-53e2f5b37dc0)

**Analisis:**
- Anime tipe TV memiliki jumlah judul terbanyak, dengan lebih dari 7.000 judul, menunjukkan bahwa TV adalah format utama untuk distribusi anime.
- Tipe Movie, OVA, dan ONA memiliki jumlah judul yang hampir setara, sekitar 4.000-5.000 judul, menandakan bahwa ketiganya memiliki pangsa pasar yang cukup besar.
- Industri anime menunjukkan diversifikasi format yang signifikan, memberikan fleksibilitas kepada produser untuk memilih medium yang sesuai dengan target audiens dan cerita.

**Analisis 10 Top Anime Berdasarkan Rank dan Jumlah Penonton**

![eda2](https://github.com/user-attachments/assets/4f7fe133-4c18-4476-821c-474e936e3e54)

**Analisis:**
- Shingeki no Kyojin (Attack on Titan) berada di peringkat 1 sebagai anime paling populer di daftar ini.
- Anime seperti Naruto dan Death Note masih mempertahankan popularitasnya meskipun sudah lama dirilis, menunjukkan bahwa cerita yang kuat memiliki daya tahan jangka panjang.
- Anime seperti Kimetsu no Yaiba dan Boku no Hero Academia menggambarkan bagaimana anime modern dengan kualitas tinggi dapat menarik perhatian penggemar baru dan lama.

![eda3](https://github.com/user-attachments/assets/0fa97cd6-e402-412d-b848-04f9e25aa338)

**Analisis:**
- Shingeki no Kyojin (Attack on Titan) memiliki jumlah penonton tertinggi, mendominasi visualisasi. Popularitasnya dapat dikaitkan dengan cerita yang mendalam dan fenomena global.
- Death Note berada di peringkat kedua dengan jumlah penonton hampir mendekati Shingeki no Kyojin, mencerminkan daya tariknya sebagai salah satu anime klasik dengan alur cerita yang unik.
- Anime baru dengan cerita inovatif seperti Kimetsu no Yaiba menunjukkan potensi untuk menjadi warisan anime berikutnya.
- Dilihat dari visualisasi sebelumnya top 10 anime populer dengan top anime berdasarkan jumlah penonton berbanding lurus antara populer dan jumlah penontonnya.

**Analisis Top Genre Anime Paling Populer**

![eda4](https://github.com/user-attachments/assets/0a0f1385-11a0-4dfc-a3a1-169c29f7d1d9)

**Analisis:**
- Comedy adalah genre dengan jumlah judul terbanyak, mendekati angka 7.000. Hal ini menunjukkan bahwa genre ini sangat populer dan banyak digunakan dalam berbagai seri anime.
- Genre Comedy mendominasi karena fleksibilitasnya yang dapat digabungkan dengan genre lain, seperti romance atau slice of life.
- Popularitas genre Fantasy dan Action mencerminkan minat audiens terhadap cerita yang imajinatif dan penuh aksi.

**Analisis Anime Premier Setiap Tahun**

![eda5](https://github.com/user-attachments/assets/9c97697c-9397-49b3-bdf5-275e324a3fae)

**Analisis:**
- Dari tahun 1960-an hingga 1980-an, jumlah anime yang dirilis meningkat secara bertahap. Industri anime mulai berkembang stabil di periode ini, dengan peningkatan signifikan di awal 2000-an.
- Jumlah anime mencapai puncaknya sekitar tahun 2010–2015, dengan lebih dari 250 judul anime dirilis per tahun. Hal ini mencerminkan puncak popularitas anime di pasar global.
- Penurunan setelah tahun 2015 dapat mengindikasikan saturasi pasar atau bergesernya fokus industri anime ke arah kualitas daripada kuantitas. Bisa juga dipengaruhi oleh hadirnya platform streaming, di mana distribusi lebih terfokus pada judul-judul tertentu.

**Distrubusi Perilisan Anime Berdasarkan Season**

![eda6](https://github.com/user-attachments/assets/237f167c-62e0-41d1-888d-f05d74c09400)

### **Analisis:**
- Spring (32.5%) adalah musim dengan jumlah anime yang paling banyak tayang perdana. Hal ini mencerminkan bahwa musim spring mungkin dianggap sebagai waktu strategis untuk merilis anime, kemungkinan karena berdekatan dengan awal tahun akademik atau kalender budaya di Jepang.
- Spring dan Fall mungkin dipilih sebagai musim strategis untuk merilis anime baru karena adanya peningkatan aktivitas setelah liburan musim winter dan musim summer.
- Jumlah anime yang lebih sedikit pada musim summer dan musim winter dapat mencerminkan fokus industri pada melanjutkan seri yang sudah ada atau istirahat produksi.

## Data Preparation
**1. Checking dan Menghapus Data Null dan Duplicate**

![image](https://github.com/user-attachments/assets/f2057c4b-d9af-4290-acf0-40c8718b251e)

- Dari proses checking NULL dan Duplicate dari kedua dataset didapatkan hasil bahwa dataset skor pengguna memiliki 232 data NULL pada fitur username sehingga harus dihapus untuk mencegah kegagalan pada proses EDA dan modeling menggunakan code df_scores.dropna(inplace=True). Selain itu hasil dari cek duplicate untuk kedua dataset hasilnya nihil tidak ada value duplicate.

**2. Merubah Tipe Data**

![image](https://github.com/user-attachments/assets/e0857dc2-c100-4de6-a885-e68ae0740b71)
![image](https://github.com/user-attachments/assets/02b0b815-b29e-4f66-9ab4-76b214f13b81)

- Pada dataset anime terdapat fitur yang tidak seusai tipe datanya yaitu tipe data object pada fitur score dan rank sehingga perlu diatasi dengan merubah tipe datanya menjadi float. Selain dari kedua fitur juga memiliki nilai UNKNOWN yang perlu dihilangkan dan diganti, untuk pengganti nilai tersebut solusinya adalah menggunakan nilai mean dari kedua fitur.

**3. Normalisasi Data**

![image](https://github.com/user-attachments/assets/129e4a18-8cf9-448c-93cc-5082761137e4)

- Sebelum normalisasi data pada object modelling penulis membuat salinan subset dari dataframe df_scores untuk mengambil fitur 'user_id', 'anime_id', dan 'rating'. Kemudian melakukan normalisasi pada kolom rating menggunakan MinMaxScaler, sehingga nilai skor berada dalam rentang 0 hingga 1, lalu menyimpan hasil normalisasi dalam kolom baru bernama scaled_score. Proses ini penting dalam sistem rekomendasi karena algoritma tertentu bekerja lebih baik dengan data yang ter-normalisasi.

**4. Fitur Encoding**

![image](https://github.com/user-attachments/assets/92b4d609-560b-4c32-b951-f0b5ebbe804f)

- Proses encoding ini merupakan langkah pra-pemrosesan penting dalam membangun sistem rekomendasi berbasis *Collaborative Filtering*, di mana ID User dan ID Anime perlu dikonversi menjadi angka agar dapat digunakan dalam deep learning.

**5. Vektorization With TFIDF**
 TF-IDF Vectorizer untuk mengubah data teks pada kolom Genres menjadi representasi numerik. Dalam konteks Content-Based Filtering, TF-IDF berperan penting sebagai teknik untuk menghitung bobot fitur dalam data teks yang akan digunakan untuk mengukur kesamaan antar item (dalam hal ini, anime). Dengan matriks TF-IDF ini, Content-Based Filtering dapat membandingkan kemiripan antar anime berdasarkan genre menggunakan teknik seperti Cosine Similarity.

**6. Splitting Data Train dan Data Test**
- Membuat variabel baru untuk persiapan training model seperti X untuk menampung semua fitur numerikal untuk ditraining dan y untuk menampung fitur target yaitu rating. Kemudian membagi data menjadi data train dan testing yang dimana panjang data train sebesar 24314959 dan testing sebesar 10000 dengan random state 73. Data splitting ini menggunakan library sklearn untuk membagi data train dan testing.


## Modelling
Pada bagian ini, menjelaskan dua metode yang digunakan untuk menyelesaikan permasalahan rekomendasi sistem anime 2023 yaitu *Collaborative Filtering* dan *Content Based Filtering*. Proses modelling dilakukan melalui tahapan sebagai berikut:

### **A. Collaborative Filtering**
Collaborative Filtering dengan pendekatan Deep Neural Network (DNN) adalah metode rekomendasi yang mempelajari interaksi antara pengguna dan item melalui representasi vektor laten menggunakan neural network. Dalam metode ini, sistem tidak bergantung pada atribut eksplisit dari item, melainkan menggunakan data interaksi antara pengguna dan item seperti peringkat atau skor untuk mempelajari pola tersembunyi. Neural network dalam pendekatan ini memanfaatkan embedding layer untuk merepresentasikan pengguna dan item ke dalam bentuk vektor berdimensi rendah, kemudian memodelkan hubungan non-linear antara keduanya melalui lapisan dense (Dense Layers). Pendekatan ini memungkinkan model untuk menangkap hubungan kompleks dalam data yang tidak dapat dijangkau oleh teknik kolaboratif sederhana seperti Matrix Factorization.

Dalam implementasi sistem rekomendasi ini, parameter atau fitur utama yang digunakan adalah ID pengguna (user_id) dan ID anime (anime_id), yang diubah menjadi representasi numerik menggunakan Label Encoding. Kolom rating atau skor dari interaksi pengguna dengan anime kemudian dinormalisasi menggunakan MinMaxScaler agar nilainya berada dalam rentang 0 hingga 1. Data hasil encoding ini dibagi menjadi dua variabel utama: X sebagai input (berisi user_encoded dan anime_encoded) dan y sebagai target (berisi skor rating yang sudah dinormalisasi). Model DNN yang digunakan memiliki embedding layer untuk merepresentasikan pengguna dan item, kemudian menggabungkan kedua embedding tersebut melalui dot product untuk mengukur kecocokan antara pengguna dan anime. Lapisan tambahan berupa Dense Layer dengan aktivasi ReLU digunakan untuk menangkap hubungan non-linear, dan lapisan output dengan aktivasi sigmoid digunakan untuk memprediksi skor kecocokan dalam skala probabilitas.

Proses pelatihan model menggunakan learning rate scheduler untuk menyesuaikan laju pembelajaran secara dinamis, early stopping untuk mencegah overfitting, dan Model Checkpoint untuk menyimpan bobot model terbaik selama pelatihan. Dengan parameter seperti jumlah epoch (20), ukuran batch (10.000), dan learning rate awal (0.00001), sistem ini dioptimalkan untuk mempelajari pola interaksi yang kompleks antara pengguna dan anime, sehingga mampu memberikan rekomendasi yang lebih akurat dan personal.

**Kelebihan Metode:**
- DNN dapat mempelajari hubungan non-linear antara pengguna dan item melalui penggunaan Dense Layers, sehingga memberikan rekomendasi yang lebih akurat dibanding metode kolaboratif sederhana seperti Matrix Factorization.
- Dengan penggunaan embedding layer, model dapat merepresentasikan pengguna dan item dalam ruang vektor laten yang dapat belajar dari data interaksi yang kompleks.
- Metode ini hanya memerlukan data interaksi pengguna-item (rating), sehingga dapat digunakan meskipun fitur eksplisit item seperti genre atau deskripsi tidak tersedia.

**Kekurangan Metode:**
- Metode ini tidak dapat memberikan rekomendasi akurat bagi pengguna atau item baru yang belum memiliki cukup interaksi.
- Pelatihan model DNN memerlukan daya komputasi yang besar, terutama pada dataset dengan jumlah pengguna dan item yang besar.
- Jika tidak diatur dengan baik (misalnya dengan early stopping atau regularization), model berpotensi overfitting pada data pelatihan.

Berikut hasil rekomendasi metode Collaborative Filtering dengan DNN:
![image](https://github.com/user-attachments/assets/3dc4f903-fe2a-4b70-ab4d-8b564f1a4f37)


### **B. Content Based Filtering**

Content-Based Filtering adalah salah satu metode dalam sistem rekomendasi yang bekerja dengan menganalisis karakteristik atau fitur dari item yang akan direkomendasikan dan membandingkannya dengan preferensi pengguna atau item yang pernah dipilih sebelumnya. Pendekatan Cosine Similarity dalam metode ini digunakan untuk mengukur sejauh mana dua item serupa satu sama lain berdasarkan fitur yang dimiliki. Cosine Similarity menghitung kesamaan antara dua vektor dengan melihat sudut di antara mereka; semakin kecil sudut yang terbentuk, semakin tinggi nilai kesamaan kedua vektor tersebut. Dalam sistem ini, fitur yang dipakai untuk membandingkan antar-item adalah genre dari anime.

Untuk membangun sistem rekomendasi ini, dilakukan transformasi teks dari kolom "Genres" menjadi representasi numerik menggunakan TF-IDF (Term Frequency-Inverse Document Frequency). Teknik ini memberikan bobot pada setiap kata yang ada dalam kolom genre berdasarkan frekuensi kemunculannya di satu item relatif terhadap keseluruhan dataset. Kata yang sering muncul dalam satu genre tetapi jarang di genre lain akan mendapatkan bobot yang lebih tinggi, sehingga menjadi lebih informatif. Hasil transformasi ini berupa TF-IDF matrix, di mana setiap baris mewakili anime dan setiap kolom mewakili istilah unik dari genre.

Setelah matrix TF-IDF terbentuk, nilai Cosine Similarity dihitung untuk mencari tingkat kemiripan antara satu anime dengan anime lainnya. Nilai kemiripan ini digunakan sebagai dasar untuk merekomendasikan anime dengan genre yang paling mirip. Dalam implementasi sistem, tidak hanya kemiripan genre yang menjadi acuan, tetapi juga parameter tambahan berupa rating atau skor anime. Skor ini digunakan sebagai filter untuk memastikan bahwa rekomendasi yang diberikan memiliki kualitas yang baik dan relevan bagi pengguna. Dengan demikian, sistem ini mampu merekomendasikan anime berdasarkan kesamaan konten yang diukur melalui Cosine Similarity sambil mempertimbangkan kualitas item melalui skor yang valid.

**Kelebihan Metode:**
- Tidak memerlukan data preferensi pengguna lain (seperti dalam Collaborative Filtering).
- Jika sebuah anime baru ditambahkan, sistem masih bisa merekomendasikan berdasarkan atribut kontennya (genre).
- Mudah dipahami karena rekomendasi dibuat berdasarkan kesamaan fitur yang dapat dilihat langsung

**Kekurangan Metode:**
- Jika pengguna belum memiliki riwayat interaksi, sistem tidak dapat memberikan rekomendasi personal.
- Sistem hanya merekomendasikan anime dengan genre yang mirip, sehingga pengguna jarang diperkenalkan ke konten yang berbeda atau baru.
- Sistem ini hanya mengandalkan atribut eksplisit (genre) dan tidak mempertimbangkan pola preferensi yang lebih kompleks seperti perilaku pengguna.

Berikut hasil rekomendasi Content Based Filtering dengan Cosine Similarity:
![image](https://github.com/user-attachments/assets/11191ed7-55aa-4c4f-8116-e4fa4bbbff03)

