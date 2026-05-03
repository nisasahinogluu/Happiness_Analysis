# Happiness Analysis

Bu proje, **Dünya Mutluluk Raporu (World Happiness Report) 2025** verileri kullanılarak gerçekleştirilen mutluluk skoru tahmini ve kümeleme (clustering) çalışmasıdır. Analiz süreci boyunca **CRISP-DM** metodolojisi takip edilmiştir.

## 🇹🇷 Türkiye Veri Analizi
Raporda spesifik olarak değinilmeyen Türkiye'ye ait tarihsel veriler aşağıda tablolaştırılmıştır. Bu veriler; ekonomik göstergeler, sosyal destek ve özgürlükler gibi temel parametrelerin yıllara göre değişimini içermektedir.

| Yıl | Sıralama | Ülke | Mutluluk Skoru | GSYH (Log) | Sosyal Destek | Sağlıklı Yaşam | Özgürlükler | Cömertlik | Yolsuzluk Algısı | Dystopia + Residual |
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
| **2024** | 94 | Türkiye | 5.262 | 1.582 | 1.444 | 0.626 | 0.244 | 0.040 | 0.104 | 1.223 |
| **2023** | 98 | Türkiye | 4.975 | 1.702 | 1.175 | 0.631 | 0.202 | 0.068 | 0.115 | 1.083 |
| **2022** | 106 | Türkiye | 4.614 | 1.714 | 1.148 | 0.467 | 0.125 | 0.095 | 0.096 | 0.969 |
| **2021** | 112 | Türkiye | 4.744 | 1.707 | 0.865 | 0.702 | 0.209 | 0.087 | 0.115 | 1.059 |
| **2020** | 105 | Türkiye | 4.948 | 1.260 | 0.809 | 0.590 | 0.236 | 0.097 | 0.104 | 1.852 |
| **2019** | 93 | Türkiye | 5.132 | 1.127 | 1.197 | 0.781 | 0.254 | 0.086 | 0.121 | 1.565 |
| **2018** | 79 | Türkiye | 5.373 | - | - | - | - | - | - | - |
| **2017** | 74 | Türkiye | 5.483 | - | - | - | - | - | - | - |
| **2016** | 69 | Türkiye | 5.500 | - | - | - | - | - | - | - |
| **2015** | 78 | Türkiye | 5.389 | - | - | - | - | - | - | - |
| **2014** | 76 | Türkiye | 5.332 | - | - | - | - | - | - | - |
| **2012** | 77 | Türkiye | 5.345 | - | - | - | - | - | - | - |
| **2011** | 78 | Türkiye | 5.234 | - | - | - | - | - | - | - |

---

## 📊 Proje Özeti ve Bulgular
Bu çalışma, ülkelerin mutluluk düzeylerini etkileyen temel faktörleri belirlemek amacıyla veri setinde bulunan son yılın (2024) WHR verilerini analiz etmektedir.

### 🎯 Temel Amaçlar
* Mutluluk skorunu (Life Evaluation) etkileyen en önemli öznitelikleri saptamak.
* Makine öğrenmesi modelleri ile yüksek doğruluklu tahminler üretmek.
* Ülkeleri sosyo-ekonomik benzerliklerine göre kümelemek.

### 📈 Modelleme ve Performans
Tahmin aşamasında modelin karakutu probleminin görece az olması için farklı ağaç algoritmaları karşılaştırılmış ve hiperparametre optimizasyonu sonrası **XGBoost** en başarılı model olarak seçilmiştir.

| Model | RMSE | MAE | R² Score |
|:---|:---:|:---:|:---:|
| Decision Tree (Tuned) | 0.545 | 0.399 | 0.804|
| Random Forest (Tuned) | 0.362 | 0.301 | 0.913|
| **XGBoost (Tuned)** | **0.226** | **0.161** | **0.966**|

> **Önemli Bulgular:** Analizler sonucunda mutluluk ile en güçlü pozitif korelasyona sahip değişkenin **Sosyal Destek** (r=0.82) olduğu tespit edilmiştir.

### 🗺️ Kümeleme Analizi (K-Means)
Ülkeler, mutluluk seviyeleri ve sosyal destek yapılarına göre 4 ana profile ayrılmıştır:
1.  **Zirve Grup (Cluster 2):** Yüksek refah ve en yüksek sosyal destek (örn. İskandinavya).
2.  **Üst-Orta (Cluster 0):** Güçlü sosyal ağlara sahip gelişmekte olan ülkeler.
3.  **Paradoksal Grup (Cluster 3):** Sosyal desteğin düşük olduğu ve artışın mutluluğa her zaman yansımadığı bölgeler.
4.  **Riskli Grup (Cluster 1):** Sosyal desteğin ve mutluluğun en dipte olduğu kırılgan ülkeler (örn. Afganistan).

---

## 🚀 Gelecek Çalışmalar
* **Zaman Serisi Analizi:** Son 10 yılın verileri dahil edilerek mutluluktaki değişim trendlerinin LSTM gibi derin öğrenme modelleriyle incelenmesi planlanmaktadır.

---
### 📚 Kaynakça
* Veri Seti: [World Happiness Report 2025](https://www.worldhappiness.report/ed/2025/#appendices-and-data)
* İlgili Akademik Literatür:
    * Yang, B., & Xie, X. (2025). Analyzing and predicting global happiness index via
    integrated multilayer clustering and machine learning models. PloS one, 20(4),
    e0322287.
    * Zong, Y. (2024). The research on the factors affecting the World Happiness index.
    Theoretical and Natural Science, 41(1), 104-111.
    * Çelik, S., Gökdemir, T. & Çondur, F. Statistical analysis of the world happiness
    index by regions. Qual Quant 59, 4003–4018 (2025). https://doi.org/10.1007/
    s11135-025-02158-y

---
*Not: 2018 yılı ve öncesi için sadece genel skor ve sıralama verileri baz alınmıştır.*

*Not: Detaylı rapor CRISP_DM.docx kodlar ise Happiness_Analaysis.ipynb dosyasında, bulunmaktadır. Ayrıca veri seti WHR25_Data.csv dosyası ile repoda yer almaktadır.*
