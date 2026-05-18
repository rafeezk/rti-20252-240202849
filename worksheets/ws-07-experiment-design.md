# WS-07: Experimental Design & Validity

> **Bab 7 — Experimental Design & Validity**

---

## Ringkasan Materi

### Correlation ≠ Causality

Kausalitas membutuhkan 3 syarat:
1. **Covariance** — X dan Y bergerak bersama
2. **Temporal precedence** — X berubah sebelum Y
3. **Elimination of alternatives** — Tidak ada faktor lain yang menjelaskan Y

Controlled experiment adalah satu-satunya metode yang bisa membuktikan kausalitas.

### Empat Jenis Validitas

| Jenis | Pertanyaan | Ancaman Umum |
|-------|-----------|-------------|
| **Internal** | Apakah hubungan IV→DV nyata? | Confounding variable, selection bias |
| **External** | Apakah bisa digeneralisasi? | Dataset terlalu spesifik |
| **Construct** | Apakah mengukur konsep yang benar? | Metrik tidak sesuai |
| **Conclusion** | Apakah kesimpulan statistik valid? | Sample size kecil, uji salah |

Internal dan external validity sering berkonflik: semakin terkontrol (internal kuat) → semakin artificial (external lemah).

### Tiga Tipe Eksperimen dalam Riset TI

| Tipe | Deskripsi | Kapan Digunakan |
|------|----------|----------------|
| **Comparison Study** | Metode A vs B pada kondisi identik | Membandingkan pendekatan berbeda |
| **Ablation Study** | Full system → lepas komponen satu per satu | Mengukur kontribusi tiap komponen |
| **Parameter Study** | Variasikan satu parameter, amati dampak | Uji sensitifitas/robustness |

### Fairness dalam Perbandingan

Perbandingan yang adil = **kondisi identik** untuk semua metode: dataset sama, preprocessing sama, tuning effort sebanding, environment sama, metrik sama.

Contoh tidak adil: Transformer (30 fitur tambahan + Bayesian optimization) vs RF (default params) → hasilnya misleading.

### Threats to Validity = Diidentifikasi Sebelum Eksperimen

Ancaman validitas harus diidentifikasi **sebelum** eksperimen dan mitigasinya dirancang sebagai bagian dari desain — bukan ditulis sebagai boilerplate setelah selesai.

### Research vs Engineering

| Aspek | Engineering | Research |
|-------|------------|----------|
| Tujuan testing | Memastikan sistem memenuhi requirement | Membuktikan hubungan kausal antar variabel |
| Baseline | Versi sebelumnya (last release) | Metode tervalidasi dari literatur |
| Kegagalan | Bug → fix → release | H₀ tidak ditolak → tetap kontribusi ilmiah |
| Sukses | 100% test pass | Evidence valid — mendukung atau menolak hipotesis |

### Istilah Penting

- **Causality** — Hubungan sebab-akibat (covariance + temporal + elimination)
- **Controlled Experiment** — Ubah satu variabel, kontrol sisanya, amati efek
- **Fairness** — Semua metode diuji pada kondisi yang benar-benar identik
- **Threats to Validity** — Faktor yang bisa melemahkan kesimpulan jika tidak dimitigasi
- **Conclusion Validity** — Validitas statistik: power, sample size, uji yang tepat

---

## Template A.7 — Desain Eksperimen Lengkap

