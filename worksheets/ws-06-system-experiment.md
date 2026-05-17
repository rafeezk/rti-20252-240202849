# WS-06: System-Experiment Mapping

> **Bab 6 — System Design sebagai Experimental Artifact**

---

## Ringkasan Materi

### Sistem = Instrumen Pengujian, Bukan Produk

Seorang engineer bertanya "apakah sistem bekerja?" — seorang peneliti bertanya "apa yang bisa dibuktikan sistem ini?" Sistem dalam riset adalah **artifact** — objek yang sengaja dibuat untuk menguji klaim spesifik.

### System as Experiment Model

```
RQ → Variable → System Component → Experimental Setup → Output
```

Setiap komponen sistem harus bisa ditelusuri ke variabel riset (top-down), dan setiap pengukuran harus menjawab RQ (bottom-up).

### Mapping Variabel ke Komponen

| Tipe Variabel | Peran di Sistem | Contoh |
|---------------|----------------|--------|
| **IV** (Independent) | Modul yang bisa di-toggle/swap | Algoritma A vs B |
| **DV** (Dependent) | Modul pengukuran | Logger, metrics collector |
| **CV** (Control) | Config yang dikunci | Dataset, parameter tetap |

Jika variabel tidak bisa di-map ke komponen apapun → arsitektur perlu didesain ulang.

### 4 Prinsip Desain Eksperimental

| Prinsip | Pertanyaan Kunci |
|---------|-----------------|
| **Traceability** | Komponen ini melayani variabel yang mana? |
| **Modularity** | Bisakah IV diubah tanpa memengaruhi yang lain? |
| **Controllability** | Apakah CV dieksternalisasi ke config file? |
| **Measurability** | Apakah sistem otomatis menghasilkan data yang dibutuhkan? |

### Variable Isolation melalui Arsitektur

- **Modular architecture** — Pisahkan berdasarkan variabel
- **Configuration-driven** — Ubah config (YAML/JSON), bukan code
- **Feature toggles** — On/off flag untuk ablation study

  Contoh config YAML dengan feature toggles:
  ```yaml
  model:
    type: cnn          # IV: ganti "rf" untuk kondisi baseline
  features:
    use_temporal: true  # toggle komponen temporal
    use_normalization: true  # toggle preprocessing
  experiment:
    seed: 42
    runs: 5
  ```
  Dengan pendekatan ini, berbeda kondisi eksperimen = berbeda satu baris config, **tanpa mengubah kode**.

### Research vs Engineering

| Aspek | Engineering | Research |
|-------|------------|----------|
| Tujuan sistem | Memenuhi kebutuhan user | Menguji hipotesis, menghasilkan bukti |
| Arsitektur | Optimasi performa & skalabilitas | Optimasi isolasi variabel & reprodusibilitas |
| Konfigurasi | Sering hardcoded | Dieksternalisasi ke config file |
| Fitur tambahan | Menambah nilai user | Menambah noise jika tidak terkait RQ |

### Istilah Penting

- **Artifact** — Objek yang sengaja dibuat untuk memecahkan masalah atau menguji proposisi
- **Traceability** — Kemampuan menelusuri hubungan RQ → variabel → komponen → output
- **Variable Isolation** — Mengubah hanya satu variabel sambil menahan yang lain konstan
- **Ablation Study** — Menguji kontribusi tiap komponen dengan melepasnya satu per satu
- **Configuration-driven Execution** — Semua parameter di config file, bukan hardcoded

---

## Template A.6 — Mapping RQ ke Arsitektur Sistem

```
SYSTEM-EXPERIMENT MAPPING

Research Question: Apakah metode regularisasi seperti dropout dan L2 regularization pada model CNN dapat meningkatkan kemampuan generalisasi dan F1-score dibandingkan Random Forest pada prediksi penyakit jantung menggunakan dataset medis terbatas?

Variable → Component Mapping:
| Variabel | Tipe | Komponen Sistem | Cara Manipulasi/Pengukuran |
|----------|------|-----------------|---------------------------|
|     Jenis metode regularisasi     | IV   |        Modul training model CNN         |              Mengubah config regularisasi: tanpa regularisasi, dropout, atau L2 regularization             |
|     Performa model     | DV   |        Modul evaluasi & metrics collector         |             Mengukur Accuracy, Precision, Recall, F1-score, dan Generalization Error              |
|     Dataset & parameter training     | CV   |        Dataset loader dan configuration file         |             Menjaga dataset, learning rate, epoch, dan batch size tetap sama pada seluruh eksperimen              |

4 Prinsip Desain:
  [ ✓ ] Traceability — Setiap komponen bisa ditelusuri ke variabel
  [ ✓ ] Variable Isolation — IV bisa diubah tanpa mengubah CV
  [ ✓ ] Measurement Integration — Pengukuran DV built-in
  [ ✓ ] Reproducibility — Setup bisa direkonstruksi

Experimental Setup:
  Input data     : Training & testing menggunakan Heart Disease Dataset dari UCI Machine Learning Repository dengan train-test split 80:20.
  Parameter      : Epoch: 50, Batch size: 32, Learning rate: 0.001, Random seed: 42, Model comparison: CNN + Dropout vs CNN + L2 vs CNN tanpa regularisasi vs Random Forest
  Output format  : Log CSV hasil evaluasi model (Accuracy, Precision, Recall, F1-Score, Generalization Error), confusion matrix, grafik training-validation loss, dan classification report setiap model.
```

