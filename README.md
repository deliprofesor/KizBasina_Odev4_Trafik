# Trafik Kazası Analizi ve Tahmini Projesi

<img width="1097" height="617" alt="image" src="https://github.com/user-attachments/assets/fbfbcfba-a146-4448-9301-ff7cf0d3f7f7" />

Bu proje, İngiltere’de 2005-2014 yılları arasında meydana gelen trafik kazalarına ait kapsamlı bir veri seti üzerinde gerçekleştirilmiştir. Amaç, trafik kazalarının yıllara, zamana, hava ve yol koşullarına göre nasıl değiştiğini incelemek, kaza şiddetini etkileyen faktörleri belirlemek ve zaman içinde kaza oranlarını tahmin etmektir. Ayrıca kırsal ve kentsel alanlar arasındaki kaza farklılıkları analiz edilmiştir.


## Kullanılan Veri Setleri

Proje kapsamında aşağıdaki CSV dosyaları kullanılmıştır:

- accidents_2005_to_2007.csv
- accidents_2009_to_2011.csv
-accidents_2012_to_2014.csv

Bu veri setleri yıllara göre ayrılmıştır ve analiz için öncelikle birleştirilerek tek bir kapsamlı veri tabanı oluşturulmuştur.

## Veri Ön İşleme ve Temizleme

Veri birleştirme: Üç farklı CSV dosyasındaki kayıtlar, ortak sütunlar kullanılarak birleştirilmiştir.

Eksik değer analizi: Yüksek oranda eksik veri içeren sütunlar çıkarılmış, kritik sütunlardaki eksikler ise uygun yöntemlerle tamamlanmıştır.

Aykırı değerlerin tespiti: Özellikle araç sayısı ve yaralanma sayısı gibi sütunlardaki anormal değerler analiz edilmiştir.

Zaman bilgisi dönüştürme: Tarih ve saat verileri datetime formatına çevrilerek zaman serisi analizine uygun hale getirilmiştir.

Yeni değişken oluşturma: Saat, gün, yıl gibi yeni zaman bileşenleri çıkarılmıştır.


# 1. Trafik akışının değişmesi kazaları nasıl etkiler?

## Trafik Akışının Değişmesinin Kazalar Üzerindeki Etkisi

Yaptığımız analizlerde, trafik akışındaki değişimlerin kaza sayıları üzerinde belirgin etkileri olduğu gözlemlenmiştir. Özellikle aşağıdaki noktalar öne çıkmaktadır:

<img width="948" height="460" alt="image" src="https://github.com/user-attachments/assets/ee3e2267-be7a-4116-a49a-7879c8658611" />

- **Yıllara Göre Kaza Sayısı:**
  
  2005-2014 yılları arasında kaza sayılarında dalgalanmalar görülüyor. En yüksek kaza sayısı 2005 yılında (198,735) iken, sonraki yıllarda genel bir azalma trendi var. 2012 yılında ise tekrar bir artış gözleniyor. 2008 yılı verilerinin olmadığı düşünüldüğünde, bu dönemlerdeki trafik koşulları ve politikalar kaza sayılarındaki değişimlerde etkili olmuş olabilir. Kaza sayılarındaki bu iniş çıkışlar, trafik hacmindeki değişiklikler, yol güvenliği önlemleri ve araç sayısındaki değişimlerle ilişkilendirilebilir.

<img width="907" height="471" alt="image" src="https://github.com/user-attachments/assets/3af3429b-6b45-4496-91cc-6a18c24288b4" />

- **Saat Bazlı Kaza Dağılımı:**
  
 Kaza sayıları gün içinde belirgin bir dalgalanma gösteriyor. Gece geç saatlerde (00:00-05:00 arası) kaza sayıları nispeten düşük, sabah işe gidiş (07:00-09:00) ve akşam iş çıkışı saatlerinde (15:00-18:00) kaza sayılarında önemli artışlar var. Özellikle 8:00, 17:00 ve 16:00 saatlerinde kaza sayıları çok yüksek. Bu saatlerde trafik yoğunluğunun artması, yol kullanıcılarının strese ve yorgunluğa daha açık olması nedeniyle kaza riskini yükseltiyor. Gece geç saatlerde kaza sayısının azalması ise trafik yoğunluğunun düşmesiyle açıklanabilir.
  
<img width="1108" height="452" alt="image" src="https://github.com/user-attachments/assets/2b3ffbdf-d6d3-4452-a395-87e1bc63e334" />

- **Hız Limitleri ve Yol Tipi:**
  
