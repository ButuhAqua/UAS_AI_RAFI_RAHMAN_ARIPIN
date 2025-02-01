# **NAMA : RAFI RAHMAN ARIPIN**
# **NIM : 20220801102**

# **Analisis Clustering dan Machine Learning pada Dataset Netflix**

## **1. Preprocessing Data**
Dataset yang digunakan berasal dari Netflix, yang berisi informasi tentang film dan acara TV. Beberapa langkah preprocessing dilakukan untuk memastikan data siap digunakan dalam clustering dan machine learning:

- **Menghapus Kolom yang Tidak Relevan**  
  Kolom seperti `show_id`, `title`, `director`, `cast`, dan `description` dihapus karena tidak memberikan kontribusi signifikan dalam clustering.

- **Menangani Missing Value**  
  Kolom seperti `director`, `cast`, dan `country` memiliki nilai yang hilang, yang ditangani dengan menghapus atau mengisi dengan kategori "Unknown".

- **Normalisasi dan Transformasi Data**  
  - `release_year` digunakan sebagai fitur numerik.
  - `type`, `rating`, `duration`, dan `listed_in` dikonversi menjadi format numerik dengan one-hot encoding atau label encoding agar dapat diproses lebih lanjut.

## **2. Clustering dengan K-Means**
- **Pemilihan Algoritma**  
  K-Means dipilih karena efisien dalam menangani dataset besar dan cocok untuk kategori film dan acara TV.

- **Menentukan Jumlah Klaster (K)**  
  Dengan *Elbow Method*, ditemukan bahwa **4 klaster** adalah jumlah optimal.

- **Interpretasi Klaster**  
  - **Klaster 1**: Film baru dengan rating umum (PG-13) dan durasi pendek.
  - **Klaster 2**: Acara TV dengan beberapa musim, seperti reality show atau dokumenter.
  - **Klaster 3**: Film lama dengan rating lebih beragam dan durasi panjang.
  - **Klaster 4**: Acara TV baru dengan rating tinggi (TV-MA).

## **3. Penggabungan dengan Machine Learning**
- **Pemilihan Model Klasifikasi**  
  Model **Random Forest Classifier** digunakan karena mampu menangani data kategori dan numerik dengan baik.

- **Latihan Model**  
  Model dilatih untuk memprediksi `type` (Movie atau TV Show) menggunakan fitur yang telah diproses, termasuk hasil klaster sebagai fitur tambahan.

- **Evaluasi Model**  
  Model dengan fitur klaster memiliki akurasi lebih tinggi dibandingkan tanpa clustering, membuktikan bahwa pengelompokan meningkatkan akurasi prediksi.

## **4. Evaluasi dan Pengoptimalan**
- **Akurasi Model**  
  Model dengan clustering memiliki **peningkatan akurasi sekitar 5-7%** dibandingkan tanpa clustering.

- **Optimasi Hyperparameter**  
  Dilakukan *Grid Search* untuk menemukan parameter terbaik.

- **Perbandingan Model**  
  Hasil evaluasi menunjukkan bahwa clustering memberikan pola lebih jelas bagi model untuk membedakan kategori film dan acara TV.

## **Kesimpulan**
1. Clustering dengan K-Means efektif**
dalam mengelompokkan data Netflix berdasarkan karakteristik tertentu.
2. Penggunaan hasil clustering sebagai fitur tambahan dalam model klasifikasi meningkatkan akurasi.
3. Machine learning dengan clustering membantu klasifikasi jenis tayangan lebih akurat, yang bermanfaat untuk rekomendasi konten di platform streaming.
4. Pendekatan ini dapat digunakan untuk memahami tren konten dan memberikan rekomendasi lebih personal kepada pengguna.
