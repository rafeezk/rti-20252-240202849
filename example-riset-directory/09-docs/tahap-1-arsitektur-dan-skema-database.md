# Tahap 1 — Perancangan Arsitektur Penelitian dan Desain Eksperimen

**Status:** Selesai

---

# 1. Arsitektur Penelitian

Penelitian ini bertujuan mengembangkan model machine learning untuk prediksi penyakit jantung pada kondisi **dataset medis berukuran terbatas** dengan fokus utama pada **pengurangan overfitting** serta **peningkatan kemampuan generalisasi model**.

Arsitektur penelitian terdiri atas lima komponen utama.

## Dataset Medis

Dataset merupakan sumber utama penelitian yang berisi atribut klinis pasien, seperti:

- usia
- jenis kelamin
- tekanan darah
- kadar kolesterol
- gula darah
- detak jantung maksimum
- jenis nyeri dada
- exercise induced angina
- oldpeak
- slope
- jumlah pembuluh darah utama
- thalassemia

Dataset kemudian melalui proses preprocessing sebelum digunakan pada proses pelatihan model.

---

## Data Preprocessing

Tahapan preprocessing meliputi:

- pembersihan data (data cleaning)
- penanganan missing value
- penghapusan data duplikat
- encoding variabel kategorikal
- normalisasi atau standardisasi fitur numerik
- pembagian dataset menjadi data latih dan data uji
- validasi menggunakan Stratified K-Fold Cross Validation

Tahap ini bertujuan menghasilkan data yang siap digunakan pada proses pelatihan model.

---

## Model Machine Learning

Beberapa algoritma machine learning digunakan sebagai model klasifikasi, antara lain:

- Logistic Regression
- Decision Tree
- Random Forest
- Support Vector Machine (SVM)
- K-Nearest Neighbor (KNN)
- Naïve Bayes
- Artificial Neural Network (opsional)

Setiap model dievaluasi menggunakan konfigurasi parameter yang sama agar perbandingan berlangsung secara adil.

---

## Strategi Pencegahan Overfitting

Untuk meningkatkan kemampuan generalisasi model digunakan beberapa strategi, yaitu:

- Stratified K-Fold Cross Validation
- Hyperparameter Tuning
- Feature Selection
- Regularization
- Early Stopping (untuk model tertentu)

Seluruh strategi dibandingkan berdasarkan performa model terhadap data yang belum pernah dilihat sebelumnya.

---

## Evaluasi Model

Model dievaluasi menggunakan beberapa metrik klasifikasi, yaitu:

- Accuracy
- Precision
- Recall
- F1-Score
- ROC-AUC
- Confusion Matrix

Selain itu dilakukan analisis selisih performa antara data pelatihan dan data pengujian sebagai indikator tingkat overfitting.

---

# 2. Alur Penelitian

```text
Dataset Medis
      │
      ▼
Data Cleaning
      │
      ▼
Preprocessing
      │
      ├── Missing Value Handling
      ├── Encoding
      ├── Feature Scaling
      └── Train-Test Split
      │
      ▼
Machine Learning Model
      │
      ├── Logistic Regression
      ├── Decision Tree
      ├── Random Forest
      ├── Support Vector Machine
      ├── KNN
      └── Naïve Bayes
      │
      ▼
Cross Validation
      │
      ▼
Hyperparameter Tuning
      │
      ▼
Evaluasi Model
      │
      ├── Accuracy
      ├── Precision
      ├── Recall
      ├── F1 Score
      ├── ROC-AUC
      └── Confusion Matrix
      │
      ▼
Analisis Overfitting
      │
      ▼
Pemilihan Model Terbaik
```

---

# 3. Desain Dataset

Dataset penelitian terdiri atas data pasien dengan dua kelas.

| Komponen | Keterangan |
|----------|------------|
| Target | Penyakit Jantung |
| Label | 0 = Tidak Mengidap, 1 = Mengidap |
| Jenis Data | Tabular |
| Jumlah Fitur | Disesuaikan dengan dataset yang digunakan |
| Missing Value | Ditangani pada preprocessing |
| Ketidakseimbangan Data | Dianalisis sebelum pelatihan model |

---

# 4. Pipeline Eksperimen

Setiap algoritma dijalankan menggunakan pipeline yang sama sehingga hasil dapat dibandingkan secara objektif.

```text
Dataset
   │
   ▼
Preprocessing
   │
   ▼
Train-Test Split
   │
   ▼
Cross Validation
   │
   ▼
Training Model
   │
   ▼
Hyperparameter Tuning
   │
   ▼
Testing
   │
   ▼
Performance Evaluation
   │
   ▼
Generalization Analysis
```

---

# 5. Parameter Eksperimen

Parameter utama yang digunakan pada penelitian meliputi:

| Parameter | Nilai |
|-----------|-------|
| Train-Test Split | 80:20 |
| Cross Validation | Stratified K-Fold (k=5 atau k=10) |
| Random State | Tetap agar eksperimen dapat direplikasi |
| Feature Scaling | StandardScaler atau MinMaxScaler |
| Hyperparameter Tuning | Grid Search atau Random Search |
| Evaluation Metrics | Accuracy, Precision, Recall, F1-Score, ROC-AUC |

---

# 6. Keputusan Teknis (Final)

Keputusan teknis yang digunakan dalam penelitian adalah sebagai berikut.

- Dataset berupa dataset medis penyakit jantung dengan jumlah data terbatas.
- Penelitian berfokus pada masalah overfitting pada model machine learning.
- Seluruh algoritma dilatih menggunakan pipeline preprocessing yang sama.
- Validasi model menggunakan Stratified K-Fold Cross Validation.
- Hyperparameter tuning dilakukan menggunakan Grid Search atau Random Search.
- Seluruh model dibandingkan menggunakan metrik Accuracy, Precision, Recall, F1-Score, dan ROC-AUC.
- Analisis overfitting dilakukan dengan membandingkan performa pada data pelatihan dan data pengujian.
- Model terbaik dipilih berdasarkan kemampuan generalisasi, bukan hanya nilai akurasi tertinggi.
- Seluruh eksperimen diimplementasikan menggunakan Python dengan pustaka Scikit-learn, Pandas, NumPy, dan Matplotlib/Seaborn.
- Seluruh proses penelitian dirancang agar dapat direplikasi pada dataset medis lain dengan karakteristik serupa.
- 
