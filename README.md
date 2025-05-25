# 🏁 F1 Grand Prix – İlk 3 Sıra Tahmini (Top 3 Classification)

## 🎯 Giriş (Amaç)

Bu proje, **Akbank ML Bootcamp 2025** kapsamında gerçekleştirilmiştir.  
Projenin amacı, Formula 1 yarış verilerini kullanarak bir sürücünün bir yarışı **ilk 3’te (podyumda)** bitirip bitirmeyeceğini tahmin eden bir makine öğrenimi modeli geliştirmektir.  
Böylece geçmiş performanslara ve yarış bilgilerine göre podyum tahmini yapılabilmesi hedeflenmiştir.

---

## 📊 Kullanılan Veri Seti

- Kaynak: [Kaggle – F1 Grand Prix DataVault](https://www.kaggle.com/datasets/harshitstark/f1-grandprix-datavault)
- Veri kümesi 13+ CSV dosyası içermektedir.
- Kullanılan dosyalar:
  - `results.csv`
  - `races.csv`
  - `drivers.csv`
  - `constructors.csv`
- Veriler 1950’den günümüze F1 yarışlarını kapsamaktadır.
- `positionOrder` sütunu kullanılarak hedef değişken olan `top3` oluşturulmuştur.

---

## 🧠 Kullanılan Yöntemler ve Modeller

### 🔧 Veri Ön İşleme

- Eksik veriler temizlendi (`\N`, boşluklar)
- Tahmin sonucunu etkileyebilecek sızıntı içeren sütunlar çıkarıldı (`laps`, `points`, `time`, `fastestLapTime` gibi)
- Kategorik değişkenler dönüştürüldü (`pd.get_dummies`)

### 🤖 Modelleme

- **Algoritma:** Random Forest Classifier (`sklearn.ensemble`)
- Eğitim/test verileri ayrıldı (`train_test_split`)
- 5-fold **çapraz doğrulama** uygulandı (`cross_val_score`)
- Modelin karar mekanizması için **özellik önem sıralaması** çıkarıldı
- Model başarısı için **ROC eğrisi** ve **AUC skoru** hesaplandı

---

## ✅ Sonuç ve Gelecek Çalışmalar

### 📈 Başarı Skorları

- Accuracy: `1.00`
- Precision, Recall, F1-score: `1.00`
- Cross-validation ortalaması: `~0.9998`
- AUC skoru: `1.00`

### 📌 Yorum

Model yüksek doğruluk oranı ile tahmin yapmaktadır.  
Bu durum veri setindeki sınıf dağılımı, özellikler arası ayrım gücü ve potansiyel veri sızıntısının etkileriyle açıklanabilir.  
Bu nedenle model değerlendirilirken dikkatli olunmalı, veri çeşitliliği artırılmalıdır.

### 🔮 Gelecek Çalışmalar

- `GridSearchCV` ile hiperparametre optimizasyonu yapılabilir  
- Farklı algoritmalar denenebilir (XGBoost, LightGBM, CatBoost)  
- Web arayüzü (Streamlit) ile tahmin uygulaması geliştirilebilir  
- F1 tarihine göre analizler yapılabilir (örneğin yıl bazında başarı değişimi)

---

## 🔗 Linkler

- 📁 https://www.kaggle.com/code/niisagulec/model-training
- 📁 https://www.kaggle.com/code/niisagulec/f1-top3

