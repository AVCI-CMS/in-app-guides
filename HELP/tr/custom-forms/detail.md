# Form Yönetimi: Tasarım, Alanlar ve İnceleme

> 💡 **Adım adım kullanım rehberi ve detaylı iş akışları için:**  
> Kapsamlı kullanıcı kılavuzuna [AVCI CMS Dokümantasyon Portalı](https://doc.avcicms.com/docs/guides/modules/communication/custom-forms) üzerinden ulaşabilirsiniz.

Form alanlarını dinamik olarak tasarlayabilir, sistem nitelikleri ile akıllı eşleme yapabilir ve gelen başvuruları 2 sütunlu inceleme ekranında yönetebilirsiniz.

---

## 🛠️ Alan Yapılandırması ve Türler

* **Standart Girdi Alanları:** Metin, Sayı, E-posta, Tarih, Uzun Metin (Textarea), Telefon.
* **Seçim Elemanları:** Açılır Liste (Select), Tekil Seçim (Radio), Çoklu Seçim (Checkbox).
* **Dosya ve Belgeler:** Boyut ve format kısıtlamalı dosya yükleme alanları (Örn: Vergi Levhası PDF).
* **İç İçe Gruplar (`OBJECT`):** İlgili alt alanları tek bir nesnede toplayan yapılar (Örn: Yetkili Temsilci Bilgileri).

---

## ⚡ Akıllı Nitelik Eşleme (Smart Mapping)

Başvuru amaçlı formlarda (`MERCHANT_APPLICATION`, `BRAND_APPLICATION`, `ORGANIZATION_APPLICATION`), form alanını doğrudan bir varlık niteliğine bağlayabilirsiniz:
1. İlgili alandaki **"Varlık Niteliğine Bağla"** seçeneğini açın.
2. Açılır listeden ilgili niteliği seçin.
3. Başvuru onaylandığında bu alana girilen değer otomatik olarak oluşturulan varlığın normalize `attributes` dizisine aktarılır.

---

## 🚦 İki Sütunlu Başvuru İnceleme Alanı

`/custom-forms/:id/answers/:subId` adresindeki başvuru inceleme ekranında:
* **Sol Sütun:** Başvuru sahibinin doldurduğu tüm alanları, belgeleri ve nitelik eşleme önizlemelerini listeler.
* **Sağ Sütun:** Durum geçişlerini (`PENDING` &rarr; `UNDER_REVIEW` &rarr; `APPROVED` / `REJECTED`), ekip içi notları ve tek tıkla varlık oluşturma aksiyonunu yönetir.

> 📖 **Detaylı Rehber:** [Özel Formlar ve Başvuru Süreçleri](https://doc.avcicms.com/docs/guides/modules/communication/custom-forms)
