# 🛒 Power BI Satış Verisi Analizi Projesi
Proje google drive linkinden de çalıştırabilirsiniz 
https://drive.google.com/drive/u/0/folders/1boYmJwK6vFly-HD9CK32QTmOOOjA3GyB

Bu proje, satış verilerini Power BI kullanarak analiz etmek, anlamlı içgörüler elde etmek ve kullanıcı dostu görselleştirmeler ile sunmak amacıyla hazırlanmıştır. Çalışma kapsamında çeşitli grafikler, kart görselleri ve filtreler kullanılmış; veri hazırlama sürecinden görsel raporlamaya kadar olan tüm adımlar detaylandırılmıştır.

## 🎯 Projenin Amacı

Bu çalışmanın temel amacı, saatlik, günlük ve haftalık bazda satış verilerini analiz ederek;
- Satış performansını ölçmek,
- Kullanıcıların farklı zaman dilimlerine göre eğilimlerini belirlemek,
- Karar destek süreçlerine katkı sunmak,
- Görsel, anlaşılır ve interaktif raporlar oluşturmaktır.

## 🧩 Kullanılan Teknolojiler ve Araçlar

| Teknoloji / Araç | Açıklama |
|------------------|----------|
| **Power BI Desktop** | Veri modelleme, DAX kullanımı ve görselleştirme için |
| **Microsoft Excel / CSV** | Ham veri dosyaları için |
| **DAX (Data Analysis Expressions)** | Hesaplanmış sütunlar ve ölçüler (measures) oluşturmak için |
| **GitHub** | Projeyi paylaşmak ve versiyon kontrolü amacıyla |
| **Google Drive** _(isteğe bağlı)_ | Büyük dosya paylaşımı için alternatif platform |

## 📁 Dosya Yapısı

```bash
📦 SatisVerisiPowerBI
├── SatisAnalizi.pbix           # Power BI proje dosyası
├── Veriseti.csv                # Örnek satış veri seti (isteğe bağlı)
├── README.md                   # Proje açıklaması ve dokümantasyon
```

### 🔍 Veriler ve Ön Hazırlık Süreci
1. Veri Kaynağı
Ham veriler .csv formatında alınmıştır ve içinde şunlar yer almaktadır:

Tarih

Saat

Satış Tutarı

Kategori

Ürün

Müşteri ID

İl / Bölge

### 2. Veri Temizleme ve Hazırlık
Power BI üzerinde aşağıdaki işlemler gerçekleştirilmiştir:

Tarih ve saat sütunları DateTime biçimine dönüştürüldü.

Haftanın günü, ay, yıl gibi bilgiler DAX ile türetildi.

Saat sütunu ayrı bir kolon olarak oluşturuldu.

Hafta içi / Hafta sonu ayrımı yapıldı.

Eksik veya boş veriler Power Query üzerinden temizlendi.

## 📊 Oluşturulan Görselleştirmeler

## 🗂️ Kullanılan Veriler

Veri setinde yer alan başlıca sütunlar:

- Order ID: Her satışa ait benzersiz kimlik numarası.
- Date: Satışın gerçekleştiği tarih.
- Time: Satışın gerçekleştiği saat.
- Region: Satışın yapıldığı bölge.
- Amount: Satış tutarı (ciro bilgisi).
- Product: Satılan ürün bilgisi.

## 🧱 Sayfa Yapısı

Power BI raporu 4 sayfadan oluşmaktadır:

### 1. Giriş Sayfası

Kullanıcının diğer raporlara yönlendirilmesini sağlayan sade bir navigasyon sayfasıdır. 3 perspektife göre butonlar yerleştirilmiştir:

- Özet Rapor
- Hafta Tipi Analizi
- Bölge ve Saat Bazlı Analiz

### 2. Özet Sayfa

- Toplam satış adedi, toplam ciro gibi temel ölçümler kartlarla sunulmuştur.
- Genel performansı hızlıca görmeye yarar.
- Tarih slicer (filtreleme) ile dinamik değişen görseller mevcuttur.

### 3. Hafta Tipi Analizi Sayfası

Bu sayfada satışların hafta içi ve hafta sonu dağılımı analiz edilmiştir.

#### 📌 Hafta Tipi Kolonu Oluşturma

Power BI'da yeni bir sütun oluşturularak satışın hafta içi mi yoksa hafta sonu mu yapıldığı belirlenmiştir:

```DAX
HaftaTipi = 
VAR gun = WEEKDAY('Sales'[Date],2)
RETURN IF(gun >=6, "Hafta Sonu", "Hafta İçi")
```
## 📊 Kullanılan Grafik

### ✅ Yığılmış Sütun Grafiği (Stacked Column Chart) Kullanımı

