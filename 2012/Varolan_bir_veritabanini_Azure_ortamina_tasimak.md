---
FallbackID: 2773
Title: Varolan bir veritabanını Azure ortamına taşımak!
PublishDate: 6/5/2012
EntryID: Varolan_bir_veritabanini_Azure_ortamina_tasimak
IsActive: True
Section: software
MinutesSpent: 0
Tags: SQL Azure, Windows Azure
---
**[Aşağıdaki makalenin SDK2.5 ile beraber yeni Azure özelliklerine uygun
veritabanı ile nasıl ilerleyebileceğinizi kestiremiyorsunuz. Gelin o
zaman beraber bir göz atalım. Birincisi ilk olarak web panelinde nasıl
araçlarımız var bir ona bakalım.

![SQL Azure veritabanını
yönetmek.](http://cdn.daron.yondem.com/assets/2773/sqlmanage.png)
*SQL Azure veritabanını yönetmek.*

SQL Azure üzerinde yarattığınız bir veritabanını yönetmek isterseniz en
kolay yöntemlerden biri web üzerinden kullanılabilen management studio
tadındaki Silverlight uygulaması. Uygulama açıldıktan sonra admin
kullanıcı adı ve şifresini girerseniz herşey kendini yavaş yavaş
göstermeye başlayacaktır.

![Web tabanlı SQL Management
Studio](http://cdn.daron.yondem.com/assets/2773/sqlmanage2.png)
*Web tabanlı SQL Management Studio*

Güzel bir Metro UI implementasyonu olan web tabanlı SQL Management
Studio tamamen Silverlight ile yazılmış durumda. Uygulama içerisinde
veritabanınız tasarım sürecinde ihtiyacınız olacak çoğu şeyi bulmakla
beraber performans analizi (Query Analyzer) gibi şeyleri de
kullanabilirsiniz. Eğer web tabanlı araçların hayranı değilseniz :) tabi
ki hala masaüstünüzdeki SQL Server Management Studio da işinizi
görebilir.

### Var olan bir veritabanını Azure'a taşımak

Gelelim asıl konumuza. Elimizdeki bir veritabanı var ve onu SQL Azure
ortamına taşımak istiyoruz. En basit yöntemlerden biri veritabanınızın
scriptini alıp SQL Azure'a doğru çalıştırmak :) Bunu yaparken dikkat
etmeniz gereken birkaç ufak nokta var, isterseniz onlara bir bakalım.

![Bildiğimiz "Generate
Scripts"](http://cdn.daron.yondem.com/assets/2773/sqlmanage3.png)
*Bildiğimiz "Generate Scripts"*

Bildiğimiz eski teknikler ile **Generate Scripts** diyerek yola
çıkacağız. Ama bunu yapmadan önce SQL Server Management Studio'nun 2008
R2 sürümüne sahip olduğunuzdan emin olun. Aksi halde göreceğimiz bazı
seçenekler maalesef sizdeki kopyalarda bulunmayacaktır.

"Generate Scripts" sihirbazında yolunuza devam ederken, tam da Script'i
nereye kaydetmek istediğiniz sorusu geldiğinde durun ve :) "Advanced"
düğmesine tıklayın.

![SQL Azure yolunda ufak
ayarlar.](http://cdn.daron.yondem.com/assets/2773/sqlmanage4.png)
*SQL Azure yolunda ufak ayarlar.*

Yukarıdaki üç farklı ayar sanırım ekran görüntüsünde net olarak
gözüküyordur :) Biri UDDT'lerden vaz geçmek anlamına geliyor. Diğeri ise
"USE" keyword'ü ve filegroup gibi ayarlarla ilgili T-SQL'lerin
yaratılmamasını sağlamak adına "Database Engine Type"ı değiştiriyor, son
ayar ise sadece veritabanı şemasını değil berbarinde datayı da almamızı
sağlıyor.

Tüm bu ayarlarla beraber aldığınız bir script SQL Azure tarafında %99.95
:) çalışacaktır.

Hepinize kolay gelsin ;)

