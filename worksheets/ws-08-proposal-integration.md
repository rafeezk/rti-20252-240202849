# WS-08: Proposal Integration (UTS)

> **Bab 8 — Proposal & Checkpoint**

---

## Ringkasan Materi

### Proposal = Satu Argumen Utuh

Proposal riset bukan kumpulan bab yang independen. Ia adalah **satu argumen** yang mengalir dari masalah ke rencana solusi. Jika satu koneksi putus, seluruh proposal kehilangan koherensi.

### Integration Map — 6 Koneksi Kritis

```
Problem (Bab 2) → Gap (Bab 3) → RQ & H (Bab 4) → Metrik (Bab 5) → Sistem (Bab 6) → Eksperimen (Bab 7)
```

| Koneksi             | Pertanyaan Verifikasi                                          |
| ------------------- | -------------------------------------------------------------- |
| Problem → Gap       | Apakah gap muncul dari analisis literatur terhadap masalah?    |
| Gap → RQ            | Apakah RQ langsung menjawab gap yang teridentifikasi?          |
| RQ → Metrik         | Apakah setiap variabel di RQ punya metrik terdefinisi?         |
| Metrik → Sistem     | Apakah setiap metrik bisa diukur oleh komponen sistem?         |
| Sistem → Eksperimen | Apakah desain eksperimen menggunakan sistem sebagai instrumen? |

### Koherensi Vertikal + Horizontal

* **Vertikal** — Alur logis atas-ke-bawah (problem → experiment). Setiap section menjawab pertanyaan yang diangkat section sebelumnya dan memunculkan pertanyaan baru.
* **Horizontal** — Konsistensi terminologi (nama variabel di RQ = di hipotesis = di metrik = di desain)

**Operasionalisasi Red Thread** (benang merah):

```
Bab 2 (Problem) → | memperkenalkan masalah X + evidensi |
                          ↓ menimbulkan pertanyaan: "apa akar gap-nya?"
Bab 3 (Gap)     → | menjawab pertanyaan tadi + membuka "lalu apa yang perlu diteliti?" |
                          ↓
Bab 4 (RQ/H)    → | menjawab gap dengan pertanyaan spesifik + prediksi terukur |
                          ↓
Bab 5-7 (Method)→ | menjawab RQ melalui desain eksperimen yang tepat |
```

Jika ada lompatan (section B tidak menjawab pertanyaan section A), red thread putus.

### Jebakan Kognitif

| Jebakan                   | Deskripsi                                                                              |
| ------------------------- | -------------------------------------------------------------------------------------- |
| "Selling" Introduction    | Menulis promosi, bukan menyajikan data dan gap                                         |
| Copy-paste Methodology    | Menyalin deskripsi textbook tanpa menyesuaikan ke RQ                                   |
| Optimistic Timeline       | Meremehkan waktu implementasi; selalu tambah buffer 30-50%                             |
| No Possibility of Failure | Mengimplikasikan hasil pasti sukses — proposal jujur mengakui H₀ mungkin tidak ditolak |

### Struktur Proposal

1. **Pendahuluan** — Latar belakang + problem statement (Bab 1-2)
2. **Tinjauan Pustaka** — Literature review + gap + baseline (Bab 3)
3. **RQ / Kontribusi / Hipotesis** — (Bab 4)
4. **Metodologi** — Metrik + sistem + desain eksperimen (Bab 5-7)
5. **Timeline & Output**

### Istilah Penting

* **Integration Map** — Diagram 6 koneksi kritis antar komponen proposal
* **Vertical Coherence** — Alur logis atas-ke-bawah
* **Horizontal Coherence** — Konsistensi terminologi di semua bagian
* **Checkpoint** — Titik self-assessment sebelum transisi dari desain ke eksekusi

---

## Template A.8 — Integration Checklist

