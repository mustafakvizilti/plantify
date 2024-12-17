Giriş 
Doğayla etkileşim ve çevre bilinci modern yaşamda önem kazanmıştır. Ancak şehirleşme nedeniyle insanlar 
doğal ortamlardan uzaklaşmıştır. Bu proje, kullanıcıların sanal bir bahçe oluşturmasını, bitki bilgileri edinmesini 
ve hava durumu bilgilerini görüntülemesini sağlayan bir mobil uygulama geliştirmeyi amaçlamaktadır. Ana 
hedefler: 
1. Kullanıcı ve admin hesap yönetimi. 
2. OpenWeatherMap API ile hava durumu bilgisi. 
3. Trefle API ile rastgele bitki bilgisi sunulmasıdır. 
Yöntem 
Uygulama, Kotlin ile geliştirilmiş ve Android Studio’da tasarlanmıştır. Veriler Firebase ile saklanmış, 
OpenWeatherMap API hava durumu, Trefle API ise bitki bilgisi sunmuştur. 
Ana fonksiyonlar: 
 Hesap Yönetimi: Firebase Authentication ile kullanıcı ve admin giriş işlemleri yapılmıştır. 
 Hava Durumu Bilgisi: Kullanıcının konumuna göre hava durumu gösterimi sağlanmıştır. 
 Rastgele Bitki Bilgisi: Trefle API ile rastgele bitki bilgileri alınmıştır. 
Sözde Kod 
PROGRAM SanalBahçe 
START 
DISPLAY "Uygulama Ana Ekranı" 
DISPLAY "Kullanıcı Girişi, Admin Girişi, Hava Durumu, Rastgele Bitki 
Bilgisi" butonları 
WHILE Kullanıcı uygulama açık 
IF Kullanıcı "Kullanıcı Girişi" butonuna tıklar THEN 
CALL KullanıcıGirisEkrani() 
ELSE IF Kullanıcı "Admin Girişi" butonuna tıklar THEN 
CALL AdminGirisEkrani() 
ELSE IF Kullanıcı "Hava Durumu" butonuna tıklar THEN 
CALL HavaDurumuEkrani() 
ELSE IF Kullanıcı "Rastgele Bitki Bilgisi" butonuna tıklar THEN 
CALL RastgeleBitkiEkrani() 
END IF 
END WHILE 
END PROGRAM 
FUNCTION KullanıcıGirisEkrani() 
DISPLAY "Kullanıcı adı ve şifre giriş ekranı" 
IF Giriş bilgileri doğru THEN 
DISPLAY "Başarıyla giriş yaptınız" 
CALL KullanıcıAnaEkranı() 
ELSE 
DISPLAY "Hatalı giriş bilgileri" 
END IF 
END FUNCTION 
FUNCTION AdminGirisEkrani() 
DISPLAY "Admin giriş ekranı" 
IF Giriş bilgileri doğru THEN 
DISPLAY "Admin paneline hoş geldiniz" 
CALL AdminPaneli() 
ELSE 
DISPLAY "Hatalı giriş bilgileri" 
END IF 
END FUNCTION 
FUNCTION HavaDurumuEkrani() 
INPUT Kullanıcıdan "Şehir Adı" 
CALL OpenWeatherMapAPI(şehir_adı) 
IF API_Cağrısı_Başarılı THEN 
DISPLAY "Hava durumu: sıcaklık ve açıklama" 
ELSE 
DISPLAY "Hata: API'ye ulaşılamadı" 
END IF 
END FUNCTION 
FUNCTION RastgeleBitkiEkrani() 
CALL TrefleAPI() 
IF API_Cağrısı_Başarılı THEN 
DISPLAY "Bitki Adı ve Bilimsel Ad" 
ELSE 
DISPLAY "Hata: API'ye ulaşılamadı" 
END IF 
END FUNCTION 
FUNCTION OpenWeatherMapAPI(şehir_adı) 
SEND GET request TO "https://api.openweathermap.org/data/2.5/weather" 
WITH PARAMETERS: şehir_adı, API_KEY 
RECEIVE response 
RETURN sıcaklık ve açıklama 
END FUNCTION 
FUNCTION TrefleAPI() 
SEND GET request TO "https://trefle.io/api/v1/plants/random" 
WITH PARAMETERS: API_KEY 
RECEIVE response 
RETURN bitki_adı ve bilimsel_ad 
END FUNCTION 
FUNCTION KullanıcıAnaEkranı() 
DISPLAY "Sanat bahçesine bitki ekleyebilir veya mevcut bahçeyi 
görüntüleyebilirsiniz" 
WHILE Kullanıcı seçim yapıyor 
IF Kullanıcı "Bitki Ekle" seçerse THEN 
CALL BitkiEkle() 
ELSE IF Kullanıcı "Bahçeyi Görüntüle" seçerse THEN 
CALL BahceGoruntule() 
END IF 
END WHILE 
END FUNCTION 
FUNCTION BitkiEkle() 
DISPLAY "Bitki adı girin ve 4 farklı resim arasından seçim yapın" 
SAVE Bitki adı ve seçilen resim TO Firebase Veritabanı 
DISPLAY "Bitki başarıyla eklendi" 
END FUNCTION 
FUNCTION BahceGoruntule() 
FETCH Kullanıcı bahçesindeki bitkiler FROM Firebase Veritabanı 
DISPLAY Kullanıcı bahçesindeki bitkilerin listesi 
END FUNCTION 
FUNCTION AdminPaneli() 
DISPLAY "Kullanıcıları yönet, sistem loglarını görüntüle" 
WHILE Admin seçim yapıyor 
IF Admin "Kullanıcıyı Yönet" seçerse THEN 
CALL KullanıcıYönet() 
ELSE IF Admin "Logları Görüntüle" seçerse THEN 
CALL LoglariGoruntule() 
END IF 
END WHILE 
END FUNCTION 
FUNCTION KullanıcıYönet() 
DISPLAY "Kullanıcıları listele ve düzenle" 
END FUNCTION 
Deneysel Sonuçlar 
 Hesap Yönetimi: Kullanıcı ve admin giriş işlemleri Firebase ile başarıyla yapılmıştır. 
 Hava Durumu: OpenWeatherMap API’den doğru veriler alınmıştır. 
 Rastgele Bitki Bilgisi: Trefle API farklı bitkilerin bilgilerini hızlıca göstermiştir. 
 Performans: Gerçek cihazlarda yapılan testlerde hızlı ve sorunsuz bir deneyim sağlanmıştır. 
