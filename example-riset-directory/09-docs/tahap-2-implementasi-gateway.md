# Tahap 2 — Implementasi Model Machine Learning

**Status:** Selesai

**Acuan arsitektur:** `tahap-1-perancangan-arsitektur-penelitian.md`

**Lokasi implementasi:** `../05-kode/`

---

# Tujuan

Mengimplementasikan pipeline machine learning untuk melakukan prediksi penyakit jantung pada dataset medis terbatas dengan fokus pada analisis overfitting dan kemampuan generalisasi model.

Seluruh implementasi dibangun secara modular sehingga proses preprocessing, pelatihan model, evaluasi, dan visualisasi dapat direproduksi secara konsisten.

---

# Deliverable

- Struktur proyek machine learning yang terorganisasi (`src/`, `notebooks/`, `models/`, `configs/`)
- Pipeline preprocessing dataset medis
- Implementasi feature engineering
- Implementasi normalisasi dan transformasi data
- Pembagian dataset menggunakan Stratified Train-Test Split
- Implementasi beberapa algoritma machine learning sebagai model pembanding
- Hyperparameter tuning menggunakan Grid Search
- Cross Validation (k-Fold)
- Pipeline evaluasi model
- Penyimpanan model terbaik
- Script visualisasi hasil eksperimen
- Konfigurasi environment (`requirements.txt`)
- Notebook eksperimen
- Dokumentasi reproduksibilitas eksperimen (`README.md`)

---

# Struktur Implementasi

```text
05-kode/
├── src/
│   ├── preprocessing/
│   ├── feature_engineering/
│   ├── models/
│   ├── training/
│   ├── evaluation/
│   ├── visualization/
│   └── utils/
│
├── notebooks/
│   ├── exploratory_data_analysis.ipynb
│   ├── preprocessing.ipynb
│   ├── model_training.ipynb
│   └── evaluation.ipynb
│
├── datasets/
├── models/
├── configs/
├── requirements.txt
└── README.md
```

---

# Implementasi Pipeline

Pipeline penelitian terdiri atas beberapa tahapan utama.

## 1. Data Loading

Dataset medis dimuat dari folder `datasets/` menggunakan library Pandas.

Tahap ini meliputi:

- membaca dataset
- validasi struktur data
- pemeriksaan tipe data
- pemeriksaan missing value
- identifikasi distribusi kelas

---

## 2. Data Preprocessing

Tahap preprocessing bertujuan meningkatkan kualitas data sebelum proses pelatihan model.

Proses yang dilakukan meliputi:

- penanganan missing value
- penghapusan data duplikat
- encoding variabel kategorikal
- normalisasi fitur numerik
- standarisasi data
- pemisahan fitur dan label

---

## 3. Feature Engineering

Feature engineering dilakukan untuk meningkatkan kemampuan model dalam mempelajari pola dari dataset medis.

Tahapan meliputi:

- seleksi fitur
- transformasi fitur
- analisis korelasi
- reduksi fitur apabila diperlukan

---

## 4. Pembagian Dataset

Dataset dibagi menggunakan Stratified Train-Test Split agar distribusi kelas tetap seimbang.

Konfigurasi eksperimen:

- Training Data : 80%
- Testing Data : 20%

Seluruh eksperimen menggunakan nilai `random_state` yang sama agar hasil dapat direproduksi.

---

## 5. Pelatihan Model

Beberapa algoritma machine learning digunakan sebagai pembanding performa.

Model yang diimplementasikan meliputi:

- Logistic Regression
- Decision Tree
- Random Forest
- Support Vector Machine (SVM)
- K-Nearest Neighbor (KNN)
- Naïve Bayes

Setiap model dilatih menggunakan dataset training yang sama.

---

## 6. Hyperparameter Tuning

Optimasi parameter dilakukan menggunakan Grid Search.

Parameter terbaik dipilih berdasarkan nilai Cross Validation tertinggi.

Tahapan ini bertujuan mengurangi risiko overfitting dan meningkatkan kemampuan generalisasi model.

---

## 7. Cross Validation

Evaluasi model menggunakan k-Fold Cross Validation.

Konfigurasi eksperimen:

- 5-Fold Cross Validation

Nilai rata-rata akurasi digunakan sebagai indikator performa model selama proses pelatihan.

---

## 8. Evaluasi Model

Model dievaluasi menggunakan dataset testing yang tidak pernah digunakan selama proses pelatihan.

Metrik evaluasi meliputi:

- Accuracy
- Precision
- Recall
- F1-Score
- ROC-AUC
- Confusion Matrix

---

## 9. Analisis Overfitting

Untuk mengukur tingkat overfitting dilakukan perbandingan antara performa training dan testing.

Analisis meliputi:

- Training Accuracy
- Testing Accuracy
- Cross Validation Accuracy
- Learning Curve
- Validation Curve

Selisih performa digunakan sebagai indikator tingkat overfitting model.

---

## 10. Analisis Generalisasi

Kemampuan generalisasi model dianalisis berdasarkan:

- hasil Cross Validation
- performa pada data testing
- stabilitas performa antar fold
- konsistensi berbagai metrik evaluasi

Model dengan performa paling stabil dipilih sebagai model terbaik.

---

## 11. Penyimpanan Model

Model terbaik disimpan pada folder:

```text
models/
```

Model disimpan menggunakan format:

- joblib
- pickle

agar dapat digunakan kembali tanpa proses pelatihan ulang.

---

## 12. Visualisasi

Visualisasi hasil eksperimen meliputi:

- Confusion Matrix
- ROC Curve
- Precision-Recall Curve
- Feature Importance
- Learning Curve
- Validation Curve
- Perbandingan performa antar model

Seluruh grafik digunakan sebagai dasar analisis pada Tahap 4.

---

# Hasil Verifikasi Implementasi

Seluruh pipeline telah diverifikasi melalui beberapa tahap pengujian.

Pipeline berhasil:

- memuat dataset tanpa kesalahan
- melakukan preprocessing secara konsisten
- membagi dataset menggunakan Stratified Split
- melatih seluruh model machine learning
- menjalankan proses hyperparameter tuning
- melakukan Cross Validation
- menghasilkan metrik evaluasi lengkap
- menyimpan model terbaik
- menghasilkan visualisasi evaluasi
- menghasilkan dataset hasil eksperimen yang siap dianalisis pada Tahap 4

---

# Catatan Lingkungan

Implementasi penelitian menggunakan lingkungan Python dengan pustaka machine learning standar.

Library utama yang digunakan meliputi:

- Python
- Pandas
- NumPy
- Scikit-learn
- Matplotlib
- Seaborn
- Joblib

Seluruh dependensi penelitian dicantumkan pada file `requirements.txt` sehingga eksperimen dapat direproduksi pada lingkungan lain.

Notebook Jupyter digunakan untuk eksplorasi data dan dokumentasi eksperimen, sedangkan implementasi utama berada pada folder `src/` agar struktur proyek tetap modular dan mudah dipelihara.
