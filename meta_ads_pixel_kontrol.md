## Meta Ads ve Pixel Ayarlarında Kontrol Etmen Gereken Tüm Noktalar

Görselde sadece PageView ve ViewContent event’lerinin tetiklendiği görülüyor. Form gönderimi sonrası özel bir dönüşüm event’i (ör. Lead) görünmüyor.  
Aşağıdaki adımları kontrol ederek, hem pixel hem de Meta reklam ayarlarının doğru olduğundan emin olabilirsin:

---

### 1. **Meta Pixel Kurulumu**

- [ ] **Pixel kodu tüm sayfalarda yüklü mü?**  
  (PageView ve ViewContent event’leri her sayfada tetiklenmeli. Görselde bu doğru görünüyor.)
- [ ] **Form gönderimi sonrası Lead event’i tetikleniyor mu?**  
  (Şu anda eksik. Sadece form gönderimi sonrası Lead event’i eklemelisin.)

---

### 2. **Lead Event’i Ekleme (En Önemlisi!)**

**Teşekkür sayfası kullanıyorsan:**  
Teşekkür sayfasının koduna şunu ekle:
```html
fbq('track', 'Lead');
```

**Form AJAX ile gönderiliyorsa:**  
Quform’un JavaScript ayarlarına şunu ekle:
```javascript
document.addEventListener('quform:success', function () {
  fbq('track', 'Lead');
});
```

---

### 3. **Meta Events Manager (Olay Yöneticisi) Ayarları**

- [ ] **Pixel’in aktif ve doğru alan adına kurulu olduğundan emin ol.**
- [ ] **Lead event’i Events Manager’da görünüyor mu?**  
  (Form gönderimi test ettikten sonra burada Lead event’ini görebilmelisin.)

---

### 4. **Meta Reklam Paneli (Ads Manager) Ayarları**

- [ ] **Kampanya hedefi olarak “Lead” veya “Dönüşüm” seçili mi?**
- [ ] **Dönüşüm olarak sadece Lead event’i seçili mi?**  
  (PageView veya ViewContent dönüşüm olarak seçilmemeli.)
- [ ] **Kampanya, doğru pixel ve doğru event ile eşleşiyor mu?**

---

### 5. **Test ve Doğrulama**

- [ ] **Formu test ederek Lead event’inin sadece form gönderimi sonrası tetiklendiğini kontrol et.**
- [ ] **Meta Pixel Helper ile form gönderimi sonrası “Lead” event’ini görmelisin.**
- [ ] **Meta Events Manager’da test conversion ile Lead event’ini doğrula.**

---

### 6. **Ekstra Güvenlik ve Doğruluk**

- [ ] **Bot ve spam başvurulara karşı reCAPTCHA veya benzeri koruma ekle.**
- [ ] **Birden fazla Lead event’i tetiklenmediğinden emin ol (her başvuru için sadece bir kez).**

---

## Özet Kontrol Tablosu

| Kontrol Noktası                                 | Açıklama                                      | Durum   |
|-------------------------------------------------|-----------------------------------------------|---------|
| Pixel tüm sayfalarda yüklü                      | PageView ve ViewContent görünüyor             | ✔️      |
| Lead event’i sadece form sonrası tetikleniyor   | Teşekkür sayfası veya başarı mesajında         | ❌      |
| Events Manager’da Lead event’i gözüküyor        | Test sonrası kontrol et                        | ❓      |
| Reklam panelinde sadece Lead dönüşüm seçili     | Dönüşüm olarak PageView seçili olmamalı        | ❓      |
| Form testinde Lead event’i tetikleniyor         | Pixel Helper ile kontrol et                    | ❓      |

---

## Sonuç

Yukarıdaki tüm adımları kontrol edip eksikleri tamamlarsan, Meta reklamlarındaki lead sayısı ile Quform’daki gerçek başvuru sayın birebir eşleşir.  
Takıldığın bir adımda bana ekran görüntüsüyle tekrar ulaşabilirsin!

[1] https://pplx-res.cloudinary.com/image/private/user_uploads/17287615/c09879a3-c587-4c5b-aadd-4f082592c037/WhatsApp-Gorsel-2025-06-16-saat-13.24.27_964522de.jpg