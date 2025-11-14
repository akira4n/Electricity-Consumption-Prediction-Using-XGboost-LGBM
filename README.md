# Electricity Consumption Prediction (XGBoost + LightGBM Ensemble)

Repository ini berisi pipeline machine learning untuk memprediksi **electricity consumption** berdasarkan fitur cuaca dan waktu.  
Model utama menggunakan **XGBoost**, **LightGBM**, dan **5-Fold Cross-Validation** dengan ensembel rata-rata.

Project ini dibuat untuk **Seleksi DSA Compfest 17**.

---

## 📊 Dataset

Dataset berasal dari kompetisi:

**Seleksi DSA Compfest 17**  
Dataset terdiri dari:

- `train.csv`
- `test.csv`

Fitur mencakup informasi cuaca (temperature, wind, sunshine, dsb) dan tanggal.

---

## 🧠 Feature Engineering

Proses feature engineering mencakup:

### **📅 Fitur berbasis tanggal**

- `year`, `month`, `day`
- `dayofweek`
- `is_weekend`
- `season`

### **🌡️ Fitur temperatur**

- `temperature_2m_max - temperature_2m_min`
- `apparent_temperature_max - apparent_temperature_min`
- `temp_mean_3d` (rolling mean 3 hari)

### **🌞 Interaksi penting**

- `sunshine_duration × temperature_2m_max`

### **💨 Fitur angin**

- `wind_speed_10m_max × wind_gusts_10m_max`

### **🔠 One-hot encoding**

- `cluster_id`
- `season`

---

## 🤖 Model yang Digunakan

### **1. XGBoost Regressor**

- n_estimators = 2000
- learning_rate = 0.015
- max_depth = 7
- early stopping = 30
- eval_metric = rmse

---

### **2. LightGBM Regressor**

- n_estimators = 5000
- learning_rate = 0.01
- num_leaves = 31
- early stopping = 100

---

### **3. Ensemble**

Prediksi dilakukan dengan:
Prediksi test final = rata-rata prediksi dari seluruh fold.

---

## 🔁 Cross-Validation

Model menggunakan **5-Fold Cross Validation**

Model memberikan hasil validasi rata-rata:

📈 RMSE (5-Fold) ≈ 20.9019

## 📝 Requirements

Lihat requirements.txt
