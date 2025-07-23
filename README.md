



# 1. Trafik akışının değişmesi kazaları nasıl etkiler?

## Trafik Akışının Değişmesinin Kazalar Üzerindeki Etkisi

Yaptığımız analizlerde, trafik akışındaki değişimlerin kaza sayıları üzerinde belirgin etkileri olduğu gözlemlenmiştir. Özellikle aşağıdaki noktalar öne çıkmaktadır:

- **Yıllara Göre Kaza Sayısı:**  
  2005-2014 yılları arasında kaza sayıları genel olarak dalgalı bir seyir izlemiştir. Trafik hacmindeki artış veya azalış, kaza sayısına doğrudan yansımaktadır. Örneğin yoğun trafik dönemlerinde kaza sayılarında artış gözlenmektedir.

- **Saat Bazlı Kaza Dağılımı:**  
  Trafik akışının yoğun olduğu sabah ve akşam saatlerinde (özellikle 07:00-10:00 ve 15:00-18:00 arası) kaza sayılarının en yüksek seviyede olduğu tespit edilmiştir. Bu da trafik yoğunluğunun kaza riskini artırdığını göstermektedir.

- **Hız Limitleri ve Yol Tipi:**  
  Trafik akışının hızlı ve yoğun olduğu çift yönlü yollar ve yüksek hız limitlerine sahip bölgelerde farklı kaza profilleri görülmektedir. Yavaş ve yoğun trafiğin olduğu düşük hız limitli yollarda ise kaza sayısı yüksek ancak genellikle daha hafif kazalar görülmektedir.

- **Kentsel ve Kırsal Alanlar:**  
  Kentsel alanlarda yoğun trafik akışı nedeniyle kaza sayıları daha fazladır. Kırsal alanlarda ise trafik akışı daha seyrek olmasına rağmen, yüksek hızların etkisiyle daha ciddi kazalar yaşanabilmektedir.

**Özetle, trafik akışındaki artışlar genellikle kaza sayılarında artışa sebep olurken, akışın yoğunluğu ve yol koşulları kaza şiddetini de etkileyebilmektedir. Trafik yönetimi ve akış kontrolü, kaza riskinin azaltılması için kritik öneme sahiptir.**




   
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