```
EXPERIMENT DESIGN

Research Question : Apakah metode regularisasi Dropout dan L2 Regularization dapat meningkatkan performa generalisasi model CNN dalam prediksi penyakit jantung dibandingkan CNN tanpa regularisasi pada dataset Heart Disease UCI?
Hypothesis        : H₀ : Tidak ada perbedaan signifikan performa F1-Score antara CNN tanpa regularisasi dengan CNN yang menggunakan Dropout dan L2 Regularization.

H₁ : CNN dengan Dropout dan L2 Regularization menghasilkan F1-Score yang lebih tinggi secara signifikan dibandingkan CNN tanpa regularisasi.
Tipe Eksperimen   : [ ✓ ] Comparison  [ ✓ ] Ablation  [ ] Parameter

Kondisi Eksperimen:
| Kondisi | Deskripsi | IV Value | CV Settings |
|---------|-----------|----------|-------------|
| Control |     CNN baseline tanpa regularisasi      |     CNN standar     |      Dataset Heart Disease UCI, train-test split 80:20, seed 42, epoch 50, learning rate 0.001       |
| Treatment |    CNN dengan Dropout     |     CNN + Dropout     |      Dataset, preprocessing, epoch, dan learning rate dibuat identik       |
| Treatment |    CNN dengan L2 Regularization     |     CNN + L2     |      Dataset, preprocessing, epoch, dan learning rate dibuat identik       |
| Treatment |    CNN dengan Dropout + L2     |     CNN + Dropout + L2     |      Semua parameter kontrol dibuat sama       |


Fairness Checklist:
[✓] Dataset identik untuk semua kondisi
Semua model menggunakan dataset Heart Disease UCI yang sama persis, baik data training maupun testing, sehingga tidak ada model yang mendapat keuntungan dari data berbeda.

[✓] Preprocessing setara
Semua data diproses menggunakan tahapan preprocessing yang sama seperti normalisasi fitur, handling missing value, dan encoding data kategorikal sebelum masuk ke model CNN.

[✓] Tuning effort setara
Setiap model dilatih menggunakan jumlah epoch, batch size, learning rate, optimizer, dan waktu training yang sama agar proses pelatihan tetap adil.

[✓] Environment identik
Seluruh eksperimen dijalankan pada perangkat laptop, sistem operasi, versi Python, TensorFlow, dan library yang sama sehingga tidak ada perbedaan performa akibat hardware/software.

[✓] Metrik evaluasi sama
Semua model dibandingkan menggunakan Accuracy, Precision, Recall, F1-Score, dan Generalization Error dengan metode perhitungan yang sama.

Threat Analysis:
| Threat Type | Ancaman Spesifik | Mitigasi |
|-------------|-----------------|----------|
| Internal    |        Hasil model bisa berbeda hanya karena random initialization bobot awal CNN, bukan karena efek regularisasi         |     Menggunakan random seed yang sama dan menjalankan eksperimen beberapa kali lalu mengambil rata-rata hasil     |
| External    |        Menggunakan random seed yang sama dan menjalankan eksperimen beberapa kali lalu mengambil rata-rata hasil         |     Menuliskan batasan penelitian secara eksplisit dan menyarankan pengujian pada dataset medis yang lebih besar     |
| Construct   |        Accuracy saja tidak cukup untuk menilai kualitas model medis karena data bisa imbalance         |     Menambahkan Precision, Recall, dan F1-Score agar pengukuran lebih representatif     |
| Conclusion  |         Jumlah eksperimen terlalu sedikit dapat membuat hasil tidak signifikan secara statistik        |     Melakukan repeated experiment dan menggunakan uji statistik untuk memastikan perbedaan performa benar benar nyata     |

Statistical Plan:
  Uji statistik   : Independent Sample T-Test
  Justifikasi      : Digunakan untuk membandingkan rata-rata performa dua kelompok model yang berbeda, misalnya CNN tanpa regularisasi dibanding CNN dengan Dropout atau L2 Regularization.
  Alpha            : α=0.05
  Effect size min  : d≥0.5
```

---

## Latihan 1 — Desain Eksperimen

Susun desain eksperimen berdasarkan RQ, variabel, dan sistem dari WS-04 sampai WS-06.

**RQ:** Bagaimana pengaruh penggunaan metode regularisasi Dropout dan L2 Regularization terhadap kemampuan generalisasi model CNN dalam prediksi penyakit jantung pada dataset medis terbatas dibandingkan CNN tanpa regularisasi?
**Tipe eksperimen:** [ ] Comparison / [ ] Ablation / [ ] Parameter

| Kondisi | Deskripsi | IV Value | CV Settings |
|---------|-----------|----------|-------------|
| Control | Pengujian model baseline tanpa regularisasi untuk melihat performa dasar CNN terhadap dataset penyakit jantung | Menggunakan CNN standar tanpa Dropout dan tanpa L2 Regularization | Dataset Heart Disease UCI, train-test split 80:20, epoch 50, learning rate 0.001, batch size 32, random seed 42 |
| Treatment | Pengujian CNN dengan regularisasi Dropout untuk mengurangi overfitting saat training | Menggunakan CNN + Dropout 0.5 | Dataset, preprocessing, epoch, learning rate, batch size, dan random seed dibuat identik |
| Treatment | Pengujian CNN dengan L2 Regularization untuk membatasi bobot model agar tidak terlalu kompleks | Menggunakan CNN + L2 Regularization (0.001) | Dataset, preprocessing, epoch, learning rate, batch size, dan random seed dibuat identik |
| Treatment | Pengujian kombinasi dua regularisasi sekaligus untuk melihat apakah performa generalisasi semakin meningkat | Menggunakan CNN + Dropout + L2 Regularization | Dataset, preprocessing, epoch, learning rate, batch size, dan random seed dibuat identik |


