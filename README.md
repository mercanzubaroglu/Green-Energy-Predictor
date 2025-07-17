# 🌞 Green Energy Predictor / Yeşil Enerji Tahmincisi

Bu proje, güneş enerjisi üretimini etkileyen çevresel faktörleri analiz ederek, **AC güç çıkışını tahmin eden bir makine öğrenmesi modeli** geliştirmeyi amaçlamaktadır.  
This project aims to develop a **machine learning model that predicts AC power output** by analyzing environmental factors affecting solar energy production.

Güneş paneli verimliliği, özellikle ortam sıcaklığı, panel sıcaklığı ve güneş ışınımı gibi değişkenlerden etkilenir.  
Solar panel efficiency is especially affected by variables like ambient temperature, panel temperature, and solar irradiation.

---

## 🎯 Proje Amacı / Project Objective

Güneş enerji santralinde yer alan üretim ve hava durumu verilerini birleştirerek:

- Hangi çevresel faktörlerin AC güç üretimi üzerinde daha etkili olduğunu görmek  
- Geliştirilen makine öğrenmesi modeli ile güç çıkışını önceden tahmin etmek  
- Bu modeli enerji verimliliği artırımı için potansiyel bir karar destek sistemi olarak kullanmak  

---

By combining production and weather data from a solar power plant:

- Identify which environmental factors impact AC power output most  
- Forecast future power output using a trained machine learning model  
- Use the model as a decision support tool to improve energy efficiency  

---

## 📁 Veri Seti / Dataset

Veri, Kaggle'dan alınmıştır:  
📎 [Solar Power Generation Data (Kaggle)](https://www.kaggle.com/datasets/anikannal/solar-power-generation-data)

### Veri Seti Açıklaması / Dataset Description

🔹 `Plant_1_Generation_Data.csv`  
- Panel bazlı üretim verileri: DC Power, AC Power, günlük ve toplam verim  
- Panel-level generation data: DC/AC Power, daily and total yield

🔹 `Plant_1_Weather_Sensor_Data.csv`  
- Ortam sıcaklığı, modül sıcaklığı ve ışınım ölçümleri  
- Ambient temperature, module temperature, and irradiation readings

> Bu iki veri, zaman damgası (`DATE_TIME`) üzerinden birleştirilmiştir.  
> These two datasets were merged using the `DATE_TIME` column.

---

## 📊 Görselleştirmeler / Visualizations

### 🔸 Zaman Serisi Grafikleri / Time Series Plots

Güneş ışınımı, sıcaklıklar ve güç üretiminin zamana göre değişimi incelenmiştir.  
Trends in irradiation, temperatures, and power generation over time are explored.

### 🔸 Öznitelik Önemi / Feature Importance

Modelin tahminlerde hangi değişkenlere daha çok ağırlık verdiği görselleştirilmiştir.  
The importance of each feature in the model’s predictions is visualized.

---

## 🧪 Kullanılan Model / Model Used

- **Random Forest Regressor** kullanılmıştır.  
- **Why?** Decision-tree-based models handle non-linear relationships well and provide feature importance analysis.

### 🎯 Girdi Özellikleri / Input Features:

- `AMBIENT_TEMPERATURE`  
- `MODULE_TEMPERATURE`  
- `IRRADIATION`  
- `DAILY_YIELD`  
- `TOTAL_YIELD`

### 🎯 Hedef / Target:
- `AC_POWER`

---

## 📈 Model Performansı / Model Performance

| Metrik / Metric              | Sonuç / Result |
|-----------------------------|----------------|
| MAE (Mean Absolute Error)   | 14.36 kW        |
| RMSE (Root Mean Squared Error) | 37.52 kW     |
| R² Skoru / R² Score         | 0.9909         |

✅ Model, yüksek doğrulukla AC güç çıkışını tahmin etmektedir.  
✅ The model predicts AC power output with high accuracy.

---

## 🔍 Örnek Tahminler / Sample Predictions

| Örnek / Sample | AMBIENT_TEMP | MODULE_TEMP | IRRADIATION | DAILY_YIELD | TOTAL_YIELD | 🔮 Tahmin / Prediction (kW) | ✅ Gerçek / Actual (kW) |
|----------------|--------------|-------------|-------------|-------------|-------------|-----------------------------|-------------------------|
| 1              | 23.12°C      | 20.88°C     | 0.000       | 7836        | 7263053     | 0.00                        | 0.00                    |
| 2              | 28.20°C      | 48.01°C     | 0.813       | 2131        | 7016049     | 1050.75                     | 976.24                  |
| 3              | 24.03°C      | 24.98°C     | 0.172       | 51          | 7123578     | 242.43                      | 240.07                  |

---
