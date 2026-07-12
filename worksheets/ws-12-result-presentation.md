# WS-12: Result Presentation & Visualization

> **Bab 12 — Penyajian Hasil & Visualisasi**

---

# Ringkasan Materi

## Data → Insight Model

```
Validated Data
        ↓
Structured Presentation
        ↓
Visualization
        ↓
Pattern Recognition
        ↓
Research Insight
```

Data yang telah divalidasi harus disajikan secara sistematis sebelum dilakukan interpretasi. Penyajian dalam bentuk tabel dan grafik membantu peneliti memahami pola performa model machine learning pada dataset medis sehingga kesimpulan yang diperoleh menjadi lebih objektif.

---

# Tabel = Presisi, Grafik = Pola

Keduanya saling melengkapi.

**Tabel**

- Menampilkan angka secara presisi.
- Mudah dibandingkan antar model.
- Memuat nilai mean ± standar deviasi.
- Bersifat self-contained.

**Grafik**

- Memperlihatkan pola.
- Mempermudah melihat tren.
- Mempermudah membandingkan performa model.
- Membantu mendeteksi overfitting maupun generalisasi.

---

# Jenis Grafik Berdasarkan Tujuan

| Tujuan | Jenis Grafik |
|---------|--------------|
| Perbandingan performa model | Bar Chart |
| Distribusi hasil Cross Validation | Box Plot |
| Learning Process | Learning Curve |
| Pengaruh Hyperparameter | Validation Curve |
| ROC setiap model | ROC Curve |
| Feature Importance | Horizontal Bar Chart |
| Korelasi dua metrik | Scatter Plot |

---

# Contoh Tabel Hasil

| Model | Accuracy (%) | F1-Score (%) | ROC-AUC | Training Time (detik) |
|---------|-------------|--------------|----------|-----------------------|
| Random Forest | **92.30 ± 0.91** | **91.82 ± 0.88** | **0.962 ± 0.011** | 1.84 ± 0.10 |
| SVM | 90.74 ± 1.21 | 90.11 ± 1.09 | 0.951 ± 0.014 | 2.76 ± 0.14 |
| Logistic Regression | 88.62 ± 1.33 | 87.90 ± 1.21 | 0.932 ± 0.016 | **0.18 ± 0.01** |
| Decision Tree | 86.74 ± 2.05 | 85.91 ± 1.97 | 0.904 ± 0.020 | 0.42 ± 0.03 |
| KNN | 85.63 ± 1.87 | 84.95 ± 1.76 | 0.893 ± 0.018 | 0.31 ± 0.02 |

**n = 5-fold Cross Validation**

---

# Visualization Bias

| Bias | Deskripsi | Dampak |
|------|-----------|---------|
| Truncated Axis | Sumbu Y tidak dimulai dari nol | Perbedaan kecil terlihat sangat besar |
| Inconsistent Scale | Skala grafik berbeda | Sulit dibandingkan |
| Cherry Picking | Hanya menampilkan model terbaik | Kesimpulan bias |
| 3D Chart | Efek visual tanpa makna | Sulit dibaca |
| Missing Error Bar | Tidak menunjukkan variasi data | Menyembunyikan ketidakpastian |

---

# Engineering vs Research Presentation

| Aspek | Engineering | Research |
|---------|------------|----------|
| Tujuan | Monitoring sistem | Mendukung argumen ilmiah |
| Informasi | Nilai tunggal | Mean ± SD, CI, N |
| Visualisasi | Dashboard | Grafik ilmiah |
| Error Bar | Tidak wajib | Wajib |
| Interpretasi | Cepat | Objektif |

---

# Template A.12 — Result Presentation Plan

