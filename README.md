# Visualisasi Data Medis Berdimensi Tinggi (PCA & t-SNE)
**Mata Kuliah:** Machine Learning (Pertemuan 25)

## Anggota Kelompok
1.  **Farrel Faza** (24523031)
2.  **Muhammad Hafizh Hakim** (24523062)

---

## Deskripsi Proyek
Proyek ini dibuat untuk memenuhi Tugas Praktik Pertemuan ke 25-Dimensionality Reduction with Python. Fokus utama proyek ini adalah menerapkan teknik **Dimensionality Reduction** (Reduksi Dimensi) untuk memvisualisasikan dataset medis yang kompleks agar polanya mudah dipahami oleh manusia.

### Masalah
Dataset *Breast Cancer Wisconsin* memiliki **30 fitur numerik** (seperti radius, tekstur, area, dll) yang digunakan untuk menentukan apakah tumor bersifat ganas (*Malignant*) atau jinak (*Benign*). Karena manusia tidak dapat melihat atau membayangkan ruang 30 dimensi, sulit untuk mengetahui apakah kedua jenis tumor ini memiliki karakteristik fisik yang benar-benar berbeda dan terpisah.

### Solusi & Tujuan
Kami menggunakan dua metode reduksi dimensi, yaitu **PCA (Principal Component Analysis)** dan **t-SNE**, untuk memadatkan data dari 30 dimensi menjadi **2 dimensi (2D)**. Hasilnya divisualisasikan dalam bentuk Scatter Plot untuk melihat seberapa jelas pemisahan (*clustering*) antara kelompok tumor ganas dan jinak.

---

## Dataset
* **Nama Dataset:** Breast Cancer Wisconsin (Diagnostic).
* **Sumber:** UCI Machine Learning Repository (diakses via `sklearn.datasets`).
* **Jumlah Sampel:** 569 data pasien.
* **Jumlah Fitur:** 30 fitur numerik + 1 kolom target.
* **Target:**
    * 0: Malignant (Ganas) - *Warna Merah di visualisasi*
    * 1: Benign (Jinak) - *Warna Hijau di visualisasi*

---

## Metode yang Digunakan
1.  **Standard Scaler (Preprocessing)**
    Menormalisasi data agar semua fitur memiliki skala yang setara (rata-rata=0, variansi=1). Langkah ini sangat krusial agar fitur dengan nilai satuan besar (misal: Area) tidak mendominasi hasil analisis.

2.  **PCA (Principal Component Analysis)**
    Metode statistik linear yang mereduksi dimensi dengan mencari kombinasi fitur yang menyimpan variansi (informasi) terbesar dari data asli.

3.  **t-SNE (t-Distributed Stochastic Neighbor Embedding)**
    Metode non-linear canggih yang bekerja dengan prinsip probabilitas untuk mempertahankan struktur "bertetangga" (kemiripan lokal) antar data.

---

## Analisis Hasil Visualisasi

### 1. Hasil PCA (Linear)
Hasil visualisasi data menggunakan Principal Component Analysis (PCA) menunjukkan bahwa penyebaran data membentuk pola yang cenderung memanjang secara linear. Hal ini mencerminkan sifat dasar PCA yang mereduksi dimensi dengan mempertahankan hubungan linear antar fitur. Pada proyeksi dua komponen utama, kelas tumor Ganas dan Jinak sudah mulai terlihat terpisah, di mana masing-masing kelompok cenderung berada pada sisi yang berbeda dari ruang fitur hasil transformasi. Meskipun demikian, masih ditemukan area tumpang tindih di sekitar batas pemisahan kedua kelas. Tumpang tindih ini menunjukkan bahwa terdapat sejumlah data dengan karakteristik yang mirip secara linear, sehingga sulit dipisahkan secara sempurna menggunakan pendekatan PCA saja. Namun, kelebihan utama PCA terletak pada kemampuannya dalam mempertahankan informasi penting dari data asli. Dalam hal ini, sekitar 63% variansi data berhasil dipertahankan hanya dengan dua komponen utama, sehingga representasi data yang dihasilkan masih cukup informatif untuk analisis awal dan eksplorasi pola global.


### 2. Hasil t-SNE (Non-Linear)
Berbeda dengan PCA, hasil visualisasi menggunakan t-Distributed Stochastic Neighbor Embedding (t-SNE) memperlihatkan pemetaan data yang jauh lebih kontras dan non-linear. Data terdistribusi membentuk dua cluster besar yang terpisah secara sangat jelas antara pasien dengan tumor Ganas dan Jinak. Pola ini menunjukkan bahwa t-SNE mampu menangkap struktur lokal dan hubungan non-linear antar data dengan sangat baik. Hampir tidak terdapat tumpang tindih antar kelas, yang menandakan bahwa data dengan karakteristik tumor yang serupa dikelompokkan secara rapat dalam satu cluster yang sama. Jarak yang jauh antar cluster menggambarkan perbedaan karakteristik yang signifikan antara kedua kelas tumor. Hasil ini menegaskan keunggulan t-SNE dalam visualisasi dan eksplorasi pemisahan kelas, meskipun metode ini lebih difokuskan pada representasi struktur lokal daripada interpretasi variansi global seperti pada PCA.

---

## Kesimpulan Akhir
Berdasarkan perbandingan kedua metode, kami menyimpulkan bahwa:

Metode **t-SNE lebih unggul dan sesuai** untuk kasus visualisasi dataset Breast Cancer ini.

**Alasannya:**
t-SNE berhasil menangkap struktur non-linear data, sehingga mampu memisahkan kelompok tumor ganas dan jinak secara tajam (*distinct*). Hal ini membuat visualisasi jauh lebih intuitif dan meyakinkan untuk menunjukkan bahwa kedua jenis tumor tersebut memang memiliki perbedaan karakteristik fisik yang signifikan.