```
PROPOSAL INTEGRATION CHECKLIST

Koneksi Vertikal (Flow Atas-Bawah):
  [x] Problem → Gap: masalah terdokumentasi di literatur
  [x] Gap → RQ: pertanyaan menjawab gap spesifik
  [x] RQ → Hypothesis: hipotesis memprediksi jawaban
  [x] Hypothesis → Metric: metrik mengukur variabel dalam hipotesis
  [x] Metric → System: komponen sistem menghasilkan/mengukur metrik
  [x] System → Experiment: desain eksperimen menggunakan sistem

Koneksi Horizontal (Konsistensi):
  [x] Istilah sama di semua bagian
  [x] Variabel di RQ = variabel di hipotesis = metrik di desain
  [x] Scope tidak berubah dari masalah ke eksperimen

Cognitive Trap Checklist:
  [x] Tidak ada paragraf "promosi" di pendahuluan (hanya data & gap)
  [x] Metodologi disesuaikan ke RQ, bukan copy-paste textbook
  [x] Timeline sudah ditambah buffer 30-50% dari estimasi awal
  [x] Proposal mengakui kemungkinan H0 tidak ditolak (honest uncertainty)
  [x] Tidak ada klaim "pasti berhasil" atau "meningkatkan signifikan"
```

Rubrik Self-Assessment:

| Kriteria    | 1 (Lemah)                     | 2 (Cukup)                               | 3 (Baik)                                    | Skor |
| ----------- | ----------------------------- | --------------------------------------- | ------------------------------------------- | ---- |
| Koherensi   | >2 koneksi vertikal terputus  | 1-2 koneksi lemah                       | Semua 6 koneksi terhubung, red thread jelas | 3    |
| Specificity | Variabel/metrik masih abstrak | Sebagian metrik numerik                 | Semua metrik + threshold + unit jelas       | 3    |
| Feasibility | Timeline >6 bulan             | Timeline 3-6 bulan                      | Timeline 1-3 bulan realistis                | 3    |
| Rigor       | Baseline tidak jelas          | 1-2 baseline dengan justifikasi parsial | 2+ baseline dengan justifikasi lengkap      | 3    |

---

## Latihan 1 — Kompilasi Proposal Mini

Kumpulkan hasil dari WS-02 sampai WS-07 menjadi satu ringkasan proposal.

| Komponen          | Sumber | Isi (1-2 kalimat)                                                                                                                                                                            |
| ----------------- | ------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Problem Statement | WS-02  | Model CNN pada prediksi penyakit jantung rentan mengalami overfitting ketika jumlah data terbatas sehingga kemampuan generalisasi terhadap data baru menjadi rendah.                         |
| Gap               | WS-03  | Belum banyak penelitian yang secara khusus mengevaluasi kontribusi Dropout dan L2 Regularization terhadap peningkatan kemampuan generalisasi CNN pada Heart Disease Dataset berukuran kecil. |
| RQ                | WS-04  | Apakah penerapan Dropout dan L2 Regularization pada model CNN dapat meningkatkan kemampuan generalisasi dan F1-Score dibandingkan CNN tanpa regularisasi dan Random Forest?                  |
| Hipotesis         | WS-04  | H₁: CNN dengan regularisasi menghasilkan F1-Score dan kemampuan generalisasi lebih tinggi dibandingkan CNN tanpa regularisasi maupun Random Forest.                                          |
| Variabel & Metrik | WS-05  | IV = jenis model; DV = F1-Score, akurasi, dan gap train-validation; CV = Heart Disease Dataset, learning rate, epoch, dan batch size yang dikunci.                                           |
| Sistem            | WS-06  | Sistem terdiri dari Dataset Loader, Modul Training CNN, dan Metrics Collector yang dibangun secara modular agar seluruh variabel dapat dipetakan ke komponen sistem.                         |
| Desain Eksperimen | WS-07  | Penelitian menggunakan comparison study dan ablation study dengan dataset, preprocessing, environment, dan metrik evaluasi yang identik pada seluruh kondisi pengujian.                      |

---

## Latihan 2 — Integration Checklist

