# WS-13: Data Preprocessing

> **Bab 13 — Preprocessing & Persiapan Data untuk Analisis**

---

# Ringkasan Materi

## Data Refinement Pipeline

```
Raw Dataset
      ↓
Data Cleaning
      ↓
Data Transformation
      ↓
Feature Scaling / Normalization
      ↓
Processed Dataset
      ↓
Machine Learning Model
      ↓
Performance Evaluation
```

Pada penelitian machine learning, preprocessing merupakan tahapan penting yang bertujuan meningkatkan kualitas data sebelum proses pelatihan model dilakukan. Seluruh proses preprocessing harus terdokumentasi dengan baik agar penelitian dapat direplikasi dan menghasilkan kesimpulan yang valid.

---

# Empat Prinsip Preprocessing

| Prinsip | Deskripsi |
|---------|-----------|
| Consistency | Seluruh data diproses menggunakan metode yang sama. |
| Transparency | Setiap tahapan preprocessing didokumentasikan dengan jelas. |
| Reproducibility | Peneliti lain dapat mengulang seluruh proses dengan hasil yang sama. |
| Minimal Distortion | Perubahan terhadap data dilakukan seminimal mungkin agar karakteristik data tetap terjaga. |

---

# Cleaning Triad

| Masalah | Strategi | Risiko |
|---------|----------|--------|
| Missing Values | Imputasi median atau penghapusan data sesuai proporsi missing | Kehilangan informasi atau bias |
| Duplicate Data | Identifikasi kemudian hapus data duplikat | Salah menghapus data yang sebenarnya valid |
| Error Format | Menyeragamkan tipe data dan encoding | Kehilangan informasi bila konversi tidak tepat |

---

# Normalisasi Data

| Metode | Formula | Output | Sensitif terhadap Outlier |
|---------|----------|---------|--------------------------|
| Min-Max Scaling | (x-min)/(max-min) | 0–1 | Ya |
| Z-Score Standardization | (x-μ)/σ | Tidak terbatas | Cukup Robust |
| Robust Scaling | (x-median)/IQR | Tidak terbatas | Sangat Robust |

Pada penelitian ini, normalisasi hanya diterapkan apabila algoritma yang digunakan memerlukannya, misalnya Support Vector Machine (SVM) dan K-Nearest Neighbor (KNN). Model berbasis Decision Tree dan Random Forest tidak memerlukan normalisasi karena tidak sensitif terhadap skala fitur.

---

# Pencegahan Data Leakage

Data leakage dapat menyebabkan performa model terlihat jauh lebih baik dibandingkan kondisi sebenarnya.

Hal-hal yang harus dihindari:

- Menghitung parameter normalisasi menggunakan seluruh dataset.
- Melakukan feature selection sebelum train-test split.
- Menggunakan informasi dari data testing selama proses preprocessing.
- Melakukan preprocessing yang memanfaatkan label pada data testing.

Seluruh proses preprocessing dilakukan **setelah pembagian data training dan testing** sehingga informasi dari data testing tidak memengaruhi proses pelatihan model.

---

# Template A.13 — Preprocessing Documentation Log

```
PREPROCESSING LOG

Dataset           : Heart Disease Dataset
Jumlah data awal  : 303 records

Cleaning

| Masalah | Jumlah Kasus | Penanganan | Justifikasi |
|---------|--------------|------------|-------------|
| Missing Value | 5 | Median Imputation | Jumlah sedikit dan hanya pada fitur numerik |
| Duplicate | 2 | Dihapus | Data identik |
| Error Format | 0 | Tidak ada | - |

Transformation

| Transformasi | Variabel | Detail | Alasan |
|--------------|----------|--------|--------|
| Label Encoding | Target | 0 = Tidak sakit, 1 = Sakit | Memudahkan klasifikasi |
| Feature Selection | Seluruh fitur | Berdasarkan korelasi dan literatur | Mengurangi overfitting |

Normalization

Metode    : StandardScaler (Z-Score)
Alasan    : Digunakan untuk model SVM dan KNN
Parameter : Dihitung hanya dari training set

Leakage Check

[x] Parameter normalisasi berasal dari training set
[x] Tidak ada informasi test set digunakan
[x] Cross Validation dilakukan setelah preprocessing training

Jumlah data akhir : 301 records
Script tersedia   : Ya → 05-kode/preprocessing/preprocessing.py
```

---

# Latihan 1 — Cleaning Plan

## Pemeriksaan Dataset

| Masalah | Jumlah Kasus | Penanganan | Justifikasi |
|---------|--------------|------------|-------------|
| Missing Value | 5 | Median Imputation | Missing <5% |
| Duplicate | 2 | Dihapus | Record identik |
| Outlier | 3 | Dipertahankan | Masih merupakan kondisi medis yang valid |

Jumlah data sebelum cleaning : **303**

Jumlah data setelah cleaning : **301**

Persentase data berubah :

```
(303-301)/303 ×100 = 0,66%
```

---

# Latihan 2 — Keputusan Normalisasi

| Variabel | Range Asli | Distribusi | Outlier | Metode | Alasan |
|----------|------------|------------|----------|---------|--------|
| Age | 29–77 | Normal | Tidak | Tidak dinormalisasi | Decision Tree tidak memerlukan scaling |
| Cholesterol | 126–564 | Right Skewed | Ya | StandardScaler | Digunakan pada SVM |
| Resting Blood Pressure | 94–200 | Hampir normal | Sedikit | StandardScaler | Menyamakan skala fitur |
| Maximum Heart Rate | 71–202 | Normal | Tidak | StandardScaler | Mempermudah optimasi model |

Apakah normalisasi diperlukan?

**Ya**, tetapi hanya diterapkan pada algoritma yang sensitif terhadap skala data, seperti SVM dan KNN.

### Leakage Check

- [x] Parameter dihitung dari training set.
- [x] Normalisasi dilakukan setelah train-test split.

---

# Latihan 3 — Preprocessing Report

```
PREPROCESSING SUMMARY

1. Dataset
   Heart Disease Dataset (UCI Repository)

2. Data Awal
   303 records
   13 fitur
   1 label

3. Cleaning
   Missing Value : 5 kasus
   Metode        : Median Imputation

   Duplicate     : 2 kasus
   Tindakan      : Dihapus

   Error Format  : Tidak ditemukan

4. Transformation

   - Label Encoding
   - Feature Selection berdasarkan literatur
   - Konversi seluruh fitur numerik ke format float

5. Normalisasi

   Metode :
   StandardScaler

   Parameter dihitung dari :
   Training Set

6. Data Akhir

   301 records
   13 fitur

7. Leakage Check

   [x] Lulus

   Tidak ditemukan indikasi data leakage selama preprocessing.
```

---

# Refleksi

Apakah normalisasi selalu diperlukan?

Tidak. Normalisasi hanya diperlukan apabila algoritma machine learning sensitif terhadap skala data. Algoritma berbasis pohon keputusan, seperti Decision Tree dan Random Forest, umumnya tidak memerlukan normalisasi.

Apa risiko over-preprocessing?

Melakukan preprocessing secara berlebihan dapat mengubah distribusi asli data sehingga informasi penting hilang. Selain itu, preprocessing yang tidak tepat dapat menyebabkan data leakage, menghasilkan performa model yang terlihat tinggi pada proses evaluasi tetapi buruk ketika diterapkan pada data baru. Oleh karena itu, setiap langkah preprocessing harus memiliki alasan yang jelas, terdokumentasi, dan dapat direproduksi.
