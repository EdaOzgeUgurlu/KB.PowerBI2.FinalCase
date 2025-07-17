# 📊 Power BI Satış Analizi Projesi

## 🔍 Proje Amacı

Bu projenin amacı, bir satış veri seti üzerinde Power BI kullanarak görsel ve etkileşimli raporlar oluşturmaktır. Proje kapsamında kullanıcıların satış verilerini anlamlandırabilmesi için çeşitli grafikler, kartlar ve sayfa navigasyonları kullanılmıştır. Veriler hafta içi/hafta sonu, saatlik ve bölgesel gibi farklı bakış açılarından analiz edilmiştir.

## 🗂️ Kullanılan Veriler

Veri setinde yer alan başlıca sütunlar:

- `Order ID`: Her satışa ait benzersiz kimlik numarası.
- `Date`: Satışın gerçekleştiği tarih.
- `Time`: Satışın gerçekleştiği saat.
- `Region`: Satışın yapıldığı bölge.
- `Amount`: Satış tutarı (ciro bilgisi).
- `Product`: Satılan ürün bilgisi.

---

## 🧱 Sayfa Yapısı

Power BI raporu 4 sayfadan oluşmaktadır:

### 1. Giriş Sayfası

Kullanıcının diğer raporlara yönlendirilmesini sağlayan sade bir navigasyon sayfasıdır. 3 perspektife göre butonlar yerleştirilmiştir:

- Özet Rapor
- Hafta Tipi Analizi
- Bölge ve Saat Bazlı Analiz

---

### 2. Özet Sayfa

- Toplam satış adedi, toplam ciro gibi temel ölçümler kartlarla sunulmuştur.
- Genel performansı hızlıca görmeye yarar.
- Tarih slicer (filtreleme) ile dinamik değişen görseller mevcuttur.

---

### 3. Hafta Tipi Analizi Sayfası

Bu sayfada satışların hafta içi ve hafta sonu dağılımı analiz edilmiştir.

#### 📌 Hafta Tipi Kolonu Oluşturma

Power BI'da yeni bir sütun oluşturularak satışın hafta içi mi yoksa hafta sonu mu yapıldığı belirlenmiştir:

```DAX
HaftaTipi = 
VAR gun = WEEKDAY('Sales'[Date],2)
RETURN IF(gun >=6, "Hafta Sonu", "Hafta İçi")
---
## 📊 Kullanılan Grafik

### ✅ Yığılmış Sütun Grafiği (Stacked Column Chart) Kullanımı

- **Grafik Tipi:** Yığılmış Sütun Grafiği  
- **X Ekseni:** `HaftaTipi`  
- **Y Ekseni:** `Amount (Satış Tutarı)`  
- **Değerler:** Toplam Satış Tutarı  

📌 Bu grafik ile kullanıcılar **hafta sonu ve hafta içi arasındaki satış farkını** net şekilde görebilmektedir.

---

## 📍 4. Bölge ve Saat Analizi Sayfası

### 🧭 Bölgelere Göre Satış Adedi

- **Grafik Tipi:** Sütun Grafiği (Clustered Column Chart)  
- **X Ekseni:** `Region`  
- **Y Ekseni:** Satış Sayısı (`COUNT of Order ID`)  

---

### ⏰ Saatlik Satış Tutarı Analizi

#### 🕒 Saat Kolonu Oluşturma

Power BI'da yeni bir sütun oluşturarak saat bilgisi çıkarılmıştır:

```DAX
Saat = HOUR('Sales'[Time])


## 📊 Grafik Tipi: Çizgi Grafik (Line Chart)

- **X Ekseni:** Saat  
- **Y Ekseni:** Amount (Toplam Satış Tutarı)

### 📌 Açıklama
Bu grafik sayesinde satışların gün içindeki saatlik dağılımı incelenebilir.

---

## 🧾 Kullanılan Ölçüler (Measures)

### 1️⃣ Toplam Satış Tutarı
```DAX
ToplamCiro = SUM('Sales'[Amount])


2️⃣ Toplam Satış Adedi
DAX
Kopyala
Düzenle
ToplamAdet = COUNT('Sales'[Order ID])
3️⃣ Ortalama Satış
DAX
Kopyala
Düzenle
OrtalamaSatis = AVERAGE('Sales'[Amount])


## 🎨 Tasarım Notları

- Renk uyumu, sade ve okunabilir tema tercih edilmiştir.  
- Her görsel için başlıklar eklenmiştir.  
- Navigasyon için butonlar kullanılmıştır.  
- Sayfa filtreleriyle kullanıcı etkileşimi artırılmıştır.

---

## 🚀 Sonuç

Bu proje ile satış verileri çok yönlü analiz edilmiştir.  
Kullanıcılar farklı bakış açılarından veriyi inceleyebilir ve karar alma süreçlerinde veriye dayalı içgörüler elde edebilir.  

Power BI’ın güçlü görselleştirme ve etkileşim özellikleri sayesinde veriler anlaşılır ve dikkat çekici hale getirilmiştir.

---

## 📁 Dosya Yapısı

- `.pbix` uzantılı Power BI dosyası  
- `README.md` dosyası  
- Gerekirse örnek veri seti (`.csv` formatında)

---
