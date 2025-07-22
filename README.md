# Proyek Prediksi Klaim Asuransi Perjalanan

Proyek ini adalah *final project* untuk Modul 3, bertujuan untuk membangun model *machine learning* yang dapat memprediksi kemungkinan seorang nasabah mengajukan klaim asuransi perjalanan.

---

## Latar Belakang

Perusahaan asuransi perjalanan menghadapi tantangan dalam mengelola risiko finansial akibat klaim yang tidak terduga. Kemampuan untuk mengidentifikasi nasabah berisiko tinggi sejak dini dapat membantu perusahaan dalam penetapan premi yang lebih akurat dan meningkatkan efisiensi operasional dalam penanganan klaim.

## Pernyataan Masalah

Bagaimana cara membangun sebuah sistem yang dapat memprediksi secara akurat nasabah mana yang berpotensi tinggi untuk mengajukan klaim asuransi perjalanan berdasarkan data historis mereka?

## Tujuan

1.  **Tujuan Utama:** Membangun model klasifikasi yang mampu memprediksi secara akurat apakah seorang nasabah akan mengajukan klaim ('Yes') atau tidak ('No').
2.  **Tujuan Pendukung:** Mengidentifikasi faktor-faktor kunci yang paling signifikan memengaruhi kemungkinan nasabah mengajukan klaim dan memberikan rekomendasi bisnis yang dapat ditindaklanjuti.

---

## Data

Dataset yang digunakan adalah data historis nasabah asuransi perjalanan, yang berisi fitur-fitur sebagai berikut:
* **Informasi Transaksi:** `Agency`, `Agency Type`, `Distribution Channel`, `Product Name`, `Net Sales`, `Commision (in value)`
* **Informasi Nasabah:** `Gender`, `Age`
* **Informasi Perjalanan:** `Duration`, `Destination`
* **Target:** `Claim` (Yes/No)

Salah satu karakteristik utama dari dataset ini adalah sangat tidak seimbang, di mana kelas minoritas ('Yes') hanya sekitar 1.1% dari total data.

---

## Metodologi

Proyek ini dikerjakan melalui beberapa tahapan utama:
1.  **Data Cleaning:** Menangani nilai yang hilang, menghapus data duplikat, dan memperbaiki kesalahan struktural pada data (seperti durasi negatif).
2.  **Exploratory Data Analysis (EDA):** Melakukan visualisasi untuk memahami distribusi data, mengidentifikasi pola, dan menemukan hubungan antar variabel.
3.  **Preprocessing:** Mengubah data kategorikal menjadi numerik menggunakan *One-Hot Encoding* dan melakukan standardisasi pada data numerik menggunakan *StandardScaler*.
4.  **Modeling:** Melatih model `RandomForestClassifier` dengan parameter `class_weight='balanced'` untuk menangani ketidakseimbangan data.
5.  **Evaluation:** Mengevaluasi performa model menggunakan metrik **F1-Score** dan **ROC AUC Score** yang cocok untuk kasus klasifikasi tidak seimbang.

---

## Hasil

Model final berhasil mencapai performa yang sangat baik dengan hasil sebagai berikut pada data uji:
* **ROC AUC Score:** 0.8249
* **F1-Score (untuk kelas 'Yes'):** 0.63
* **Recall (untuk kelas 'Yes'):** 0.71
* **Precision (untuk kelas 'Yes'):** 0.57

Hasil ini menunjukkan bahwa model memiliki kemampuan yang kuat untuk mengidentifikasi nasabah berisiko tinggi dengan keseimbangan yang baik antara Recall dan Precision.

---

## Kesimpulan dan Rekomendasi

**Kesimpulan:** Berhasil dibangun sebuah model *machine learning* yang fungsional dan efektif untuk memprediksi klaim asuransi, meskipun dihadapkan pada tantangan dataset yang sangat tidak seimbang.

**Rekomendasi Bisnis:**
1.  **Implementasi Model:** Mengintegrasikan model untuk *scoring* risiko polis baru secara *real-time*.
2.  **Optimalisasi Operasional:** Menggunakan hasil prediksi untuk memprioritaskan investigasi oleh tim klaim.
3.  **Strategi Produk:** Menganalisis fitur-fitur paling berpengaruh (seperti `Product Name`, `Agency Type`) untuk menginformasikan strategi pengembangan produk dan pemasaran.
