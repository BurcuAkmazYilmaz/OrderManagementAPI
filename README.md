# OrderManagementAPI
OrderManagementAPI siparişlerin oluşturulması, değiştirilmesi, silinmesi ve görüntülenmesi için metotlar ve ayrıca müşteri  ve ürün eklenmesi gibi metotlar içerir.

<br/>

İlgili API kapsamında Customer, Product ve OrderProduct tabloları oluşturulmuştur. Tablolar için eklenen diyagram için ***Diyagram.png*** görseli eklenmiştir.

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
