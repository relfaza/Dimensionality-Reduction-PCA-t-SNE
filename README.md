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
### Gambaran Umum
Hasil penerapan **Principal Component Analysis (PCA)** menunjukkan bahwa data memiliki pola penyebaran yang cenderung memanjang secara linear pada ruang dua dimensi. Hal ini mengindikasikan bahwa sebagian besar variasi data dapat dijelaskan melalui kombinasi linier dari fitur-fitur asli. Distribusi ini mencerminkan karakteristik PCA sebagai metode reduksi dimensi yang berfokus pada pemaksimalan variansi global tanpa mempertimbangkan label kelas.

### Pemisahan Kelas
Berdasarkan visualisasi PCA, kelas tumor **Ganas** dan **Jinak** mulai menunjukkan pemisahan yang cukup jelas. Kedua kelas tersebut cenderung terdistribusi pada sisi kiri dan kanan bidang PCA. Kondisi ini menunjukkan bahwa dua komponen utama yang digunakan telah mampu menangkap perbedaan karakteristik utama antara kedua kelas, meskipun PCA bukan metode yang secara khusus dirancang untuk klasifikasi.

### Overlap Data
Meskipun pemisahan kelas sudah terlihat, masih terdapat area tumpang tindih (*overlap*) yang cukup signifikan di sekitar batas pertemuan kedua kelas. Hal ini menandakan adanya beberapa sampel dengan karakteristik yang saling menyerupai sehingga tidak dapat dipisahkan secara sempurna melalui proyeksi linear. Overlap ini merupakan hal yang wajar karena PCA tidak memanfaatkan informasi label kelas.

### Informasi Variansi
Secara kuantitatif, dua komponen utama PCA mampu mempertahankan sekitar **63% variansi data asli**. Nilai ini menunjukkan bahwa sebagian besar informasi penting telah berhasil direpresentasikan dalam dimensi yang lebih rendah. Namun, masih terdapat sekitar 37% variansi yang tidak terwakili, yang kemungkinan mengandung pola non-linear atau informasi tambahan yang relevan untuk pemisahan kelas.

### Kesimpulan
PCA efektif digunakan sebagai tahap awal eksplorasi data dan visualisasi untuk memahami struktur dan distribusi data. Namun, untuk memperoleh pemisahan yang lebih optimal antara tumor ganas dan jinak, diperlukan metode lanjutan seperti reduksi dimensi non-linear atau algoritma klasifikasi yang mampu menangkap hubungan kompleks antar fitur.


### 2. Hasil t-SNE (Non-Linear)
* **Observasi:** Visualisasi t-SNE menunjukkan hasil yang sangat berbeda dan lebih "ekstrem".
* **Pemisahan:** Terbentuk dua **cluster (pulau)** besar yang terpisah sangat jelas dan jauh antara pasien tumor Ganas dan Jinak.
* **Keunggulan:** Hampir tidak ada data yang tumpang tindih. Pasien dengan karakteristik tumor yang mirip berkumpul sangat rapat.

---

## Kesimpulan Akhir
Berdasarkan perbandingan kedua metode, kami menyimpulkan bahwa:

Metode **t-SNE lebih unggul dan sesuai** untuk kasus visualisasi dataset Breast Cancer ini.

**Alasannya:**
t-SNE berhasil menangkap struktur non-linear data, sehingga mampu memisahkan kelompok tumor ganas dan jinak secara tajam (*distinct*). Hal ini membuat visualisasi jauh lebih intuitif dan meyakinkan untuk menunjukkan bahwa kedua jenis tumor tersebut memang memiliki perbedaan karakteristik fisik yang signifikan.
