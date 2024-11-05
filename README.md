# BMÜ329 Veri Tabanı Sistemleri Dersi Dönem Projesi Gereksinimleri ve E-R Diyagramı Formatı

## Proje Başlığı
**Dijital Oyun Platformlarında Dinamik Listeleme ve Keşif Sistemi**

## Proje Ekibindeki Kişiler
**Furkan Boynueğri, Eren Güzel, Eren Albayrak**

---

## 1. Dönem Projesi Gereksinimleri

Projemiz dijital oyun platformu veri tabanını kapsayacaktır. Bu platformda kullanıcı olarak giriş yapıp piyasadaki oyunları satın alma, indirme, oynama; arkadaşlar ve topluluklarla etkileşimde bulunma; platform üzerinden oynanacak oyunun bazı kontrol ayarlarını yapma gibi işlemler gerçekleştirilebilecektir.
### Genel Gereksinimler ve İşlemler

## 1. Kullanıcı Yönetimi
- **Kullanıcı Kaydı ve Girişi**: Kullanıcılar platforma kaydolabilir ve giriş yapabilirler.
- **Profil Yönetimi**: Kullanıcılar kişisel bilgilerini güncelleyebilir, hesap ayarlarını düzenleyebilirler.
- **Arkadaşlık İlişkileri**: Kullanıcılar diğer kullanıcıları arkadaş olarak ekleyebilir ve arkadaşlık talepleri gönderebilirler.
- **Mesajlaşma**: Arkadaşlar arasında mesajlaşma imkanı sunulmaktadır.
  
## 2. Oyun Yönetimi
- **Oyun Listesi Görüntüleme**: Kullanıcılar platformdaki oyunları kategoriler ve fiyatlarla görüntüleyebilirler.
- **Oyun Arama**: Belirli oyunlar arama fonksiyonu aracılığıyla bulunabilir.
- **Oyun Satın Alma**: Kullanıcılar oyunları platform üzerinden satın alabilirler.
- **Oyun İndirme ve Yükleme**: Satın alınan oyunlar indirilebilir ve yüklenebilir.
  
## 3. Oyun Aktivitesi
- **Oynanan Oyunlar**: Kullanıcıların oynadıkları oyunlar kaydedilir ve oyun aktiviteleri izlenebilir.
- **Oyun Süresi Takibi**: Kullanıcıların oyunları oynama süreleri kaydedilir.
  
## 4. Topluluk Yönetimi
- **Topluluklara Katılım**: Kullanıcılar farklı topluluklara katılabilir ve topluluk içindeki etkinliklere katılabilirler.
- **Topluluk İçi Etkileşim**: Topluluklar içinde içerik paylaşılabilir, yorum yapılabilir.
  
## 5. Oyun Ayarları
- **Grafik ve Ses Ayarları**: Kullanıcılar, oyunların grafik ve ses ayarlarını değiştirebilirler.
- **Dil Seçenekleri**: Platform dilini kullanıcı tercihine göre ayarlayabilirler.
- **Bildirim Ayarları**: Bildirim tercihleri düzenlenebilir, hangi bildirimlerin alınacağı belirlenebilir.

## 6. Başarılar
- **Başarı Sistemi**: Kullanıcılar oyunlarındaki başarıları takip edebilirler.
- **Başarı Kazanma**: Kullanıcılar oyun içindeki başarıları kazanabilir ve bunları profilinde görüntüleyebilirler.

## 7. Ödeme İşlemleri
- **Ödeme Yapma**: Kullanıcılar oyunları satın almak için ödeme yapabilirler.
- **Ödeme Geçmişi**: Kullanıcılar geçmiş ödeme işlemlerini görüntüleyebilirler.
  
## 8. Kullanıcı İlişkileri
- **Arkadaşlık İlişkileri**: Kullanıcılar birbirini arkadaş olarak ekleyebilir, arkadaşlık talepleri gönderebilir ve alabilirler.
- **Topluluk Etkileşimi**: Kullanıcılar, topluluk üyeleri ile etkileşimde bulunabilir, içerik paylaşabilirler.


---

