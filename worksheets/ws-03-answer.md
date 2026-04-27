# WS-03: Literature Mapping & Gap  
## Bab 3 — Literature Review, Research Gap & Baseline  

---

## 📚 LITERATURE MAPPING

- **Topik**      : Prediksi penyakit menggunakan Machine Learning  
- **Database**   : Google Scholar  
- **Query**      : "machine learning disease prediction overfitting dataset small medical"  
- **Tahun**      : 2020–2024  
- **Hasil awal** : 120 paper → Screening → 5 paper final  

---

## 📊 Literature Matrix (Concept-Centric)

| Study | Tahun | Method | Dataset | Result | Limitation |
|------|------|--------|--------|--------|-----------|
| Rahman et al. | 2023 | CNN | Medical Image Dataset | Acc 91% | Overfitting pada dataset kecil |
| Lee et al. | 2022 | Random Forest | Clinical Data | Acc 85% | Tidak scalable |
| Kumar et al. | 2021 | SVM | Heart Disease Dataset | Acc 82% | Sensitif terhadap parameter |
| Zhang et al. | 2024 | Transformer | Multi-hospital Data | Acc 93% | Resource tinggi |
| Ahmed et al. | 2023 | Logistic Regression | Small dataset | Acc 78% | Akurasi rendah |

---

## 🔍 Pola yang ditemukan
- **Metode dominan**     : CNN dan Machine Learning klasik (RF, SVM)  
- **Dataset umum**       : Dataset medis kecil atau terbatas  
- **Limitasi berulang**  : Overfitting dan kurangnya generalisasi  

---

# ⚠️ GAP IDENTIFICATION

### Gap 1 — Data Gap
- **Deskripsi**    : Sebagian besar penelitian menggunakan dataset kecil atau tidak representatif  
- **Bukti**        : 4 dari 5 paper menggunakan dataset terbatas  
- **Signifikansi** : Mengurangi kemampuan generalisasi model di dunia nyata  

---

### Gap 2 — Method Gap
- **Deskripsi**    : Kurangnya eksplorasi metode regularisasi untuk mengatasi overfitting  
- **Bukti**        : Tidak ada paper yang fokus pada perbandingan metode regularisasi  
- **Signifikansi** : Penting untuk meningkatkan performa model pada data terbatas  

---

## 🎯 Gap utama yang dipilih
**Data Gap + Method Gap (kombinasi)**  

**Alasan:**  
Masalah overfitting tidak hanya berasal dari metode, tetapi juga dari keterbatasan dataset. Kombinasi kedua gap ini memberikan kontribusi yang lebih kuat dan relevan.

---

# ⚙️ BASELINE SELECTION

| Baseline | Relevansi | Representatif | Source |
|----------|----------|--------------|--------|
| Random Forest | Digunakan untuk prediksi penyakit | Umum di banyak paper | Lee et al., 2022 |
| CNN | Digunakan untuk klasifikasi medis | Banyak dipakai sebagai standar | Rahman et al., 2023 |

---

# 🧪 Latihan 1 — Concept-Centric Literature Table

- **Topik riset** : Prediksi penyakit dengan ML  
- **Query pencarian** : "machine learning disease prediction accuracy overfitting"  
- **Database** : Google Scholar  

| # | Study | Tahun | Method | Dataset | Result | Limitasi |
|--|------|------|--------|--------|--------|-----------|
| 1 | Rahman et al. | 2023 | CNN | Medical Image | 91% | Overfitting |
| 2 | Lee et al. | 2022 | RF | Clinical | 85% | Tidak scalable |
| 3 | Kumar et al. | 2021 | SVM | Heart | 82% | Sensitif parameter |
| 4 | Zhang et al. | 2024 | Transformer | Multi-hospital | 93% | Resource tinggi |
| 5 | Ahmed et al. | 2023 | Logistic Regression | Small data | 78% | Akurasi rendah |

---

### 📌 Pola yang terlihat
- **Metode dominan** : CNN & Random Forest  
- **Limitasi berulang** : Overfitting & dataset kecil  

---

# 🔎 Latihan 2 — Gap Identification

| Jenis Gap | Ditemukan? | Gap Statement |
|----------|-----------|--------------|
| Performance Gap | ☑ Ya | Akurasi rendah pada dataset kecil |
| Method Gap | ☑ Ya | Belum ada perbandingan metode regularisasi |
| Data Gap | ☑ Ya | Dataset tidak representatif |
| Context Gap | ☐ Tidak | — |

---

### 🎯 Gap utama yang dipilih
**Method Gap + Data Gap**  

**Mengapa penting:**  
Karena kedua faktor ini secara langsung mempengaruhi performa dan generalisasi model, bukan sekadar karena “belum diteliti”.

---

# 🧩 Latihan 3 — Baseline Selection

| # | Baseline | Mengapa Relevan | Mengapa Representatif | Apakah SOTA? | Sumber |
|--|----------|----------------|----------------------|--------------|--------|
| 1 | Random Forest | Task prediksi penyakit | Digunakan banyak paper | Tidak | Lee et al., 2022 |
| 2 | CNN | Klasifikasi medis | Standar umum | Mendekati | Rahman et al., 2023 |

---

### ❗ Straw Man Check
**Apakah termasuk straw man?** ❌ Tidak  

**Justifikasi:**  
Baseline yang dipilih merupakan metode umum dan relevan, bukan metode lemah yang sengaja dipilih agar terlihat lebih baik.

---

# 💭 Refleksi

Perbedaan antara:
- **"Belum ada yang meneliti"** → klaim lemah tanpa bukti  
- **Research gap valid** → didukung oleh:
  - Pencarian literatur sistematis  
  - Pola dari banyak paper  
  - Limitasi yang konsisten  

### Cara membuktikan gap:
1. Gunakan database terpercaya (Google Scholar, IEEE, dll)  
2. Dokumentasikan query pencarian  
3. Bandingkan minimal beberapa paper  
4. Tunjukkan pola dan kekurangan yang berulang  

➡️ Dengan begitu, gap bukan asumsi, tapi **evidence-based conclusion**  

---
