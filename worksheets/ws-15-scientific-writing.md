# WS-15: Scientific Writing

> **Bab 15 — Penulisan Ilmiah**

---

# Ringkasan Materi

## Scientific Argument Flow

```
Medical Problem
        ↓
Research Gap
        ↓
Research Question
        ↓
Method
        ↓
Results
        ↓
Discussion
        ↓
Conclusion
        ↓
Research Contribution
```

Penulisan ilmiah merupakan proses menyusun argumen penelitian secara sistematis mulai dari identifikasi masalah hingga kontribusi yang dihasilkan. Pada penelitian ini, argumen difokuskan pada bagaimana mengurangi **overfitting** dan meningkatkan **kemampuan generalisasi model machine learning** untuk prediksi penyakit menggunakan dataset medis yang berukuran terbatas.

---

# Struktur IMRAD

| Section | Peran | Pertanyaan Kunci |
|----------|--------|------------------|
| Introduction | Menjelaskan latar belakang, gap penelitian, dan tujuan | Mengapa penelitian ini diperlukan? |
| Method | Mendeskripsikan metodologi secara rinci | Bagaimana penelitian dilakukan? |
| Results | Menyajikan hasil eksperimen secara objektif | Apa yang ditemukan? |
| Discussion | Menginterpretasikan hasil penelitian | Apa makna dari hasil tersebut? |
| Conclusion | Menyimpulkan kontribusi penelitian | Apa kontribusi penelitian ini? |

---

# Logical Flow (Red Thread)

Setiap paragraf harus memiliki hubungan logis dengan paragraf sebelumnya maupun sesudahnya.

Alur logis harus terlihat pada tiga level:

- Antar kalimat dalam satu paragraf.
- Antar paragraf dalam satu section.
- Antar section dalam keseluruhan paper.

Dengan demikian pembaca dapat mengikuti alur berpikir peneliti tanpa kehilangan konteks.

---

# Internal Consistency

Seluruh pertanyaan penelitian (Research Question) yang diperkenalkan pada bagian **Introduction** harus dijawab pada bagian **Results**, **Discussion**, dan **Conclusion**.

## Consistency Matrix

| Komponen | Introduction | Method | Results | Discussion | Conclusion |
|----------|--------------|---------|----------|------------|------------|
| RQ1 | ✓ | ✓ | ✓ | ✓ | ✓ |
| RQ2 | ✓ | ✓ | ✓ | ✓ | ✓ |
| Accuracy | ✓ | ✓ | ✓ | ✓ | ✓ |
| Precision | ✓ | ✓ | ✓ | ✓ | ✓ |
| Recall | ✓ | ✓ | ✓ | ✓ | ✓ |
| F1-Score | ✓ | ✓ | ✓ | ✓ | ✓ |
| ROC-AUC | ✓ | ✓ | ✓ | ✓ | ✓ |
| Overfitting Analysis | ✓ | ✓ | ✓ | ✓ | ✓ |
| Generalization Analysis | ✓ | ✓ | ✓ | ✓ | ✓ |

Seluruh komponen penelitian muncul secara konsisten pada setiap bagian sehingga tidak terdapat inkonsistensi antar section.

---

# Writing Quality Triad

## Clarity

Tulisan harus mudah dipahami dalam sekali baca.

**Contoh**

Kurang baik

> Model menunjukkan peningkatan performa.

Lebih baik

> Model Random Forest meningkatkan accuracy dari **88,14% menjadi 91,27%** dibandingkan Logistic Regression.

---

## Precision

Gunakan istilah yang spesifik dan berbasis data.

**Contoh**

Kurang baik

> Hasilnya signifikan.

Lebih baik

> Hasil pengujian menunjukkan perbedaan yang signifikan secara statistik (**p = 0,012; η² = 0,42**).

---

## Conciseness

Setiap kalimat harus memberikan informasi baru dan menghindari pengulangan yang tidak diperlukan.

---

# Urutan Penulisan yang Disarankan

Agar proses penulisan lebih efisien, urutan berikut direkomendasikan:

1. Method
2. Results
3. Discussion
4. Introduction
5. Abstract
6. Conclusion

Pendekatan ini memudahkan penulis menyesuaikan latar belakang dan kontribusi berdasarkan hasil penelitian yang telah diperoleh.

---

# Target Jumlah Kata

