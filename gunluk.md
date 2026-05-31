# Proje Günlüğü
**Öğrenci:** Burak Eren
**Ders:** Yapay Zeka Temelleri

---

## 19.05.2026 — 1. Gün
**Ne yaptım?:** Proje ortamını Jupyter Notebook üzerinde kurdum, veriyi indirdim ve yükledim. Sütunları incelerken Installs sütununda "10,000+" gibi metinsel ifadeler olduğunu gördüm.
 [cite_start]**Kullanılan Kaynak/AI:** Claude [cite: 139]
**Karşılaşılan Sorun & Çözüm:** Python metni sayı olarak göremiyordu. Claude yardımıyla "+", "," gibi karakterleri temizleyip `pd.to_numeric()` ile dönüştürdüm.
**Bir sonraki adım:** Size sütunundaki karmaşık birimleri temizlemek.

---

## 22.05.2026 — 2. Gün
**Ne yaptım?:** Size sütununda yer alan "19M" ve "512k" gibi iki farklı metinsel birimi tek bir standarda getirmek için çalıştım.
**Kullanılan Kaynak/AI:** Claude
**Karşılaşılan Sorun & Çözüm:** Farklı birimler modeli yanıltacaktı. `clean_size` adında özel bir fonksiyon yazarak k olanları 1024'e böldüm ve MB'a çevirip `apply()` ile uyguladım.
**Bir sonraki adım:** Eksik değerlerin yönetimi ve hedef değişkeni tanımlamak.

---

## 23.05.2026 — 3. Gün
**Ne yaptım?:** Verideki eksik değerleri (NaN) temizledim ve projenin sınıflandırma mantığına uygun hedef değişkeni ürettim.
**Kullanılan Kaynak/AI:** Claude
**Karşılaşılan Sorun & Çözüm:** Rating ve Size eksikliklerine farklı yaklaşmalıydım. Rating tahmin hedefi olduğu için eksik satırları sildim (`dropna`). Girdi olan Size sütununu ise veri kaybetmemek için medyan ile doldurdum (`fillna`). Ardından `(df['Rating'] >= 4.0).astype(int)` ile hedef değişkeni oluşturdum.
**Bir sonraki adım:** Veriyi eğitim/test olarak bölmek ve model seçimi yapmak.

---

## 27.05.2026 — 4. Gün
**Ne yaptım?:** Temizlenen verileri eğitim ve test seti olarak ayırdım. Kılavuzda istenen Random Forest ve Logistic Regression modellerini kurdum.
**Kullanılan Kaynak/AI:** Claude [cite: 139]
**Karşılaşılan Sorun & Çözüm:** Modellerin farkını ve neden ikisini seçtiğimizi analiz ettim. Logistic Regression'ın hızlı ve çizgisel çalıştığını, Random Forest'ın ise 100 karar ağacıyla karmaşık ilişkileri çözdüğünü öğrendim.
**Bir sonraki adım:** Özellik ölçeklendirme (Scaling) hatalarını çözmek ve modelleri eğitmek.

---

## 30.05.2026 — 5. Gün
**Ne yaptım?:** Verileri ölçeklendirerek modelleri eğittim ve ilk tahmin sonuç raporlarını çıkardım.
**Kullanılan Kaynak/AI:** Claude [cite: 139]
**Karşılaşılan Sorun & Çözüm:** Installs milyonlardayken Price 0-5 arasındaydı ve bu durum Logistic Regression'ı yanıltıyordu. `StandardScaler` kullanarak verileri aynı ölçeğe çektim. Random Forest ağaç yapısı kullandığı için onu ham veriyle eğittim.
**Bir sonraki adım:** Çıkan başarı metriklerini analiz etmek ve hata matrisini çizdirmek.

---

## 31.05.2026 — 6. Gün
**Ne yaptım?:** Modellerin Accuracy ve F1-Score sonuçlarını kıyasladım, hata matrisini (Confusion Matrix) görselleştirip diske kaydettim ve tüm projeyi GitHub'a yükledim.
**Kullanılan Kaynak/AI:** Claude [cite: 139]
**Karşılaşılan Sorun & Çözüm:** Logistic Regression doğrulukta (%78.76) öndeyken F1-Score'da Random Forest kazandı. Verideki başarılı örnek sayısı çok fazla olduğu için accuracy'nin yanıltıcı olduğunu, F1-Score'un daha güvenilir olduğunu fark ettim. Sunum slaytlarını hazırlayıp projeyi tamamladım.
**Bir sonraki adım:** Ders saatinde 5 dakikalık sözlü savunmayı gerçekleştirmek.