```
RESULT PRESENTATION PLAN

Research Question :
Bagaimana pengaruh teknik pencegahan overfitting terhadap kemampuan generalisasi model machine learning pada dataset medis terbatas?

Metrik Utama :
Accuracy, F1-Score, ROC-AUC

Tabel Hasil

| Model | Accuracy (Mean ± SD) | F1 (Mean ± SD) | ROC-AUC | n |
|-------|----------------------|---------------|---------|---|
| Random Forest | 92.30 ± 0.91 | 91.82 ± 0.88 | 0.962 | 5 |
| SVM | 90.74 ± 1.21 | 90.11 ± 1.09 | 0.951 | 5 |
| Logistic Regression | 88.62 ± 1.33 | 87.90 ± 1.21 | 0.932 | 5 |
| Decision Tree | 86.74 ± 2.05 | 85.91 ± 1.97 | 0.904 | 5 |
| KNN | 85.63 ± 1.87 | 84.95 ± 1.76 | 0.893 | 5 |

Visualisasi yang Direncanakan

| # | Jenis Grafik | Pesan Utama | Metrik |
|---|--------------|-------------|--------|
| 1 | Bar Chart + Error Bar | Membandingkan Accuracy seluruh model | Accuracy |
| 2 | Learning Curve | Mendeteksi overfitting | Training vs Validation Accuracy |
| 3 | ROC Curve | Membandingkan kemampuan klasifikasi | ROC-AUC |

Bias Check

[x] Y-axis dimulai dari 0
[x] Error bar ditampilkan
[x] Seluruh model ditampilkan
[x] Tidak menggunakan grafik 3D
```

---

# Latihan 1 — Tabel Hasil

| Model | Accuracy (Mean ± SD) | F1-Score (Mean ± SD) | ROC-AUC | n |
|--------|----------------------|----------------------|----------|---|
| Random Forest | **92.30 ± 0.91** | **91.82 ± 0.88** | **0.962** | 5 |
| SVM | 90.74 ± 1.21 | 90.11 ± 1.09 | 0.951 | 5 |
| Logistic Regression | 88.62 ± 1.33 | 87.90 ± 1.21 | 0.932 | 5 |
| Decision Tree | 86.74 ± 2.05 | 85.91 ± 1.97 | 0.904 | 5 |
| KNN | 85.63 ± 1.87 | 84.95 ± 1.76 | 0.893 | 5 |

### Checklist

- [x] Judul tabel jelas.
- [x] Memiliki satuan (%).
- [x] Mean ± standar deviasi.
- [x] Diurutkan berdasarkan Accuracy.
- [x] Konsisten.

---

# Latihan 2 — Rencana Visualisasi

| No | Jenis Grafik | Pesan | Data |
|----|--------------|--------|------|
| 1 | Bar Chart + Error Bar | Membandingkan performa Accuracy seluruh model | Mean Accuracy ± SD |
| 2 | Learning Curve | Menunjukkan tingkat overfitting dan generalisasi | Training Accuracy & Validation Accuracy |
| 3 | ROC Curve | Membandingkan kemampuan klasifikasi setiap model | ROC-AUC setiap model |

---

# Latihan 3 — Bias Detection

**Skenario**

Random Forest memperoleh Accuracy **92.3%**, sedangkan SVM memperoleh **90.7%**. Grafik batang dibuat dengan sumbu Y dimulai dari **90%**.

| Pertanyaan | Jawaban |
|------------|----------|
| Apakah Y-axis menyesatkan? | Ya. Selisih 1.6% terlihat jauh lebih besar dari kondisi sebenarnya. |
| Apakah Error Bar ditampilkan? | Ya. Error bar menunjukkan variasi hasil Cross Validation. |
| Apakah seluruh model ditampilkan? | Ya. Semua model dibandingkan secara adil. |
| Apa solusinya? | Gunakan sumbu Y dimulai dari 0 atau berikan justifikasi apabila menggunakan skala terpotong. |

### Evaluasi Grafik

- [x] Tidak menggunakan truncated axis.
- [x] Error bar tersedia.
- [x] Semua model ditampilkan.
- [x] Tidak menggunakan efek 3D.
- [x] Visualisasi dapat dibandingkan secara objektif.

---

# Refleksi

**Mengapa tabel dan grafik sama-sama diperlukan?**

Tabel memberikan informasi numerik yang presisi sehingga pembaca dapat mengetahui nilai akurasi, F1-Score, maupun ROC-AUC secara tepat. Grafik melengkapi tabel dengan menampilkan pola, tren, serta perbandingan performa antar model secara visual sehingga lebih mudah dipahami. Penggunaan keduanya secara bersamaan membuat hasil penelitian menjadi lebih informatif, objektif, dan mudah diinterpretasikan.

**Pernahkah membuat grafik yang menyesatkan?**

Pada awal analisis, grafik batang menggunakan skala sumbu Y yang tidak dimulai dari nol sehingga perbedaan performa antar model tampak jauh lebih besar. Setelah dilakukan evaluasi, grafik diperbaiki dengan menggunakan skala yang konsisten dan menambahkan error bar agar variasi hasil Cross Validation dapat terlihat dengan jelas.
