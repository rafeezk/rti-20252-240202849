# WS-16: Presentation & Defense (UAS)

> **Bab 16 — Presentasi & Pertahanan Ilmiah**

---

# Ringkasan Materi

## Scientific Defense Model

```
Research
    ↓
Presentation
    ↓
Question & Answer
    ↓
Scientific Defense
    ↓
Evaluation
    ↓
Research Acceptance
```

Presentasi ilmiah merupakan tahap akhir dalam proses penelitian. Tujuannya bukan hanya menyampaikan hasil penelitian, tetapi juga mempertahankan setiap keputusan ilmiah yang diambil selama penelitian.

Pada penelitian ini, presentasi difokuskan pada evaluasi beberapa algoritma **Machine Learning** untuk **prediksi penyakit jantung pada dataset medis terbatas** dengan perhatian utama terhadap **overfitting** dan **kemampuan generalisasi model**.

---

# Presentasi ≠ Ringkasan Paper

| Paper | Presentasi |
|--------|------------|
| Dibaca oleh reviewer | Didengar oleh audiens |
| Menjelaskan seluruh detail | Menyampaikan ide utama |
| Banyak tabel dan angka | Grafik dan visualisasi |
| Dapat dibaca berulang | Hanya didengar satu kali |

Prinsip utama:

> **Presentasi bukan sekadar mempersingkat paper, tetapi menyampaikan inti penelitian secara efektif.**

---

# Claim – Evidence – Reasoning (CER)

Setiap jawaban ketika sidang sebaiknya mengikuti pola berikut.

## Claim

Jawaban utama terhadap pertanyaan penguji.

## Evidence

Bukti berupa hasil eksperimen, tabel, grafik, atau literatur.

## Reasoning

Penjelasan logis yang menghubungkan bukti dengan jawaban.

---

## Contoh CER

| Pertanyaan | Jawaban CER |
|------------|-------------|
| Mengapa menggunakan Random Forest? | **Claim:** Random Forest dipilih karena menghasilkan performa terbaik. **Evidence:** Accuracy 91,27%, F1-score 90,84%, ROC-AUC 0,95. **Reasoning:** Algoritma ensemble mampu mengurangi overfitting pada dataset berukuran kecil sehingga memberikan generalisasi yang lebih baik. |
| Mengapa hanya menggunakan satu dataset? | **Claim:** Dataset dipilih karena merupakan dataset medis yang banyak digunakan dalam penelitian. **Evidence:** Cleveland Heart Disease Dataset telah digunakan pada berbagai penelitian sebelumnya. **Reasoning:** Hal ini memudahkan proses reproduksi penelitian dan perbandingan hasil dengan studi terdahulu. |
| Mengapa Neural Network tidak menjadi model terbaik? | **Claim:** Neural Network mengalami overfitting. **Evidence:** Selisih accuracy training dan testing cukup besar serta variasi antar-fold tinggi. **Reasoning:** Ukuran dataset yang terbatas menyebabkan model terlalu kompleks sehingga kemampuan generalisasi menurun. |

---

# Slide Design — One Slide, One Message

## Rencana Presentasi 15 Menit

| No | Slide | Waktu | Pesan |
|----|--------|-------|--------|
| 1 | Judul Penelitian | 1 menit | Gambaran umum penelitian |
| 2 | Latar Belakang | 2 menit | Pentingnya prediksi penyakit jantung |
| 3 | Research Gap & Research Question | 2 menit | Celah penelitian yang ingin diselesaikan |
| 4 | Metodologi | 2 menit | Dataset, preprocessing, algoritma, evaluasi |
| 5 | Hasil Eksperimen | 2 menit | Perbandingan performa model |
| 6 | Visualisasi Hasil | 2 menit | Grafik Accuracy, F1-score, ROC-AUC |
| 7 | Analisis & Failure Analysis | 2 menit | Penyebab overfitting dan generalisasi |
| 8 | Keterbatasan & Future Work | 1 menit | Batasan penelitian |
| 9 | Kesimpulan | 1 menit | Kontribusi penelitian |

---

# Anticipatory Defense

Prediksi pertanyaan yang kemungkinan diajukan penguji.

| Kategori | Contoh Pertanyaan |
|----------|-------------------|
| Problem | Mengapa memilih prediksi penyakit jantung? |
| Literature | Apa kebaruan penelitian dibanding penelitian sebelumnya? |
| Method | Mengapa memilih Random Forest, SVM, dan Neural Network? |
| Dataset | Mengapa menggunakan dataset berukuran kecil? |
| Evaluation | Mengapa menggunakan Accuracy dan F1-Score? |
| Generalization | Bagaimana memastikan model tidak overfitting? |
| Future Work | Bagaimana penelitian ini dapat dikembangkan? |