| Section | Target Kata |
|----------|------------:|
| Abstract | 200–250 |
| Introduction | 500–700 |
| Related Work | 700–1000 |
| Method | 800–1200 |
| Results | 500–800 |
| Discussion | 600–900 |
| Conclusion | 200–400 |

---

# Jebakan Kognitif

Beberapa kesalahan yang sering ditemukan pada penulisan ilmiah:

- Menganggap tulisan yang lebih panjang selalu lebih baik.
- Menulis Introduction sebelum mengetahui hasil penelitian.
- Menggunakan istilah teknis secara berlebihan.
- Mengulang isi Results pada Discussion tanpa interpretasi.
- Menarik kesimpulan yang tidak didukung oleh data.

---

# Template A.15 — Paper Structure Checklist

## PAPER STRUCTURE CHECKLIST

**Judul**

> Prediksi Penyakit Jantung Menggunakan Machine Learning pada Dataset Medis Terbatas dengan Fokus pada Overfitting dan Generalisasi Model

**Target**

☑ Jurnal Nasional Terakreditasi (Sinta)

☐ Konferensi

☐ Laporan Penelitian

---

## Section Check

☑ **Abstract**

- Menjelaskan masalah penelitian.
- Menjelaskan metode yang digunakan.
- Menyampaikan hasil utama.
- Menjelaskan kontribusi penelitian.

☑ **Introduction**

- Latar belakang.
- Research Gap.
- Research Question.
- Tujuan penelitian.
- Kontribusi penelitian.

☑ **Related Work**

- Penelitian terdahulu mengenai prediksi penyakit.
- Machine Learning pada dataset medis.
- Overfitting.
- Generalisasi model.

☑ **Method**

- Dataset.
- Data preprocessing.
- Feature selection.
- Machine Learning.
- Cross Validation.
- Evaluasi performa.

☑ **Results**

- Tabel hasil eksperimen.
- Grafik performa model.
- Hasil uji statistik.

☑ **Discussion**

- Interpretasi hasil.
- Perbandingan dengan penelitian sebelumnya.
- Analisis overfitting.
- Analisis generalisasi.
- Keterbatasan penelitian.

☑ **Conclusion**

- Menjawab Research Question.
- Menyampaikan kontribusi penelitian.
- Future Work.

---

# Consistency Matrix

| Komponen | Intro | Method | Results | Discussion | Conclusion |
|-----------|:----:|:------:|:-------:|:----------:|:----------:|
| Research Question 1 | ✓ | ✓ | ✓ | ✓ | ✓ |
| Research Question 2 | ✓ | ✓ | ✓ | ✓ | ✓ |
| Accuracy | ✓ | ✓ | ✓ | ✓ | ✓ |
| Precision | ✓ | ✓ | ✓ | ✓ | ✓ |
| Recall | ✓ | ✓ | ✓ | ✓ | ✓ |
| F1-Score | ✓ | ✓ | ✓ | ✓ | ✓ |
| ROC-AUC | ✓ | ✓ | ✓ | ✓ | ✓ |
| Overfitting Analysis | ✓ | ✓ | ✓ | ✓ | ✓ |
| Generalization Analysis | ✓ | ✓ | ✓ | ✓ | ✓ |
| Kontribusi Penelitian | ✓ | ✓ | ✓ | ✓ | ✓ |

Seluruh bagian telah menunjukkan konsistensi antara tujuan penelitian, metode, hasil, pembahasan, dan kesimpulan.

---

# Writing Quality Checklist

☑ Clarity

Seluruh istilah dijelaskan secara jelas dan mudah dipahami.

☑ Precision

Semua klaim didukung oleh angka, hasil eksperimen, dan uji statistik.

☑ Conciseness

Tidak terdapat pengulangan informasi yang tidak diperlukan.

---

# Latihan 1 — Paper Outline

