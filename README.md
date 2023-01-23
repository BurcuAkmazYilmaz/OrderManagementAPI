# OrderManagementAPI
OrderManagementAPI siparişlerin oluşturulması, değiştirilmesi, silinmesi ve görüntülenmesi için metotlar ve ayrıca müşteri  ve ürün eklenmesi gibi metotlar içerir.

## Genel Yapı

ASP.NET Core Web API tipinde proje açılarak .NET 6 ile geliştirilmiştir. Log yapısı için **Microsoft.Extensions.Logging.Log4Net.AspNetCore** kullanılmıştır. Data katmanında *Repository* ve *UnitOfWork* pattern'leri kullanılmıştır.

OrderManagementAPI solution'ı altına OrderManagementAPI, OrderManagementData, OrderManagementServices projeleri eklenmiştir. Bu solution ve projeler ile ilgili görseller eklenmiştir -> ***Solution.png***, ***OrderManagementAPI.png***, ***OrderManagementData.png***, ***OrderManagementServices.png*** 

## Veritabanı ve Tablo Bilgileri

İlgili API kapsamında SQLServer'da OnlineRetailCompany isimli veritabanı ve Customer, Product ve OrderProduct tabloları oluşturulmuştur. 

Tablolar için eklenen diyagram için ***Diyagram.png*** görseli eklenmiştir.
Oluşturulan OnlineRetailCompany isimli veritabanı için ***OnlineRetailCompany.bak*** dosyası eklenmiştir.

Customer tablosuna ait alanlar ve açıklamaları aşağıda verilmiştir.

| Property Name | Description | Nullable |
| :---          | :---        | :---: |
| Id | Müşteri için unique değer tutar. | + |
| Name | Müşterinin adını tutar. | + |
| Address | Müşterinin adres bilgisini tutar. | + |

Product tablosuna ait alanlar ve açıklamaları aşağıda verilmiştir.

| Property Name | Description | Nullable |
| :---          | :---        | :---: |
| Id | Ürün için unique değer tutar. | + |
| Barcode | Ürün barkod bilgisini tutar. | + |
| Description | Ürün açıklama bilgisini tutar. | - |
| Quantity | Ürün miktar bilgisini tutar. | - |
| Price | Ürün fiyat bilgisini tutar. | + |

CustomerOrder tablosuna ait alanlar ve açıklamaları aşağıda verilmiştir.

| Property Name | Description | Nullable |
| :---          | :---        | :---: |
| Id | Ürün için unique değer tutar. | + |
| OrderId | Sipariş için unique değer tutar. | + |
| CustomerId | Müşteri unique değeri tutar. | + |
| ProductId | Ürün unique değeri tutar. | + |
| Quantity | Sipariş ürün miktarı bilgisini tutar. | + |
| Address | Sipariş adresi bilgisini tutar. | + |

<br/>

## API Swagger

OrderManagementAPI projesi için swagger arayüzü ekran görüntüsü ***OrderManagementAPI_swagger.png*** görseli ile verilmiştir. Schemas altında request için kullanılacak modeller ve ilgili metotların response modelleri yer almaktadır. Ayrıca bu proje kapsamında sadece siparişler ile ilgileniceğinden Customer ve Product için eklenen metotlar açıklanmamıştır. Bu metotlar sipariş için debug yapılabilmesi için eklenmiştir.

### CustomerOrder/GetCustomerOrderByOrderID metodu
Sipariş numarasına göre sipariş bilgisini verir. Sipariş bilgisi için kullanılacak response modeli ***OrderResultModel*** olarak verilmiştir.
**A76EF935-45E5-4AB4-8BC7-C12DE06DDBC4** numaralı sipariş için metot çıktısı ***OrderIDResponse.png*** görselinde verilmiştir.

### CustomerOrder/GetCustomerOrderByCustomerID metodu
Müşteri numarasına göre sipariş listesini verir. Sipariş listesi için kullanılacak response modeli ***OrderListModel*** olarak verilmiştir.
**A46440CF-C6BD-4778-B3FC-EF1050202C9C** numaralı müşteri için alınan sipariş listesi ***CustomerIDResponse.png*** görselinde verilmiştir.

### CustomerOrder/CreateCustomerOrder metodu
Sipariş kaydetmek için kullanılır. Sipariş eklemek için kullanılacak request modeli ***OrderCreateModel*** olarak verilmiştir.
Yeni sipariş eklemek için örnek request ***CreateCustomerOrderRequest.json*** dosyasında verilmiştir. Ayrıca ilgili request görseli ***CreateCustomerOrderRequest.png*** görselinde verilmiştir.

### CustomerOrder/UpdateCustomerOrder metodu
Sipariş güncellemek için kullanılır. Sipariş güncelleme işleminde sipariş adresi değiştirilebilir; mevcut ürünün miktarı değiştirilebilir; mevcut ürün silinebilir veya yeni ürün eklenebilir. Sipariş güncellemek için kullanılacak request modeli ***OrderUpdateModel*** olarak verilmiştir.
Sipariş güncellemek için örnek request ***UpdateCustomerOrderRequest.json*** dosyasında verilmiştir. Ayrıca ilgili request görseli ***UpdateCustomerOrderRequest.png*** görselinde verilmiştir.

### CustomerOrder/DeleteCustomerOrder metodu
Sipariş silmek için kullanılır. Unique sipariş numarası ile sipariş silinir.