---

## Latihan 2 — Fairness Checklist

Evaluasi apakah desain eksperimen di Latihan 1 sudah fair.

| Kriteria | Status | Detail |
|----------|--------|--------|
| Dataset identik | ✅ | Semua model menggunakan dataset Heart Disease UCI yang sama persis, baik data training maupun testing. Tidak ada penambahan atau pengurangan data pada salah satu model. |
| Preprocessing setara | ✅ | Seluruh data diproses menggunakan tahapan preprocessing yang sama seperti normalisasi fitur, handling missing value, dan encoding data kategorikal. |
| Tuning effort setara | ✅ | Semua model dilatih dengan jumlah epoch, learning rate, optimizer, batch size, dan waktu training yang sama agar tidak ada model yang mendapat keuntungan lebih besar. |
| Environment identik | ✅ | Seluruh eksperimen dijalankan pada laptop dan environment software yang sama (Python, TensorFlow, dan library identik) sehingga performa hardware tidak mempengaruhi hasil secara berbeda. |
| Metrik evaluasi sama | ✅ | Semua model dibandingkan menggunakan Accuracy, Precision, Recall, F1-Score, dan Generalization Error dengan rumus evaluasi yang sama. |

**Ada yang tidak fair?** [ ] Ya / [ ✓ ] Tidak
> Jika ya, bagaimana cara memperbaikinya? Karena seluruh model diuji menggunakan dataset, preprocessing, parameter training, environment, dan metrik evaluasi yang sama, maka desain eksperimen sudah dianggap fair dan tidak memerlukan perbaikan tambahan.

---

## Latihan 3 — Threat Analysis

Identifikasi ancaman validitas untuk desain eksperimen ini.

| Threat Type | Ancaman Spesifik | Mitigasi |
|-------------|-----------------|----------|
| Internal | Model CNN tertentu bisa mendapatkan hasil lebih baik hanya karena faktor random initialization bobot awal, bukan karena regularisasi yang digunakan. | Menggunakan random seed yang sama dan menjalankan eksperimen beberapa kali lalu mengambil rata-rata hasil performa. |
| External | Dataset Heart Disease UCI memiliki jumlah data terbatas sehingga hasil penelitian mungkin tidak dapat digeneralisasi untuk seluruh kondisi medis di dunia nyata | Menyatakan batasan penelitian secara eksplisit dan menyarankan pengujian lanjutan menggunakan dataset rumah sakit yang lebih besar dan beragam. |
| Construct | Accuracy saja bisa menyesatkan jika distribusi kelas tidak seimbang karena model bisa terlihat tinggi performanya meskipun gagal mendeteksi pasien sakit. | Menambahkan metrik Precision, Recall, dan F1-Score agar evaluasi benar benar merepresentasikan kualitas prediksi medis. |
| Conclusion | Jumlah eksperimen terlalu sedikit dapat membuat selisih performa antar model hanya terjadi karena kebetulan statistik. | Melakukan repeated experiment dan menggunakan uji statistik seperti Independent Sample T-Test untuk memastikan perbedaan performa benar benar signifikan. |

**Ancaman mana yang paling sulit dimitigasi?** External validity
**Mengapa?**
> Karena dataset medis publik biasanya terbatas dan tidak selalu mewakili kondisi pasien nyata dari berbagai rumah sakit, usia, maupun latar belakang kesehatan yang berbeda.

---

## Refleksi

> Sebuah paper melaporkan "metode kami mengalahkan semua baseline." Apa 3 pertanyaan pertama yang harus diajukan untuk mengevaluasi klaim ini?

**Jawaban:**
1. Apakah semua baseline diuji menggunakan dataset, preprocessing, dan kondisi eksperimen yang sama?
2. Apakah tuning parameter dilakukan secara adil untuk semua metode, atau hanya metode peneliti yang dioptimasi?
3. Apakah peningkatan performa yang dilaporkan benar benar signifikan secara statistik dan menggunakan metrik evaluasi yang tepat?
