


## Predict Customer Clicked Ads Classification by Using Machine Learning

Sebuah perusahaan di Indonesia ingin mengetahui efektifitas sebuah iklan yang mereka tayangkan, hal ini penting bagi perusahaan yang bergerak di bidang consultant digital marketing agar dapat mengetahui seberapa besar ketercapainnya iklan yang dipasarkan sehingga dapat menarik customers untuk melihat iklan.
Pada mini project kali ini, kamu ditugaskan sebagai anggota pada tim data perusahaan tersebut. Anda bertanggung jawab untuk mencari insight terkait perilaku user dari data tersebut dengan membuatkan visualisasinya, membuat sebuah machine learning yang relevan dengan kebutuhan perusahaan, serta membuat rekomendasi dari hasil penemuan-penemuan yang didapat.


#### Customer Type and Behaviour Analysis on Advertisement
##### Univariate Analysis
- Fitur Area Income memiliki distribusi negative skewed, artinya kebanyakan customer berpendapatan rendah dibandingkan berpendapatan tinggi.
- Fitur Age memiliki distribusi positive skewed, artinya kebanyakan customer memiliki umur lebih dari 30 tahun dibandingkan customer yang memiliki umur kurang dari itu.
- Feature yang memiliki distribusi normal : Daily Time Spent on Site and Daily Internet Usage
- Feature yang memiliki outlier : Area Income
- Daily Time Spent on Site:
Waktu yang dihabiskan oleh user yang mengklik iklan memiliki distribusi skew kanan artinya waktu yang dihabiskan cenderung sedikit yaitu 40-45 menit.
Sedangkan waktu yang dihabiskan user yang tidak menklik iklan memiliki distribusi skew kiri artinya waktu yang di habiskan cenderung banyak yaitu 75-80 menit.
- Usia Pengguna:
Usia yang mengklik iklan memiliki distribusi normal dengan rata-ratanya adalah 40 tahun. Sedangkan usia user yang tidak mengklik iklan memiliki distribusi skew kanan artinya usian pengguna cenderung lebih muda yaitu di bawah 40 tahun.
- Daily Internet Usage:
Penggunaan internet harian untuk user yang mengklik iklan memiliki distribusi skew kanan, artinya penggunaan internet harian user cenderung rendah yaitu 100-150 menit. Sedangkan penggunaan internet harian untuk user yang tidak mengklik iklan memiliki disribusi skew kiri, artinya penggunaan internet harian user cenderung tinggi yaitu 200-250 menit.
- Area Income
Pendapatan wilayah geografis user yang mengklik iklan memiliki distribusi normal, sedangkan pendapatan wilayah geografis user yang tidak mengklik iklan memiliki distribusi skew kiri yang artinya user dengan pendapatan wilayah geografis tinggi.
- Jumlah "Yes" dan "No" pada fitur "Clicked on Ad" seimbang. Keseimbangan ini mengindikasikan bahwa dataset memiliki distribusi yang relatif seragam antara pengguna yang mengklik iklan ("Yes") dan yang tidak ("No")
- Jumlah perempuan dan laki-laki dalam fitur "Male" tidak terlalu timpang. Ini menunjukkan bahwa dataset memiliki seimbang antara kedua jenis kelamin, yang bisa berguna dalam analisis selanjutnya.
-  Fitur "Province" didominasi oleh dua nilai utama, yaitu "DKI Jakarta" dan "Jawa Barat". Hal ini menunjukkan bahwa sebagian besar pengguna berasal dari dua provinsi ini, sementara provinsi-provinsi lainnya mungkin memiliki kontribusi yang lebih rendah dalam dataset.

##### Bivariate Analysis
- User dengan penggunaan internet harian rendah memiliki waktu yang dihabiskan disitus juga rendah yang memiliki kecenderungan untuk mengklik iklan, sedangkan user dengan penggunaan internet harian tinggi memiliki waktu yang dihabiskan di situs juga tinggi memiliki kecenderungna untuk tidak mengklik iklan.
- User dengan usia yang lebih tua, penggunaan internet harian yang lebih rendah, dan waktu yang dihabiskan di situs yang lebih rendah cenderung untuk mengklik iklan.
- User dengan usia yang lebih muda, penggunaan internet harian tinggi, dan waktu yang dihabiskan di situs juga tinggi memiliki kecenderungan untuk tidak mengklik iklan.