En fazla kaza, 30 mph hız limitine sahip yollarda gerçekleşmiş (968,284 kaza). Bu hız limiti genellikle yerleşim alanlarında ve şehir içi yollarda kullanılır, dolayısıyla araç trafiğinin yoğun olduğu yerlerde kazalar daha sık yaşanıyor. Hız limiti arttıkça kaza sayısı azalıyor gibi görünse de, yüksek hız limitine sahip (60-70 mph) yollarda da önemli sayıda kaza gerçekleşmiş. Düşük hız limitlerinde (10-20 mph) ise kaza sayısı oldukça az, çünkü bu limitler genellikle çok sakin, az trafiğe sahip veya özel alanlar için geçerli olabilir.

<img width="1106" height="448" alt="image" src="https://github.com/user-attachments/assets/ab30c6ba-d068-4353-a42c-b378702a90ad" />

- **Kentsel ve Kırsal Alanlar:**
  
Kaza sayısının en yüksek olduğu yol tipi "Single carriageway" (tek yönlü yol) olmuş (1,126,951 kaza). Bu tür yollar genellikle dar ve trafik yoğunluğu yüksek olan kırsal veya şehir çevresi yollar olabilir. "Dual carriageway" (çift yönlü yol) ve "Roundabout" (dönel kavşak) da kaza açısından önemli yer tutuyor. Diğer yol tiplerinde ise kaza sayısı daha az.

Kentsel alanlarda kaza sayısı (972,007) kırsal alanlardan (532,011) oldukça fazla. Bu, şehirlerde daha yoğun trafik ve araç sayısının etkisini gösteriyor. Ortalama kaza şiddeti açısından ise kentsel alanlar (2.86) kırsal alanlardan (2.79) biraz daha yüksek. Yani şehirlerde hem kaza sayısı hem de kaza şiddeti biraz daha fazla. Bu durum, kentsel alanlarda trafik yoğunluğunun ve karmaşıklığının artmasıyla birlikte kazaların hem sayısını hem de ciddiyetini yükselttiğini gösteriyor.

## Genel Değerlendirme

Veriler, trafik akışının yoğun olduğu şehir içi ve sabah-akşam saatlerinde kaza riskinin daha yüksek olduğunu ortaya koyuyor. Yerleşim yerlerindeki 30 mph hız limiti olan yollarda kazalar en çok yaşanırken, kırsal alanlarda hem kaza sayısı hem de şiddeti kentsel alanlara göre biraz daha düşük. Yol tipi ve hız limitleri kazaların oluşma biçimini etkilerken, trafik yoğunluğu kaza sayısını artıran en önemli faktörlerden biri olarak öne çıkıyor. Trafik güvenliğini artırmak için bu alanlarda özel önlemler alınması faydalı olacaktır.


   
# 2. Kaza oranlarını ne artırır? 

## Trafik Kazası Analizi Özeti

Bu veri setinde 2005-2014 yılları arasında gerçekleşen toplam **1.504.150** trafik kazası yer almaktadır. Analizimizde kazaların şiddeti, hava koşulları, yol tipi, hız limiti, günün saati ve kırsal/kentsel alan farkları incelenmiştir.

## Kaza Şiddeti Dağılımı
- Hafif kazalar (Seviye 3): **1.280.205** adet  
- Ciddi kazalar (Seviye 2): **204.504** adet  
- Ölümcül kazalar (Seviye 1): **19.441** adet  

Kazaların çoğunluğu hafif şiddette olup, ciddi ve ölümcül kazalar daha azdır.

<img width="1082" height="681" alt="image" src="https://github.com/user-attachments/assets/3a618473-b92d-43b7-9a18-03c14b54db80" />

## Hava Koşullarına Göre Kaza Sayısı
- En çok kaza "**Fine without high winds**" (açık, rüzgarsız) havalarda (**1.204.069** adet) gerçekleşmiştir.  
- Yağmur, sis, kar gibi olumsuz hava koşullarında da önemli sayıda kaza yaşanmıştır.  
- Hava koşulları, kaza sıklığını etkileyen önemli faktörlerden biridir.

<img width="945" height="562" alt="image" src="https://github.com/user-attachments/assets/8f4c054e-2253-4e0c-97b0-af13c0fd1487" />

## Yol Tipine Göre Kaza Sayısı
- Tek yönlü yollar ("**Single carriageway**") kazaların büyük çoğunluğuna ev sahipliği yapmıştır (**1.126.951** adet).  
- İki yönlü yollar ("**Dual carriageway**") ve dönel kavşaklar ("**Roundabout**") daha az kaza içermektedir.

<img width="912" height="477" alt="image" src="https://github.com/user-attachments/assets/8316a922-ce5d-41f5-ab74-66ae7b6c8694" />

## Hız Limitine Göre Kaza Sayısı
- **30** ve **60** mph hız limitlerine sahip yollarda en fazla kaza gerçekleşmiştir.  
- Düşük hız limitlerindeki kazaların çokluğu, bu bölgelerdeki trafik yoğunluğunu göstermektedir.

<img width="1087" height="537" alt="image" src="https://github.com/user-attachments/assets/e418ec56-2347-4fb9-a923-d34fd936ca20" />