## 2. Varlıklar ve Nitelikler

### 2.1 Kullanıcılar (Users)

- **Nitelikler**:
  - KullanıcıID (PK): Benzersiz kullanıcı tanımlayıcısı.
  - KullanıcıAdı: Kullanıcının platformdaki adı.
  - Email: Kullanıcının e-posta adresi (Benzersiz).
  - Parola: Güvenlik için hashlenmiş şifre bilgisi.
  - KayıtTarihi: Kullanıcının kayıt olduğu tarih.
  - Durum: Kullanıcının aktif veya pasif durumu.
- **Kısıtlamalar**:
  - Email benzersiz olmalıdır.
- **İlişkiler**:
  - Satın Almalar tablosu ile 1-n: Bir kullanıcı birden fazla oyun satın alabilir, ancak her satın alma işlemi yalnızca bir kullanıcıya aittir.
  - Oyun Aktivitesi tablosu ile 1-n: Bir kullanıcı birden fazla oyunu oynayabilir ve her oyun aktivitesi yalnızca bir kullanıcıya aittir.

---

### 2.2 Oyunlar (Games)

- **Nitelikler**:
  - OyunID (PK): Benzersiz oyun tanımlayıcısı.
  - OyunAdı: Oyunun adı (Benzersiz).
  - Açıklama: Oyun hakkında açıklama metni.
  - Fiyat: Oyunun satış fiyatı.
  - KategoriID (FK): Oyunun ait olduğu kategoriye referans.
  - Geliştirici: Oyunun geliştiricisi.
- **Kısıtlamalar**:
  - OyunAdı benzersiz olmalıdır.
  - Fiyat sıfır veya pozitif olmalıdır.
- **İlişkiler**:
  - Kategoriler tablosu ile 1-n: Her oyun yalnızca bir kategoriye ait olabilir, ancak bir kategoride birden fazla oyun bulunabilir.
  - Oyun Aktivitesi tablosu ile 1-n: Bir oyun birden fazla kullanıcı tarafından oynanabilir ve her oynama aktivitesi tek bir oyuna aittir.

---

### 2.3 Kategoriler (Categories)

- **Nitelikler**:
  - KategoriID (PK): Benzersiz kategori tanımlayıcısı.
  - KategoriAdı: Kategorinin adı (Benzersiz).
- **Kısıtlamalar**:
  - KategoriAdı benzersiz olmalıdır.
- **İlişkiler**:
  - Oyunlar tablosu ile 1-n: Bir kategoriye birden fazla oyun ait olabilir, ancak her oyun yalnızca bir kategoriye aittir.

---

### 2.4 Ayarlar (Settings)

- **Nitelikler**:
  - AyarID (PK): Benzersiz ayar tanımlayıcısı.
  - KullanıcıID (FK): Ayarların ait olduğu kullanıcıya referans.
  - Dil: Platform dili seçeneği.
  - GörselAyarlar: Grafik ve çözünürlük ayarları.
  - SesAyarları: Ses seviyesi ve diğer ses ayarları.
  - BildirimAyarları: Bildirimlerin durumu ve tercihleri.
- **Kısıtlamalar**:
  - Her kullanıcıya ait yalnızca bir ayar kaydı olabilir (1-1).
- **İlişkiler**:
  - Kullanıcılar tablosu ile 1-1: Her kullanıcıya ait yalnızca bir ayar kaydı olabilir.

---

### 2.5 Ödemeler (Payments)

- **Nitelikler**:
  - ÖdemeID (PK): Benzersiz ödeme işlemi tanımlayıcısı.
  - KullanıcıID (FK): Ödemeyi yapan kullanıcıya referans.
  - OyunID (FK): Ödeme yapılan oyuna referans.
  - ÖdemeTarihi: Ödemenin yapıldığı tarih.
  - Tutar: Ödemenin toplam tutarı.
  - Durum: Ödeme durumu (tamamlandı, beklemede).
- **Kısıtlamalar**:
  - Tutar pozitif olmalıdır.
