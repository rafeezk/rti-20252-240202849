# Tahap 4 — Analisis Data dan Visualisasi Hasil

**Status:** Selesai — seluruh hasil eksperimen telah dianalisis dan divisualisasikan. Seluruh tabel dan grafik tersedia pada folder `06-output/`.

**Bergantung pada:** `tahap-3-pengujian-eksperimen-model.md`

**Lokasi kode:** `../05-kode/src/visualization/`

---

# Tujuan

Mengolah hasil eksperimen machine learning menjadi statistik deskriptif, visualisasi, serta analisis performa model untuk mengevaluasi kemampuan prediksi penyakit pada dataset medis terbatas.

Tahap ini berfokus pada identifikasi model terbaik berdasarkan kemampuan generalisasi serta analisis tingkat overfitting menggunakan berbagai metrik evaluasi.

---

# Deliverable

- Ekstraksi seluruh hasil eksperimen ke dalam format tabular
- Statistik deskriptif performa setiap model
- Perbandingan hasil Cross Validation
- Analisis overfitting setiap model
- Analisis kemampuan generalisasi model
- Visualisasi Confusion Matrix
- Visualisasi ROC Curve
- Visualisasi Precision-Recall Curve
- Visualisasi Learning Curve
- Visualisasi Validation Curve
- Visualisasi Feature Importance
- Ringkasan hasil evaluasi untuk Tahap 5

---

# Desain Implementasi

## Struktur Folder

```text
05-kode/
├── src/
│   └── visualization/
│       ├── descriptive_statistics.py
│       ├── evaluation_analysis.py
│       ├── learning_curve.py
│       ├── validation_curve.py
│       ├── roc_curve.py
│       ├── confusion_matrix.py
│       ├── feature_importance.py
│       ├── comparison.py
│       └── run_all.py
```

Seluruh proses analisis dijalankan secara otomatis menggunakan `run_all.py`.

---

# Modul Analisis

| Modul | Fungsi | Output |
|--------|--------|--------|
| descriptive_statistics.py | Statistik deskriptif seluruh model | `descriptive_statistics.csv` |
| evaluation_analysis.py | Ringkasan Accuracy, Precision, Recall, F1-Score, ROC-AUC | `evaluation_results.csv` |
| learning_curve.py | Analisis overfitting | `learning_curve.png` |
| validation_curve.py | Analisis kompleksitas model | `validation_curve.png` |
| roc_curve.py | Kurva ROC | `roc_curve.png` |
| confusion_matrix.py | Confusion Matrix | `confusion_matrix.png` |
| feature_importance.py | Analisis fitur penting | `feature_importance.png` |
| comparison.py | Perbandingan performa seluruh model | `model_comparison.png` |

---

# Cara Menjalankan

Dari folder proyek:

```bash
python src/visualization/run_all.py
```

Pipeline akan secara otomatis:

1. Membaca seluruh hasil eksperimen.
2. Mengolah data evaluasi.
3. Menghasilkan statistik.
4. Membuat visualisasi.
5. Menyimpan seluruh output pada folder `06-output/`.

---

# Analisis Statistik

Statistik deskriptif dihitung untuk setiap algoritma machine learning.

Metrik yang dianalisis meliputi:

- Accuracy
- Precision
- Recall
- F1-Score
- ROC-AUC
- Cross Validation Score
- Training Accuracy
- Testing Accuracy

Setiap nilai disajikan dalam bentuk:

- Mean
- Standard Deviation
- Minimum
- Maximum

---

# Analisis Overfitting

Tingkat overfitting dievaluasi menggunakan beberapa indikator, yaitu:

- Perbandingan Training Accuracy dan Testing Accuracy
- Cross Validation Score
- Learning Curve
- Validation Curve

Model dianggap mengalami overfitting apabila memiliki akurasi tinggi pada data pelatihan tetapi mengalami penurunan performa yang signifikan pada data pengujian.

---

# Analisis Generalisasi