---

# Tiga Prinsip Menjawab Pertanyaan

## 1. Direct

Jawab inti pertanyaan terlebih dahulu.

---

## 2. Data-Based

Gunakan hasil eksperimen sebagai bukti.

---

## 3. Honest

Akui keterbatasan penelitian apabila memang ada.

---

# Jebakan Kognitif

Kesalahan yang sering terjadi saat presentasi:

- Menampilkan terlalu banyak isi paper pada slide.
- Terlalu fokus pada animasi dibanding isi penelitian.
- Menjawab pertanyaan tanpa didukung data.
- Menghindari pembahasan keterbatasan penelitian.
- Tidak berlatih presentasi sebelum sidang.

---

# Template A.16 — Defense Preparation Sheet

## DEFENSE PREPARATION

### Slide Deck Plan

Total slide : **11 slide**

Waktu per slide : **±1,5 menit**

Total waktu : **15 menit**

---

## Slide Outline

| No | Pesan Utama | Visual | Waktu |
|----|-------------|--------|-------|
| 1 | Judul Penelitian | Cover | 1 menit |
| 2 | Latar Belakang | Diagram masalah penyakit jantung | 2 menit |
| 3 | Research Gap & Research Question | Diagram alur penelitian | 2 menit |
| 4 | Metodologi | Flowchart penelitian | 2 menit |
| 5 | Dataset & Preprocessing | Diagram preprocessing | 1,5 menit |
| 6 | Perbandingan Model | Tabel hasil eksperimen | 2 menit |
| 7 | Visualisasi Hasil | Bar Chart Accuracy & F1-Score | 2 menit |
| 8 | Failure Analysis | Grafik overfitting | 1,5 menit |
| 9 | Kesimpulan | Ringkasan kontribusi | 1 menit |
| 10 | Future Work | Diagram pengembangan penelitian | 0,5 menit |
| 11 | Terima Kasih & Q&A | Slide penutup | 0,5 menit |

---

## Anticipatory Defense Matrix

| Kategori | Pertanyaan Potensial | Jawaban (CER) |
|----------|----------------------|---------------|
| Problem | Mengapa memilih penyakit jantung? | **Claim:** Penyakit jantung merupakan penyebab kematian utama di dunia. **Evidence:** WHO melaporkan penyakit kardiovaskular menjadi penyebab kematian tertinggi. **Reasoning:** Model prediksi dini berpotensi membantu proses diagnosis klinis. |
| Literature | Apa kebaruan penelitian ini? | **Claim:** Penelitian berfokus pada overfitting dan generalisasi pada dataset medis terbatas. **Evidence:** Sebagian penelitian sebelumnya hanya melaporkan accuracy tanpa analisis generalisasi. **Reasoning:** Penelitian ini memberikan evaluasi yang lebih komprehensif. |
| Method | Mengapa menggunakan Random Forest? | **Claim:** Random Forest menghasilkan performa terbaik. **Evidence:** Accuracy dan F1-score tertinggi dengan standar deviasi kecil. **Reasoning:** Ensemble learning lebih tahan terhadap overfitting. |
| Results | Mengapa Neural Network memiliki variasi hasil yang besar? | **Claim:** Model mengalami overfitting. **Evidence:** Selisih training dan testing accuracy cukup tinggi. **Reasoning:** Kompleksitas model tidak sebanding dengan ukuran dataset. |
| Generalization | Apakah model dapat digunakan pada dataset lain? | **Claim:** Berpotensi digunakan tetapi memerlukan validasi tambahan. **Evidence:** Penelitian hanya menggunakan satu dataset medis. **Reasoning:** Validasi eksternal diperlukan untuk memastikan kemampuan generalisasi. |

---

# Latihan 1 — Slide Outline

## Presentasi 15 Menit

| No | Pesan Utama | Visual | Waktu |
|----|-------------|--------|-------|
| 1 | Judul dan tujuan penelitian | Cover | 1 menit |
| 2 | Latar belakang penyakit jantung | Statistik WHO | 2 menit |
| 3 | Research Gap dan Research Question | Diagram literatur | 1,5 menit |
| 4 | Dataset dan preprocessing | Flowchart preprocessing | 2 menit |
| 5 | Algoritma machine learning | Diagram workflow model | 2 menit |
| 6 | Hasil eksperimen | Tabel Accuracy, Precision, Recall, F1-Score | 2 menit |
| 7 | Visualisasi performa model | Bar Chart dan ROC Curve | 2 menit |
| 8 | Analisis overfitting dan generalisasi | Grafik Training vs Validation | 1,5 menit |
| 9 | Kesimpulan | Ringkasan kontribusi | 1 menit |

