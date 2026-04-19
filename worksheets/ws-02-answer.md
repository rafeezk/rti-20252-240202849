# WS-02: Problem Statement  
## Bab 2 — Problem Formulation & System Context  

---

## 📌 Template A.2 — Problem Statement Builder  

### Domain & Konteks
- **Domain**  : Machine Learning / Sistem Prediksi  
- **Konteks** : Aplikasi prediksi penyakit berbasis data medis pada perangkat dengan resource terbatas  

---

### System Context
- **Input**       : Data pasien (gejala, riwayat medis, hasil lab)  
- **Process**     : Pemrosesan data dan prediksi menggunakan algoritma machine learning  
- **Output**      : Hasil prediksi penyakit  
- **Outcome**     : Membantu diagnosis lebih cepat dan akurat  
- **Constraints** : Keterbatasan RAM (<64KB), kualitas dataset, latency  
- **Stakeholders**: Dokter, pasien, pengembang sistem, institusi kesehatan  

---

### Fenomena → Problem
- **Fenomena yang diamati** :  
  Banyak sistem prediksi penyakit mengklaim akurasi tinggi  

- **Gejala (symptom) yang terukur** :  
  Performa model menurun ketika digunakan pada data baru  

- **Masalah yang didiagnosis (root cause)** :  
  Overfitting dan dataset tidak representatif  

- **Masalah riset (researchable)** :  
  Belum ada evaluasi komparatif terhadap metode regularisasi untuk mengurangi overfitting pada dataset medis terbatas  

- **Variabel yang terukur** :  
  Akurasi, Precision, Recall, F1-Score, Generalization Error  

---

### ✅ Problem Quality Check
- [x] Clarity  
- [x] Measurability  
- [x] Relevance  
- [x] Testability  
- [x] Impact  

---

### 🧠 Problem Statement
Banyak model machine learning dalam prediksi penyakit menunjukkan akurasi tinggi pada data pelatihan, namun mengalami penurunan performa saat diterapkan pada data baru akibat overfitting dan keterbatasan representasi dataset. Hingga saat ini, belum terdapat evaluasi komparatif yang sistematis terhadap efektivitas berbagai metode regularisasi dalam meningkatkan generalisasi model pada dataset medis berukuran terbatas, sehingga diperlukan penelitian untuk mengukur dan membandingkan performa metode tersebut menggunakan metrik kuantitatif seperti akurasi, precision, recall, dan F1-score.

---

# 🧪 Latihan 1 — Dari Topik ke Masalah Riset

**Topik awal:**  
Prediksi penyakit menggunakan machine learning  

| Tahap | Hasil |
|------|------|
| Reality | Sistem prediksi penyakit sering tidak akurat pada data baru |
| Observed Issue (Symptom) | Akurasi turun dari 95% ke 75% pada data testing |
| Diagnosed Problem (Root Cause) | Overfitting dan dataset tidak representatif |
| Researchable Problem | Kurangnya evaluasi metode untuk mengurangi overfitting |
| Measurable Variable | Akurasi, F1-score, Generalization Error |

- **Solution-first thinking?** : ❌ Tidak  

---

# ⚙️ Latihan 2 — System Context Decomposition

| Komponen | Deskripsi |
|--------|----------|
| Input | Data pasien |
| Process | Model machine learning |
| Output | Prediksi penyakit |
| Outcome | Diagnosis lebih cepat |
| Constraints | Dataset kecil, resource terbatas |
| Stakeholders | Dokter, pasien, developer |

**Komponen paling relevan:**  
➡️ Process (model machine learning)  

---

# 📊 Latihan 3 — Problem Quality Check

| Kriteria | Skor (1–5) | Justifikasi |
|--------|-----------|-----------|
| Clarity | 5 | Masalah jelas dan spesifik |
| Measurability | 5 | Menggunakan metrik kuantitatif |
| Relevance | 5 | Penting dalam domain kesehatan |
| Testability | 4 | Dapat diuji melalui eksperimen |
| Impact | 5 | Berdampak pada akurasi diagnosis |

**Skor Total:** ⭐ 24 / 25  

---

### 🧾 Final Problem Statement
Model machine learning dalam prediksi penyakit sering mengalami penurunan performa pada data baru akibat overfitting dan keterbatasan dataset, meskipun menunjukkan akurasi tinggi pada data pelatihan. Kurangnya evaluasi komparatif terhadap metode regularisasi menyebabkan belum jelasnya pendekatan terbaik untuk meningkatkan generalisasi model pada kondisi dataset terbatas, sehingga penelitian ini bertujuan mengukur dan membandingkan performa berbagai metode menggunakan metrik kuantitatif seperti akurasi dan F1-score.

---

# 💭 Refleksi

Masalah dalam coding biasanya bersifat **praktis**, seperti bug atau error yang harus segera diperbaiki agar sistem berjalan.

Sedangkan masalah riset bersifat **konseptual**, yaitu memahami dan membuktikan suatu fenomena.

### Perbedaan utama:
- **Engineering** → solve problem  
- **Research** → understand & prove  

Dalam riset:
- Tidak langsung ke solusi  
- Harus measurable  
- Harus bisa diuji (falsifiable)  

---
