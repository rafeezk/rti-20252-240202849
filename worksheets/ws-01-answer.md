# WS-01: Distorsi & Paradigma  
## Bab 1 — Research Mindset in IT  

---

## Template A.1 — Research Mindset Self-Assessment

**Nama Peneliti** : raavfy azzaqee  
**Tanggal** : 13 April 2026  

### 1. Ketika membaca klaim "metode X 95% akurat":
- **Pertanyaan pertama saya:**  
  "95% pada kondisi apa? Dataset seperti apa, ukuran data, dan apakah ada pembanding (baseline)?"

- **Data yang dibutuhkan untuk verifikasi:**  
  - Dataset yang digunakan (train/test split)  
  - Confusion matrix (precision, recall, F1-score)  
  - Metode validasi (cross-validation atau tidak)  
  - Perbandingan dengan metode lain  
  - Distribusi data (imbalanced atau tidak)

---

### 2. Posisi paradigma:
- **Pendekatan:**  
  [x] Positivis  
  [ ] Interpretivis  
  [x] Design Science  
  [ ] Mixed  

- **Alasan:**  
  Dalam bidang IT, fenomena dapat diuji secara objektif melalui eksperimen terkontrol. Selain itu, pembuatan sistem (artefak) digunakan sebagai alat untuk menguji hipotesis, bukan sekadar produk akhir.

---

### 3. Identifikasi distorsi:
- **Asumsi tersembunyi:**  
  Dataset dianggap merepresentasikan kondisi dunia nyata.

- **Sumber bias potensial:**  
  - Sampling bias (data tidak beragam)  
  - Overfitting pada data training  
  - Confounding variable yang tidak dikontrol  

- **Langkah mitigasi:**  
  - Menggunakan dataset yang beragam  
  - Cross-validation  
  - Pemisahan data train, validation, dan test  
  - Melaporkan limitasi secara eksplisit  

---

### 4. Komitmen etika:
- **Data yang tidak akan dimanipulasi:**  
  Semua hasil eksperimen, termasuk yang tidak signifikan (negative results)

- **Batasan yang diakui sejak awal:**  
  - Dataset terbatas  
  - Model mungkin tidak dapat digeneralisasi  
  - Eksperimen dilakukan dalam kondisi tertentu saja  

---

## Latihan 1 — Identifikasi Distorsi

**Paper yang dipilih:**

- **Judul:** Deep Learning for Image Classification  
- **Penulis (Tahun):** Smith et al. (2022)  

| Tahap | Apa yang Dilakukan | Potensi Distorsi |
|------|-------------------|------------------|
| Reality → Data | Mengambil dataset gambar dari internet | Dataset tidak representatif |
| Data → Processing | Cleaning dan labeling data | Label bias / human error |
| Processing → Analysis | Training model CNN | Overfitting |
| Analysis → Inference | Model mencapai akurasi tinggi | Tidak diuji pada data baru |
| Inference → Knowledge | Klaim metode lebih unggul | Generalisasi berlebihan |

- **Distorsi paling besar di tahap:**  
  Processing → Analysis  

- **Dua distorsi spesifik:**  
  - Overfitting terhadap dataset  
  - Dataset bias (tidak mencerminkan kondisi nyata)  

---

## Latihan 2 — Analisis Kasus Etika

| Perspektif | Analisis |
|----------|----------|
| Kejujuran ilmiah | Harus melaporkan hasil dengan dan tanpa outlier |
| Transparansi | Menjelaskan alasan penghapusan outlier secara jelas |
| Peer review | Reviewer berhak mempertanyakan keputusan tersebut |

- **Keputusan akhir dan justifikasi:**  
  Outlier tidak boleh dihapus hanya untuk membuat hasil signifikan. Jika dihapus, harus ada alasan metodologis yang kuat, dan kedua hasil tetap dilaporkan untuk menjaga integritas ilmiah.

---

## Latihan 3 — Posisi Paradigma

**Topik riset:**  
Pengaruh penggunaan AI chatbot terhadap efisiensi layanan pelanggan  

| Kriteria | Positivis | Interpretivis | Design Science |
|--------|----------|--------------|----------------|
| Kesesuaian | 4 | 3 | 5 |
| Jenis data | Data kuantitatif (response time, accuracy) | Wawancara pengguna | Prototype chatbot |
| Limitasi | Tidak menangkap pengalaman subjektif | Sulit digeneralisasi | Fokus ke artefak |

- **Paradigma yang dipilih:**  
  Design Science + Positivis  

- **Alasan:**  
  Penelitian melibatkan pembuatan sistem (chatbot) sekaligus pengujian performanya secara objektif.

---

## Refleksi

Sebelum membaca materi ini, saya cenderung menerima klaim seperti "95% akurat" tanpa mempertanyakan konteksnya secara mendalam.  

Setelah memahami rantai distorsi, saya sekarang akan bertanya:
- Dataset apa yang digunakan?  
- Apakah ada bias?  
- Bagaimana metode validasinya?  
- Apakah hasilnya dapat digeneralisasi?  
- Apakah ada kemungkinan HARKing?  

**Kesimpulan:**  
Saya menjadi lebih kritis dan tidak langsung percaya pada angka tanpa memahami proses di baliknya.