## Günün Saatine Göre Kaza Sayısı
- Sabah erken saatler (07:00-10:00), öğle saatleri ve akşamüstü (15:00-18:00) kazaların yoğunlaştığı zamanlardır.  
- Bu saatler trafik yoğunluğunun yüksek olduğu dönemlerdir.

<img width="605" height="388" alt="image" src="https://github.com/user-attachments/assets/820f9fc2-e844-4cb5-99cf-abe85f7d2dfd" />

## Kırsal ve Kentsel Alanlara Göre Kaza Sayısı
- Kentsel alanlarda **972.007** kaza, kırsal alanlarda ise **532.011** kaza kaydedilmiştir.  
- Kentsel alanlarda kaza sayısının daha fazla olması, yoğun trafik ve yol koşullarının etkisini göstermektedir.



## Kaza Şiddeti ve Faktörler Arasındaki İstatistiksel İlişki

Yapılan Ki-Kare testleri sonucunda aşağıdaki kategorik değişkenlerin kaza şiddeti (Accident_Severity) üzerinde **istatistiksel olarak anlamlı** etkisi olduğu bulunmuştur (p < 0.05):

| Değişken                | Chi2 İstatistiği | p-değeri | Sonuç                                |
|-------------------------|------------------|----------|------------------------------------|
| Weather_Conditions      | 1692.98          | 0.0000   | Weather Conditions ile kaza şiddeti arasında anlamlı ilişki var. |
| Road_Type               | 4986.63          | 0.0000   | Road Type ile kaza şiddeti arasında anlamlı ilişki var.          |
| Urban_or_Rural_Area     | 11591.73         | 0.0000   | Kırsal/Kentsel alan ile kaza şiddeti arasında anlamlı ilişki var.|

Bu bulgular, hava koşulları, yol tipi ve kırsal-kentsel alan farklarının kaza şiddeti üzerinde önemli etkileri olduğunu göstermektedir.


# 3. Zaman İçinde Kaza Oranlarını Tahmin Edebilir Miyiz?
Zaman serisi analizi kullanarak, geçmiş verilere dayanarak gelecekteki kaza sayısını tahmin etmek mümkündür. Bu amaçla, aylık kaza sayıları hesaplanmış ve Facebook Prophet modeli ile tahmin yapılmıştır.

Model, aylık kaza sayılarını öğrenerek gelecekteki 12 ay için tahminler üretmiştir. Bu yöntem sayesinde, kaza oranlarının mevsimsellik, trend gibi bileşenleri yakalanabilir ve trafik güvenliği stratejileri planlanabilir.

Aşağıdaki grafik, modelin tahmin ettiği aylık kaza sayısı ve zaman içindeki değişimini göstermektedir. Ayrıca bileşen grafikleri ile trend ve mevsimsel etkiler analiz edilmiştir.

<img width="1000" height="603" alt="image" src="https://github.com/user-attachments/assets/57d15ce6-36fe-4a7e-8fcd-260fecee7cc3" />

<img width="903" height="625" alt="image" src="https://github.com/user-attachments/assets/85e94f0b-6c4d-4833-8da3-9adf5f0b45db" />


### Kentsel ve Kırsal Alanlarda Kaza Şiddeti


<img width="940" height="537" alt="image" src="https://github.com/user-attachments/assets/f71d6134-15e4-4055-bca5-d0a5defe1988" />

Kentsel alanlarda (Urban_or_Rural_Area=1) toplam 972,007 kaza yaşanmıştır. Bunların 6,943'ü hafif, 119,632'si orta şiddette, 845,432'si ise ciddi şiddette kazalardır.  
Kırsal alanlarda (Urban_or_Rural_Area=2) ise toplam 532,011 kaza yaşanmış, 12,498 hafif, 84,855 orta ve 434,658 ciddi şiddette kaza gerçekleşmiştir.  
Kentsel alanlarda kaza sayısı daha yüksek olmakla birlikte, her iki bölgede de ciddi şiddette kazaların oranı oldukça fazladır.



### Kentsel ve Kırsal Alanlarda Saat Bazlı Kaza Sayıları


<img width="1051" height="541" alt="image" src="https://github.com/user-attachments/assets/d6d9cdeb-9c9c-4f9f-9569-06cf23f8cc64" />

Saat bazında incelendiğinde, kentsel alanlarda gece yarısı (00:00) saatlerinde 14,716, kırsal alanlarda ise 8,687 kadar kaza gerçekleşmiştir.  
Her iki bölgede de gece ve sabah erken saatlerde kaza sayılarının daha düşük olduğu, gündüz saatlerinde ise arttığı gözlemlenmektedir.  
Bu veriler, kaza riskinin saat dilimlerine ve alan tipine göre değişiklik gösterdiğini ortaya koymaktadır.


