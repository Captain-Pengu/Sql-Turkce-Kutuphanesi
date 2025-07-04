# TrSql – Türkçe SQL Yardımcı Sınıfı (V0.1)

> 4 Temmuz 2025 tarihinde **Çağrı Sarıhanoğlu** (Takma adı: **PenguBey**) tarafından hazırlanmıştır.

Bu proje, C# ile MSSQL veritabanı kullananlar için basit, anlaşılır ve **TÜRKÇE** isimlendirilmiş bir yardımcı kütüphanedir.

Amacım, karmaşık `SqlConnection`, `ExecuteNonQuery` gibi şeylerle uğraşmak yerine işleri sadeleştirmek.  
Yeni başlayanlar da rahatlıkla kullanabilsin diye yazdım.

---

## 🔧 Özellikler

- SQL bağlantısını kontrol eder
- Bağlantıyı açma / kapatma
- Tablo oluşturma / silme
- Veri ekleme / güncelleme / silme
- Tabloyu DataTable olarak çekme (örneğin `DataGridView` için birebir)
- Arama fonksiyonu (LIKE ile)

---

## ⚙️ Kullanım Örnekleri

1. Sınıfı Başlat

    var db = new TrSql("Data Source=.;Initial Catalog=OrnekDb;Integrated Security=True;");
    db.BaglantiAc(); // Bağlantıyı aç

2. Tablo Ekle

    db.TabloEkle(@"CREATE TABLE Kisiler (Id INT PRIMARY KEY, Ad NVARCHAR(50))");

3. Veri Ekle

    db.VeriEkle("INSERT INTO Kisiler (Id, Ad) VALUES (1, N'Çağrı')");

4. Veri Güncelle

    db.VeriGuncelle("UPDATE Kisiler SET Ad = N'Ahmet' WHERE Id = 1");

5. Veri Sil

    db.VeriSil("DELETE FROM Kisiler WHERE Id = 1");

6. Tabloyu Getir

    DataTable dt = db.TabloGetir("Kisiler");
    // DataGridView.DataSource = dt;

7. Tablo İçinde Arama Yap

    DataTable sonuc = db.TabloAra("Kisiler", "Ad", "Çağrı");
    // Örnek: SELECT * FROM Kisiler WHERE Ad LIKE '%Çağrı%'

8. Bağlantıyı Kapat

    db.BaglantiKapat();

9. Hata Kontrolü

    Console.WriteLine(db.SqlHataKontrol);
    // Her işlem sonrası sonucu öğrenmek için kullanılır
