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
* **Observasi:** Visualisasi PCA menunjukkan pola penyebaran data yang memanjang (linear).
* **Pemisahan:** Kelompok tumor Ganas dan Jinak sudah terlihat terpisah di sisi kiri dan kanan.
* **Kekurangan:** Masih terdapat **area tumpang tindih (*overlap*)** yang cukup terlihat di perbatasan antara kedua kelas. Ini wajar karena PCA hanya melakukan proyeksi linear.
* **Informasi Terjaga:** Sekitar **63%** informasi (variansi) data asli dapat dipertahankan dalam 2 komponen utama.

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
