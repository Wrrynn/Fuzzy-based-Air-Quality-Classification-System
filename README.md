# Fuzzy Logic System for Comfort Classification
### Mamdani & Sugeno Inference System

## Overview
Project ini mengimplementasikan **sistem fuzzy logic** untuk mengklasifikasikan
**tingkat kenyamanan lingkungan** berdasarkan **suhu (temperature)** dan
**kelembaban (humidity)** menggunakan dua metode inferensi fuzzy:

- **Mamdani Fuzzy Inference System**
- **Sugeno Fuzzy Inference System**

Hasil kedua metode dibandingkan dan dievaluasi menggunakan metrik klasifikasi.

---

## Dataset
Dataset berasal dari file CSV yang telah dibersihkan.

### Fitur:
- `ta` → Temperature (°C)
- `rh` → Relative Humidity (%)

### Label Keluaran:
- Tidak Nyaman
- Cukup Nyaman
- Nyaman

Contoh data:

| ta | rh | mamdani | sugeno | ground_truth |
|----|----|---------|--------|--------------|
| 25 | 55 | 72.3 | 70.1 | Nyaman |

---

## Fuzzy System Design

### 1. Input Variables
**Temperature (ta):**
- Dingin
- Sedang
- Panas

**Humidity (rh):**
- Kering
- Normal
- Lembab

Membership function menggunakan **trapezoidal function**.

---

### 2. Rule Base
Total terdapat **9 fuzzy rules**, contoh:

---

### 3. Mamdani Inference
- Operator AND: min
- Aggregation: max
- Defuzzification: Centroid
- Output: nilai crisp (0–100)

---

### 4. Sugeno Inference
- Output singleton:
  - Tidak Nyaman → 20
  - Cukup Nyaman → 60
  - Nyaman → 90
- Defuzzification: Weighted Average

---

## Output Labeling
Nilai crisp dikonversi menjadi kelas:

- 0 – 39   → Tidak Nyaman
- 40 – 74  → Cukup Nyaman
- 75 – 100 → Nyaman

---

## Evaluation
Evaluasi dilakukan menggunakan:
- Classification Report
- Perbandingan Mamdani vs Sugeno
- Persentase kesesuaian antar metode

---

## Experiment
Sampling acak untuk analisis dan visualisasi:

```python
sample_data = fuzzy_df.sample(n=100, random_state=42)
```

### How to Run
```python
pip install pandas numpy matplotlib scikit-learn
jupyter notebook
```
