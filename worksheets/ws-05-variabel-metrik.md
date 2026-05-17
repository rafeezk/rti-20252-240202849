# WS-05: Variabel & Metrik

> **Bab 5 — Metric, Measurement & Data**

---

## Ringkasan Materi

### Measurement Alignment Model

Setiap pengukuran yang valid harus bisa ditelusuri melalui rantai ini tanpa lompatan logis:

```
Problem → Concept → Variable → Metric → Data → Result
```

### Operationalization = Keputusan Desain

Menerjemahkan konsep abstrak menjadi variabel terukur bukan proses mekanis. "Code quality" yang diukur via SonarQube code smells membawa asumsi implisit. Setiap operasionalisasi harus didokumentasikan dan dijustifikasi.

### Empat Tipe Data (NOIR)

| Tipe | Ciri | Contoh | Operasi Valid |
|------|------|--------|---------------|
| **Nominal** | Kategori, tanpa urutan | Jenis algoritma (RF, SVM, CNN) | Modus, chi-square |
| **Ordinal** | Urutan, interval tidak sama | Skala Likert (1-5) | Median, Spearman |
| **Interval** | Jarak bermakna, tanpa nol absolut | Suhu Celsius | Mean, Pearson, t-test |
| **Ratio** | Jarak bermakna + nol absolut | Waktu eksekusi (ms) | Semua operasi |

Tipe data menentukan uji statistik yang valid. Kebanyakan metrik performa TI = ratio; persepsi pengguna = ordinal.

### Kriteria Pemilihan Metrik

- **Representative** — Mewakili konsep yang diteliti
- **Sensitive** — Cukup peka menangkap perbedaan bermakna (hindari ceiling effect)
- **Feasible** — Bisa dikumpulkan dalam batasan waktu dan biaya

### Pre-registration

Metrik harus ditentukan **sebelum** eksperimen. Memilih metrik setelah melihat data = **p-hacking**. Metrik tambahan yang ditemukan kemudian dilaporkan sebagai *exploratory*, bukan *confirmatory*.

### Primary vs Secondary Metric

- **Primary Metric** — Langsung terikat ke hipotesis, menentukan kesimpulan
- **Secondary Metric** — Pendukung, dilaporkan di samping primary; statusnya suplementer

### Research vs Engineering

| Aspek | Engineering | Research |
|-------|------------|----------|
| Pemilihan metrik | Berdasarkan kebiasaan/tool yang ada | Berdasarkan construct validity |
| Anomali | Dihapus untuk laporan bersih | Diinvestigasi — bisa jadi temuan |
| Kapan dipilih | Setelah sistem jadi (monitoring) | Sebelum eksperimen (by design) |

### Istilah Penting

- **Operationalization** — Transformasi konsep abstrak menjadi variabel terukur
- **Construct Validity** — Sejauh mana pengukuran benar-benar mengukur konsep yang dimaksud
- **Measurement Scale** — Klasifikasi data (NOIR) yang menentukan analisis valid
- **Multi-metric Evaluation** — Menggunakan beberapa metrik untuk menangkap konsep kompleks

---

## Template A.5 — Definisi Variabel, Metrik & Justifikasi

```
VARIABLE & METRIC DEFINITION

Research Question: Apakah metode regularisasi seperti dropout dan L2 regularization pada model CNN dapat meningkatkan kemampuan generalisasi dan F1-score dibandingkan Random Forest pada prediksi penyakit jantung menggunakan dataset medis terbatas?

| Variabel | Tipe | Konsep | Metrik | Skala | Satuan | Cara Mengukur | Justifikasi |
|----------|------|--------|--------|-------|--------|---------------|-------------|
|     Jenis metode regularisasi     | IV   |    Teknik untuk mengurangi overfitting pada model CNN    |    Tanpa regularisasi, Dropout, L2 Regularization    |   Nominal   |    -    |        Membandingkan model berdasarkan metode regularisasi yang diterapkan       |       Mewakili perlakuan utama yang diuji dalam eksperimen      |
|     Performa model prediksi penyakit jantung     | DV   |    Kemampuan model dalam memprediksi penyakit jantung dan melakukan generalisasi    |    Accuracy, Precision, Recall, F1-score, Generalization Error    |   Ratio    |    %    |       Menghitung hasil prediksi model pada data testing        |       F1-score dan generalization error mampu menggambarkan performa model secara lebih lengkap dibanding hanya accuracy      |
|     Dataset dan parameter training     | CV   |    Faktor yang dijaga tetap agar eksperimen adil    |    Dataset, learning rate, epoch, batch size    |   Nominal    |    -    |       Menetapkan parameter yang sama pada seluruh eksperimen        |      Menghindari bias akibat perbedaan konfigurasi training       |

Alignment Check:
  RQ → Concept → Variable → Metric → Data → Result
  [ x ] Setiap langkah terdokumentasi
  [ x ] Tidak ada "lompatan logis"
  [ x ] Metrik mengukur apa yang dimaksud (construct validity)
```

---

## Latihan 1 — Operationalization Chain

Gunakan RQ dari WS-04. Definisikan variabel dan metriknya.

**RQ:** Apakah metode regularisasi seperti dropout dan L2 regularization dapat meningkatkan kemampuan generalisasi dan F1-score model CNN dibandingkan Random Forest pada prediksi penyakit jantung menggunakan dataset medis terbatas?

