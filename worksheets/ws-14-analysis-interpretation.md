# WS-14: Analysis, Interpretation & Failure Analysis

> **Bab 14 — Analisis Data, Interpretasi & Failure Analysis**

---

# Ringkasan Materi

## Data → Knowledge Model

```
Dataset
      ↓
Data Analysis
      ↓
Interpretation
      ↓
Failure Analysis
      ↓
Research Knowledge
```

Pada penelitian machine learning, analisis data bertujuan tidak hanya untuk mengetahui model dengan performa terbaik, tetapi juga memahami penyebab keberhasilan maupun kegagalan model. Interpretasi hasil harus selalu dikaitkan dengan tujuan penelitian, sedangkan *failure analysis* membantu menjelaskan kondisi ketika model mengalami overfitting atau gagal melakukan generalisasi terhadap data baru.

---

# Tiga Level Analisis

## Analysis

Menjawab pertanyaan:

> **"Apa yang terjadi?"**

Meliputi:

- Statistik deskriptif
- Evaluasi performa model
- Perbandingan antar algoritma
- Pengujian hipotesis
- Evaluasi metrik klasifikasi

---

## Interpretation

Menjawab pertanyaan:

> **"Apa arti hasil tersebut?"**

Interpretasi harus dikaitkan dengan:

- Research Question
- Hipotesis penelitian
- Literatur terdahulu
- Implikasi terhadap overfitting
- Implikasi terhadap kemampuan generalisasi model

---

## Failure Analysis

Menjawab pertanyaan:

> **"Mengapa model tidak memberikan hasil seperti yang diharapkan?"**

Failure analysis bertujuan menemukan batas kemampuan model sehingga dapat menjadi kontribusi ilmiah bagi penelitian selanjutnya.

---

# Beyond p-value

Keberhasilan penelitian tidak cukup hanya ditunjukkan oleh nilai **p-value**.

Setiap penelitian sebaiknya melaporkan:

- p-value
- Effect Size
- Confidence Interval (CI)

## Interpretasi Cohen's d

| Cohen's d | Interpretasi |
|------------|-------------|
| < 0.20 | Small Effect |
| 0.20 – 0.80 | Medium Effect |
| > 0.80 | Large Effect |

---

# Pemilihan Uji Statistik

| Kondisi | Uji Statistik |
|----------|---------------|
| Dua model, data normal | Paired t-test |
| Dua model, data tidak normal | Wilcoxon Signed Rank Test |
| Lebih dari dua model, data normal | One-Way ANOVA |
| Lebih dari dua model, data tidak normal | Kruskal-Wallis Test |
| Hubungan dua variabel numerik | Pearson Correlation / Spearman Correlation |

---

# Failure Analysis sebagai Kontribusi Penelitian

Hipotesis yang tidak didukung bukan berarti penelitian gagal.

Contoh hasil eksperimen:

| Model | Accuracy (%) | F1-Score (%) | p-value | Cohen's d |
|--------|--------------|--------------|----------|-----------|
| Logistic Regression | 85.62 ± 2.18 | 84.93 ± 2.41 | 0.031 | 0.64 |
| Support Vector Machine | 88.14 ± 1.73 | 87.65 ± 1.80 | 0.018 | 0.81 |
| Random Forest | **91.27 ± 1.21** | **90.84 ± 1.35** | <0.001 | 1.12 |
| Neural Network | 90.84 ± 3.86 | 89.95 ± 4.12 | 0.184 | 0.18 |

## Insight

Neural Network memperoleh rata-rata akurasi yang tinggi, namun memiliki standar deviasi terbesar dibandingkan model lainnya. Hal tersebut menunjukkan bahwa model mengalami overfitting pada beberapa fold cross validation sehingga kemampuan generalisasinya kurang stabil.

Sebaliknya, Random Forest memberikan performa yang lebih konsisten dengan variabilitas yang rendah sehingga lebih sesuai digunakan pada dataset medis yang jumlah datanya terbatas.

---

# Jenis Keterbatasan Penelitian

| Jenis | Contoh |
|--------|--------|
| Internal Validity | Hyperparameter belum dioptimasi secara menyeluruh |
| External Validity | Dataset hanya berasal dari satu institusi kesehatan |
| Construct Validity | Accuracy belum sepenuhnya merepresentasikan kualitas diagnosis |
| Statistical Limitation | Jumlah data relatif kecil |