Verifikasi 6 koneksi kritis. Isi dengan merujuk tabel di Latihan 1.

| Koneksi             | Status | Bukti                                                                                                                          |
| ------------------- | ------ | ------------------------------------------------------------------------------------------------------------------------------ |
| Problem → Gap       | ✅      | Gap muncul dari masalah overfitting dan rendahnya kemampuan generalisasi CNN pada dataset berukuran kecil.                     |
| Gap → RQ            | ✅      | RQ secara langsung mempertanyakan pengaruh regularisasi terhadap peningkatan kemampuan generalisasi dan F1-Score.              |
| RQ → Hypothesis     | ✅      | H₁ memprediksi bahwa CNN dengan regularisasi menghasilkan performa lebih baik dibandingkan baseline.                           |
| Hypothesis → Metric | ✅      | Hipotesis diuji menggunakan F1-Score, akurasi, dan gap train-validation sebagai indikator kemampuan generalisasi.              |
| Metric → System     | ✅      | Metrics Collector menghasilkan confusion matrix, akurasi, F1-Score, serta loss training dan validation secara otomatis.        |
| System → Experiment | ✅      | Sistem modular digunakan sebagai instrumen eksperimen sehingga setiap kondisi dapat direproduksi dan dibandingkan secara adil. |

**Koneksi mana yang paling lemah?** Metric → System

**Bagaimana cara memperkuatnya?**

> Menambahkan dokumentasi lebih rinci mengenai mekanisme perhitungan F1-Score, akurasi, dan gap train-validation pada modul Metrics Collector agar hubungan antara metrik dan sistem menjadi lebih eksplisit.

**Konsistensi horizontal — apakah istilah dan scope konsisten?** [x] Ya

> Jika tidak, di bagian mana terjadi inkonsistensi? —

---

## Latihan 3 — Rubrik Self-Assessment

Evaluasi proposal mini menggunakan rubrik.

| Kriteria    | Skor (1-3) | Justifikasi                                                                                                                                |
| ----------- | ---------- | ------------------------------------------------------------------------------------------------------------------------------------------ |
| Koherensi   | 3          | Seluruh hubungan dari problem hingga eksperimen saling terhubung dan membentuk red thread yang jelas.                                      |
| Specificity | 3          | Variabel, metrik, baseline, threshold, dan metode pengukuran telah didefinisikan secara spesifik.                                          |
| Feasibility | 3          | Dataset tersedia secara publik dan eksperimen dapat diselesaikan dalam rentang waktu 1–3 bulan dengan sumber daya komputasi yang tersedia. |
| Rigor       | 3          | Penelitian memiliki lebih dari satu baseline, fairness checklist, dan analisis ancaman validitas sebelum eksperimen dilakukan.             |

**Skor total:** 12 / 12

**Apakah proposal siap untuk fase eksekusi?** [x] Ya

> Jika belum, apa yang perlu diperbaiki? —

---

## Refleksi

> Dari seluruh proses WS-01 sampai WS-08, bagian mana yang paling mudah dan paling sulit? Mengapa? Apa yang akan dilakukan berbeda jika mengulang dari awal?

**Bagian termudah:** Mendefinisikan variabel penelitian dan metrik evaluasi karena hubungan antara model klasifikasi dan performa dapat diukur secara langsung.

**Bagian tersulit:** Menentukan gap penelitian dan menjaga konsistensi hubungan antara problem, gap, RQ, hipotesis, sistem, dan eksperimen agar tidak terjadi lompatan logis.

**Yang akan dilakukan berbeda:**

> Jika mengulang dari awal, pencarian literatur dan identifikasi gap akan dilakukan lebih sistematis agar ruang lingkup penelitian menjadi lebih spesifik sejak awal.

> Selain itu, desain sistem dan eksperimen akan dirancang bersamaan dengan perumusan hipotesis sehingga keterhubungan antarbagian proposal menjadi lebih kuat dan lebih mudah dipertahankan hingga tahap implementasi.
