# WS-04: Research Question & Hypothesis

> **Bab 4 — Research Question, Contribution & Hypothesis**

---

## Ringkasan Materi

### RQ Bukan Pertanyaan Biasa

Research Question yang baik secara implisit mengandung cetak biru eksperimen: subjek, baseline, metrik, domain, dataset.

| Kualitas | Contoh |
|----------|--------|
| **Buruk** | "Bagaimana pengaruh deep learning terhadap deteksi malware?" |
| **Baik** | "Apakah CNN menghasilkan F1-Score lebih tinggi dari RF pada CIC-MalMem-2022?" |

Perbedaan: RQ yang baik menyebutkan **metode spesifik**, **metrik terukur**, **baseline**, dan **dataset**.

### Tiga Jenis RQ

| Jenis | Pola | Kebutuhan |
|-------|------|-----------|
| **Comparison** | A vs B → mana lebih baik? | ≥ 2 metode, metrik sama |
| **Improvement** | A' vs A → modifikasi lebih baik? | Pre/post, bukti perbaikan |
| **Exploratory** | Faktor X₁...Xₙ → pengaruh terhadap Y? | Multi-variabel, korelasi/regresi |

### Contribution Statement

Tiga jenis kontribusi: **Improvement** (metode terbukti lebih baik), **Comparison** (perbandingan sistematis yang belum ada), **Novel Approach** (pendekatan baru). Kontribusi harus terhubung langsung dengan gap — kontribusi tanpa gap = klaim tanpa justifikasi.

### Hypothesis H₀ / H₁

- **H₀** (Null) = Tidak ada perbedaan signifikan — asumsi default, harus dibuktikan salah
- **H₁** (Alternative) = Ada perbedaan signifikan — diterima hanya jika H₀ ditolak
- Harus **falsifiable**, mengandung **metrik terukur**, dirumuskan **SEBELUM eksperimen**

### Rantai Operasionalisasi

```
RQ → Variable → Metric → Data → Analysis
```

Jika rantai ini tidak lengkap, RQ belum mature. Bi-directional: RQ yang tidak bisa jadi hipotesis testable harus direvisi mundur.

### Research vs Engineering

| Aspek | Engineering | Research |
|-------|------------|----------|
| Tujuan pertanyaan | Apa yang harus dibangun? | Apa yang harus dibuktikan? |
| Bentuk jawaban | Sistem yang berfungsi | Bukti empiris terukur |
| Sukses diukur oleh | User satisfaction, uptime | Signifikansi statistik, effect size |
| Jika gagal | Debug dan perbaiki | Laporkan, analisis mengapa |

### Istilah Penting

- **Research Question (RQ)** — Pertanyaan spesifik: variabel terukur + metrik + konteks
- **Contribution Statement** — Apa yang diketahui setelah riset selesai yang sebelumnya belum ada
- **H₀ / H₁** — Null vs Alternative Hypothesis
- **Falsifiability** — Kondisi hipotesis ditolak harus bisa didefinisikan sebelum eksperimen
- **Operationalization** — Proses mewujudkan konsep abstrak menjadi variabel terukur

---

## Template A.4 — RQ-Contribution-Hypothesis

```
RQ-CONTRIBUTION-HYPOTHESIS

Gap Statement  : ____________________

Research Question:
  Tipe         : [ ] Comparison  [ ] Improvement  [ ] Exploratory
  Formulasi    : ____________________
  Variabel IV  : ____________________
  Variabel DV  : ____________________
  Metrik       : ____________________
  Dataset      : ____________________
  Baseline     : ____________________

Quality Check RQ:
  [ ] Variabel spesifik
  [ ] Metrik jelas
  [ ] Baseline ada
  [ ] Konteks disebutkan
  [ ] Memerlukan eksperimen (bukan hanya survei literatur)

Contribution Statement:
  Apa yang baru diketahui : ____________________
  Jenis kontribusi        : [ ] Improvement  [ ] Comparison  [ ] Novel approach
  Gap yang diisi          : ____________________

Hypothesis Pair:
  H₀ : ____________________
  H₁ : ____________________
  Threshold              : ____________________
  Justifikasi threshold  : ____________________
```

---

## Latihan 1 — Dari Gap ke RQ

Gunakan gap yang ditemukan di WS-03. Transformasikan menjadi Research Question.

**Gap dari WS-03:** Belum ada evaluasi komparatif yang secara langsung membandingkan efektivitas metode regularisasi seperti dropout dan L2 regularization dalam mengurangi overfitting dan meningkatkan kemampuan generalisasi model CNN pada prediksi penyakit jantung menggunakan dataset medis terbatas.

**RQ versi pertama (tulis bebas):**
> Bagaimana pengaruh metode regularisasi terhadap performa model CNN dalam prediksi penyakit jantung pada dataset medis terbatas?

**Evaluasi RQ:**