- **İlişkiler**:
  - Kullanıcılar ve Oyunlar tabloları ile 1-n: Bir kullanıcı birden fazla ödeme yapabilir ve her ödeme yalnızca bir kullanıcıya aittir. Aynı şekilde, bir oyun farklı kullanıcılar tarafından defalarca satın alınabilir.

---

### 2.6 Arkadaşlar (Friends)

- **Nitelikler**:
  - Kullanıcı1ID (FK): Arkadaşlık isteği gönderen kullanıcıya referans.
  - Kullanıcı2ID (FK): Arkadaşlık isteği alan kullanıcıya referans.
  - Durum: Arkadaşlık isteğinin durumu (kabul edildi, reddedildi, beklemede).
  - OluşturmaTarihi: Arkadaşlık isteğinin gönderildiği tarih.
- **Kısıtlamalar**:
  - Kullanıcı1ID ve Kullanıcı2ID çifti benzersiz olmalıdır.
- **İlişkiler**:
  - Kullanıcılar tablosu ile n-m: Bir kullanıcı birden fazla kullanıcıyı arkadaş olarak ekleyebilir ve bir kullanıcı, birçok kullanıcı tarafından arkadaş olarak eklenebilir.

---

### 2.7 Topluluklar (Communities)

- **Nitelikler**:
  - ToplulukID (PK): Benzersiz topluluk tanımlayıcısı.
  - Ad: Topluluk adı (Benzersiz).
  - Açıklama: Topluluğun amacı hakkında açıklama.
- **Kısıtlamalar**:
  - Ad benzersiz olmalıdır.
- **İlişkiler**:
  - Topluluk Üyelikleri tablosu ile 1-n: Bir topluluğa birçok kullanıcı katılabilir.

---

### 2.8 Topluluk Üyelikleri (CommunityMemberships)

- **Nitelikler**:
  - KullanıcıID (FK): Topluluğa katılan kullanıcıya referans.
  - ToplulukID (FK): Kullanıcının katıldığı topluluğa referans.
  - KatılımTarihi: Topluluğa katılım tarihi.
- **İlişkiler**:
  - Kullanıcılar ve Topluluklar tabloları ile n-m: Bir kullanıcı birden fazla topluluğa katılabilir ve bir topluluk birçok kullanıcıyı içerebilir.

---

### 2.9 Başarılar (Achievements)

- **Nitelikler**:
  - BaşarıID (PK): Benzersiz başarı tanımlayıcısı.
  - BaşarıAdı: Başarının adı.
  - Açıklama: Başarı hakkında açıklama.
- **İlişkiler**:
  - Kullanıcı Başarıları tablosu ile 1-n: Her başarı birden fazla kullanıcı tarafından kazanılabilir.

---

### 2.10 Kullanıcı Başarıları (UserAchievements)

- **Nitelikler**:
  - KullanıcıID (FK): Başarıyı elde eden kullanıcıya referans.
  - BaşarıID (FK): Kullanıcının kazandığı başarıya referans.
  - KazanmaTarihi: Başarının kazanıldığı tarih.
- **İlişkiler**:
  - Kullanıcılar ve Başarılar tabloları ile n-m: Bir kullanıcı birden fazla başarı elde edebilir ve bir başarı birden fazla kullanıcı tarafından kazanılabilir.

---

### 2.11 Oyun Aktivitesi (GameActivity)

- **Nitelikler**:
  - AktiviteID (PK): Benzersiz aktivite tanımlayıcısı.
  - KullanıcıID (FK): Oyunu oynayan kullanıcıya referans.
  - OyunID (FK): Oynanan oyuna referans.
  - BaşlangıçTarihi: Oyunun oynanmaya başladığı tarih ve saat.
  - BitişTarihi: Oyunun oynanma süresinin sona erdiği tarih ve saat.
  - OynamaSüresi: Kullanıcının oyunda geçirdiği toplam süre.
- **Kısıtlamalar**:
  - OynamaSüresi pozitif olmalıdır.
- **İlişkiler**:
  - Kullanıcılar ve Oyunlar tabloları ile 1-n: Bir kullanıcı birden fazla oyun aktivitesine sahip olabilir.