---

# Jebakan Kognitif

Beberapa kesalahan yang sering terjadi dalam analisis hasil penelitian:

- Menganggap p-value kecil berarti model terbaik.
- Mengabaikan effect size.
- Tidak melaporkan hasil yang tidak sesuai hipotesis.
- Menganggap overfitting bukan bagian dari hasil penelitian.
- Tidak melakukan failure analysis.
- Menarik kesimpulan tanpa menghubungkan hasil dengan literatur.

---

# Template A.14 — Analysis & Interpretation Report

## ANALYSIS & INTERPRETATION REPORT

### 1. Statistik Deskriptif

| Model | Accuracy (Mean ± Std) | F1-Score (Mean ± Std) | Precision | Recall | n |
|--------|----------------------|-----------------------|-----------|--------|---|
| Logistic Regression | 85.62 ± 2.18 | 84.93 ± 2.41 | 85.11% | 84.76% | 10 |
| Support Vector Machine | 88.14 ± 1.73 | 87.65 ± 1.80 | 88.03% | 87.52% | 10 |
| Random Forest | **91.27 ± 1.21** | **90.84 ± 1.35** | **91.12%** | **90.76%** | 10 |
| Neural Network | 90.84 ± 3.86 | 89.95 ± 4.12 | 90.31% | 89.77% | 10 |

---

### 2. Uji Hipotesis

**Uji Statistik**

One-Way ANOVA

**Justifikasi**

Penelitian membandingkan empat algoritma machine learning pada dataset yang sama. Uji normalitas menunjukkan data berdistribusi normal sehingga One-Way ANOVA dipilih sebagai metode pengujian.

**Hasil**

- p-value = 0.012
- Effect Size (η²) = 0.42
- Confidence Interval (95%) = [0.71 ; 3.85]

---

### 3. Keputusan

☑ H₀ ditolak

☑ H₁ diterima

Terdapat perbedaan performa yang signifikan antara algoritma machine learning yang digunakan.

---

### 4. Interpretasi

#### Hubungan terhadap Research Question

Penelitian menunjukkan bahwa pemilihan algoritma machine learning memengaruhi kemampuan model dalam melakukan prediksi penyakit pada dataset medis yang berukuran terbatas.

#### Practical Significance

Random Forest memberikan performa terbaik dengan nilai accuracy dan F1-score tertinggi serta standar deviasi yang paling kecil. Hal tersebut menunjukkan bahwa model memiliki kemampuan generalisasi yang lebih baik dibandingkan algoritma lainnya.

#### Perbandingan dengan Literatur

Hasil penelitian ini konsisten dengan penelitian sebelumnya yang menunjukkan bahwa algoritma ensemble seperti Random Forest memiliki kemampuan mengurangi overfitting pada dataset kecil karena memanfaatkan proses bootstrap aggregation dan voting antar pohon keputusan.

---

### 5. Limitation

| Jenis | Ancaman | Dampak | Mitigasi |
|--------|----------|---------|----------|
| Internal Validity | Hyperparameter belum dioptimasi secara menyeluruh | Performa model mungkin belum optimal | Grid Search dan Random Search |
| External Validity | Dataset hanya berasal dari satu rumah sakit | Generalisasi terbatas | Menggunakan dataset multi-institusi pada penelitian berikutnya |
| Construct Validity | Evaluasi hanya menggunakan metrik klasifikasi | Belum mempertimbangkan interpretabilitas model | Menambahkan Explainable AI (SHAP/LIME) |
| Statistical Limitation | Dataset hanya terdiri dari ±300 sampel | Power statistik relatif rendah | Menambah jumlah sampel dan validasi eksternal |

---

### 6. Failure Analysis

#### Penyebab Potensial

Neural Network memiliki jumlah parameter yang lebih besar dibandingkan algoritma lainnya sehingga membutuhkan jumlah data latih yang lebih banyak. Pada dataset medis yang terbatas, model cenderung menghafal data pelatihan sehingga mengalami overfitting.

#### Boundary Condition