- **Grafik Tipi:** Yığılmış Sütun Grafiği  
- **X Ekseni:** `HaftaTipi`  
- **Y Ekseni:** `Amount (Satış Tutarı)`  
- **Değerler:** Toplam Satış Tutarı  

📌 Bu grafik ile kullanıcılar **hafta sonu ve hafta içi arasındaki satış farkını** net şekilde görebilmektedir.

### 📈 Saatlik Satış Analizi
Saat sütununa göre toplam satış tutarı hesaplandı.

Bar chart (çubuk grafik) ile saat bazlı analiz yapıldı.

Zirve saatler tespit edildi.

## 📊 Grafik Tipi: Çizgi Grafik (Line Chart)

- **X Ekseni:** Saat  
- **Y Ekseni:** Amount (Toplam Satış Tutarı)

### 📌 Açıklama
Bu grafik sayesinde satışların gün içindeki saatlik dağılımı incelenebilir.


### 📅 Günlük ve Haftalık Karşılaştırma
Yığılmış Sütun Grafiği (Stacked Column Chart) ile hafta içi ve hafta sonu karşılaştırması yapıldı.

Sütun Grafikleri ile günlük bazda toplam satışlar incelendi.

### 🧮 Kartlar (KPI)
Toplam Satış Tutarı

Toplam Sipariş Sayısı

Ortalama Satış Tutarı

En Yoğun Satış Günü

En Yoğun Satış Saati

### 🔄 Filtreler ve Etkileşimler
Tarih aralığı seçimi

Hafta içi / hafta sonu filtreleri

Ürün kategorisi filtreleri

İl / bölge filtreleri

Tüm sayfalar arası senkronize filtre yapısı

### 🧪 Hesaplanan Ölçüler (Measures)
```DAX
Toplam Satış = SUM(Satislar[SatisTutari])

Ortalama Satış = AVERAGE(Satislar[SatisTutari])

Saat = HOUR(Satislar[SatisZamani])

Hafta Günü = FORMAT(Satislar[Tarih], "dddd")

Hafta Tipi = IF( WEEKDAY(Satislar[Tarih], 2) <= 5, "Hafta İçi", "Hafta Sonu" )
```
## 🧾 Kullanılan Ölçüler (Measures)

### 1️⃣ Toplam Satış Tutarı
```DAX
ToplamCiro = SUM('Sales'[Amount])
```
### 2️⃣ Toplam Satış Adedi
```DAX
ToplamAdet = COUNT('Sales'[Order ID])
```
### 3️⃣ Ortalama Satış
```DAX
OrtalamaSatis = AVERAGE('Sales'[Amount])
```

### 🎨 Tasarım Notları
Renk uyumu sade ve gözü yormayan tonlarda seçilmiştir.

Her grafik için açıklayıcı başlıklar eklenmiştir.

Kart görselleri ile önemli metrikler ön plana çıkarılmıştır.

Navigasyonu kolaylaştırmak için sayfa geçiş butonları eklenmiştir.

Sayfa filtreleriyle kullanıcı etkileşimi artırılmıştır.

### 🚀 Sonuç
Bu proje ile satış verileri çok yönlü analiz edilmiştir. Kullanıcılar farklı bakış açılarından veriyi inceleyebilir, anlamlı içgörüler elde edebilir ve stratejik kararlar verebilir.

Power BI’ın güçlü görselleştirme ve etkileşim özellikleri sayesinde veriler sadece analiz edilmekle kalmamış, aynı zamanda dikkat çekici ve anlaşılır bir şekilde sunulmuştur.

### ☁️ Yayınlama ve Paylaşım
Power BI raporu .pbix uzantısıyla hazırlanmıştır.

GitHub’a yüklenebilmesi için 25 MB altında tutulmalıdır.

Daha büyük boyutlu dosyalar için Google Drive gibi alternatif paylaşım yöntemleri önerilir.

### 📝 Notlar
Proje yalnızca Power BI Desktop üzerinde lokal olarak çalıştırılabilir.

Her yeni veriyle rapor kolayca güncellenebilir (veri kaynağı güncellemesiyle).

Geliştirmeye açık bir projedir. Kullanıcı giriş sayfası, canlı veriler, mobil uyum gibi özellikler gelecekte eklenebilir.

### 📝 Notlar
Proje google drive linkinden de çalıştırabilirsiniz 
https://drive.google.com/drive/u/0/folders/1boYmJwK6vFly-HD9CK32QTmOOOjA3GyB

### 👩‍💻 Hazırlayan
Eda Özge Uğurlu
📧 edaozge@example.com
🔗 GitHub: github.com/edaozgeugurlu
