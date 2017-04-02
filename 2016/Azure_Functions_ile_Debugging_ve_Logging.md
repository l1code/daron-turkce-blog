---
FallbackID: 3037
Title: Azure Functions ile Debugging ve Logging
PublishDate: 12/2/2016
EntryID: Azure_Functions_ile_Debugging_ve_Logging
IsActive: True
Section: software
MinutesSpent: 68
Tags: Azure Functions
---
Dünkü [Azure Functions giriş yazısı](http://daron.yondem.com/software/post/Azure_Functions_ile_ilk_Serverless_Maceramiz)ndan sonra Azure Functions ortamında Debugging için ne gibi özellikler bulunduğundan bahsetmek istiyorum. Hatırlarsanız local debugging özelliğinden zaten bahsetmiştik. Hatta doğrudan projemiz açıkken F5'e basıp local Azure Functions CLI'ı indirerek projeyi localde çalıştırabilmiştik. Fakat yine hatırlarsanız :) her trigger tipinin bu şekilde çalışmayacağından da bahsetmiştim. O neden deployment yapıp test ediyor olmak bazı senaryolarda tek seçenek oluyor. Tabi, bunun haricinde, genel bir strateji olarak da ne olursa olsun son bir testi cloud ortamında, en azından staging gibi bir ortamda yapmanızda fayda var.

### Remote Debugging

Azure Functions ile beraber remote debugging yapma şansımız var. Yani localdeki Visual Studio'yu alıp cloud ortamındaki Functions App'e bağlayabiliyoruz. 

![Remote Debugging](http://blob.daron.yondem.com/assets/3037/af-debugging.png)

Bunun için tabi ki ilk başta bir deployment yapmanız şart :) Sonrasında Visual Studio içerisinde "Server Explorer"a giderek Azure Subscriptionı'nızı bağlamanız gerekiyor. Son olarak da App Service'i buldunuz mu sağ tıklayın ve "Attach Debugger" deyin. Sonrasında web portalına gidip bir test request'i gönderebilirsiniz. Bu arada, eğer web portalında function'ınız görünmez olursa bu bir bug :) tekrar bir deployment yaparsanız herşey sakinleşecektir. 

![Remote Debugging](http://blob.daron.yondem.com/assets/3037/af-debugging-2.png)

Yukarıdaki ekran görüntüsünde de görüldüğü üzere req.RequestUri'a baktığımızda doğrudan production / live ortamında Uri gözüküyor. Böylece hızlı bir şekilde live ortama debugger ataçlamak mümkün. Ben ne kadar "hızlı" desem de aslında debugger epey yavaş çalışıyor, ama o kadar olur değil mi? :)

### Logging

Debugging konusunda bir diğer yardımcınız da tabi ki loglarınız. Eğer web portalı üzerinden Azure Functions'ı çalıştırdıysanız aşağıdaki pencere dikkatinizi çekmiştir.

![Azure Functions Logları Portalda](http://blob.daron.yondem.com/assets/3037/af-debugging-3.png)

Bu pencerede hem functions içerisinde attığımız trace bilgilerini hem de bazı ekstra durumlara ait bilgileri görebiliyoruz. Aslında bunların hepsi biz bir Azure Function App Service yaratırken beraberinde otomatik olarak gelen Storage Account'a atılıyor. 

![Azure Functions için oluşturulan Storage Account](http://blob.daron.yondem.com/assets/3037/af-debugging-4.png)

Eğer bu Storage Account'a ayrıca Azure Storage Explorer ile bağlanırsanız normalde portalda gözükenden çok daha fazla data görebilirsiniz. Unutmadan, bu Storage Account'un maliyeti Azure Functions'ın fiyatlandırmasına dahil değil :) Benden söylemesi.

Storage Account'a bağlandığınızda Table Services kısmına göz atarsanız her ay için ayrı bir table yaratıldığını görebilirsiniz. Bu table'lar içerisinde de bizim koddan attığımız loglar bulunuyor. Portalde gördüğünüz logların ciddi bir kısmını portal kendisi atıyor, logluyor. Bunu özellikle debugging esnasında işe yarasın diye yapmışlar. Fakat productiondan giden triggerlar için daha temiz bir şekilde sadece trigger logları tutuluyor. Yani, özetle, siz eğer bir şey loglamazsanız herhangi bir log tutulmaz. Fakat portalden test için çalıştırırsanız bol bol log bulursunuz. 

![Azure Functions Detaylı Logları](http://blob.daron.yondem.com/assets/3037/af-debugging-5.png)

Yukarıdaki log verisi aşağıdaki kodun sonucu. Log atarken verdiğimiz verilen LogOutput kolonuna yerleştirilmiş. Geri kalanlar runtime'ın kendi attığı bilgiler. StartTime ve EndTime arasındaki süreye bakarsan CPU Time olarak 31 milisaniye kullanmışız. 

```CS
log.Info($"C# HTTP trigger function processed a request. RequestUri={req.RequestUri}");
```

Aynı veriyi Azure Portal'ında da görme şansınız var. 

![Azure Functions Detaylı Logları](http://blob.daron.yondem.com/assets/3037/af-debugging-6.png)