Kemampuan generalisasi model dievaluasi berdasarkan:

- Stabilitas hasil Cross Validation
- Konsistensi Accuracy pada data testing
- Nilai Precision, Recall, dan F1-Score
- Nilai ROC-AUC
- Learning Curve

Model terbaik dipilih berdasarkan keseimbangan antara akurasi tinggi dan kemampuan generalisasi yang baik terhadap data baru.

---

# Visualisasi

Tahap ini menghasilkan beberapa visualisasi utama.

## 1. Perbandingan Performa Model

Grafik batang yang membandingkan:

- Accuracy
- Precision
- Recall
- F1-Score
- ROC-AUC

untuk seluruh algoritma machine learning.

---

## 2. Confusion Matrix

Menampilkan jumlah prediksi:

- True Positive
- True Negative
- False Positive
- False Negative

untuk masing-masing model.

---

## 3. ROC Curve

ROC Curve digunakan untuk mengevaluasi kemampuan model dalam membedakan kelas positif dan negatif.

Nilai Area Under Curve (ROC-AUC) digunakan sebagai indikator performa klasifikasi.

---

## 4. Precision-Recall Curve

Kurva ini digunakan untuk mengevaluasi keseimbangan antara Precision dan Recall, terutama pada dataset dengan distribusi kelas yang tidak seimbang.

---

## 5. Learning Curve

Learning Curve digunakan untuk mengidentifikasi apakah model mengalami:

- Overfitting
- Underfitting
- Generalisasi yang baik

berdasarkan perubahan performa terhadap jumlah data pelatihan.

---

## 6. Validation Curve

Validation Curve menunjukkan pengaruh perubahan hyperparameter terhadap performa model.

Visualisasi ini membantu menentukan parameter optimal yang menghasilkan kemampuan generalisasi terbaik.

---

## 7. Feature Importance

Untuk model yang mendukung interpretasi fitur, dilakukan analisis tingkat kepentingan setiap fitur medis dalam proses prediksi penyakit.

Visualisasi ini memberikan gambaran fitur-fitur yang paling berkontribusi terhadap keputusan model.

---

# Output

Seluruh hasil analisis disimpan pada folder `06-output/`.

```text
06-output/
├── tables/
│   ├── descriptive_statistics.csv
│   ├── evaluation_results.csv
│   ├── cross_validation_results.csv
│   ├── classification_report.csv
│   ├── model_comparison.csv
│   └── feature_importance.csv
│
└── figures/
    ├── model_comparison.png
    ├── confusion_matrix.png
    ├── roc_curve.png
    ├── precision_recall_curve.png
    ├── learning_curve.png
    ├── validation_curve.png
    └── feature_importance.png
```

---

# Hasil

Tahap analisis berhasil menghasilkan:

- Statistik deskriptif seluruh model machine learning.
- Perbandingan performa antar model.
- Evaluasi tingkat overfitting.
- Analisis kemampuan generalisasi model.
- Visualisasi lengkap untuk interpretasi hasil penelitian.
- Dataset hasil analisis yang siap digunakan pada Tahap 5 sebagai dasar penyusunan naskah ilmiah.

---

# Catatan untuk Tahap 5

Seluruh tabel dan visualisasi yang dihasilkan pada tahap ini menjadi dasar penyusunan bagian **Hasil dan Pembahasan** pada naskah ilmiah.

Fokus pembahasan meliputi:

- Perbandingan performa setiap algoritma.
- Dampak dataset medis yang terbatas terhadap overfitting.
- Analisis kemampuan generalisasi model.
- Identifikasi model terbaik berdasarkan keseimbangan antara akurasi dan generalisasi.
- Implikasi hasil penelitian terhadap pengembangan sistem prediksi penyakit berbasis machine learning pada dataset medis terbatas.

Seluruh analisis telah diverifikasi dan siap digunakan sebagai dasar penyusunan manuskrip penelitian pada Tahap 5.
