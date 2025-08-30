# Earthquake-Warning-system

Kişisel Deprem Uyarı Sistemi (n8n)
Bu proje, n8n otomasyon platformu kullanılarak geliştirilmiş, kişisel ve gerçek zamanlı bir deprem uyarı sistemidir. Kandilli Rasathanesi ve Deprem Araştırma Enstitüsü'nün (KRDAE) canlı deprem verilerini kullanarak, kullanıcının dinamik konumuna yakın ve belirlenen büyüklüğün üzerindeki sarsıntıları anında Telegram üzerinden bildirir.

(NOT: Yukarıdaki görsel yolunu kendi dosya adınızla güncelleyin.)

Projenin Amacı
Türkiye'nin bir deprem ülkesi olduğu gerçeğinden yola çıkarak, genel deprem bildirimlerinden ziyade, kişisel olarak risk oluşturabilecek, yani yakın çevremde gerçekleşen ve belirli bir büyüklüğün üzerindeki sarsıntılardan anında haberdar olma ihtiyacını karşılamak amacıyla geliştirilmiştir.

Özellikler
Gerçek Zamanlı Veri: Kandilli Rasathanesi'nin API'sinden her dakika canlı verileri çeker.

Dinamik Konum Takibi: Bir Android cihazdan (MacroDroid ile) gelen veriler sayesinde kullanıcının konumu periyodik olarak güncellenir.

Kişiselleştirilebilir Filtreler: Sadece belirlenen mesafe (örn: 50 km) ve minimum büyüklük (örn: 4.0) kriterlerine uyan depremler işleme alınır.

Anlık Bildirim: Kriterlere uyan depremler, tüm detaylarıyla (konum, büyüklük, derinlik, kullanıcıya uzaklık) birlikte anında Telegram mesajı olarak gönderilir.

Tekrarlanan Bildirim Engeli: Aynı deprem için tekrar tekrar bildirim gönderilmesini engelleyen bir kontrol mekanizması içerir.

Çalışma Prensibi
Sistem, birbiriyle entegre çalışan iki ana n8n iş akışından (flow) oluşur:

Konum Kaydetme Akışı:

Android cihazdaki MacroDroid uygulaması, 15 dakikada bir mevcut GPS konumunu tetikler.

Bu konum bilgisi bir Webhook aracılığıyla n8n'e gönderilir.

n8n, gelen konumu işleyerek Google Sheets'teki ilgili tabloya kaydeder.

Deprem Kontrol ve Bildirim Akışı:

Bu akış, bir Cron tetikleyicisi ile her dakika otomatik olarak çalışır.

Kandilli Rasathanesi API'sinden en son deprem verilerini çeker.

Google Sheets'ten en güncel kullanıcı konumunu okur.

Her bir depremin, kullanıcının konumuna olan uzaklığını hesaplar ve filtrelerden geçirir.

Eğer kriterlere uyan yeni bir deprem varsa, Telegram üzerinden özelleştirilmiş bir mesaj gönderir.

Kullanılan Teknolojiler
Otomasyon Platformu: n8n

Veri Kaynağı: Kandilli Rasathanesi ve Deprem Araştırma Enstitüsü (KRDAE) Canlı Veri API'si

Veritabanı/Depolama: Google Sheets

Bildirim Servisi: Telegram

Konum Tetikleyicisi: MacroDroid (Android) & n8n Webhooks

<img width="1335" height="587" alt="Image" src="https://github.com/user-attachments/assets/2282e933-bedd-4f8d-96b3-fc73a3ea3866" />

![Image](https://github.com/user-attachments/assets/498e0da5-8745-4e9e-abcb-e31c3b7b32d2)

