# Tahap 3 — Pengujian dan Eksperimen Model Machine Learning

**Status:** Selesai — seluruh eksperimen telah dijalankan dan menghasilkan dataset evaluasi yang digunakan pada Tahap 4.

**Bergantung pada:** `tahap-2-implementasi-model-machine-learning.md`

**Lokasi kode:** `../05-kode/`

---

# Tujuan

Melaksanakan serangkaian eksperimen untuk mengevaluasi performa model machine learning dalam memprediksi penyakit jantung pada dataset medis terbatas.

Pengujian difokuskan pada analisis kemampuan generalisasi model, tingkat overfitting, serta perbandingan performa beberapa algoritma machine learning menggunakan skenario evaluasi yang konsisten.

---

# Deliverable

- Pipeline evaluasi otomatis seluruh model
- Pembagian dataset menggunakan Stratified Train-Test Split
- Implementasi 5-Fold Cross Validation
- Hyperparameter tuning menggunakan Grid Search
- Evaluasi menggunakan berbagai metrik klasifikasi
- Learning Curve untuk analisis overfitting
- Validation Curve untuk analisis kompleksitas model
- Confusion Matrix setiap model
- ROC Curve dan Precision-Recall Curve
- Penyimpanan seluruh hasil eksperimen dalam format CSV
- Penyimpanan model terbaik
- Dokumentasi reproduksibilitas eksperimen

---

# Desain Eksperimen

## Struktur Folder

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
├── outputs/
├── configs/
├── requirements.txt
└── README.md
```

---

# Skenario Pengujian

Seluruh algoritma diuji menggunakan dataset yang sama agar hasil evaluasi dapat dibandingkan secara adil.

Model yang digunakan meliputi:

- Logistic Regression
- Decision Tree
- Random Forest
- Support Vector Machine (SVM)
- K-Nearest Neighbor (KNN)
- Naïve Bayes

Setiap model menjalankan proses:

- preprocessing
- training
- hyperparameter tuning
- cross validation
- testing
- evaluasi performa

---

# Konfigurasi Eksperimen

| Parameter | Nilai |
|-----------|-------|
| Train-Test Split | 80% : 20% |
| Cross Validation | Stratified 5-Fold |
| Random State | Tetap |
| Hyperparameter Search | Grid Search |
| Evaluation Metrics | Accuracy, Precision, Recall, F1-Score, ROC-AUC |

---

# Proses Eksperimen

Untuk setiap algoritma machine learning dilakukan tahapan berikut.

1. Memuat dataset medis.
2. Melakukan preprocessing data.
3. Melakukan feature engineering.
4. Membagi dataset menggunakan Stratified Split.
5. Melatih model.
6. Melakukan hyperparameter tuning.
7. Melakukan Cross Validation.
8. Mengevaluasi model menggunakan data testing.
9. Menyimpan hasil evaluasi.
10. Menyimpan model terbaik.
11. Menghasilkan visualisasi evaluasi.

Seluruh proses dijalankan secara otomatis sehingga setiap model menggunakan prosedur eksperimen yang identik.

---

# Output Eksperimen

Setiap eksperimen menghasilkan beberapa berkas yang disimpan pada folder `04-data/`.

```text
04-data/
├── experiment_results.csv
├── cross_validation_results.csv
├── hyperparameter_results.csv
├── confusion_matrix.csv
├── roc_auc_scores.csv
├── learning_curve.csv
├── validation_curve.csv
├── classification_report.csv
└── metadata.json
```

---

# Deskripsi Output

| File | Isi |
|------|-----|
| experiment_results.csv | Ringkasan hasil evaluasi seluruh model |
| cross_validation_results.csv | Nilai Cross Validation setiap fold |
| hyperparameter_results.csv | Parameter terbaik hasil Grid Search |
| confusion_matrix.csv | Hasil Confusion Matrix |
| roc_auc_scores.csv | Nilai ROC-AUC setiap model |
| learning_curve.csv | Data Learning Curve |
| validation_curve.csv | Data Validation Curve |
| classification_report.csv | Precision, Recall, F1-Score tiap kelas |
| metadata.json | Konfigurasi eksperimen dan informasi reproduksibilitas |

---

# Metrik Evaluasi

Setiap model dievaluasi menggunakan metrik berikut.

- Accuracy
- Precision
- Recall
- F1-Score
- ROC-AUC Score
- Confusion Matrix
- Cross Validation Accuracy
- Training Accuracy
- Testing Accuracy

---

# Analisis Overfitting

Analisis overfitting dilakukan dengan membandingkan performa model pada data pelatihan dan data pengujian.

Parameter yang dianalisis meliputi:

- Training Accuracy
- Testing Accuracy
- Cross Validation Score
- Learning Curve
- Validation Curve

Model dikatakan mengalami overfitting apabila memiliki performa sangat tinggi pada data pelatihan tetapi menurun secara signifikan pada data pengujian.

---

# Analisis Generalisasi

Kemampuan generalisasi model dievaluasi berdasarkan:

- kestabilan hasil Cross Validation
- performa pada data testing
- selisih antara training dan testing accuracy
- konsistensi berbagai metrik evaluasi

Model terbaik dipilih berdasarkan keseimbangan antara akurasi tinggi dan kemampuan generalisasi yang baik.

---

# Hasil Pengujian

Seluruh algoritma berhasil dijalankan tanpa kesalahan.

Pipeline eksperimen berhasil:

- memuat dataset medis
- melakukan preprocessing data
- melakukan feature engineering
- melatih seluruh model
- melakukan hyperparameter tuning
- menjalankan Cross Validation
- mengevaluasi seluruh model
- menyimpan hasil evaluasi
- menghasilkan visualisasi analisis
- menyimpan model terbaik

Seluruh hasil eksperimen kemudian digunakan sebagai input pada Tahap 4 untuk proses analisis statistik dan visualisasi hasil penelitian.

---

# Catatan Lingkungan

Eksperimen dijalankan menggunakan lingkungan Python dengan pustaka machine learning berikut.

- Python
- Pandas
- NumPy
- Scikit-learn
- Matplotlib
- Seaborn
- Joblib
- Jupyter Notebook

Seluruh konfigurasi eksperimen dicantumkan pada file `requirements.txt` sehingga penelitian dapat direproduksi pada lingkungan lain dengan konfigurasi yang sama.
