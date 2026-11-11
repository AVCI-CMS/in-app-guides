# Kullanıcı Silme ve Hesap Kapatma (Deletion API)

Bu doküman, kullanıcıların kendi hesaplarını silmeleri (Unutulma Hakkı - GDPR/KVKK) veya yöneticilerin kullanıcı hesaplarını yönetimsel olarak kapatmaları için kullanılan endpointleri kapsar.

## 👥 Kullanıcı Tarafı (Hesabımı Sil)

Kullanıcının kendi hesabını silmesi için kullanılır. İki farklı silme modu desteklenir.

### 1. Hesabı Sil / Verileri Temizle
Kullanıcı oturum açtığında kendi hesabını silmek için bu endpoint'i kullanır.

**Endpoint:** `DELETE /v1/user/delete`

**Authentication:** Bearer Token (Zorunlu)

**Query Parameters:**
| Parametre | Tip | Açıklama |
| :--- | :--- | :--- |
| `mode` | `string` | `hard` (Varsayılan) veya `anonymize` |

**Silme Modları:**
1. **Hard Delete (`mode=hard`):** Kullanıcının tüm kişisel verileri, profili ve oluşturduğu içerikler (yorumlar, sipariş geçmişi vb.) veritabanından kalıcı olarak silinir. Bu işlem geri alınamaz.
2. **Anonymization (`mode=anonymize`):** Kullanıcının kişisel verileri (ad, soyad, e-posta, telefon vb.) silinir veya anonim hale getirilir, ancak oluşturduğu içerikler (siparişler, yazılar vb.) "Anonim Kullanıcı" etiketiyle sistemde tutulmaya devam eder (veri takibi/istatistik için).

**Response:**
```json
{
  "status": "success",
  "message": "User data deleted/anonymized successfully"
}
```

---

## 🛡️ Yönetici Tarafı (Kullanıcı Silme)

Yöneticilerin belirli bir kullanıcıyı sistemden silmesi veya verilerini temizlemesi için kullanılır.

### 1. Kullanıcıyı Yönetimsel Olarak Sil
Belirli bir kullanıcı ID'sini hedefleyerek hesabı kapatır.

**Endpoint:** `DELETE /v1/user/admin-delete/:id`

**Authentication:** Bearer Token (Zorunlu: `User:Edit` izni gerekir)

**Query Parameters:**
| Parametre | Tip | Açıklama |
| :--- | :--- | :--- |
| `mode` | `string` | `hard` veya `anonymize` (Kullanıcı tarafındakiyle aynı mantık) |

**Response:**
```json
{
  "status": "success",
  "message": "User deleted/anonymized by admin"
}
```

---

## 🏗️ Teknik Detaylar

- **İçerik Temizliği:** Silme işlemi sadece `User` tablosunu değil, kullanıcının ilişkili olduğu `Order`, `Comment`, `Ticket` gibi tüm modülleri tarayarak ilgili verileri temizler veya anonimleştirir.
- **Güvenlik:** Kendi hesabını silme (delete-me) işlemi sadece giriş yapmış kullanıcılar için geçerlidir. Admin silme işlemi ise sadece yüksek yetkili personeller tarafından gerçekleştirilebilir.
- **Geri Dönüş:** Silme işlemi yapıldıktan sonra istemci (Frontend/Mobile) tarafında `accessToken` ve `refreshToken` verilerinin temizlenmesi ve kullanıcının giriş ekranına yönlendirilmesi beklenir.