Sonuç 
Bu proje, kullanıcıların doğa ile bağlantısını güçlendiren yenilikçi bir platform sunmuştur. Hava durumu 
bilgileri, bitki veritabanı ve kullanıcı dostu tasarımıyla uygulama, çevre bilincini artırmayı hedeflemiştir. 
Gelecekte ek özelliklerle kapsamı genişletilebilir. 
ÖZET 
Bu proje, kullanıcıların dijital bir platform üzerinden sanal bir bahçe oluşturmasını sağlayan, modern teknolojiler 
ve API entegrasyonları ile desteklenmiş bir mobil uygulamadır. Uygulama, kullanıcıların bitkiler hakkında bilgi 
edinmelerine, sanal bahçelerine bitki eklemelerine ve gerçek zamanlı hava durumu bilgilerine erişmelerine 
olanak tanır. Bu amaçla, Firebase ile kullanıcı kimlik doğrulama ve veri yönetimi, OpenWeatherMap API ile 
hava durumu bilgileri ve Trefle API ile rastgele bitki bilgisi sağlanmıştır. Proje, kullanıcı dostu bir arayüzle 
çevre bilincini artırmayı ve interaktif bir öğrenme deneyimi sunmayı hedeflemektedir. 
KAYNAKÇA 
1. OpenWeatherMap API: https://openweathermap.org/api 
2. Trefle API: https://trefle.io 
3. Firebase Documentation: https://firebase.google.com/docs 
4. Android Developer Documentation: https://developer.android.com 
One drive linki: https://1drv.ms/f/c/629897f368feecd5/Esxqsgb-
q71LqHVxfstHe5cBc2dBhcGvQecEFxpklIH07Q?e=N2ePRZ# plantify
