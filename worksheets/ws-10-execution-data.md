# WS-10: Experiment Execution & Data Collection

> **Bab 10 — Eksekusi Eksperimen & Pengumpulan Data**

---

## Ringkasan Materi

### Experiment Execution Pipeline


Design → Execution Plan → Controlled Execution → Data Collection → Data Logging → Dataset for Analysis


### Multiple Run = Non-Negotiable

Single run **tidak pernah cukup** untuk klaim ilmiah. Minimum 5-10 run per skenario dengan seed berbeda. Multiple run menghasilkan:
- Mean, std, confidence interval
- Distribusi hasil → uji statistik
- Variabilitas → error bar di grafik

### Execution Plan

Setiap eksperimen harus memiliki plan sebelum eksekusi:
- Daftar skenario
- Jumlah run per skenario
- Random seed per run (pre-determined!)
- Urutan eksekusi (randomisasi/counterbalancing)
- Pre-execution checklist

### Data Logging Komprehensif

Setiap run menghasilkan log terstruktur:
1. **Identitas** — Run ID, timestamp, skenario  
2. **Konfigurasi** — Semua parameter, seed, code version  
3. **Hasil** — Semua metrik, output detail  
4. **Metadata** — Waktu eksekusi, resource usage, warning/error  

Format: CSV/JSON/database — **bukan stdout yang di-copy-paste**.

### Engineering vs Research Execution

| Aspek | Engineering | Research |
|-------|------------|----------|
| Run | Sekali (deploy) | Multiple (min 5-10, seed berbeda) |
| Logging | Error log, access log | Semua parameter, metrik, metadata |
| Anomali | Bug → fix → redeploy | Investigasi → dokumentasi → analisis |
| Urutan | Tidak penting | Bisa bias — perlu randomisasi |

### Anomali = Dokumentasi, Bukan Hapus

Run gagal/anomali tidak boleh dihapus tanpa dokumentasi. Bisa jadi:
- **Bug** → fix & re-run (dokumentasikan!)
- **Batas kemampuan metode** → DNF = temuan
- **Data yang bias** jika hanya simpan run "berhasil"

### Jebakan Kognitif

1. "Satu angka cukup" → tanpa distribusi, tidak bisa diuji  
2. "Seed tidak penting" → bahkan algoritma deterministik bisa dipengaruhi library stokastik  
3. "Run gagal langsung hapus" → kehilangan temuan potensial  
4. "Semua run harus hari ini" → thermal throttling, fatigue  

---

## Template A.10 — Execution Plan & Data Log

```
EXECUTION PLAN

Run #	Skenario	Seed	Parameter	Status	Waktu	Output File
1	BERT-base, DS-1	42	lr=2e-5, epoch=10	Done	10:01	run_001.json
2	BERT-base, DS-1	123	lr=2e-5, epoch=10	Done	10:12	run_002.json
3	BERT-base, DS-1	7	lr=2e-5, epoch=10	Done	10:23	run_003.json
4	BERT-base, DS-1	99	lr=2e-5, epoch=10	Done	10:34	run_004.json
5	BERT-base, DS-1	202	lr=2e-5, epoch=10	Done	10:46	run_005.json
6	BERT-base, DS-1	314	lr=2e-5, epoch=10	Done	10:58	run_006.json
7	BERT-base, DS-1	501	lr=2e-5, epoch=10	Done	11:10	run_007.json
8	BERT-base, DS-1	88	lr=2e-5, epoch=10	Done	11:22	run_008.json
9	BERT-base, DS-1	777	lr=2e-5, epoch=10	Done	11:34	run_009.json
10	BERT-base, DS-1	909	lr=2e-5, epoch=10	Done	11:46	run_010.json

Jumlah runs per skenario : 10
Total runs : 10

DATA LOG (per run):
Run ID : run-001
Timestamp : 2026-06-23T10:01:00
Skenario : BERT-base, DS-1
Input : dataset_v1.csv
Output : F1=0.82, Acc=0.85
Anomali : None
Catatan : stable training, no crash
```

---

## Latihan 1 — Execution Plan

| Run # | Skenario | Seed | Parameter Kunci | Status |
|------|----------|------|----------------|--------|
| 1 | BERT-base, DS-1 | 42  | lr=2e-5, epoch=10 | Done |
| 2 | BERT-base, DS-1 | 123 | lr=2e-5, epoch=10 | Done |
| 3 | BERT-base, DS-1 | 7   | lr=2e-5, epoch=10 | Done |
| 4 | BERT-base, DS-1 | 99  | lr=2e-5, epoch=10 | Done |
| 5 | BERT-base, DS-1 | 202 | lr=2e-5, epoch=10 | Done |

**Total skenario:** 1  
**Run per skenario:** 5  
**Total run keseluruhan:** 5  

---

## Latihan 2 — Data Log Terstruktur

**Identitas:**
| Field | Contoh |
|------|--------|
| Run ID | run-001 |
| Timestamp | 2026-06-23T10:01:00 |
| Skenario | BERT-base, DS-1 |
| Status | Completed |

**Konfigurasi:**
| Field | Contoh |
|------|--------|
| Seed | 42 |
| Code version | commit abc1234 |
| Batch size | 32 |
| Learning rate | 2e-5 |
| Epoch | 10 |

**Hasil:**
| Metrik | Tipe Data | Range Valid |
|--------|----------|-------------|
| Accuracy | float | 0.0 – 1.0 |
| Precision | float | 0.0 – 1.0 |
| Recall | float | 0.0 – 1.0 |
| F1-score | float | 0.0 – 1.0 |
| Loss | float | ≥ 0.0 |

**Format output:** ☑ CSV / ☐ JSON / ☐ Database / ☐ Lainnya

---

## Latihan 3 — Anomaly Protocol

| Jenis Anomali | Contoh | Tindakan |
|---------------|--------|----------|
| Run gagal (crash) | OOM pada batch_size=64 | Turunkan batch_size → re-run → log error tetap disimpan |
| Hasil ekstrem | F1 drop ke 0.40 | cek data, seed, dan ulang run → bandingkan distribusi |
| Waktu eksekusi anomali | run 3x lebih lambat | cek CPU/GPU usage + background process |
| Inkonsistensi dengan run lain | variance tinggi | tambah run, audit preprocessing |

**Prinsip:** Detect → Investigate → Document → Decide

---

## Refleksi

**Pengalaman sebelumnya:**
Pernah melaporkan hasil hanya dari 1 kali training model (single run), sehingga tidak ada informasi variasi performa dan rentan bias terhadap seed tertentu.

**Yang akan dilakukan berbeda:**
Menggunakan minimal 5–10 runs dengan seed berbeda, mencatat semua hasil dalam bentuk log terstruktur (CSV/JSON), menghitung mean dan standar deviasi, serta memastikan semua eksperimen dapat direplikasi dengan hasil yang konsisten.