##### Multivariate analysis
- Dari hasil korelasi yang diperoleh melalui heatmap, ditemukan fitur yang memiliki korelasi yang kuat (redundan) yaitu fitur city dengan province. Oleh karena itu, fitur city dan province tidak digunakan dalam pemodelan.
- Penggunaan internet harian memiliki korelasi positif yang tinggi (51%) dengan waktu harian yang dihabiskan di website. Artinya, semakin sering pengguna menggunakan internet, semakin lama mereka menghabiskan waktu di situs web.
- Usia pengguna memiliki korelasi negatif dengan tiga fitur lainnya: pendapatan rata-rata geografis pengguna, waktu yang dihabiskan di website, dan penggunaan internet harian. Korelasi tertinggi adalah dengan penggunaan internet harian (37%). Hal ini menunjukkan bahwa semakin tua usia pengguna, semakin jarang mereka menggunakan internet harian.



#### Data Cleaning & Preprocessing
Data Cleaning & Preprocessing Flow


#### Data Modeling
#####  Hasil Without Standardization
-   Sebagian besar model menunjukkan hasil kinerja yang serupa antara data uji dan data latih, yang menandakan bahwa tidak terdapat perbedaan yang signifikan yang mengindikasikan overfitting atau underfitting
-   Dari hasil pemodelan pada data uji, nilai recall lebih tinggi pada model Random Forest dan Gradient Boosting.
-   Selain akurasi, hasil recall pada data uji juga menunjukkan hasil yang lebih baik pada model Gradient Boosting.

##### Hasil With Standardization
-   Terjadi peningkatan pada model, hal nni menunjukkan bahwa penggunaan Min-Max Scaler telah memberikan dampak positif pada performa model.
-   Terjadi perubahan dalam hasil kinerja terbaik, di mana hasil akurasi tes tertinggi ditemukan pada model Random Forest dan Gradient Boosting. Hal ini menunjukkan bahwa kedua model tersebut adalah yang terbaik dalam memprediksi data uji setelah dilakukan normalisasi/standarisasi. Di pilih model Random Forest karena nilai recal antara train dan test gapnya lebih dekat dari pada yang Gradient Boosting.

#### Business Recommendation and Simulation
##### Confusion matrix

- Recall mengukur rasion antara jumlah user yang diprediksi mengklik iklan dan benar-benar mengklik iklan. dengan jumlah user yang diprediksi tidak mengklik iklan tetapi ada kenyatannya mengklik iklan. Memaksimalkan recall ini akan meminimalkan jumlah user yang salah prediksi akan mengklik iklan.
- Berdasarkan model yagn digunakan, terdapat 2 feature yang paling berpengaruh yaitu Daily Internet Usage dan Dailt Time Spent on Site. Terdapat feature yang cukup berpengaruh yaitu feature Area Income
##### Feature Important

- Berdasarkan model yang digunakan, terdapat 2 feature yang paling berpengaruh yaitu Daily Internet Usage dan Dailt Time Spent on Site.
- Semakin rendah Daily Internet Usage, maka semakin banyak user mengklik iklan, sedangkan semakin tinggi Daily Internet Usage, maka semakin sedikit user mengklik iklan.
- Begitu pun dengan Daily Time Spent on Site. Semakin rendah Daily Time Spent on Site, maka semakin banyak user mengklik iklan, sedangkan semakin tinggi Daily Time Spent on Site, maka semakin sedikit user mengklik iklan.
- Selain itu terdapat feature yang lain yang mempengaruhi yaitu Area Income, semaking tinggi area income, semakin tinggi area income user, semakin cenderung untuk tidak mengklik iklan.
##### Interpretasi
- Dari data yang diperoleh, terdapat 2 segmen user, yaitu segmen user aktif dan non aktif.
User aktif memiliki karakteristik dengan usia di bawah 35 tahun yaitu masuk dalam grup teen dan young profesional, memiliki penggunaan internet yang tinggi, serta banyak menghabiskan waktu di situs, memiliki pendapatan yang lebih rendah.
- Sementara user non aktif memiliki karakteristik usia di atas 35 tahun yaitu grup Middle Age, Pre Senior dan Senior, memiliki penggunaan internet rendah yang mempengaruhi waktu yang dihabiskan di situs juga rendah, serta memiliki pendapatan yang lebih tinggi. User non-aktif cenderung untuk mengklik iklan dibandingkan dengan user aktif.
##### Recommendation Business
Penyesuaian Strategi Periklanan
-   Untuk pengguna aktif (usia di bawah 35 tahun), perusahaan dapat fokus pada iklan yang menarik bagi mereka, seperti penawaran khusus, promosi, atau iklan yang lebih interaktif.
    
-   Untuk pengguna non-aktif (usia di atas 35 tahun), perusahaan dapat menggunakan pendekatan iklan yang lebih informatif, menekankan kualitas produk atau layanan, dan menawarkan solusi yang relevan.
    
Pengelolaan Iklan
-   Mengelola frekuensi dan jumlah iklan yang ditampilkan kepada pengguna aktif. Terlalu banyak iklan dapat membuat mereka merasa terganggu dan mengurangi respons positif terhadap iklan.

##### Business Impact