Neural Network akan memberikan performa yang lebih baik apabila jumlah data latih besar dan distribusi data lebih beragam. Sebaliknya, pada dataset kecil Random Forest lebih stabil karena memiliki mekanisme ensemble yang mampu mengurangi varians model.

#### Insight

Hasil penelitian menunjukkan bahwa model yang lebih kompleks tidak selalu menghasilkan performa terbaik. Pada kondisi dataset medis terbatas, algoritma dengan kompleksitas sedang seperti Random Forest mampu menghasilkan keseimbangan terbaik antara akurasi dan kemampuan generalisasi.

---

# Latihan 1 — Pemilihan Uji Statistik

| Pertanyaan | Jawaban |
|------------|----------|
| Berapa model yang dibandingkan? | Empat model (Logistic Regression, Support Vector Machine, Random Forest, Neural Network) |
| Apakah data berpasangan? | Ya. Seluruh model menggunakan dataset yang sama dengan skema Stratified K-Fold Cross Validation. |
| Apakah distribusi normal? | Ya. Berdasarkan uji Shapiro-Wilk data memenuhi asumsi normalitas. |
| Uji yang dipilih | One-Way ANOVA |
| Justifikasi | Digunakan untuk membandingkan rata-rata performa lebih dari dua model yang berdistribusi normal. |

**Effect Size yang dilaporkan**

- [ ] Cohen's d
- [x] Eta Squared (η²)
- [ ] Cliff's Delta

---

# Latihan 2 — Interpretasi Hasil

## Data

| Model | Accuracy (Mean ± Std) | n |
|--------|----------------------|---|
| Random Forest | 91.27 ± 1.21 | 10 |
| Support Vector Machine | 88.14 ± 1.73 | 10 |

Hasil pengujian:

- p = 0.018
- Cohen's d = 0.81
- CI95% = [0.52 ; 3.41]

## Interpretasi

| Aspek | Interpretasi |
|--------|--------------|
| Signifikansi Statistik | Nilai p < 0.05 menunjukkan adanya perbedaan performa yang signifikan. |
| Effect Size | Cohen's d = 0.81 menunjukkan efek yang besar. |
| Practical Significance | Random Forest memberikan peningkatan performa yang bermakna dengan kemampuan generalisasi yang lebih baik. |
| Hubungan terhadap Research Question | Hasil mendukung hipotesis bahwa algoritma ensemble lebih mampu mengurangi overfitting pada dataset medis terbatas. |
| Perbandingan Literatur | Konsisten dengan penelitian sebelumnya mengenai efektivitas Random Forest pada dataset berukuran kecil. |

---

# Latihan 3 — Failure Analysis

Misalkan diperoleh hasil sebagai berikut.

| Model | F1-Score |
|--------|----------|
| Neural Network | 89.95% |
| Random Forest | 90.84% |

Hasil uji statistik:

- p = 0.184
- Tidak signifikan.

## Analisis

| Pertanyaan | Jawaban |
|------------|----------|
| Apakah penelitian gagal? | Tidak. Hipotesis yang tidak didukung tetap merupakan temuan ilmiah yang valid. |
| Kemungkinan penyebab | Dataset medis relatif kecil sehingga Neural Network mengalami overfitting dan tidak mampu melakukan generalisasi secara optimal. |
| Boundary Condition | Neural Network lebih sesuai digunakan pada dataset yang jauh lebih besar. |
| Insight | Random Forest lebih stabil untuk dataset medis terbatas karena memiliki varians yang lebih rendah. |
| Apakah layak dilaporkan? | Ya. Failure analysis memberikan informasi mengenai batas kemampuan masing-masing algoritma dan menjadi kontribusi penting bagi penelitian selanjutnya. |

---

# Refleksi

Apakah hasil yang tidak sesuai hipotesis berarti penelitian gagal?

Tidak. Dalam penelitian machine learning, hasil yang tidak mendukung hipotesis tetap memiliki nilai ilmiah. Failure analysis membantu menjelaskan penyebab overfitting, keterbatasan generalisasi model, serta kondisi ketika suatu algoritma tidak memberikan performa terbaik. Temuan tersebut dapat menjadi dasar pengembangan metode yang lebih efektif pada penelitian selanjutnya dan mencegah pengulangan penelitian dengan pendekatan yang sama tanpa mempertimbangkan batas kemampuan model.
