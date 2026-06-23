# WS-09: Implementation & Environment

> **Bab 9 — Implementasi Riset & Kontrol Lingkungan**

---

## Ringkasan Materi

### Implementasi Riset ≠ Coding Biasa

Tujuan implementasi riset bukan membuat software yang berfungsi, melainkan membangun **instrumen pengukuran yang konsisten**. Setiap modul harus di-mapping ke variabel (dari Bab 6), parameter harus config-driven, dan logging aktif dari hari pertama.

### Mengapa reproducibility penting?

Sains dibangun di atas prinsip verifikasi — temuan harus bisa dikonfirmasi oleh peneliti lain. Replicability crisis yang terjadi di banyak paper riset ML/AI disebabkan oleh environment tidak terdokumentasi: orang lain tidak bisa reproduksi, hasil diragukan, kepercayaan terhadap temuan hilang. Prinsip: dokumentasi environment = snapshot kredibilitas riset Anda.

---

## Reproducible Implementation Model


Design → Implementation → Environment Setup → Execution Consistency → Reproducibility → Trustworthy Result


- Design → Implementation: mapping variabel ke modul (CNN, RF, Metrics)
- Implementation → Environment: dependency + hardware + seed
- Environment → Consistency: deterministic execution
- Consistency → Reproducibility: dokumentasi lengkap
- Reproducibility → Trust: hasil bisa direplikasi

---

## Repeatability vs Reproducibility

| Level | Peneliti | Environment | Hasil |
|-------|----------|-------------|-------|
| Repeatability | Sama | Sama | Sama persis |
| Reproducibility | Berbeda | Berbeda (ikuti docs) | Sama/serupa |

---

## Engineering vs Research Perspective

| Aspek | Engineering | Research |
|-------|------------|----------|
| Tujuan | Sistem berjalan | Instrumen eksperimen valid |
| Dependency | Latest version | Version locked |
| Testing | Functional testing | Repeatability test |
| Config | Default | Fully controlled |

---

## Jebakan Kognitif

- Setup dilakukan di akhir → sulit debugging  
- Dependency tidak dikunci → hasil berubah  
- Seed tidak dikontrol → eksperimen tidak valid  
- “Di laptop saya bisa” ≠ valid secara ilmiah  

---

## Dependency Locking

- Gunakan `requirements.txt`
- Gunakan `pip freeze` untuk snapshot environment
- GPU driver juga mempengaruhi hasil ML

---

## Istilah Penting

- **Environment Specification** → seluruh detail sistem  
- **Dependency** → library eksternal  
- **Config-driven** → parameter tidak hardcoded  

---

## Template A.9 — Dokumentasi Setup Eksperimen

```
EXPERIMENT SETUP DOCUMENTATION

Hardware:
CPU : Intel Core i3-1005G1 (2 Core, 4 Thread, 1.20 GHz)
RAM : 8 GB DDR4 (7.74 GB usable)
GPU : NVIDIA GeForce MX330 (2 GB) + Intel UHD Graphics (128 MB)
Storage : 238 GB SSD SAMSUNG MZVLQ256HAJD-00000

Software:
OS : Windows 11 64-bit
Runtime : Python 3.11
Framework : TensorFlow 2.16.1, Scikit-learn 1.6.1

Dependencies:

Library	Version	Sumber	Hash/Checksum
TensorFlow	2.16.1	pip	requirements.txt
Scikit-learn	1.6.1	pip	requirements.txt
Pandas	2.2.3	pip	requirements.txt
NumPy	2.0.2	pip	requirements.txt
Matplotlib	3.10.0	pip	requirements.txt

Konfigurasi:
Config file : config.yaml
Random seed : 42
Hyperparameters : CNN (filters=64, kernel=3x3, dropout=0.5, L2=0.001), RF (n_estimators=100)

Reproducibility Check:
[x] Dependency terdokumentasi (requirements.txt / lock file)
[x] Seed ditetapkan di semua level (Python, NumPy, TensorFlow)
[x] Config di version control
[x] README instruksi reproduksi lengkap
```

## Latihan 1 — Environment Specification
```
Komponen	Spesifikasi
CPU	Intel Core i3-1005G1 (2 Core, 4 Thread, 1.20 GHz)
RAM	8 GB DDR4 (7.74 GB usable)
GPU	NVIDIA GeForce MX330 (2 GB) + Intel UHD Graphics
Storage	238 GB SSD SAMSUNG MZVLQ256HAJD-00000
OS	Windows 11 64-bit
Runtime	Python 3.11
Framework	TensorFlow 2.16.1, Scikit-learn 1.6.1
Random Seed	42
Dependencies (minimal 5)
Library	Version	Alasan Dibutuhkan
TensorFlow	2.16.1	CNN training untuk klasifikasi penyakit jantung
Scikit-learn	1.6.1	Random Forest baseline + evaluasi metrik
Pandas	2.2.3	preprocessing dataset CSV
NumPy	2.0.2	operasi numerik + kontrol seed
Matplotlib	3.10.0	visualisasi loss dan accuracy
```

## Latihan 2 — Repeatability Test Plan
```
Run	Seed	Metrik Utama	Hasil Sama?
1	42	F1-Score	—
2	42	F1-Score	[x] Ya
3	42	F1-Score	[x] Ya
Jika hasil berbeda, kemungkinan penyebab:
GPU (MX330) non-deterministic computation
TensorFlow tidak fully deterministic mode
Background process Windows (update/antivirus)
Cache training model sebelumnya
Checklist kontrol:
 Random seed di semua framework
 Dataset tidak berubah
 Config konsisten
 Tidak ada background process saat eksperimen
```

## Latihan 3 — README Eksperimen
```
Judul Eksperimen: Pengaruh Regularisasi (Dropout & L2) pada CNN terhadap Generalisasi Prediksi Penyakit Jantung
1. Environment

Windows 11 64-bit, Intel Core i3-1005G1, RAM 8GB, NVIDIA MX330, Python 3.11, TensorFlow 2.16.1, Scikit-learn 1.6.1.

2. Installation

pip install -r requirements.txt

3. Data

Heart Disease Dataset (UCI Repository) berisi fitur klinis: usia, tekanan darah, kolesterol, denyut jantung maksimum, dll.

4. Execution

python train.py --config config.yaml

5. Configuration

model: CNN vs Random Forest
dropout: 0.5
l2: 0.001
epochs: 100
batch_size: 32
seed: 42

6. Expected Output
Accuracy, Precision, Recall, F1-score
Confusion Matrix
Training curve (loss & accuracy)
CSV hasil evaluasi per model
Refleksi
```

Level saat ini: [x] Repeatability / [x] Reproducibility / [ ] Belum keduanya

Komponen yang belum terdokumentasi:

- Detail driver GPU MX330 (CUDA/cuDNN jika digunakan)
- Script Docker untuk full portability
- Automation script untuk one-click reproduction
