# TatilBudurOrnekDataBaseTasarimi
SQL Eğitimi Örnek Database Projesi

TatilBudur Sitesi Örneği DataBase Tasarımı

-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

## Diagram Görünümü

![resim](https://github.com/AhmetSahinNL/TatilBudurOrnekDataBaseTasarimi/assets/139613517/c884089a-f9d1-449f-b69a-f200da7ff9cd)

-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

## 1. Addresses Tablosu

![resim](https://github.com/AhmetSahinNL/TatilBudurOrnekDataBaseTasarimi/assets/139613517/5d247acd-967e-4450-8e6c-1c0aa2a249e5)

```MSSQL
Id
City
Town
Village
Street
[Content]
GoogleMapsLocation
PhoneNumber1
PhoneNumber2
PhoneNumber3
Email
HotelId
```

AÇIKLAMA:

Bu tablo bir online tatil sitesinin veritabanındaki otelleri ve bunlarla ilgili ayrıntıları depolayan bir tabloyu temsil eder. Her bir otel bir benzersiz kimlik numarasıyla (Id) tanımlanır ve otel ile ilgili bilgiler bu kimlik altında kaydedilir. Şehir (City), ilçe (Town), köy veya kasaba (Village) gibi coğrafi konum bilgileri ile otelin bulunduğu sokak (Street) ve iletişim bilgileri (PhoneNumber1, PhoneNumber2, PhoneNumber3, Email) bu tabloda saklanır. Ek olarak otelle ilgili detaylar ve açıklamalar (Content) da burada bulunur. Bu veriler online tatil sitesi kullanıcılarına otelleri arama, inceleme ve rezervasyon yapma olanağı sunmak için kullanılır. Ayrıca her otel için benzersiz bir kimlik (HotelId) de bulunur, bu kimlik diğer veritabanı tablolarıyla otel bilgilerini ilişkilendirmek için kullanılır.

-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

## 2. Categories Tablosu

![resim](https://github.com/AhmetSahinNL/TatilBudurOrnekDataBaseTasarimi/assets/139613517/ee0d3b10-9dce-40b5-a83b-b869ecefd4cf)

```MSSQL
Id
Name
IsActive
MainCategoryId
CreatedDate
UpdatedDate
```

AÇIKLAMA:

Bu tablo online tatil sitesinin kategorilerini temsil eder. İlk sütun olan "Id," her kategorinin benzersiz bir kimlik numarası ile tanımlandığını gösterir. Bu sayede her bir kategori ayırt edilir ve kolayca erişilebilir. "Name" sütunu, her kategorinin ismini içerir, örneğin, "Plaj Tatilleri" veya "Dağ Tatilleri" gibi. "IsActive" sütunu, bir kategorinin etkin veya pasif olduğunu belirler, bu da kategorilerin görüntülenip görüntülenmeyeceğini kontrol etmek için kullanılabilir. "MainCategoryId" sütunu, kategorilerin hiyerarşik bir yapıda olup olmadığını gösterir, böylece alt kategoriler ana kategorilere bağlanabilir. "CreatedDate" ve "UpdatedDate" sütunları, her kategorinin oluşturulma ve güncelleme tarihlerini kaydeder, bu da kategori bilgilerinin izlenmesine ve yönetilmesine yardımcı olur.

Bu tablo online tatil sitesindeki kategorileri düzenlemek ve sıralamak için kullanılır. Her bir kategoriye benzersiz bir kimlik verir, hiyerarşik yapıları destekler ve hangi kategorilerin aktif olduğunu belirler. Bu kullanıcıların tatil fırsatlarını kategoriye göre sıralamasını ve aramasını kolaylaştırır ve kategorilerin yönetimini sağlar.

-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

## 3. HotelCategories Tablos

![resim](https://github.com/AhmetSahinNL/TatilBudurOrnekDataBaseTasarimi/assets/139613517/86aeaace-7b38-483b-8695-ed84a9c33814)

```MSSQL
Id
HotelId
CategoryId
CreatedDate
UpdatedDate
```

AÇIKLAMA:

Bu tablo online tatil sitesinin otel kategorilerini ve bu kategorilere ait otel ilişkilerini yönetmek için kullanılır. İlk sütun olan "Id," her bir kategori-otel ilişkisinin benzersiz bir kimlik numarası ile tanımlandığını gösterir. Bu sayede her ilişki ayrı bir entite olarak izlenebilir. "HotelId" sütunu, bir otelin benzersiz kimlik numarasını içerir ve ilgili kategorilere hangi otelin dahil olduğunu gösterir. "CategoryId" sütunu bir kategoriye ait benzersiz kimlik numarasını içerir. Bu sayede otelin hangi kategoriye ait olduğunu belirtir. "CreatedDate" ve "UpdatedDate" sütunları her kategori-otel ilişkisinin oluşturulma ve güncelleme tarihlerini saklar bu sayede ilişkilerin takibini yapar ve yönetir.

Bu tablo online tatil sitesindeki otel kategorilerini ve bu kategorilere ait otel ilişkilerini yönetmek için kullanılır. Her bir kayıt bir otelin belirli bir kategoriye ait olduğunu gösterir ve bu ilişkiyi benzersiz bir kimlikle izler. Bu kullanıcıların otelleri kategoriye göre sıralamalarını ve aramalarını sağlar ve otel-kategori ilişkilerinin izlenmesini kolaylaştırır.

-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

## 4. HotelImages Tablosu

![resim](https://github.com/AhmetSahinNL/TatilBudurOrnekDataBaseTasarimi/assets/139613517/e2275d66-6901-41f8-b500-aea6aeffa560)

```MSSQL
Id
Url
Image
HotelId
CreatedDate
UpdatedDate
```

AÇIKLAMA:

Bu tablo online tatil sitesinin otellere ait resimleri saklamak için kullanılır. İlk sütun olan "Id," her bir resmin benzersiz bir kimlik numarası ile tanımlandığını gösterir. Bu sayede her resim ayrı bir entite olarak izlenebilir. "Url" sütunu resmin internet üzerindeki yerini belirtir, yani resmin web adresini içerir. "Image" sütunu otelle ilgili resmi içerir ve resmin veri türünü saklar. "HotelId" sütunu resmin hangi otele ait olduğunu belirtir, yani resmin hangi otelle ilişkilendirildiğini gösterir. "CreatedDate" ve "UpdatedDate" sütunları her resmin oluşturulma ve güncelleme tarihlerini saklar. Bu sayede resimlerin yönetimini ve güncellemelerini takip eder.

Bu tablo online tatil sitesindeki otellere ait görsel materyali depolamak için kullanılır. Her bir kayıt bir otelle ilişkilendirilmiş bir resmi temsil eder ve bu resimlerin web adreslerini içerir. Bu otellerin tanıtımı için görsel materyalin yönetilmesini ve sunulmasını sağlar. Kullanıcılar otelleri incelediklerinde, bu resimlerden otelleri daha iyi anlayabilirler ve tatil seçimlerini yaparken görsel açıdan bilgi sahibi olabilirler.

-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

## 5. Hotels Tablosu

![resim](https://github.com/AhmetSahinNL/TatilBudurOrnekDataBaseTasarimi/assets/139613517/1a29632b-966e-416b-922e-269aa74a5a83)

```MSSQL
Id
Name
Rating
CreatedDate
UpdatedDate
```

AÇIKLAMA:

Bu tablo online tatil sitesinin otel bilgilerini depolayan temel bir tabloyu temsil eder. İlk sütun olan "Id" her bir otelin benzersiz bir kimlik numarası ile tanımlandığını gösterir. Bu sayede her otel ayrı bir entite olarak izlenebilir. "Name" sütunu otelin adını içerir ve otelin adını temsil eder. örneğin "Grand Hotel." "Rating" sütunu otelin kullanıcılar tarafından verilen puanını içerir ve otelin kalitesini veya popülerliğini gösterir. "CreatedDate" ve "UpdatedDate" sütunları her otelin oluşturulma ve son güncelleme tarihlerini saklar. Bu sayede otel bilgilerinin yönetimini ve izlenmesini sağlar.

Bu tablo online tatil sitesindeki otel bilgilerini saklamak için kullanılır. Her bir kayıt bir otelin temel bilgilerini temsil eder ve bu otelleri benzersiz kimliklerle ayırt eder. Bu bilgiler kullanıcıların otelleri araması, incelemesi ve rezervasyon yapması için kullanılır. Ayrıca otelin popülerliğini veya kalitesini gösteren puanları içerir. Böylece kullanıcılar daha iyi kararlar verebilir.

-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

## 6. HotelSpecifications Tablosu

![resim](https://github.com/AhmetSahinNL/TatilBudurOrnekDataBaseTasarimi/assets/139613517/8b7d08d0-056d-4933-b2fa-9585e58eac1f)

```MSSQL
Id
SpecificationId
HotelId
Description
CreatedDate
UpdatedDate
```

AÇIKLAMA:

Bu tablo online tatil sitesinin otellere ait özellikleri ve bu özelliklerin tanımlarını saklamak için kullanılır. İlk sütun olan "Id" her bir otel özelliği ve tanımının benzersiz bir kimlik numarası ile tanımlandığını gösterir. Bu sayede her özellik ayrı bir entite olarak izlenebilir. "SpecificationId" sütunu bir özelliğin benzersiz kimlik numarasını içerir ve bu özelliğin türünü belirtir. örneğin "Ücretsiz Wi-Fi" gibi. "HotelId" sütunu özelliğin hangi otele ait olduğunu belirtir, yani hangi otelin bu özelliği sunduğunu gösterir. "Description" sütunu, her özelliğin açıklamasını içerir, bu da özelliği daha ayrıntılı bir şekilde tanımlar. "CreatedDate" ve "UpdatedDate" sütunları her özellik ve tanımın oluşturulma ve güncelleme tarihlerini saklar. Bu sayede özelliklerin yönetimini ve güncellemelerini takip eder.

Bu tablo online tatil sitesindeki otellerin sunduğu özellikleri ve bu özelliklerin açıklamalarını saklamak için kullanılır. Her bir kayıt bir otelin özelliklerini ve bu özelliklerin ayrıntılarını temsil eder ve bu özellikleri benzersiz kimliklerle ayırt eder. Bu bilgiler kullanıcıların otel seçimlerini yaparken hangi özelliklerin sunulduğunu daha iyi anlamalarına yardımcı olur. Örneğin bir otelin ücretsiz Wi-Fi sunup sunmadığını görmek isteyen bir kullanıcı bu tabloyu kullanarak bu bilgiyi bulabilir.

-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

## 7. HotelTags Tablosu

![resim](https://github.com/AhmetSahinNL/TatilBudurOrnekDataBaseTasarimi/assets/139613517/ec64be05-c749-45ab-9a0d-f898c4dcb6a0)

```MSSQL
Id
HotelId
TagId
CreatedDate
UpdatedDate
```

AÇIKLAMA:

Bu tablo online tatil sitesinin otellerin etiketlerini ve bu etiketlerin otellere atanmasını yönetmek için kullanılır. İlk sütun olan "Id" her bir etiket-otel ilişkisinin benzersiz bir kimlik numarası ile tanımlandığını gösterir. Bu sayede her ilişki ayrı bir entite olarak izlenebilir. "HotelId" sütunu bir otelin benzersiz kimlik numarasını içerir ve bu etiketin hangi otele ait olduğunu belirtir. "TagId" sütunu bir etiketin benzersiz kimlik numarasını içerir ve hangi etiketin atanmış olduğunu gösterir. "CreatedDate" ve "UpdatedDate" sütunları her etiket-otel ilişkisinin oluşturulma ve güncelleme tarihlerini saklar. Bu sayede ilişkilerin takibini yapar ve yönetir.

Bu tablo online tatil sitesindeki otellere ait etiketleri ve bu etiketlerin hangi otellere atanmış olduğunu yönetmek için kullanılır. Her bir kayıt bir etiketin bir otele atanmasını temsil eder ve bu ilişkiyi benzersiz kimliklerle ayırt eder. Bu kullanıcıların otelleri belirli özelliklere veya kategorilere göre sıralamalarını ve aramalarını sağlar. Örneğin "Deniz Manzaralı" veya "Havuzlu" gibi etiketlerle işaretlenmiş otelleri bulmak için kullanılabilir.

-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

## 8. HotelVideos Tablosu

![resim](https://github.com/AhmetSahinNL/TatilBudurOrnekDataBaseTasarimi/assets/139613517/c9b88806-657a-4bf8-9ed0-3ad7d32f0b40)

```MSSQL
Id
Url
Video
CreatedDate
UpdatedDate
HotelId
```

AÇIKLAMA:

Bu tablo online tatil sitesinin otellere ait videoları ve bu videoların tanımlarını saklamak için kullanılır. İlk sütun olan "Id" her bir video kaydının benzersiz bir kimlik numarası ile tanımlandığını gösterir ve her kaydı ayrı bir entite olarak izlenebilir kılar. "Url" sütunu videonun internet üzerindeki yerini belirtir, yani videonun web adresini içerir. "Video" sütunu otelle ilgili videoyu içerir ve videonun veri türünü saklar. "CreatedDate" ve "UpdatedDate" sütunları her video kaydının oluşturulma ve güncelleme tarihlerini saklar. Bu sayede videoların yönetimini ve güncellemelerini izler. Son olarak "HotelId" sütunu video kaydının hangi otele ait olduğunu belirtir. Yani hangi otelin bu videoyu sunduğunu gösterir.

Bu tablo online tatil sitesindeki otellere ait videoları saklamak ve sunmak için kullanılır. Her bir kayıt bir otelle ilişkilendirilmiş bir videoyu temsil eder ve bu videoları benzersiz kimliklerle ayırt eder. Kullanıcılar otelleri daha iyi anlamak ve görsel olarak incelemek için bu videoları kullanabilirler. Örneğin bir otelin iç mekanlarını veya çevresini daha yakından görmek için bu videoları izleyebilirler.

-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

## 9. Reservations Tablosu

![resim](https://github.com/AhmetSahinNL/TatilBudurOrnekDataBaseTasarimi/assets/139613517/e1ae3551-92b4-44a9-95b6-52cebe67aaf0)

```MSSQL
Id
RoomId
Date
Name
AdultCounts
KidCounts
IsPaymentConfirm
IsHere
PaymentDate
Description
Price
```

AÇIKLAMA:

Bu tablo online tatil sitesinin otel rezervasyonlarını saklamak için kullanılır. İlk sütun olan "Id" her bir rezervasyonun benzersiz bir kimlik numarası ile tanımlandığını gösterir ve her rezervasyonu ayrı bir entite olarak izlenebilir kılar. "RoomId" sütunu rezervasyonun hangi oda ile ilişkilendirildiğini belirtir. Yani hangi odanın rezerve edildiğini gösterir. "Date" sütunu rezervasyonun tarihini içerir, yani ne zaman yapılacağını gösterir. "Name" sütunu rezervasyonu yapan kişinin adını içerir. "AdultCounts" ve "KidCounts" sütunları yetişkin ve çocuk misafir sayılarını içerir. "IsPaymentConfirm" sütunu rezervasyonun ödeme onayının alınıp alınmadığını belirtir. "IsHere" sütunu misafirin otelde olup olmadığını gösterir. "PaymentDate" sütunu ödeme tarihini içerir. Son olarak "Description" sütunu, rezervasyon ile ilgili ek açıklamaları içerebilir ve "Price" sütunu ise rezervasyonun maliyetini belirtir.

Bu tablo online tatil sitesindeki otel rezervasyonlarını kaydetmek için kullanılır. Her bir kayıt bir otel odasının belirli bir tarih aralığında rezerve edilmesini temsil eder ve bu rezervasyonları benzersiz kimliklerle ayırt eder. Bu bilgiler otel rezervasyonlarının yönetilmesine, izlenmesine ve faturalandırılmasına yardımcı olur. Kullanıcılar tatil planlarını yaparken ve otelleri seçerken bu rezervasyon bilgilerini göz önünde bulundurabilirler.

-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

## 10. RoomImages Tablosu

![resim](https://github.com/AhmetSahinNL/TatilBudurOrnekDataBaseTasarimi/assets/139613517/298dc8cc-5d70-4670-9f71-8152f6deec43)

```MSSQL
Id
RoomId
Url
CreatedDate
UpdatedDate
```

AÇIKLAMA:

Bu tablo online tatil sitesinin otel odalarına ait görsel materyali depolamak için kullanılır. İlk sütun olan "Id" her bir odanın görsel kaydının benzersiz bir kimlik numarası ile tanımlandığını gösterir ve her kaydı ayrı bir entite olarak izlenebilir kılar. "RoomId" sütunu görselin hangi odaya ait olduğunu belirtir. Yani hangi oda için bu görselin kullanıldığını gösterir. "Url" sütunu görselin internet üzerindeki yerini belirtir, yani görselin web adresini içerir. "CreatedDate" ve "UpdatedDate" sütunları her görsel kaydının oluşturulma ve güncelleme tarihlerini saklar. Bu sayede görsellerin yönetimini ve güncellemelerini izler.

Bu tablo online tatil sitesindeki otel odalarına ait görsel materyali saklamak ve sunmak için kullanılır. Her bir kayıt bir oda için görsel bilgiyi temsil eder ve bu görselleri benzersiz kimliklerle ayırt eder. Kullanıcılar otel odalarını incelemek ve seçmek için bu görselleri kullanabilirler. Özellikle görsel materyal, odaların iç düzeni, manzaraları ve diğer önemli detayları göstererek kullanıcıların daha iyi bilinçli kararlar vermesine yardımcı olur.

-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

## 11. Rooms Tablosu

![resim](https://github.com/AhmetSahinNL/TatilBudurOrnekDataBaseTasarimi/assets/139613517/9a070aa4-a29c-4b93-82d1-e644c2495161)

```MSSQL
Id
Name
CreatedDate
UpdatedDate
Description
AdultCounts
KidCounts
HotelId
```

AÇIKLAMA:

Bu tablo online tatil sitesinin otel odalarının bilgilerini saklamak için kullanılır. İlk sütun olan "Id" her bir oda kaydının benzersiz bir kimlik numarası ile tanımlandığını gösterir ve her oda kaydını ayrı bir entite olarak izlenebilir kılar. "Name" sütunu oda tipinin veya adının ne olduğunu içerir. örneğin "Standart Oda" veya "Deluxe Süit" gibi. "CreatedDate" ve "UpdatedDate" sütunları her oda kaydının oluşturulma ve güncelleme tarihlerini saklar. Bu sayede odaların yönetimini ve güncellemelerini izler. "Description" sütunu oda hakkında ek açıklamaları içerebilir ve odanın özelliklerini detaylandırabilir. "AdultCounts" ve "KidCounts" sütunları yetişkin ve çocuk misafir sayılarını içerir. Bu da bir oda için kaç yetişkin ve çocuğun kalabileceğini belirtir. Son olarak "HotelId" sütunu, oda kaydının hangi otele ait olduğunu belirtir, yani bu odanın hangi otelde bulunduğunu gösterir.

Bu tablo online tatil sitesindeki otel odalarının bilgilerini saklamak için kullanılır. Her bir kayıt bir otel odasının özelliklerini, adını, yetişkin ve çocuk misafir kapasitesini ve hangi otele ait olduğunu temsil eder. Bu bilgiler kullanıcıların otel odalarını incelemesi, karşılaştırması ve rezervasyon yapması için kullanılır. Kullanıcılar odaların tipini, fiyatını ve kapasitesini göz önünde bulundurarak tatil planlarını yapabilirler.

-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

## 12. RoomTags Tablosu

![resim](https://github.com/AhmetSahinNL/TatilBudurOrnekDataBaseTasarimi/assets/139613517/18d3cc19-0d6d-4ef9-bbc9-0b25284058ba)

```MSSQL
Id
RoomId
TagId
AdultPrice
KidPrice
CreatedDate
UpdatedDate
```

AÇIKLAMA:

Bu tablo online tatil sitesinin otel odalarına ait etiketlerin ve bu etiketlerin fiyatlarının saklandığı bir tabloyu temsil eder. İlk sütun olan "Id" her bir etiket-oda ilişkisinin benzersiz bir kimlik numarası ile tanımlandığını gösterir ve her kaydı ayrı bir entite olarak izlenebilir kılar. "RoomId" sütunu etiketin hangi odaya ait olduğunu belirtir, yani hangi oda için bu etiketin geçerli olduğunu gösterir. "TagId" sütunu etiketin benzersiz kimlik numarasını içerir ve hangi etiketin kullanıldığını gösterir. "AdultPrice" ve "KidPrice" sütunları etiketin yetişkin ve çocuk misafirler için fiyatlarını içerir. Bu da bir etiketin her iki misafir türü için farklı fiyatlar sunabileceğini gösterir. "CreatedDate" ve "UpdatedDate" sütunları her etiket-oda ilişkisinin oluşturulma ve güncelleme tarihlerini saklar. Bu sayede ilişkilerin takibini yapar ve yönetir.

Bu tablo online tatil sitesindeki otel odalarına ait etiketlerin ve bu etiketlerin fiyatlarının yönetimi için kullanılır. Her bir kayıt bir oda ile bir etiketin ilişkisini temsil eder ve bu ilişkileri benzersiz kimliklerle ayırt eder. Bu bilgiler kullanıcıların otel odalarını incelediklerinde oda fiyatlarını ve özelliklerini daha iyi anlamalarına yardımcı olur. Özellikle farklı etiketlere sahip odaların farklı fiyatlandırmaları olabileceği durumlarda kullanılır.

-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

## 13. RoomVideos Tablosu

![resim](https://github.com/AhmetSahinNL/TatilBudurOrnekDataBaseTasarimi/assets/139613517/d7b679ee-4cb3-42c6-a668-fe857122ec74)

```MSSQL
Id
RoomId
Url
CreatedDate
UpdatedDate
```

AÇIKLAMA:

Bu tablo online tatil sitesinin otel odalarına ait videoları ve bu videoların internet üzerindeki yerlerini saklamak için kullanılır. İlk sütun olan "Id" her bir video kaydının benzersiz bir kimlik numarası ile tanımlandığını gösterir ve her kaydı ayrı bir entite olarak izlenebilir kılar. "RoomId" sütunu video ile ilişkilendirilen oda numarasını içerir. Yani hangi odaya ait olduğunu gösterir. "Url" sütunu, videonun internet üzerindeki konumunu belirtir, yani videonun web adresini içerir. "CreatedDate" ve "UpdatedDate" sütunları her video kaydının oluşturulma ve güncelleme tarihlerini saklar. Bu sayede videoların yönetimini ve güncellemelerini izler.

Bu tablo online tatil sitesindeki otel odalarına ait videoların bilgilerini saklamak ve sunmak için kullanılır. Her bir kayıt bir oda ile ilişkilendirilmiş bir videoyu temsil eder ve bu videoları benzersiz kimliklerle ayırt eder. Kullanıcılar otel odalarını daha iyi anlamak ve görsel olarak incelemek için bu videoları kullanabilirler. Özellikle odaların iç düzeni, manzaraları ve diğer önemli ayrıntılar videolar aracılığıyla görsel olarak sunulur. Bu da kullanıcıların daha iyi bilinçli kararlar vermesine yardımcı olur.

-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

## 14. Specifications Tablosu

![resim](https://github.com/AhmetSahinNL/TatilBudurOrnekDataBaseTasarimi/assets/139613517/61b405bf-1848-48a0-a860-b13a4faa59d8)

```MSSQL
Id
Name
IsActive
CreatedDate
UpdatedDate
```

AÇIKLAMA:

Bu tablo online tatil sitesinin otel özelliklerini ve bu özelliklerin durumlarını (etkin veya pasif) saklamak için kullanılır. İlk sütun olan "Id" her bir özelliğin benzersiz bir kimlik numarası ile tanımlandığını gösterir ve her kaydı ayrı bir entite olarak izlenebilir kılar. "Name" sütunu özelliğin adını içerir. Örneğin "Ücretsiz Wi-Fi" gibi. "IsActive" sütunu özelliğin etkin veya pasif olduğunu belirtir. Bu sayede özelliklerin görüntülenip görüntülenmeyeceğini kontrol etmek için kullanılır. "CreatedDate" ve "UpdatedDate" sütunları her özelliğin oluşturulma ve güncelleme tarihlerini saklar. Bu sayede özelliklerin yönetimini ve güncellemelerini izler.

Bu tablo online tatil sitesindeki otel özelliklerini yönetmek için kullanılır. Her bir kayıt bir özelliği ve bu özelliğin durumunu temsil eder. Bu bilgiler otellerin sunduğu özellikleri ve kullanıcıların arama ve karşılaştırma yaparken bu özellikleri görmelerini sağlar. Özellikle kullanıcılar belirli bir özelliği seçerek otelleri filtreleyebilir ve aradıkları özelliklere sahip otelleri daha kolay bulabilirler.

-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

## 15. Tags Tablosu

![resim](https://github.com/AhmetSahinNL/TatilBudurOrnekDataBaseTasarimi/assets/139613517/cd37cb69-6951-46e8-ae5d-3ee8fae2110b)

```MSSQL
Id
Name
IsActive
CreatedDate
UpdatedDate
```

AÇIKLAMA:

Bu tablo online tatil sitesinin otel özelliklerini ve bu özelliklerin durumlarını (etkin veya pasif) saklamak için kullanılır. İlk sütun olan "Id" her bir özelliğin benzersiz bir kimlik numarası ile tanımlandığını gösterir ve her kaydı ayrı bir entite olarak izlenebilir kılar. "Name" sütunu özelliğin adını içerir. Örneğin "Ücretsiz Wi-Fi" gibi. "IsActive" sütunu özelliğin etkin veya pasif olduğunu belirtir. Bu sayede özelliklerin görüntülenip görüntülenmeyeceğini kontrol etmek için kullanılır. "CreatedDate" ve "UpdatedDate" sütunları her özelliğin oluşturulma ve güncelleme tarihlerini saklar. Bu sayede özelliklerin yönetimini ve güncellemelerini izler.

Bu tablo online tatil sitesindeki otel özelliklerini yönetmek için kullanılır. Her bir kayıt bir özelliği ve bu özelliğin durumunu temsil eder. Bu bilgiler otellerin sunduğu özellikleri ve kullanıcıların arama ve karşılaştırma yaparken bu özellikleri görmelerini sağlar. Özellikle kullanıcılar belirli bir özelliği seçerek otelleri filtreleyebilir ve aradıkları özelliklere sahip otelleri daha kolay bulabilirler.

-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