| Section | Konten Utama | Target Kata |
|----------|--------------|------------:|
| Abstract | Penelitian mengevaluasi beberapa algoritma machine learning untuk prediksi penyakit jantung pada dataset medis terbatas dengan fokus pada overfitting dan kemampuan generalisasi. Hasil menunjukkan Random Forest memberikan performa paling stabil dibandingkan model lainnya. | 200–250 |
| Introduction | Menjelaskan pentingnya diagnosis penyakit jantung, keterbatasan dataset medis, masalah overfitting, research gap, research question, tujuan, dan kontribusi penelitian. | 500–700 |
| Related Work | Membahas penelitian terdahulu mengenai machine learning untuk diagnosis penyakit, evaluasi algoritma klasifikasi, overfitting, generalisasi model, dan teknik validasi. | 700–1000 |
| Method | Menjelaskan dataset, preprocessing, feature selection, pembagian data, algoritma machine learning, cross validation, metrik evaluasi, dan analisis statistik. | 800–1200 |
| Results | Menampilkan hasil accuracy, precision, recall, F1-score, ROC-AUC, confusion matrix, serta hasil uji statistik antar model. | 500–800 |
| Discussion | Menginterpretasikan hasil eksperimen, membahas penyebab overfitting, kemampuan generalisasi model, membandingkan dengan penelitian sebelumnya, serta membahas keterbatasan penelitian. | 600–900 |
| Conclusion | Menyimpulkan hasil penelitian, menjawab research question, menjelaskan kontribusi penelitian, dan memberikan rekomendasi penelitian lanjutan. | 200–400 |

---

# Latihan 2 — Consistency Matrix

| Komponen | Introduction | Method | Results | Discussion | Conclusion |
|-----------|:------------:|:------:|:-------:|:----------:|:----------:|
| RQ1 | ✓ | ✓ | ✓ | ✓ | ✓ |
| RQ2 | ✓ | ✓ | ✓ | ✓ | ✓ |
| Accuracy | ✓ | ✓ | ✓ | ✓ | ✓ |
| Precision | ✓ | ✓ | ✓ | ✓ | ✓ |
| Recall | ✓ | ✓ | ✓ | ✓ | ✓ |
| F1-Score | ✓ | ✓ | ✓ | ✓ | ✓ |
| ROC-AUC | ✓ | ✓ | ✓ | ✓ | ✓ |
| Variabel Independen | ✓ | ✓ | ✓ | ✓ | ✓ |
| Variabel Dependen | ✓ | ✓ | ✓ | ✓ | ✓ |
| Kontribusi Penelitian | ✓ | ✓ | ✓ | ✓ | ✓ |

## Inkonsistensi yang Ditemukan

Tidak ditemukan inkonsistensi. Seluruh variabel, metrik evaluasi, dan research question telah dibahas secara konsisten pada setiap bagian paper.

## Tindakan Perbaikan

- Memastikan setiap metrik yang digunakan pada bagian Results telah dijelaskan pada bagian Method.
- Memastikan seluruh Research Question dijawab pada bagian Conclusion.
- Memastikan seluruh klaim pada Discussion didukung oleh hasil eksperimen.

---

# Latihan 3 — Writing Quality Check

## Paragraf Asli

Model Random Forest memiliki performa yang baik dibandingkan model lainnya. Hal ini menunjukkan bahwa model tersebut mampu menghasilkan hasil yang lebih baik pada dataset yang digunakan.

---

## Evaluasi

| Kriteria | Evaluasi | Perbaikan |
|----------|----------|-----------|
| Clarity | Istilah "performa yang baik" terlalu umum. | Sebutkan metrik yang meningkat. |
| Precision | Tidak terdapat nilai numerik. | Tambahkan accuracy, F1-score, dan hasil uji statistik. |
| Conciseness | Kalimat kedua mengulang makna kalimat pertama. | Gabungkan menjadi satu kalimat yang lebih ringkas. |

---

## Paragraf Setelah Perbaikan

Model **Random Forest** memperoleh **accuracy sebesar 91,27% ± 1,21%** dan **F1-score sebesar 90,84% ± 1,35%**, lebih tinggi dibandingkan algoritma lainnya. Hasil uji statistik (**p = 0,012**) menunjukkan bahwa peningkatan performa tersebut signifikan, sehingga Random Forest memiliki kemampuan generalisasi yang lebih baik pada dataset medis yang berukuran terbatas.

---

# Refleksi

Menulis **tentang penelitian** hanya berfokus pada penyampaian aktivitas yang dilakukan, sedangkan menulis sebagai **argumen penelitian** bertujuan meyakinkan pembaca bahwa penelitian memiliki dasar ilmiah yang kuat, metode yang valid, hasil yang dapat dipertanggungjawabkan, dan kontribusi yang jelas terhadap perkembangan ilmu pengetahuan.

Urutan penulisan **Method → Results → Discussion → Introduction → Abstract → Conclusion** membantu menghasilkan tulisan yang lebih konsisten karena seluruh latar belakang, tujuan, dan kontribusi disusun berdasarkan hasil penelitian yang benar-benar diperoleh, bukan berdasarkan asumsi sebelum eksperimen dilakukan.