**Total waktu estimasi: ±15 menit**

---

# Latihan 2 — Anticipatory Defense

| No | Kategori | Pertanyaan | Claim | Evidence | Reasoning |
|----|----------|------------|--------|----------|-----------|
| 1 | Problem | Mengapa memilih penyakit jantung? | Penyakit jantung memiliki tingkat kematian tinggi. | Data WHO dan penelitian terdahulu. | Prediksi dini sangat penting dalam bidang kesehatan. |
| 2 | Method | Mengapa menggunakan Random Forest? | Random Forest paling stabil. | Accuracy 91,27% dan F1-score 90,84%. | Ensemble learning mengurangi overfitting. |
| 3 | Dataset | Mengapa hanya satu dataset? | Dataset merupakan benchmark yang banyak digunakan. | Cleveland Heart Disease Dataset. | Memudahkan reproduksi dan perbandingan hasil penelitian. |
| 4 | Results | Mengapa Neural Network kurang baik? | Terjadi overfitting. | Variasi performa antar-fold cukup tinggi. | Dataset terlalu kecil untuk model kompleks. |
| 5 | Generalization | Apakah model dapat diterapkan pada rumah sakit lain? | Memungkinkan dengan validasi tambahan. | Penelitian hanya menggunakan satu sumber data. | Validasi eksternal diperlukan sebelum implementasi nyata. |

---

# Latihan 3 — Simulasi Q&A

| No | Pertanyaan | Jawaban | Evaluasi |
|----|------------|---------|----------|
| 1 | Mengapa tidak menggunakan XGBoost? | Penelitian membatasi perbandingan pada algoritma yang paling umum digunakan agar evaluasi lebih terfokus. Penggunaan XGBoost menjadi rekomendasi penelitian selanjutnya. | ☑ Direct ☑ Data-Based ☑ Honest |
| 2 | Mengapa menggunakan Accuracy dan F1-Score? | Accuracy menunjukkan performa keseluruhan, sedangkan F1-Score lebih sesuai untuk mengevaluasi keseimbangan Precision dan Recall pada klasifikasi medis. | ☑ Direct ☑ Data-Based ☑ Honest |
| 3 | Bagaimana memastikan model tidak overfitting? | Penelitian menggunakan Stratified K-Fold Cross Validation serta membandingkan performa training dan testing untuk mengevaluasi kemampuan generalisasi model. | ☑ Direct ☑ Data-Based ☑ Honest |

---

## Pertanyaan yang Paling Sulit Dijawab

Bagaimana model akan bekerja jika diterapkan pada dataset dari rumah sakit lain dengan karakteristik pasien yang berbeda?

---

## Hal yang Perlu Dipersiapkan Lebih Baik

- Menambah referensi penelitian terbaru mengenai validasi eksternal.
- Menyiapkan hasil eksperimen tambahan menggunakan dataset lain apabila tersedia.
- Menyiapkan penjelasan mengenai interpretabilitas model machine learning dalam konteks klinis.

---

# Refleksi

Seluruh rangkaian WS-01 hingga WS-16 memberikan pemahaman bahwa penelitian bukan hanya menghasilkan model dengan akurasi tinggi, tetapi juga menyusun argumen ilmiah yang dapat dipertanggungjawabkan mulai dari identifikasi masalah, metodologi, analisis hasil, hingga penyampaian hasil penelitian kepada komunitas ilmiah.

## Insight Terbesar

Kemampuan generalisasi model sama pentingnya dengan peningkatan akurasi. Model dengan performa tinggi pada data pelatihan belum tentu memberikan hasil yang baik ketika diterapkan pada data baru, sehingga evaluasi overfitting harus menjadi bagian utama dalam penelitian machine learning.

## Yang Akan Selalu Diterapkan

- Menyusun Research Question yang jelas sebelum memulai eksperimen.
- Mendokumentasikan seluruh proses preprocessing dan evaluasi agar penelitian dapat direproduksi.
- Menggunakan analisis statistik yang tepat untuk mendukung setiap klaim penelitian.
- Menjelaskan keterbatasan penelitian secara jujur.
- Menyusun presentasi berdasarkan pesan utama penelitian, bukan sekadar merangkum isi paper.
```