| Komponen | Ada? | Isi |
|----------|------|-----|
| Metode spesifik | Ya — Dropout dan L2 Regularization pada CNN | Menguji model CNN dengan menambahkan teknik regularisasi untuk melihat apakah model menjadi lebih stabil dan tidak hanya menghafal data training. |
| Metrik terukur | Ya — Accuracy, Precision, Recall, dan F1-score | Mengukur performa model menggunakan metrik kuantitatif untuk melihat kemampuan prediksi dan generalisasi model pada data baru. |
| Baseline | Ya — Random Forest dan CNN tanpa regularisasi | Performa model dibandingkan dengan metode machine learning umum dan model CNN standar tanpa regularisasi agar peningkatan performa dapat dievaluasi secara adil. |
| Dataset/konteks | Ya — Heart Disease Dataset (dataset medis terbatas) | Pengujian dilakukan menggunakan dataset pasien penyakit jantung yang memiliki jumlah data terbatas dan sering digunakan pada penelitian machine learning bidang kesehatan. |

**Tipe RQ:** [ x ] Comparison / [ x ] Improvement / [ ] Exploratory

**RQ versi revisi (setelah evaluasi):**
> Bagaimana pengaruh metode regularisasi seperti dropout dan L2 regularization terhadap peningkatan F1-score dan kemampuan generalisasi model CNN dibandingkan Random Forest pada prediksi penyakit jantung menggunakan dataset medis terbatas?

---

## Latihan 2 — Hypothesis Pair

Rumuskan pasangan hipotesis dari RQ di Latihan 1.

| Komponen | Isi |
|----------|-----|
| H₀ | Tidak terdapat perbedaan performa yang signifikan pada F1-score dan kemampuan generalisasi antara model CNN yang menggunakan metode regularisasi dan model CNN tanpa regularisasi maupun baseline Random Forest dalam prediksi penyakit jantung. |
| H₁ | Terdapat peningkatan performa yang signifikan pada F1-score dan kemampuan generalisasi model CNN setelah menggunakan metode regularisasi seperti dropout dan L2 regularization dibandingkan model tanpa regularisasi dan baseline Random Forest pada prediksi penyakit jantung. |
| Metrik | Accuracy, Precision, Recall, F1-score, dan Generalization Error |
| Threshold | Perbedaan performa minimal 5% pada F1-score dan hasil uji statistik menunjukkan p-value < 0.05 |
| Justifikasi threshold | Selisih performa minimal 5% digunakan untuk memastikan peningkatan performa model benar-benar berasal dari pengaruh metode regularisasi, bukan hanya karena variasi random saat proses training. Nilai p-value < 0.05 digunakan sebagai standar umum untuk menentukan apakah hasil eksperimen signifikan secara statistik. |

**Apakah hipotesis ini falsifiable?** [ x ] Ya / [ ] Tidak
> Bagaimana cara membuktikannya salah? Hipotesis dapat dibuktikan salah apabila setelah dilakukan eksperimen, model CNN yang menggunakan dropout atau L2 regularization tidak menunjukkan peningkatan performa yang signifikan dibandingkan CNN tanpa regularisasi maupun Random Forest.

Jika hasil pengujian statistik menunjukkan bahwa selisih F1-score sangat kecil atau tidak signifikan, maka H₁ ditolak dan H₀ diterima.

---

## Latihan 3 — Rantai Operasionalisasi

Lengkapi rantai dari RQ hingga metode analisis.

| Tahap | Isi |
|-------|-----|
| RQ | Bagaimana pengaruh metode regularisasi seperti dropout dan L2 regularization terhadap peningkatan kemampuan generalisasi model CNN pada prediksi penyakit jantung dibandingkan Random Forest? |
| Variable (IV) | Jenis metode regularisasi yang digunakan pada model CNN (tanpa regularisasi, dropout, dan L2 regularization). |
| Variable (DV) | Performa model prediksi penyakit jantung dan kemampuan generalisasi model pada data baru. |
| Metric | Accuracy, Precision, Recall, F1-score, dan Generalization Error untuk mengukur performa model serta kestabilan hasil prediksi pada data testing. |
| Data source | Heart Disease Dataset dari UCI Machine Learning Repository yang berisi data pasien seperti usia, tekanan darah, kolesterol, denyut jantung, dan hasil diagnosis penyakit jantung. |
| Analysis method | Perbandingan performa antar model menggunakan evaluasi metrik machine learning dan uji statistik untuk melihat apakah peningkatan performa signifikan secara statistik. |

**Apakah rantai lengkap?** [ x ] Ya / [ ] Tidak
> Jika tidak, tahap mana yang perlu direvisi? Tidak ada, karena seluruh komponen mulai dari RQ, variabel, metrik, dataset, hingga metode analisis sudah saling terhubung.

---

## Refleksi

> Ambil satu judul skripsi/paper yang pernah dibaca. Coba ekstrak RQ-nya. Apakah RQ tersebut memenuhi semua komponen (metode, metrik, baseline, konteks)? Jika tidak, apa yang hilang?

**Judul:** _____________________________________________
**RQ yang diekstrak:** __________________________________
**Komponen yang hilang:** _______________________________
