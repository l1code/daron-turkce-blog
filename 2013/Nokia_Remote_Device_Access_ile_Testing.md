---
FallbackID: 2863
Title: Nokia Remote Device Access ile Testing
PublishDate: 24/10/2013
EntryID: Nokia_Remote_Device_Access_ile_Testing
IsActive: True
Section: software
MinutesSpent: 0
Tags: Nokia, Windows 8, Windows 8.1, Windows Phone 8
---
Nokia tarafında yeni cihazlar çıktıkça cihaz çeşitliliği gün geçtikçe
artıyor. Durum böyle olunca uygulamalarınızı da bu farklı cihazlarda
test etmek ciddi sıkıntı olabilir. Tüm bu cihazlardan birer tane satın
alıp zulalama şansınız olmayacaktır. Özellikle bireysel olarak uygulama
geliştiren developerlar için bu iş epey zor. Seçeneklerden biri en
yüksek modeli veya belki de en alt modeli almak olabilir. En yüksek
modeli aldığınızda tüm özelliklere sahip bir telefonunuz varken en alt
model ise aslında en düşük performanslı telefonu temsil ettiği için
uygulamanızın tüm telefonlarda rahatlıkla çalışabileceğinden emin
olmanızı sağlayacaktır. Fakat işin için şimdilerde bir de farklı
Tablet'ler veya Phablet'ler girince :) konu daha da karışmaya başladı.
En son çıkan 1080P çözünürlüğe sahip Lumia 1520 yüksek çözünürlüğü ile
yeni test senaryolarına sebep olabilecekken tablet tarafında da Lumia
2520 geliyor. Gün geçtikçe bu cihazların çeşitliliği giderek artacak.

### Nokia Remote Device Access

Başlıktan da anlayabileceğiniz üzere aslında Nokia'nın **Nokia Developer
Program** çerçevesinde ilginç bir hizmeti var. Nokia Developer Program
üyeleri tüm Nokia cihazlarını uzaktan test amaçlı olarak rezerve
edebiliyor ve kullanabiliyorlar. Yani bugün gidip bir Lumia1020'ye
uzaktan istediğiniz bir süre için el koyup remote olarak kullanabilir,
uygulamanızı yükleyebilir ve test edebilirsiniz. İşiniz bittikten sonra
cihazı bırakıp çıkarsınız. Böylece tüm bu farklı cihazların elinizde
bulunması gerekmiyor ve test için ihtiyacınız olduğunda uzaktan
cihazları rezerve edip kullanabiliyorsunuz.

Tüm bu işlemleri Nokia'nın sitesinde "[Remote Device
Access](http://developer.nokia.com/Devices/Remote_device_access/)"
sayfasında başlıyor. "Start using RDA Now" dedikten sonra Nokia
Developer Program hesabınızla siteye giriş yapmanız gerek. Sonra
karşınıza çeşitli Nokia cihazlarının bir listesi geliyor.

![Nokia Remote Device Access'deki cihazların bir
kısmı.](media/Nokia_Remote_Device_Access_ile_Testing/rda_1.png)\
*Nokia Remote Device Access'deki cihazların bir kısmı.*

Bu liste içerisinden istediğiniz bir cihazı seçip uygun olduğu
aralıklarla istediğin süre için rezerve edebilirsiniz. Ben yukarıdaki
ekran görüntüsünde üzerinde hali hazırda SIM kartı da olan bir Lumia
1020 cihazını rezerve etmek için kolları sıvamıştım :) Cihaz listesi çok
geniş, o nedenle kesinlikle göz atmanızı tavsiye ederim. Rezervasyonu
tamamladıktan sonra "Start" dediğiniz anda bilgisayarınıza Java tabanlı
bir remote access yazılımı indirilecek. Bu yazılım üzerinden fiziksel
cihaza ulaşabileceksiniz.

![Remote Access için kullanacağımız
arayüz.](media/Nokia_Remote_Device_Access_ile_Testing/rda_2.png)\
*Remote Access için kullanacağımız arayüz.*

Ekran görüntüsünde de görebileceğiniz üzere telefonun tüm fiziksel
düğmeleri yazılımsal düğmelere atanmış durumda. İtiraf ediyim ki remote
olduğu için uygulamanızın performansı adına remote bağlantı kullanım
hissiyatını aktaramıyor ve teknik anlamda işlevsellik testleri için
bence süper bir seçenek. Remote bağlantı aracı hem ekran görüntüsü
almanızı hem de tüm oturumu videoya kaydetmenize de olanak sağlıyor.

![Kendi XAP dosyasını
atabilirsiniz.](media/Nokia_Remote_Device_Access_ile_Testing/rda_3.png)\
*Kendi XAP dosyasını atabilirsiniz.*

Remote Device Access Client'ının toolbarındaki **"Install Software"**
düğmesi ile XAP dosyanızı upload ederseniz doğrudan telefona
yüklenecektir. Böylece tüm testlerinizi gerçekleştirebilirsiniz. Şu an
için RDA'de Lumia 1520 ve 2520 cihazları yok ama çok yakında geleceği
haberlerini aldım :) O nedenle cihazları satın almayı planlamak yerine
belki de eğer elinizde yoksa bir Nokia Developer Account almayı
düşünebilirsiniz. Böylece tüm cihazlara test amaçlı ulaşabilirsiniz.

Hepinize kolay gelsin.


