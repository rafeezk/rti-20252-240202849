# WS-11: Data Validation & Integrity

> **Bab 11 — Validasi Data & Integritas**

---

## Ringkasan Materi

### Data Trust Model

```
Raw Data → Data Cleaning → Consistency Check → Validation Process → Trusted Data
```

Data mentah belum bisa dipercaya. Harus melewati pipeline validasi sebelum siap untuk analisis statistik.

### Empat Pilar Data Quality

| Pilar | Deskripsi | Contoh Pelanggaran |
|-------|----------|-------------------|
| **Accuracy** | Nilai dalam range masuk akal | Akurasi = 1.5 (di luar [0,1]) |
| **Consistency** | Format seragam di semua run | Run 1: CSV, Run 2: JSON |
| **Completeness** | Tidak ada data hilang dari plan | 97 dari 100 run tercatat |
| **Validity** | Data sesuai desain eksperimen | Parameter baseline tercampur treatment |

### Proses Validasi Progresif

1. Format validation — Tipe file, header, kolom
2. Range validation — Nilai dalam batas logis
3. Consistency validation — Format seragam antar-run
4. Logic validation — Data cocok dengan desain eksperimen

Jika gagal di langkah awal → tidak perlu lanjut.

### Anomaly Detection — 3 Jenis

| Jenis | Deskripsi | Deteksi |
|-------|----------|---------|
| **Statistical outlier** | Nilai di luar distribusi normal | IQR: < Q1-1.5×IQR atau > Q3+1.5×IQR |
| **Contextual anomaly** | Normal absolut, abnormal dalam konteks | Run 1-10: ~91%, Run 11-20: ~88% |
| **Pattern anomaly** | Pola sistematis (bukan random) | Performa menurun berurutan |

**Prinsip:** Detect → Investigate → Document → Decide — **JANGAN langsung hapus.**

### Engineering vs Research Validation

| Aspek | Engineering | Research |
|-------|-----------|---------|
| Tujuan | Data sesuai spesifikasi bisnis | Data layak untuk analisis statistik |
| Missing data | Impute / set default | Investigasi penyebab → dokumentasi |
| Outlier | Bug → fix | Mungkin temuan → investigasi |
| Dokumentasi | Minimal (log error) | Komprehensif (anomali + keputusan) |

### Jebakan Kognitif

1. "Logging otomatis ≠ data benar" → bisa ada bug di logger
2. "Outlier = hapus" → bisa jadi temuan penting
3. "Dataset kecil tidak perlu validasi" → justru lebih rentan
4. "Mean normal = data benar" → [94, 95, 93, 44, 94] → mean 84% terlihat wajar

---

## Template A.11 — Data Validation Checklist

```text
DATA VALIDATION CHECKLIST

Completeness:
  [x] Semua skenario tercakup
  [x] Jumlah run sesuai rencana
  [x] Tidak ada file output hilang
  Missing: 0 dari 10 data points

Format Consistency:
  [x] Semua file format sama (CSV)
  [x] Header konsisten
  [x] Tipe data konsisten (numerik tetap numerik)

Range & Logic:
  [x] Nilai dalam range masuk akal
  [x] Tidak ada waktu negatif
  [x] Metrik 0–100%, tidak di luar range
  Anomali ditemukan: 1 outlier pada Run-04 (Accuracy 78.3%)

Cross-Validation:
  [x] Run identik → hasil mendekati
  [x] Trend konsisten dengan ekspektasi teori

Keputusan:
  [x] Data siap analisis
  [ ] Perlu cleaning
  [ ] Perlu re-run (skenario: CNN + Dropout 0.5)
```

---

## Latihan 1 — Completeness Check

Verifikasi apakah semua data yang direncanakan sudah terkumpul.

| Skenario | Run Direncanakan | Run Tercatat | Missing | Alasan |
|----------|-----------------|-------------|---------|--------|
| CNN + Dropout + L2 | 5 | 5 | 0 | — |
| Random Forest | 5 | 5 | 0 | — |

**Total expected:** **10** | **Total actual:** **10** | **Missing:** **0**

**Keputusan untuk data missing:**

> Tidak terdapat data yang hilang. Seluruh eksperimen berhasil dijalankan sesuai execution plan sehingga seluruh data dapat digunakan pada tahap analisis statistik.

---

## Latihan 2 — Anomaly Investigation

Periksa data Anda untuk anomali. Gunakan metode IQR.

**Dataset sampel:**

| Run | Accuracy (%) |
|-----|-------------|
| 1 | 91.2 |
| 2 | 90.8 |
| 3 | 91.5 |
| 4 | 78.3 |
| 5 | 91.0 |

**Deteksi outlier:**

- Q1 = **90.8**
- Q3 = **91.2**
- IQR = **0.4**
- Batas bawah (Q1 − 1.5×IQR) = **90.2**
- Batas atas (Q3 + 1.5×IQR) = **91.8**
- **Outlier terdeteksi:** Run-4 (Accuracy = 78.3%)

### Investigasi

| Outlier | Nilai | Kemungkinan Penyebab | Keputusan |
|---------|-------|---------------------|-----------|
| Run-4 | 78.3 | Thermal throttling atau proses latar belakang Windows menyebabkan performa training menurun | Re-run setelah cooling interval dan memastikan tidak ada background process aktif |

---

## Latihan 3 — Validation Report

Buat laporan validasi ringkas untuk dataset eksperimen.

**1. Completeness:** **100%** data berhasil terkumpul.

**2. Format:** **[x] Konsisten**

Semua output menggunakan format CSV dengan struktur kolom yang sama.

**3. Range check (anomali):**

Ditemukan satu outlier (Accuracy 78.3%) yang berada di luar batas IQR. Outlier didokumentasikan dan tidak dihapus sebelum dilakukan investigasi.

**4. Logic check:** **[x] Parameter sesuai plan**

Semua parameter eksperimen (seed, learning rate, dropout, L2, epoch, batch size) sesuai dengan execution plan.

### Kesimpulan

**[x] Data siap analisis**

Seluruh data valid dan lengkap. Satu outlier telah didokumentasikan sebagai bagian dari proses validasi sehingga tidak mempengaruhi integritas dataset.

---

## Refleksi

**Apa perbedaan antara "data yang benar" dan "data yang dipercaya"? Mengapa proses validasi formal diperlukan meskipun data dikumpulkan secara otomatis?**

Data yang benar adalah data yang berhasil direkam oleh sistem, sedangkan data yang dipercaya adalah data yang telah melalui proses validasi sehingga terbukti akurat, konsisten, lengkap, dan sesuai dengan desain eksperimen. Walaupun proses pengumpulan dilakukan secara otomatis, kesalahan masih dapat terjadi akibat bug pada program, kegagalan logging, gangguan perangkat keras, atau inkonsistensi konfigurasi. Oleh karena itu, validasi formal diperlukan untuk memastikan bahwa data yang digunakan dalam analisis benar-benar dapat dipertanggungjawabkan secara ilmiah serta menghasilkan kesimpulan penelitian yang valid dan dapat direproduksi.
