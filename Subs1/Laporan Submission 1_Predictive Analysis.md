# Laporan Proyek Machine Learning - Anak Agung Gde Pradnyana

## Domain Proyek

Domain proyek yang dipilih dalam proyek _machine learning_ ini adalah mengenai ekonomi dan bisnis dengan judul proyek "Prediksi Customer Churn".

![Customer Churn](https://www.leadsquared.com/wp-content/uploads/2022/09/Customer-churn.webp)

Memprediksi *customer churn* adalah tugas penting bagi bisnis di berbagai industri, termasuk telekomunikasi, ritel, dan perbankan. Churn pelanggan mengacu pada fenomena di mana pelanggan berhenti menggunakan produk atau layanan perusahaan, yang secara signifikan dapat memengaruhi pendapatan dan pertumbuhan perusahaan. Untuk mengatasi masalah ini, teknik machine learning telah banyak diadopsi untuk memprediksi churn dan membantu bisnis menerapkan strategi retensi yang efektif. Beberapa penelitian telah mengeksplorasi berbagai algoritma pembelajaran mesin untuk prediksi churn. Misalnya, dalam industri telekomunikasi, berbagai model seperti K-Nearest Neighbor (KNN), Random Forest (RF), dan XGBoost telah diuji untuk mengidentifikasi pengklasifikasi yang paling efektif untuk memprediksi churn pelanggan. Salah satu studi menemukan bahwa XGBoost mengungguli model lainnya dengan akurasi 79,67%, presisi 64,67%, recall 51,87%, dan F1-score 57,57% [[1]](https://core.ac.uk/download/pdf/588297321.pdf). Studi lain menyoroti bahwa Random Forest mencapai akurasi 96,25% dalam memprediksi churn pelanggan kartu kredit, menekankan pentingnya transaksi yang sering terjadi dalam mengurangi tingkat churn [[2]](https://doi.org/10.2991/aebmr.k.220307.104). Di sektor ritel, model pembelajaran mesin seperti Regresi Logistik, Random Forest, Decision Tree, KNN, dan XGBoost telah diterapkan untuk memprediksi perpindahan pelanggan. Studi ini menunjukkan bahwa XGBoost adalah pengklasifikasi yang paling efisien, melampaui model lain dalam semua metrik evaluasi kinerja [[3]](https://ieeexplore.ieee.org/abstract/document/9776921/).

Oleh karena itu algoritma machine learning seperti KNN, Random Forest, dan XGBoost telah terbukti efektif dalam memprediksi perpindahan pelanggan di berbagai industri. Model-model ini membantu bisnis mengidentifikasi pelanggan yang berisiko dan menerapkan strategi retensi yang ditargetkan untuk meminimalkan churn dan memaksimalkan profitabilitas.

## Business Understanding
### Problem Statements
Berdasarkan domain proyek yang telah diuraikan, terdapat beberapa permasalahan utama yang menjadi dasar dari pembuatan model ini, yaitu:
- Bagaimana hasil exploratory data analysis pada dataset prediksi customer churn?
- Bagaimana kinerja model Random Forest, KNN, XGBoost dalam memprediksi customer churn?
- Apa model terbaik antara ketiga model terbaik dalam memprediksi customer churn?

### Goals
Berdasarkan problem statement yang dijelaskan pada bagian sebelumnya, maka pembuatan model ini akan memiliki beberapa tujuan diantaranya adalah:
- Memberikan wawasan awal tentang faktor yang dapat memengaruhi prediksi churn, yang akan menjadi input penting untuk pemodelan.
- Membandingkan dan mengetahui kinerja model Random Forest, KNN, dan XGBoost dalam memprediksi customer churn. 
- Menentukan model prediksi customer churn terbaik antara Random Forest, KNN dan XGBoost.

### Solution statements
Dalam solusi ini, digunakan tiga algoritma machine learning yaitu Random Forest, K-Nearest Neighbors (KNN), dan XGBoost untuk membandingkan performa prediksi customer churn. Prosesnya melibatkan:

**1. Preprocessing Data:**
- Menghapus fitur yang tidak ada hubungan untuk modelling.
- Mengatasi nilai kosong dan duplikasi.
- Encoding fitur kategorikal menjadi numerik.
- Normalisasi data numerik untuk KNN agar fitur memiliki skala yang sebanding menggunakan StandarScaller.

**2. Training dan Evaluasi Model:**
- Melatih masing-masing model menggunakan data training.
- Menggunakan metrik evaluasi seperti Accuracy, Precision, Recall, dan F1-Score untuk menilai performa setiap model.

**3. Memilih Model Terbaik:**
- Model dengan kombinasi metrik terbaik (misalnya, keseimbangan antara Precision dan Recall) akan dipilih sebagai solusi untuk prediksi customer churn.

**4. Testing model**
- Model yang sudah ditraining dilakukan testing menggunakan confusion matrix untuk mengetahui seberapa handal dalam memprediksi churn atau non churn.

## Data Understanding
![Image of Dataset](https://i.postimg.cc/9fcqSMND/Screenshot-2024-08-26-152103.png)
Informasi dataset dapat dilihat pada tabel dibawah ini :
Jenis | Keterangan
--- | ---
Sumber | [Kaggle Dataset : Churn Customer Prediction Dataset](https://www.kaggle.com/datasets/muhammadshahidazeem/customer-churn-dataset)
Lisensi | Data files © GPL 2
Kategori | Ekonomi, Bisnis, Classification
Jenis dan Ukuran Berkas | CSV (7 Mb)
Konsdisi Dataset | Terdapat missing value dan tidak ada data duplicate
---
Pada berkas yang diunduh yakni customer churn_dataset-training-master.csv berisi 440.833 baris dan 12 kolom. Kolom-kolom tersebut terdiri dari 3 buah kolom bertipe objek dan 9 buah kolom bertipe desimal (tipe data float). Untuk penjelasan mengenai variabel-variable pada dataset stroke ini dapat dilihat sebagai berikut:
* **CustomerID:** Identifikasi unik untuk setiap pelanggan dalam dataset. Fitur ini digunakan untuk membedakan setiap pelanggan dan menghindari duplikasi data.
* **Age:** Usia pelanggan dalam tahun. Fitur ini memberikan informasi tentang demografi pelanggan berdasarkan usia.      
* **Gender:**  Jenis kelamin pelanggan. Fitur ini mengklasifikasikan pelanggan berdasarkan gender, biasanya dengan nilai seperti 'Laki-laki' atau 'Perempuan'.
* **Tenure:** Lama waktu (biasanya dalam bulan atau tahun) sejak pelanggan pertama kali mulai menggunakan layanan. Fitur ini mencerminkan loyalitas dan pengalaman pelanggan dengan layanan.        
* **Usage Frequency:**  Frekuensi penggunaan layanan oleh pelanggan, biasanya dalam hitungan harian, mingguan, atau bulanan. Fitur ini memberikan gambaran seberapa sering pelanggan menggunakan layanan.  
* **Support Calls:** Jumlah panggilan yang dilakukan customer ke layanan dukungan selama periode tertentu. Fitur ini mengindikasikan kebutuhan atau masalah yang dialami customer saat menggunakan layanan.
* **Payment Delay:** Indikator apakah customer mengalami keterlambatan dalam pembayaran, sering kali diukur dalam hari keterlambatan atau jumlah kali keterlambatan. Fitur ini dapat menunjukkan potensi risiko finansial atau perilaku pembayaran customer.
* **Subscription Type:** Tipe langganan yang diambil oleh pelanggan, seperti paket standard, premium, dan basic. Fitur ini menggambarkan pilihan layanan yang diambil oleh customer dan nilai yang mereka bayarkan.
* **Contract Length:** Panjang kontrak yang telah disepakati oleh customer seperti _annual_,_monthly_,_quarterly_. Fitur ini mencerminkan komitmen jangka panjang customer terhadap layanan. 
* **Total Spend:** Total pengeluaran yang dilakukan oleh customer selama periode tertentu. Fitur ini mencakup semua pembayaran yang telah dilakukan dan memberikan gambaran tentang nilai finansial dari setiap customer.
* **Last Interaction:** Waktu atau tanggal terakhir kali customer berinteraksi dengan layanan atau melakukan kontak dengan perusahaan. Fitur ini berguna untuk mengukur keterlibatan terkini customer.
* **Churn:** Indikator apakah customer telah berhenti berlangganan layanan atau tidak, dengan nilai 0 untuk tidak churn dan 1 untuk churn.

### EDA (Exploratory Data Anlysis)
**Demographic Analysis**:

![Proporsi Churn berdasarkan Gender](https://i.postimg.cc/wM92pxQn/download0.png)
![Rata-rata umur berdasarkan Churn](https://i.postimg.cc/qqQLMfmq/download1.png)
![Proporsi Churn berdasarkan Sebaran Umur](https://i.postimg.cc/PfMKMZtH/download2.png)

**Analisis**
**Proportion of Churn by Gender**
- Pelanggan pria dan wanita memiliki tingkat churn yang mirip. Kedua kelompok menunjukkan proporsi churn yang signifikan.
- Tidak ada perbedaan mencolok antara gender terkait dengan churn. Ini menunjukkan bahwa gender mungkin bukan faktor yang menentukan dalam perilaku churn.
- Fokus pada faktor lain seperti penggunaan layanan atau interaksi terakhir pelanggan karena gender tidak menjadi prediktor utama churn.

**Average Age by Churn**
- Pelanggan yang Churn (Bar Merah): Memiliki rata-rata usia yang lebih tinggi (sekitar 40 tahun). Hal ini menunjukkan bahwa pelanggan dengan usia yang lebih tua cenderung lebih mungkin untuk churn dibandingkan pelanggan dengan usia yang lebih muda.
Pelanggan yang Tidak Churn (Bar Hijau): Memiliki rata-rata usia yang lebih rendah (sekitar 35 tahun). Pelanggan yang tidak churn cenderung berasal dari kelompok usia yang lebih muda.

**Proportion of Churn by Age Group**
- Kelompok Usia Muda (0-20 Tahun): Pelanggan muda memiliki proporsi churn lebih tinggi dibandingkan dengan pelanggan yang tidak churn.
Hal ini menunjukkan bahwa pelanggan dalam kelompok usia ini lebih rentan meninggalkan layanan.
- Kelompok Usia 20-50 Tahun: Kelompok usia ini memiliki distribusi churn yang lebih seimbang antara churn ("Yes") dan non-churn ("No"). Ini menunjukkan bahwa pelanggan di rentang usia ini cenderung memiliki perilaku churn yang tidak terlalu ekstrem, mungkin tergantung pada faktor lain seperti penggunaan layanan atau pengalaman pelanggan.
- Kelompok Usia Tua (50-70 Tahun): Hampir seluruh pelanggan di kelompok usia ini churn (proporsi bar oranye mendominasi). Ini menunjukkan bahwa pelanggan di kelompok usia ini memiliki kecenderungan yang sangat tinggi untuk churn.

---
**Subscription Type and User Interaction Analysis**:

![Proportion of Churn by Subscription Type](https://i.postimg.cc/655cb33v/download3.png)
![Proportion of Churn by Contract Length](https://i.postimg.cc/vHqzJsgS/download4.png)

**Analisis:**
**Proportion of Churn by Subscription Type**
- Semua jenis langganan (Basic, Premium, Standard) memiliki proporsi churn yang signifikan.
- Proporsi churn (warna oranye) terlihat hampir sama di antara ketiga jenis langganan.
Artinya, jenis langganan tidak memiliki perbedaan besar dalam menentukan tingkat churn.

**Proportion of Churn by Contract Length**
- Langganan tahunan (Annual) memiliki proporsi churn yang lebih rendah dibandingkan langganan bulanan (Monthly) dan kuartalan (Quarterly).
- Langganan bulanan dan kuartalan menunjukkan tingkat churn yang lebih tinggi, yang mungkin disebabkan oleh kurangnya keterikatan pelanggan pada kontrak jangka pendek.
---

**Usage Frequency Distribution Analysis**

![Distribution Usage Frequency](https://i.postimg.cc/7Z5VDWSP/download5.png)

**Analisis:**
- Distribusi frekuensi penggunaan layanan cukup merata, dengan mayoritas pelanggan memiliki penggunaan layanan yang konsisten.
- Pelanggan dengan frekuensi penggunaan yang lebih rendah mungkin berisiko churn jika dibandingkan dengan pelanggan dengan frekuensi tinggi (perlu analisis tambahan untuk memastikan).
---

## Data Preparation
Pada bagian ini Anda menerapkan dan menyebutkan teknik data preparation yang dilakukan. Teknik yang digunakan pada notebook dan laporan harus berurutan.

**1. Menghapus Data Null dan Duplicate**

![Data Null](https://i.postimg.cc/RhFkmz9C/Screenshot-2024-11-28-103249.png)
- Pada dataset ini semua fitur memiliki nilai NULL sebanyak 1, hal ini patut dicurigai karena bisa hanya 1 baris yang memiliki nilai NULL. Hasilnya baris 199295	semua fiturnya memiliki value NULL dan harus dihapus bari tersebut menggunakan df.dropna(inplace=True). Selaain itu hasil dari cek duplicate nihil tidak ada value duplicate.

**2. Drop Kolom CustomerID**

![Drop Customerl](https://i.postimg.cc/TPvvDSjQ/Screenshot-2024-11-28-102952.png)
- Terdapat 12 kolom pada dataset ini namun, kolom CustomerID harus dihilangkan menggunakan code df.drop('CustomerID', axis=1) karena tidak dibutuhkan untuk modelling.

**3. Label Encoding**

![Data Mapping](https://i.postimg.cc/W33VNZwP/Screenshot-2024-11-28-103653.png)
![Label Encoding](https://i.postimg.cc/Jn2LGhpH/Screenshot-2024-11-28-103710.png)
- Gambar pertama melakukan cek kolom yang mempunyai tipe data object untuk memahami kolom mana yang perlu diproses lebih lanjut, karena algoritma machine learning hanya dapat menangani data numerik. Kemudian mapping kolom Gender karena memiliki 2 kategori Female: 0 dan Male: 1.
- Selanjutnya one hot encoding adalah metode yang merubah setiap nilai di dalam kolom menjadi kolom baru dan mengisinya dengan nilai biner dan cocok untuk banyak kategori. Dilihat pada gambar 2 salah satu kolom yaitu Subscription Type merubah isi kategori premium , basic, dan standard menjadi biner kemudian terbentuk kolom baru.

**4. Splitting Data Train dan Data Test**
- Membuat variabel baru untuk persiapan training model seperti X untuk menampung semua fitur numerikal untuk ditraining dan y untuk menampung fitur target klasifikasi. Kemudian membagi data menjadi data train dan testing dengan rasio 80:20,  data train: 80% dan data test: 20% dengan menggunakan library sklearn.

**5. Standarisasi Data**
- Melakukan standardisasi data pada data train dan data test. Tahap terakhir yaitu melakukan standarisasi data. Hal ini dilakukan untuk membuat semua fitur berada dalam skala data yang sama yaitu dengan range 0-1. Strandadisasi data ini menggunakan fungsi StandardScaler.

## Modeling
Pada bagian ini, menjelaskan tiga algoritma machine learning yang digunakan untuk menyelesaikan permasalahan prediksi customer churn, yaitu Random Forest, K-Nearest Neighbors (KNN), dan XGBoost. Proses modelling dilakukan melalui tahapan sebagai berikut:

**1. Random Forest**

Random Forest adalah algoritma ensemble berbasis pohon keputusan yang menggunakan metode bagging untuk meningkatkan akurasi prediksi. Model ini dibuat dengan menggunakan library sklearn.ensemble.RandomForestClassifier.
Parameter yang digunakan:
- random_state=42: Untuk memastikan hasil yang konsisten.
- Parameter lainnya menggunakan nilai default.

**Kelebihan:**
- Tahan terhadap overfitting karena menggunakan multiple trees.
- Dapat menangani data dengan fitur yang sangat banyak.

**Kekurangan:**
- Dapat menjadi lambat ketika dataset memiliki banyak fitur atau data sangat besar.
- Interpretasi model lebih sulit dibandingkan dengan model linear.
---
**2. K-Nearest Neighbors (KNN)**

KNN adalah algoritma berbasis instance-based learning yang memprediksi kelas berdasarkan mayoritas tetangga terdekat. Model ini dibuat dengan menggunakan library sklearn.neighbors.KNeighborsClassifier.
Parameter yang digunakan:
- n_neighbors=5: Menggunakan 5 tetangga terdekat.
- Parameter lainnya menggunakan nilai default.

**Kelebihan:**
- Mudah dipahami dan diimplementasikan.
- Tidak memerlukan proses training; prediksi dilakukan langsung pada data.

**Kekurangan:**
- Lambat pada data besar karena menghitung jarak untuk setiap data pada prediksi.
- Sensitif terhadap skala fitur, sehingga memerlukan normalisasi.
- Rentan terhadap noise dalam data.
---
**3. XGBoost**

XGBoost (Extreme Gradient Boosting) adalah algoritma boosting berbasis pohon keputusan yang mengoptimalkan loss function secara iteratif. Model ini dibuat dengan menggunakan library xgboost.XGBClassifier.
Parameter yang digunakan:
- random_state=42: Untuk memastikan hasil yang konsisten.
- eval_metric='logloss': Fungsi evaluasi untuk meminimalkan kesalahan logaritmik.
- use_label_encoder=False: Menonaktifkan encoding label secara otomatis.

**Kelebihan:**
- Salah satu algoritma terbaik dalam menangani data tabular.
- Mendukung tuning hyperparameter yang luas.
- Efisien dalam menangani dataset besar.

**Kekurangan:**
- Membutuhkan tuning hyperparameter untuk performa optimal.
- Interpretasi model lebih kompleks dibandingkan model lainnya.
---
Ketiga model yang sudah diimplentasikan didapatkan model terbaik yang dipilih adalah XGBoost karena dari kelebihan dari model dan hasil evaluasi yang sudah diciptakan dari model XGBoost, yang dimana detailnya bisa dilihat pada bagian **Evaluasi**.

## Evaluation
Pada tahap evaluation, percobaan modelling untuk customer churn prediction menggunakan beberapa metriks evaluasi seperti Accuracy, F1-Score, Precission, Recall dan Conffusion Matrix. Berikut penjelsannya:

**1. Accuracy**

Akurasi mengukur proporsi prediksi yang benar dibandingkan dengan keseluruhan prediksi.Akurasi memberikan gambaran umum kinerja model, tetapi dapat menyesatkan jika dataset tidak seimbang.
**formula:** ![Akurasi](https://i.postimg.cc/3NR0M9R5/pasted-image-0.png)

**2. Precision**

Precision mengukur proporsi prediksi positif yang benar terhadap semua prediksi positif. Precision penting dalam kasus di mana False Positives (FP) harus diminimalkan, misalnya ketika salah memprediksi pelanggan churn dapat berdampak negatif pada strategi bisnis.
**formula:**

![Precision](https://i.postimg.cc/QN4WgL4X/pasted-image-0-1.png)
**3. Recall**

Recall mengukur proporsi prediksi positif yang benar terhadap semua kasus sebenarnya positif. Recall penting ketika False Negatives (FN) harus diminimalkan, misalnya ketika perusahaan ingin memastikan semua pelanggan churn terdeteksi.
**formula:**

![Recall](https://i.postimg.cc/RhD6vf63/pasted-image-0-2.png)

**4. F1-Score**

F1-Score adalah rata-rata harmonis antara precision dan recall, memberikan keseimbangan antara keduanya.F1-Score berguna ketika penting untuk menemukan keseimbangan antara precision dan recall.
**formula:**![F1-Score](https://i.postimg.cc/PxKvF0dQ/pasted-image-0-3.png)
---
**Analisis Hasil:**

![F1-Score](https://i.postimg.cc/br8qXvN7/Screenshot-2024-11-28-140636.png)
- Random Forest dan XGBoost memiliki performa yang sangat tinggi, dengan akurasi hampir sempurna (99.99%). Kedua model menunjukkan keseimbangan yang sangat baik antara precision, recall, dan F1-Score, menunjukkan kemampuan untuk memprediksi pelanggan churn dengan akurasi tinggi tanpa mengabaikan kelas tertentu.
- KNN memiliki akurasi lebih rendah (96.60%) dibandingkan dua model lainnya, tetapi tetap menunjukkan performa yang baik. Precision dan recall lebih rendah dibandingkan dengan Random Forest dan XGBoost, menunjukkan bahwa KNN mungkin kurang efektif dalam menangani data besar atau kompleksitas tinggi.
---
**Model Testing**

Testing model menggunakan confusion matrix,  confusion matrix adalah tabel yang menunjukkan perbandingan antara prediksi model dan nilai aktual. Matriks ini terdiri dari empat komponen utama:
- True Positive (TP): Prediksi positif yang benar (kelas positif terdeteksi dengan benar).
- True Negative (TN): Prediksi negatif yang benar (kelas negatif terdeteksi dengan benar).
- False Positive (FP): Prediksi positif yang salah (kelas negatif terdeteksi sebagai positif, juga disebut Type I Error).
- False Negative (FN): Prediksi negatif yang salah (kelas positif terdeteksi sebagai negatif, juga disebut Type II Error). Berikut hasil confusion matrix dari ketiga model.

**Random Forest**

![CM_RF](https://i.postimg.cc/Cx94Ks4G/download7.png)

**K-Nearest Neighbor**

![CM_RF](https://i.postimg.cc/25v7LLHP/download8.png)

**XGBoost**

![CM_RF](https://i.postimg.cc/LXpBt4wh/download9.png)

Dilihat dari ketiga testing model menggunakan confusion matrix, XGBoost merupakan model yang benar mempredict churn dan non-churn dengan jumlah yang paling banyak.

## Kesimpulan
Proyek prediksi customer churn ini berhasil menjawab problem statement dengan memberikan wawasan melalui EDA terkait faktor-faktor yang memengaruhi churn dan membandingkan kinerja model Random Forest, KNN, dan XGBoost. Hasil evaluasi menunjukkan XGBoost sebagai model terbaik dengan akurasi tinggi (99,99%) serta keseimbangan metrik evaluasi lainnya. Tujuan proyek tercapai, yakni memahami faktor churn, menentukan model terbaik, dan memberikan solusi berbasis data untuk strategi retensi pelanggan. Model XGBoost mampu mendeteksi pelanggan berisiko churn secara akurat, memungkinkan perusahaan mengambil langkah proaktif seperti penawaran khusus atau peningkatan layanan. Solusi ini berdampak signifikan dalam mengurangi tingkat churn, menghemat biaya akuisisi, serta meningkatkan profitabilitas bisnis melalui optimalisasi customer lifetime value (CLV).

## Refrensi
[1] Chong, A., Khaw, K., Yeong, W., & Chuah, W. (2023). Customer Churn Prediction of Telecom Company Using Machine Learning Algorithms. Journal of Soft Computing and Data Mining. https://doi.org/10.30880/jscdm.2023.04.02.001.

[2] Miao, X., & Wang, H. (2022). Customer Churn Prediction on Credit Card Services using Random Forest Method. Proceedings of the 2022 7th International Conference on Financial Innovation and Economic Development (ICFIED 2022). https://doi.org/10.2991/aebmr.k.220307.104.

[3] Reddy, M., Raghavaraju, S., & Lashyry, P. (2022). Ensemble Approach on the Online Shopping Churn Prediction. 2022 6th International Conference on Trends in Electronics and Informatics (ICOEI), 01-08. https://doi.org/10.1109/ICOEI53556.2022.9776921.
