# Estimasi Kekeruhan Air Berdasarkan Citra Digital Menggunakan ANN dan Random Forest

## Deskripsi

Proyek ini bertujuan untuk mengestimasi tingkat kekeruhan air (turbiditas) melalui pemrosesan citra digital guna mendukung **SDG 6 (Clean Water and Sanitation)**. Sistem ini dikembangkan untuk menyediakan solusi pemantauan kualitas air yang murah, cepat, dan objektif tanpa bergantung sepenuhnya pada sensor fisik yang mahal.

Sistem dikembangkan menggunakan pendekatan **Hybrid Feature Extraction**, yaitu:

* **Analisis Warna:** Ruang warna RGB dan HSV untuk menangkap karakteristik kromatika air.
* **Analisis Tekstur (GLCM):** Matriks spasial untuk mendeteksi keberadaan partikel tersuspensi melalui pola piksel.

---

## Tujuan

* Mengestimasi tingkat kekeruhan air secara otomatis dari input citra digital.
* Mengekstraksi fitur kualitatif air menjadi data kuantitatif (Hybrid Features).
* Membandingkan performa model **Artificial Neural Network (ANN)** dan **Random Forest Regression**.
* Menyediakan instrumen monitoring kualitas air yang aksesibel untuk mendukung target pembangunan berkelanjutan.

---

## Dataset

Dataset yang digunakan berasal dari Mendeley Data (Dataset **UIDLEIA**):

👉 [Link Dataset UIDLEIA - Mendeley Data](https://data.mendeley.com/datasets/8p66npxp82/1)

Dataset berisi citra bawah air dengan berbagai tingkat kejernihan. Label target yang digunakan adalah:
* **MAV (Mean Acceptance Value):** Nilai subjektivitas manusia terhadap kejernihan air yang telah dikuantifikasi untuk kebutuhan pelatihan model machine learning.

---

## Metodologi

### 1. Preprocessing
* Sinkronisasi nama file citra dengan label MAV pada file Excel.
* Standardisasi ukuran citra menjadi **128x128 piksel**.
* Normalisasi fitur menggunakan **StandardScaler (Z-Score Scaling)** untuk menyeimbangkan skala antara fitur warna dan tekstur.

### 2. Ekstraksi Fitur (Hybrid Method)
* **Fitur Warna:** Ekstraksi nilai rata-rata (*mean*) pada kanal **RGB** dan **HSV**. Ruang warna HSV digunakan karena lebih stabil terhadap fluktuasi intensitas cahaya bawah air.
* **Fitur Tekstur (GLCM):** Menggunakan *Gray Level Co-occurrence Matrix* untuk menghitung metrik **Contrast** (kekasaran tekstur) dan **Homogeneity** (keseragaman tekstur).

### 3. Pemodelan (Machine Learning)
* **Artificial Neural Network (ANN):** Mengimplementasikan `MLPRegressor` dengan arsitektur dua *hidden layers* (100, 50) dan fungsi aktivasi untuk memetakan hubungan non-linear.
* **Random Forest Regression:** Menggunakan metode *ensemble learning* dengan 100 *decision trees* untuk mendapatkan prediksi yang stabil.

---

## Evaluasi Model

Performa model dievaluasi menggunakan metrik standar regresi:

* **R-Squared ($R^2$):** Menilai seberapa akurat model dalam merepresentasikan varians data target.
* **Mean Absolute Error (MAE):** Menghitung rata-rata selisih absolut antara nilai prediksi sistem dengan nilai MAV aktual.

---

## Teknologi

* **Bahasa:** Python 3
* **Library:**
    * `OpenCV` & `Scikit-Image` (Pemrosesan & Ekstraksi Fitur)
    * `Scikit-Learn` (Machine Learning & Scaling)
    * `Pandas` & `Numpy` (Manajemen Data Tabel & Matriks)
    * `Matplotlib` & `Seaborn` (Visualisasi Hasil)

---

## Anggota Kelompok 6

* **Abyan Raga Kusuma** - 234311001
* **Iqbal Khafidz Abrori** - 234311015

---

## Catatan

Dataset citra tidak diunggah ke repositori ini karena keterbatasan ukuran file. Silakan unduh dataset secara mandiri melalui tautan Mendeley Data yang disediakan di atas dan simpan pada direktori yang sesuai sebelum menjalankan notebook.