| Variabel | Tipe | Konsep Abstrak | Metrik Konkret | Skala (NOIR) | Satuan |
|----------|------|---------------|----------------|-------------|--------|
| Jenis regularisasi | IV | Teknik mengurangi overfitting | Dropout, L2 Regularization | Nominal | — |
| Performa model | DV | Kemampuan model melakukan prediksi dan generalisasi | Accuracy, Precision, Recall, F1-score | Ratio | % |
| Parameter training & dataset | CV | Faktor kontrol eksperimen | Epoch, learning rate, batch size, dataset | Nominal | - |

**Apakah ada lompatan logis dalam rantai?** [ ] Ya / [ x ] Tidak
> Jika ya, di mana? Tidak ada, karena seluruh konsep abstrak sudah diterjemahkan menjadi variabel dan metrik yang dapat diukur secara langsung melalui eksperimen machine learning.

---

## Latihan 2 — Evaluasi Metrik

Evaluasi metrik DV yang dipilih di Latihan 1 menggunakan 3 kriteria.

| Kriteria | Skor (1-5) | Justifikasi |
|----------|-----------|-------------|
| Representative | 5 | F1-score mampu mewakili keseimbangan precision dan recall sehingga cocok untuk dataset medis yang tidak seimbang |
| Sensitive | 4 | F1-score cukup sensitif untuk menangkap perubahan performa model akibat regularisasi |
| Feasible | 5 | Perhitungan F1-score dapat dilakukan langsung menggunakan library machine learning seperti Scikit-learn |

**Apakah perlu secondary metric?** [ x ] Ya / [ ] Tidak
> Jika ya, apa dan mengapa? Secondary metric yang digunakan adalah Accuracy & Generalization Error. Accuracy digunakan sebagai gambaran umum performa model, sedangkan generalization error digunakan untuk melihat apakah model mengalami overfitting atau tidak.
**Contoh kasus ceiling effect untuk metrik ini:**
> Jika seluruh model menghasilkan accuracy di atas 99%, maka accuracy menjadi kurang sensitif untuk membedakan performa antar model. Dalam kondisi ini, F1-score dan generalization error lebih penting digunakan karena dapat menangkap perbedaan kecil yang tidak terlihat dari accuracy saj

---

## Latihan 3 — Data Quality Check

Bayangkan data yang akan dikumpulkan dari eksperimen. Evaluasi 4 dimensi kualitas data.

| Dimensi | Pertanyaan | Jawaban | Strategi Mitigasi |
|---------|-----------|---------|------------------|
| Completeness | *Apakah semua data point terkumpul?* | Belum tentu 100% Karena dataset medis yang digunakan bisa saja memiliki missing value atau data pasien yang tidak lengkap, misalnya hasil lab yang kosong atau atribut pasien yang hilang. Selain itu, proses preprocessing juga berpotensi membuang sebagian data yang dianggap tidak valid. | Melakukan pengecekan missing value sebelum training model. Jika jumlah data hilang sedikit maka dilakukan imputasi data, sedangkan jika terlalu banyak maka data tersebut dihapus agar tidak merusak kualitas training model. |
| Consistency | *Apakah ada kontradiksi internal?* | Bisa saja terjadi Contohnya, ada data pasien dengan umur sangat muda tetapi tercatat memiliki indikator penyakit yang tidak masuk akal, atau format data antar atribut tidak konsisten. | Melakukan normalisasi dan validasi dataset sebelum training. Seluruh atribut dicek ulang agar memiliki format yang sama dan tidak ada nilai yang bertentangan secara logika medis. |
| Validity | *Apakah benar-benar mengukur yang dimaksud?* | Ya F1-score, precision, recall, dan generalization error merupakan metrik yang valid untuk mengukur performa model prediksi penyakit, terutama pada dataset medis yang tidak seimbang (imbalanced dataset). | Menggunakan dataset medis terpercaya dari UCI Machine Learning Repository dan melakukan evaluasi menggunakan data testing terpisah agar hasil benar benar mengukur kemampuan generalisasi model, bukan hanya kemampuan menghafal data training. |
| Representativeness | *Apakah sampel mewakili populasi target?* | Belum sepenuhnya Karena dataset medis yang digunakan mungkin hanya berasal dari kelompok pasien atau rumah sakit tertentu sehingga belum tentu mewakili seluruh populasi pasien di dunia nyata. | Menggunakan dataset dengan jumlah sampel yang cukup beragam serta melaporkan keterbatasan penelitian secara eksplisit agar hasil penelitian tidak digeneralisasi secara berlebihan. |

---

## Refleksi

> Mengapa memilih metrik setelah melihat data dianggap p-hacking? Apa bedanya dengan eksplorasi data yang sah?

**Jawaban:**
> Memilih metrik setelah melihat hasil data dianggap p-hacking karena peneliti bisa memilih metrik yang paling menguntungkan agar hasil penelitian terlihat berhasil. Hal ini membuat penelitian menjadi bias dan mengurangi validitas hasil.

Contohnya, model mungkin memiliki accuracy tinggi tetapi recall rendah dalam mendeteksi pasien sakit. Jika hanya accuracy yang dilaporkan, maka hasil penelitian menjadi menyesatkan.

Berbeda dengan itu, eksplorasi data yang sah dilakukan untuk memahami pola atau anomali setelah eksperimen selesai. Namun hasil eksplorasi tidak boleh dijadikan bukti utama hipotesis jika tidak direncanakan sejak awal.

Dari materi ini saya memahami bahwa metrik utama seperti F1-score dan generalization error harus ditentukan sebelum eksperimen dimulai agar penelitian tetap objektif, valid, dan tidak bias.
