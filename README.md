# 📱 Google Play Store Uygulama Başarı Tahmini

> **Yapay Zeka Temelleri Dersi — Final Projesi**  
> Öğrenci: Burak Eren

---

## 📌 Problem Tanımı

Mobil uygulama pazarı her geçen gün büyümektedir. Bir uygulamanın kullanıcılar tarafından beğenilip beğenilmeyeceğini önceden tahmin etmek; geliştiricilerin zaman ve kaynaklarını doğru yönetmelerine yardımcı olur.

Bu projede, bir uygulamanın **indirilme sayısı, boyutu, fiyatı ve yorum sayısı** gibi parametrelerine bakarak **4.0 ve üzeri puan alıp almayacağını** (yani "başarılı" olup olmayacağını) tahmin eden bir sınıflandırma modeli geliştirilmiştir.

**Hedef Değişken:**
- `1` → Yüksek Puan (Rating ≥ 4.0) — Başarılı
- `0` → Düşük Puan (Rating < 4.0) — Başarısız

---

## 📂 Veri Seti

| Özellik | Bilgi |
|---------|-------|
| Kaynak  | [Kaggle — Google Play Store Apps](https://www.kaggle.com/datasets/lava18/google-play-store-apps) |
| Ham Satır Sayısı | 10.841 |
| Temizlenmiş Satır Sayısı | 9.366 |
| Özellik Sayısı | 13 sütun |

**Temizlenen Sütunlar:**
- `Installs` → `+` ve `,` karakterleri kaldırıldı, sayıya dönüştürüldü
- `Price` → `$` işareti kaldırıldı, sayıya dönüştürüldü
- `Size` → `M` (Megabyte) ve `k` (kilobyte) ifadeleri sayısal MB değerine çevrildi

---

## 🤖 Kullanılan Yöntemler

### 1. Logistic Regression
Doğrusal bir sınıflandırma algoritmasıdır. Temel karşılaştırma modeli olarak kullanıldı. Özellik ölçeklerinin farklılığı nedeniyle `StandardScaler` ile standardizasyon uygulandı.

### 2. Random Forest Classifier
100 karar ağacından oluşan bir topluluk (ensemble) algoritmasıdır. Veri setimizde hem büyük sayılar (indirilme sayısı) hem de küçük ondalıklar (fiyat) bulunduğundan, ölçeklendirme gerektirmeyen ve doğrusal olmayan ilişkileri de modelleyebilen Random Forest tercih edildi.

---

## 📊 Performans Sonuçları

| Model               | Accuracy | F1-Score (Weighted) |
|---------------------|:--------:|:-------------------:|
| Logistic Regression | 0.7876   | 0.6965              |
| **Random Forest**   | **0.7663** | **0.7544**        |

> **Değerlendirme:** Sınıf dengesizliğinin olduğu bu veri setinde F1-Score daha güvenilir bir başarı metriğidir. Random Forest, F1-Score'da belirgin şekilde daha iyi performans göstermiştir.

### Confusion Matrix

![Confusion Matrix](confusion_matrix.png)

### Model Karşılaştırması

![Model Comparison](model_comparison.png)

### Feature Importance

![Feature Importance](feature_importance.png)

---

## 🗂️ Proje Dosya Yapısı

```
PlayStore_YZ_Projesi/
├── PlayStore_Basari_Tahmini.ipynb   # Ana Jupyter Notebook
├── googleplaystore.csv              # Ham veri seti
├── confusion_matrix.png             # Hata matrisi görseli
├── model_comparison.png             # Model karşılaştırma grafiği
├── feature_importance.png           # Özellik önemi grafiği
├── category_distribution.png        # Kategori dağılımı
├── gunluk.md                        # 3 günlük proje günlüğü
└── README.md                        # Bu dosya
```

---

## ⚙️ Kurulum ve Çalıştırma

```bash
# Gerekli kütüphaneleri yükle
pip install pandas numpy matplotlib seaborn scikit-learn jupyter

# Jupyter Notebook'u başlat
jupyter notebook PlayStore_Basari_Tahmini.ipynb
```

---

## 🔍 Proje Sınırlılıkları

- Veri seti 2018 yılına aittir; güncel Play Store verileriyle sonuçlar farklılık gösterebilir.
- Metin tabanlı özellikler (uygulama açıklaması, yorumlar) modele dahil edilmemiştir.
- Sınıf dengesizliği (başarılı: 7.368 vs başarısız: 1.998) model performansını etkilemektedir.

---

## 📚 Kaynaklar

- [Scikit-learn Dokümantasyonu](https://scikit-learn.org/stable/)
- [Pandas Dokümantasyonu](https://pandas.pydata.org/docs/)
- [Kaggle Veri Seti](https://www.kaggle.com/datasets/lava18/google-play-store-apps)