---

## Latihan 1 — Variable-to-Component Mapping

Gunakan RQ dan variabel dari WS-05. Petakan ke komponen sistem.

**RQ:** Apakah metode regularisasi seperti dropout dan L2 regularization dapat meningkatkan kemampuan generalisasi dan F1-score model CNN dibandingkan Random Forest pada prediksi penyakit jantung menggunakan dataset medis terbatas?

| Variabel | Tipe | Komponen Sistem | Cara Manipulasi / Pengukuran |
|----------|------|-----------------|---------------------------|
| Jenis regularisasi | IV | Modul CNN training | Mengubah parameter regularisasi pada configuration file |
| Performa model | DV | Metrics collector | Menghitung Accuracy, Recall, Precision, F1-score |
| Dataset & parameter training | CV | Dataset loader & config system | Menjaga dataset dan parameter training tetap sama |

**Apakah semua variabel bisa di-map?** [ ✓ ] Ya / [ ] Tidak
> Jika tidak, komponen apa yang perlu ditambahkan? Tidak perlu penambahan komponen karena seluruh variabel penelitian sudah memiliki modul yang sesuai di dalam sistem eksperimen.

---

## Latihan 2 — 4 Prinsip Desain

Evaluasi desain sistem terhadap 4 prinsip.

| Prinsip | Status | Bukti / Penjelasan |
|---------|--------|-------------------|
| Traceability | ✅ | Setiap modul sistem terhubung langsung dengan variabel penelitian |
| Modularity | ✅ | Metode regularisasi dapat diganti tanpa mengubah modul lain |
| Controllability | ✅ | Seluruh parameter training disimpan di configuration file |
| Measurability | ✅ | Sistem otomatis menghasilkan metrik evaluasi setelah training selesai |

**Prinsip mana yang paling sulit dipenuhi?** Variable Isolation / Controllability
**Strategi untuk mengatasinya:**
> Menggunakan configuration-driven experiment sehingga seluruh parameter seperti epoch, batch size, dan learning rate dikontrol melalui config file, bukan diubah manual di kode program. Selain itu, random seed dibuat tetap agar hasil eksperimen lebih konsisten dan reproducible.
---

## Latihan 3 — Ablation Study Planning

Jika sistem memiliki 3 komponen utama, rencanakan ablation study.

> **Panduan jumlah kondisi:** Untuk 3 komponen (A, B, C), kondisi minimal yang direkomendasikan:
> Full + (-A) + (-B) + (-C) = **4 kondisi dasar**. Jika waktu memungkinkan, tambahkan kombinasi ganda: (-A,-B), (-A,-C), (-B,-C) = **7 kondisi**. Sesuaikan dengan *computational cost* dan tenggat waktu penelitian.

| Kondisi | Komponen A | Komponen B | Komponen C | Hasil yang Diharapkan |
|---------|-----------|-----------|-----------|----------------------|
| Full | ✅ CNN | ✅ Dropout | ✅ L2 Regularization | Performa terbaik — CNN mampu mempelajari pola hubungan antar fitur medis, dropout membantu mengurangi overfitting dengan menonaktifkan neuron secara acak, dan L2 regularization menjaga bobot model tetap stabil sehingga generalization error paling rendah |
| – A | ❌ (ganti RF) | ✅ | ✅ | Penurunan F1-Score karena Random Forest tidak melakukan feature learning otomatis seperti CNN. Model hanya mengandalkan pemisahan berbasis tree sehingga pola kompleks antar fitur medis lebih sulit dipelajari |
| – B | ✅ | ❌ (tanpa dropout) | ✅ | Overfitting meningkat karena seluruh neuron selalu aktif selama training sehingga model lebih mudah menghafal data training dibanding memahami pola umum data pasien |
| – C | ✅ | ✅ | ❌ (tanpa L2 Regularization) | Generalization error meningkat karena bobot model menjadi terlalu besar dan tidak terkontrol. Model cenderung terlalu sensitif terhadap pola tertentu pada data training sehingga performa pada data testing menurun |

**Komponen mana yang diprediksi paling berkontribusi?** Dropout
**Mengapa?**
> Karena dropout membantu mencegah overfitting dengan cara menonaktifkan sebagian neuron secara acak selama proses training. Dengan begitu model tidak terlalu bergantung pada pola tertentu di data training dan kemampuan generalisasi terhadap data baru menjadi lebih baik, terutama pada dataset medis yang ukurannya terbatas.

---

## Refleksi

> Apa risiko jika sistem dibangun seperti produk (monolitik, fitur lengkap) lalu baru dilakukan eksperimen? Mengapa arsitektur modular penting untuk riset?

**Jawaban:**
> Jika sistem dibangun seperti produk monolitik dengan banyak fitur sekaligus, maka eksperimen menjadi sulit dikontrol karena banyak komponen saling terhubung. Akibatnya, peneliti akan kesulitan mengetahui apakah perubahan hasil berasal dari variabel penelitian atau dari fitur lain yang ikut memengaruhi sistem.

Arsitektur modular penting dalam riset karena setiap komponen dapat dipisahkan dan diuji secara independen. Dengan begitu, variabel penelitian lebih mudah diisolasi, eksperimen lebih reproducible, dan peneliti dapat melakukan ablation study untuk melihat kontribusi setiap komponen terhadap hasil akhir.
