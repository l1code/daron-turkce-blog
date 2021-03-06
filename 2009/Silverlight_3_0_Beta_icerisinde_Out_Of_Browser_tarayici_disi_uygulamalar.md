---
FallbackID: 2358
Title: Silverlight 3.0 Beta içerisinde (Out Of Browser) tarayıcı dışı uygulamalar.
PublishDate: 27/4/2009
EntryID: Silverlight_3_0_Beta_icerisinde_Out_Of_Browser_tarayici_disi_uygulamalar
IsActive: True
Section: software
MinutesSpent: 0
Tags: Silverlight 3.0
old.EntryID: 4283a271-24a9-4a62-aed6-d38d291dd9a2
---
Silverlight 3.0 Beta ile beraber gelen ilginç özelliklerden biri de
herhangi bir Silverlight uygulamasını doğrudan masaüstüne alabiliyor
olmamız. Gelin öncelikle hızlı bir demo ile yeni yarattığımız bir
uygulamayı nasıl masaüstüne aldığımıza ve nasıl gözüktüğüne bakalım.

Yeni bir Silverlight uygulaması yarattıktan sonra tarayıcı içerisinde bu
uygulamayı çalıştırıp üzerine farenizin sağ tuşu ile tıklarsanız gelen
menüde ilginç bir komut dikkatinizi çekecektir.

![Install onto this
computer?](media/Silverlight_3_0_Beta_icerisinde_Out_Of_Browser_tarayici_disi_uygulamalar/26042009_1.png)\
*Install onto this computer?*

Gördüğünüz üzere komutun anlamı aslında epey açık :) diyor ki "Bu
uygulamayı bilgisayarına yükle!" Tabi şu an için bu komut kullanılamıyor
çünkü aktif değil. Gelin hemen bu komutu nasıl aktif hale
getirebileceğimize göz atalım.

![AppManifest dosyamız
burada.](media/Silverlight_3_0_Beta_icerisinde_Out_Of_Browser_tarayici_disi_uygulamalar/26042009_2.png)\
*AppManifest dosyamız burada.*

Visual Studio içerisinde Solution Explorer'dan uygulamanızın
**AppManifest.xml** dosyasına erişmemiz gerekiyor. Bunun için ilk olarak
hemen Solution Explorer penceresinin en üstündeki ikinci düğme olan
"Show all files" düğmesine tıklıyoruz ve "My Project" altında Manifest
dosyamızı bulup açıyoruz.

**[AppManifest.xml]**

<span style="color: blue;">\<</span><span
style="color: #a31515;">Deployment</span><span style="color: blue;">
</span><span style="color: red;">xmlns</span><span
style="color: blue;">=</span>"<span
style="color: blue;">http://schemas.microsoft.com/client/2007/deployment</span>"

<span style="color: blue;">        </span><span
style="color: red;">xmlns:x</span><span
style="color: blue;">=</span>"<span
style="color: blue;">http://schemas.microsoft.com/winfx/2006/xaml</span>"

<span style="color: blue;">\></span>

<span style="color: blue;">    \<</span><span
style="color: #a31515;">Deployment.Parts</span><span
style="color: blue;">\></span>

<span style="color: blue;">    \</</span><span
style="color: #a31515;">Deployment.Parts</span><span
style="color: blue;">\></span>

 

<span style="color: blue;">    \<!--</span><span style="color: green;">
Uncomment the markup and update the fields below to make your
application offline enabled</span>

<span style="color: green;">   
\<Deployment.ApplicationIdentity\></span>

<span style="color: green;">        \<ApplicationIdentity </span>

<span style="color: green;">            ShortName="Out of Browser
Silverlight Application" </span>

<span style="color: green;">            Title="Window Title of Your
Silverlight Application"\></span>

<span style="color: green;">           
\<ApplicationIdentity.Blurb\>Description of your Silverlight
application\</ApplicationIdentity.Blurb\></span>

<span style="color: green;">        \</ApplicationIdentity\></span>

<span style="color: green;">   
\</Deployment.ApplicationIdentity\></span>

<span style="color: green;">    </span><span
style="color: blue;">--\></span>

<span style="color: blue;">\</</span><span
style="color: #a31515;">Deployment</span><span
style="color: blue;">\></span>

Yukarıdaki manifest dosyasının içeriğini görebilirsiniz. Bu dosya
içeriğinde "yorum" satırı olarak yerleştirilmiş olan yeşil kısımlar
aslında uygulamanın "Out Of Browser" yani "Tarayıcı Dışı" moduna
alınabilmesini sağlayacak olan kodların ta kendisi. Basit bir şekilde
buradaki kodları yorum olmaktan çıkarmamız uygulamamızın tarayıcı dışına
taşınabilmesini sağlayacaktır. Tabi bu süreçte var olan XML kodlarının
anlamına da bir göz atalım.

**[AppManifest.xml]**

<span style="color: blue;">\<</span><span
style="color: #a31515;">Deployment</span><span style="color: blue;">
</span><span style="color: red;">xmlns</span><span
style="color: blue;">=</span>"<span
style="color: blue;">http://schemas.microsoft.com/client/2007/deployment</span>"

<span style="color: blue;">        </span><span
style="color: red;">xmlns:x</span><span
style="color: blue;">=</span>"<span
style="color: blue;">http://schemas.microsoft.com/winfx/2006/xaml</span>"

<span style="color: blue;">\></span>

<span style="color: blue;">    \<</span><span
style="color: #a31515;">Deployment.Parts</span><span
style="color: blue;">\></span>

<span style="color: blue;">    \</</span><span
style="color: #a31515;">Deployment.Parts</span><span
style="color: blue;">\></span>

 

<span style="color: blue;">    \<</span><span
style="color: #a31515;">Deployment.ApplicationIdentity</span><span
style="color: blue;">\></span>

<span style="color: blue;">        \<</span><span
style="color: #a31515;">ApplicationIdentity</span><span
style="color: blue;"> </span>

<span style="color: blue;">            </span><span
style="color: red;">ShortName</span><span
style="color: blue;">=</span>"<span style="color: blue;">Uygulama adı
uraya gelir!</span>"<span style="color: blue;"> </span>

<span style="color: blue;">            </span><span
style="color: red;">Title</span><span
style="color: blue;">=</span>"<span style="color: blue;">Uygulama
penceresinde gösterilecek metin burada!</span>"<span
style="color: blue;">\></span>

<span style="color: blue;">            \<</span><span
style="color: #a31515;">ApplicationIdentity.Blurb</span><span
style="color: blue;">\></span>Uygulamanın uzun uzun tanımı, açıklaması
da buraya gelecektir.<span style="color: blue;">\</</span><span
style="color: #a31515;">ApplicationIdentity.Blurb</span><span
style="color: blue;">\></span>

<span style="color: blue;">        \</</span><span
style="color: #a31515;">ApplicationIdentity</span><span
style="color: blue;">\></span>

<span style="color: blue;">    \</</span><span
style="color: #a31515;">Deployment.ApplicationIdentity</span><span
style="color: blue;">\></span>

 

<span style="color: blue;">\</</span><span
style="color: #a31515;">Deployment</span><span
style="color: blue;">\></span>

**ApplicationIdentity** XML tagları aslında uygulamanızın kimliğini
tanımlayacaktır. Bu kimlik tabi ki son kullanıcı tarafından farklı
noktalarda uygulamanızın adını vs özelliklerini yansıtacak bilgileri
barındırıyor. Örneğin **ShortName** özelliğine uygulama adını kısaca
yazıyoruz, **Title** özelliğinde ise uygulama **Windows** içerisinde
tarayıcı dışında çalıştırılırken sahip olacağı kendi penceresinin
üstünde yazılacak metni tanımlıyor. Diğer yandan **Blurb** kısmında ise
uygulama ile ilgili açıklayıcı bilgilere yer veriyoruz.

Tüm bu ayarları tamamladıktan sonra uygulamamızı çalıştırmanın zamanı
geldi.

![Uygulamamızı artık tarayıcı dışına
alabiliyoruz!](media/Silverlight_3_0_Beta_icerisinde_Out_Of_Browser_tarayici_disi_uygulamalar/26042009_3.png)\
*Uygulamamızı artık tarayıcı dışına alabiliyoruz!*

Artık uygulamamızın ekranında herhangi bir yere sağ tuş ile
tıkladığımızda gelen menüdeki "Install" deyiminin bulunduğu komutun
aktif olduğunu görebiliyoruz. Ayrıca bizim manifest içerisinde
**ShortName** olarak tanımladığımız uygulama adının da hemen bu komut
içerisinde uygun yere yerleştirildiğini gördük. Eh bu durumda söz konusu
komuta tıklayalım bakalım neler oluyor.

![Uygulamayı yükleme onay
penceresi.](media/Silverlight_3_0_Beta_icerisinde_Out_Of_Browser_tarayici_disi_uygulamalar/26042009_4.jpg)\
*Uygulamayı yükleme onay penceresi.*

Yükleme komutunu verdiğimiz anda karşımıza yukarıdaki ekran geliyor ve
bizi manifest içerisinde **Title** olarak verdiğimiz değeri de gösterek
söz konusu uygulamayı bilgisayarımıza yüklemek üzere olduğumuza dair
uyarıyor. Yükleme süresince istersek uygulamanın birer kısayolunu
masaüstüne ve/veya başlat menüsüne alabiliyoruz.

Yükleme işlemini onayladığımız gibi Silverlight uygulaması karşımıza
normal bir Windows programıymış gibi geliyor. Kendi penceresine sahip,
tamamen tarayıcıdan bağımsız olarak uygulamamız karşımızda.

![Silverlight artık tarayıcının
dışında!](media/Silverlight_3_0_Beta_icerisinde_Out_Of_Browser_tarayici_disi_uygulamalar/26042009_5.jpg)\
*Silverlight artık tarayıcının dışında!*

Bu noktada dikkat etmeniz gereken noktalardan biri de uygulamanın
penceresinde Title metninin yanı sıra uygulamanın yüklendiği adresin
(bizim örneğimizde localhost) de aynı şekilde pencere adına eklenmiş
olması. Böylece kullanıcılar her zaman uygulamayı hangi adresten
yüklediklerine görebilecekler. Unutmayın artık uygulamamızın masaüstünde
ve başlat menüsünde kısayolları var!

![Silverlight uygulamamızın masaüstü ve başlat
menüsünde!](media/Silverlight_3_0_Beta_icerisinde_Out_Of_Browser_tarayici_disi_uygulamalar/26042009_6.jpg)\
*Silverlight uygulamamızın masaüstü ve başlat menüsünde!*

Yukarıdaki ekran görüntüsünde de görebileceğiniz üzere uygulamamızın bir
kısayolu masaüstünde bulunuyor. Bu kısayolun adı manifest içerisinde
**ShortName**. Aynı şekilde başlat menüsüne konan kısayolun adı da
ShortName üzerinden gelirken bu kısayollar üzerinde fare ile
durduğumuzda gelen açıklamada ise **Blurb** bilgisini görüyoruz. Artık
Silverlight uygulamamızın söz konusu bilgisayarda internet bağlantısı
olmasa da rahatlıkla bu kısayollardan çalıştırılabilecektir.

Eğer kullanıcılar bu programı bilgisayarlarından silmek isterlerse
doğrudan programı çalıştırıp Silverlight uygulamasının üzerinde herhangi
bir yerde sağ tuş ile gelen menüden  "**Remove Application**" komutunu
seçmek durumundalar. Silverlight 3 Beta ile beraber gelen bu özellik ile
bilgisayarlara yüklenen Silverlight uygulamaları Denetim Masası'nda
"Program/Ekle Kaldır" bölümünde gözükmeyecektir.

![Silvelright uygulamasının bilgisayardan kaldırmak
isterseniz...](media/Silverlight_3_0_Beta_icerisinde_Out_Of_Browser_tarayici_disi_uygulamalar/26042009_7.jpg)\
*Silvelright uygulamasının bilgisayardan kaldırmak isterseniz...*

Tüm bu manzara içerisinde belki de hemen değiştirmek isteyeceğiniz
şeylerden biri uygulamanın her yerde gözüken varsayılan ikonu olacaktır.
Hem masaüstündeki hem başlat menüsündeki hem de uygulama penceresindeki
ikonların hepsini birden tek tek değiştirebiliyorsunuz.

![Tek tek ayarlanmış
logolar...](media/Silverlight_3_0_Beta_icerisinde_Out_Of_Browser_tarayici_disi_uygulamalar/26042009_8.jpg)\
*Tek tek ayarlanmış logolar...*

Uygulamamızda kullanılmak üzere dört farklı boyutta logolar ayarlamamız
gerekiyor. Bu logoların 16, 32, 64, 128 piksellik dosyalarını doğrudan
PNG olarak kaydedebilirsiniz. Söz konusu dosyaları Silverlight projenize
eklemek için Visual Studio içerisinde Solution Explorer'a sağ tıklayıp
"Add Existing Item" diyebilirsiniz. Önemli olan tüm bu dosyaları
projenize ekledikten sonra **Build Action**'larını **Content** olarak
ayarlamanız.

![PNG'lerinin hepsinin de Content olarak ayarlanması
şart!](media/Silverlight_3_0_Beta_icerisinde_Out_Of_Browser_tarayici_disi_uygulamalar/26042009_9.png)\
*PNG'lerinin hepsinin de Content olarak ayarlanması şart!*

Artık logolarımız hazır olduğuna göre geçip manifest dosyamızdaki
ayarları yapabiliriz. Kabaca manifest dosyasında **ApplicationIdentity**
tagına **Icons** adında bir seri ekleyip farklı boyutlar için hangi
dosyaların kullanılması gerektiğini belirteceğiz.

**[AppManifest.xml]**

<span style="color: gray;">\<Deployment xmlns=</span>"<span
style="color: gray;">http://schemas.microsoft.com/client/2007/deployment</span><span
style="color: gray">"</span>

<span style="color: gray;">        xmlns:x=</span>"<span
style="color: gray;">http://schemas.microsoft.com/winfx/2006/xaml</span><span
style="color: gray">"</span>

<span style="color: gray;">\></span>

<span style="color: gray;">  \<Deployment.Parts\></span>

<span style="color: gray;">  \</Deployment.Parts\></span>

 

<span style="color: gray;">  \<Deployment.ApplicationIdentity\></span>

<span style="color: gray;">    \<ApplicationIdentity</span>

<span style="color: gray;">        ShortName=</span>"<span
style="color: gray;">Uygulama adı uraya gelir!</span><span
style="color: gray">"</span>

<span style="color: gray;">        Title=</span>"<span
style="color: gray;">Uygulama penceresinde gösterilecek metin
burada!</span>"<span style="color: gray;">\></span>

<span style="color: gray;">     
\<ApplicationIdentity.Blurb\></span><span
style="color: gray">Uygulamanın uzun uzun tanımı, açıklaması da buraya
gelecektir.</span><span
style="color: gray;">\</ApplicationIdentity.Blurb</span><span
style="color: blue;">\></span>

<span style="color: blue;">      \<</span><span
style="color: #a31515;">ApplicationIdentity.Icons</span><span
style="color: blue;">\></span>

<span style="color: blue;">        \<</span><span
style="color: #a31515;">Icon</span><span style="color: blue;">
</span><span style="color: red;">Size</span><span
style="color: blue;">=</span>"<span
style="color: blue;">16x16</span>"<span
style="color: blue;">\></span>logo\_16.png<span
style="color: blue;">\</</span><span
style="color: #a31515;">Icon</span><span style="color: blue;">\></span>

<span style="color: blue;">        \<</span><span
style="color: #a31515;">Icon</span><span style="color: blue;">
</span><span style="color: red;">Size</span><span
style="color: blue;">=</span>"<span
style="color: blue;">32x32</span>"<span
style="color: blue;">\></span>logo\_32.png<span
style="color: blue;">\</</span><span
style="color: #a31515;">Icon</span><span style="color: blue;">\></span>

<span style="color: blue;">        \<</span><span
style="color: #a31515;">Icon</span><span style="color: blue;">
</span><span style="color: red;">Size</span><span
style="color: blue;">=</span>"<span
style="color: blue;">64x64</span>"<span
style="color: blue;">\></span>logo\_64.png<span
style="color: blue;">\</</span><span
style="color: #a31515;">Icon</span><span style="color: blue;">\></span>

<span style="color: blue;">        \<</span><span
style="color: #a31515;">Icon</span><span style="color: blue;">
</span><span style="color: red;">Size</span><span
style="color: blue;">=</span>"<span
style="color: blue;">128x128</span>"<span
style="color: blue;">\></span>logo\_128.png<span
style="color: blue;">\</</span><span
style="color: #a31515;">Icon</span><span style="color: blue;">\></span>

<span style="color: blue;">      \</</span><span
style="color: #a31515;">ApplicationIdentity.Icons</span><span
style="color: blue;">\></span>

<span style="color: gray;">    \</ApplicationIdentity\></span>

<span style="color: gray;">  \</Deployment.ApplicationIdentity\></span>

 

<span style="color: gray;">\</Deployment</span><span
style="color: blue;">\></span>

Artık manifest dosyamızın son halini yukarıda inceleyebilirsiniz.
**Icons** adındaki serinin içerisinde tek tek Icon'ları tanımladık ve
her **Size** için ayrı ayrı hazırladığımız **Content** olarak uygulama
içerisinde bulunan dosyaların adlarını verdik. Silverlight uygulamamızın
bulunduğu sayfayı açıp uygulamayı masaüstüne kaydetmeye kalktığımızda
artık bu ikonlar ile karşılaşacağız.

![Yükleme esnasında özel logo!
:)](media/Silverlight_3_0_Beta_icerisinde_Out_Of_Browser_tarayici_disi_uygulamalar/26042009_10.jpg)\
*Yükleme esnasında özel logo! :)*

![Uygulamanın kısayollarında özelleştirilmiş
logolar...](media/Silverlight_3_0_Beta_icerisinde_Out_Of_Browser_tarayici_disi_uygulamalar/26042009_11.jpg)\
*Uygulamanın kısayollarında özelleştirilmiş logolar...*

![Uygulama penceresinde özel
logo!](media/Silverlight_3_0_Beta_icerisinde_Out_Of_Browser_tarayici_disi_uygulamalar/26042009_12.jpg)\
*Uygulama penceresinde özel logo!*

Here yere özel logolarımız geldiğinde göre artık uygulama kimliğini çok
daha rahat bir şekilde müşteriye yansıtabiliriz. Hatta Windows
Taskbar'da da söz konusu logomuz ayrıca gözüküyor.

![Taskbarda özel
logo.](media/Silverlight_3_0_Beta_icerisinde_Out_Of_Browser_tarayici_disi_uygulamalar/26042009_13.jpg)\
*Taskbarda özel logo.*

**Ya kullanıcılar sağ tıklamaz ise uygulamamıza?**

Bu noktaya kadar hoş bir şekilde uygulamaya sağ tıkladık yükledik ve
aynı şekilde sağ tıklayıp bilgisayarımızdan sildik. Diyelim ki silme
işlemi çok önemli değil :) Kimsenin pek de uygulamamızı silmesini
istemiyoruz fakat yükleme noktasında daha kolay bir kullanıcı deneyimi
sağlamak zorundayız. İnsanların uygulamamıza sağ tıklayarak o yükleme
komutunu keşfetlemelerini bekleyemeyiz. Böyle bir durumda basit bir
şekilde uygulama içerisinde herhangi bir yere "Yükle" düğmesi koymak
bile sorunumuzu çözebilir.

**[VB]**

        <span style="color: blue;">If</span> App.Current.Detach <span
style="color: blue;">Then</span>

            MessageBox.Show(<span
style="color: #a31515;">"Oldu!"</span>)

        <span style="color: blue;">End</span> <span
style="color: blue;">If</span>

Yukarıdaki kodu herhangi bir düğmenin arkasına yazabilirsiniz.
**App.Current.Detach** metodu otomatik olarak daha önceki örneklerimizde
gördüğümüz yükleme ekranını kullanıcının karşına getirecektir. Bu metod
geriye bir **Boolean** döndürdüğü için kullanıcının yükleme işlemini
yapıp yapmadığını da rahatlıkla öğrenebilirsiniz. Burada özellikle
dikkat etmeniz gereken bir nokta var, **App.Current.Detach** metodunu
kullanıcı tarafından başlatılmış metodlarda çağırabilirsiniz, yani
Page.Load gibi istediğiniz yerlerde bu pencereyi açamazsınız :)
Bilginize.

**Derinlere dalalım!**

Artık uygulamamızı kendi kendimize kod ile de tarayıcıdan bağımsız hale
getirebiliyoruz fakat ortalık biraz karışık durumda. Kendi yarattığımız
düğmeler aracılığı ile kod ile kullanıcı uygulamamızı masaüstüne alırsa
biz de bundan haberdar olabiliyoruz fakat ya kullanıcı gibip sağ tuş ile
gelen menüden uygulamayı bilgisayarına alırsa? Bazı durumlarda biz
bundan da haberdar olmak isteyebiliriz. Peki neden mi haberdar olmak
isteriz?

Unutmayın ki bir Silverlight uygulaması normal şartlarda Online çalışmak
üzere hazırlanır ve programlanır. Örneğin veritabanından veri çekmek
için sonuçta bir sunucuya bağlanırız. Uygulama masaüstüne alındıktan
sonra ise Offline da çalışabilir hale geliyor. Yani artık Silverlight
uygulamanız her çalıştığında internete erişimi olmayacak! Bu durumda
bizim uygulamanın tarayıcı içerisinde mi çalıştırıldığını yoksa dışarıda
mı olduğunu anlamamız gerekiyor. Diğer yandan uygulama tarayıcı dışında
olabilir fakat internet bağlantısı da o an için makinede bulunabilir.

**İnternet var mı?**

İlk olarak gelin uygulama her nerede olursa olsun, ister tarayıcı içinde
ister tarayıcı dışında, internet bağlantısının durumundan nasıl haberdar
olabileceğimize bakalım. Söz konusu durumla ilgili bize bilgi verecek
olan Event-Handler **System.Net.NetworkInformation.NetworkChange**
olarak geliyor. Bu event'ı yakalayarak bir değişiklik olduğunda
**System.Net.NetworkInformation.NetworkInterface.GetIsNetworkAvailable**
komutu ile makinede net olup olmadığını anlayabilirsiniz.

**[VB]**

<span style="color: blue;">Partial</span> <span
style="color: blue;">Public</span> <span
style="color: blue;">Class</span> MainPage

    <span style="color: blue;">Inherits</span> UserControl

 

    <span style="color: blue;">Public</span> <span
style="color: blue;">Sub</span> <span style="color: blue;">New</span>()

        InitializeComponent()

        <span style="color: blue;">AddHandler</span>
System.Net.NetworkInformation.NetworkChange.NetworkAddressChanged, <span
style="color: blue;">AddressOf</span> Network\_NetworkAddressChanged

    <span style="color: blue;">End</span> <span
style="color: blue;">Sub</span>

 

    <span style="color: blue;">Private</span> <span
style="color: blue;">Sub</span> Network\_NetworkAddressChanged(<span
style="color: blue;">ByVal</span> sender <span
style="color: blue;">As</span> <span style="color: blue;">Object</span>,
<span style="color: blue;">ByVal</span> e <span
style="color: blue;">As</span> System.EventArgs)

        <span style="color: blue;">If</span>
System.Net.NetworkInformation.NetworkInterface.GetIsNetworkAvailable
<span style="color: blue;">Then</span>

            MessageBox.Show(<span style="color: #a31515;">"NET
VAR!"</span>)

        <span style="color: blue;">Else</span>

            MessageBox.Show(<span style="color: #a31515;">"yok"</span>)

        <span style="color: blue;">End</span> <span
style="color: blue;">If</span>

    <span style="color: blue;">End</span> <span
style="color: blue;">Sub</span>

<span style="color: blue;">End</span> <span
style="color: blue;">Class</span>

[C\#]

    <span style="color: blue;">public</span> <span
style="color: blue;">partial</span> <span
style="color: blue;">class</span> <span
style="color: #2b91af;">MainPage</span> : <span
style="color: #2b91af;">UserControl</span>

    {

        <span style="color: blue;">public</span> MainPage()

        {

            InitializeComponent();

            System.Net.NetworkInformation.<span
style="color: #2b91af;">NetworkChange</span>.NetworkAddressChanged +=

                <span style="color: blue;">new</span>
System.Net.NetworkInformation.<span
style="color: #2b91af;">NetworkAddressChangedEventHandler</span>(NetworkChange\_NetworkAddressChanged);

        }

 

        <span style="color: blue;">void</span>
NetworkChange\_NetworkAddressChanged(<span
style="color: blue;">object</span> sender, <span
style="color: #2b91af;">EventArgs</span> e)

        {

            <span style="color: blue;">if</span>
(System.Net.NetworkInformation.<span
style="color: #2b91af;">NetworkInterface</span>.GetIsNetworkAvailable())

            {

                <span
style="color: #2b91af;">MessageBox</span>.Show(<span
style="color: #a31515;">"NET VAR!"</span>);

            }

            <span style="color: blue;">else</span>

            {

                <span
style="color: #2b91af;">MessageBox</span>.Show(<span
style="color: #a31515;">"yok"</span>);

            }

        }

    }

Yukarıdaki kodumuzda ilk olarak sayfanın **Init** durumunda ihtiyacımız
olan **NetworkAddressChanged** event'ını bağlıyoruz. Sonrasında ise söz
konusu event her çağrıldığında **GetIsNetworkAvailable** ile internet
bağlantısı olup olmadığını kontrol ediyoruz. Böylece siz de
uygulamalarınızda İnternet bağlantısından haberdar olup farklı
senaryolar oluşturabilir belki kullanıcılarının offline data üzerinde
çalışabilmesini sağlayıp değişiklikleri de IsolatedStorage içerisinde
bir süre için kaydedebilirsiniz.

**Uygulamam nerede çalışıyor?**

Silverlight uygulamalarımızı hiçbir değişiklik yapmadan masaüstüne
taşıyabiliyor olsak da aslında uygulamanın masaüstündeki hali ile
internet tarayıcı içerisinde hali arasında görsel anlamda farklılıklar
da yaratmak isteyebilirsiniz. Özetle uygulamanızın tarayıcı içerisinde
mi yoksa dışarısında mı çalıştırıldığını anlamanız gerekebilir. Bu gibi
bir durumda basit bir şekilde **App.Current.RunningOffline** metodundan
faydalanabilirsiniz. Bu metod size doğrudan bir **Boolean**
döndürecektir. Eğer sonuç **True** olursa uygulamanın tarayıcı dışında,
**False** olursa tarayıcı içerisinde olduğunu anlayabilirsiniz. Metodun
ismi aklınızı karıştırmasın söz konusu metodun internet bağlantısı olup
olmaması ile herhangi bir ilişkisi yok.

**Update mekanizması ne durumda?**

İnternet üzerinden bilgisayarına Silverlight uygulamamızı yüklemiz
kişiler rahatlıkla offline olarak da çalışabilecekler fakat eğer biz
sunucu tarafında bir değişiklik yapar ve Silverlight uygulamamızı
değiştirirsek ne olacak? Aslında buradaki Update mekanizması .NET
Framework içerisinde **ClickOnce** mekanizmasına çok benziyor.
Silverlight uygulaması masaüstünden çalıştırıldığında hemen online olup
olmadığını otomatik olarak kontrol ediyor ve eğer online ise webdeki
sürüme bakıyor. Webdeki uygulama ile lokaldeli aynı ise zaten bir sorun
yok demektir. Eğer webdeki daha yeni bir sürüm ise arkaplanda yeni sürüm
bilgisayara indiriliyor ve uygulama tekrar çalıştırıldığında istemci
tarafında artık yeni sürüm çalıştırılmış oluyor. Bu mekanizma bu şekilde
ilerlerken biz de tabi ki bu işleyişten haberdar olabiliyoruz. Örneğin
belki de yeni bir sürüm var ise kullanıcıyı uyarmak isteyebiliriz!

Uygulamanın update mekanizmasının işleyişinden haberdar olmak için
Application (uygulama) bazındaki event'lardan birini kullanmamız
gerekiyor. Söz konusu event'ın adı **ExecutionStateChanged**. Bu event'a
tabi ki uygulama içerisinde App.XAML'ın arkasında kod dosyasından
ulaşabiliyoruz.

**[VB]**

    <span style="color: blue;">Private</span> <span
style="color: blue;">Sub</span> App\_ExecutionStateChanged(<span
style="color: blue;">ByVal</span> sender <span
style="color: blue;">As</span> <span style="color: blue;">Object</span>,
<span style="color: blue;">ByVal</span> e <span
style="color: blue;">As</span> System.EventArgs) <span
style="color: blue;">Handles</span> <span
style="color: blue;">Me</span>.**ExecutionStateChanged**

        <span style="color: blue;">If</span>
App.Current.**ExecutionState** =
ExecutionStates.**DetachedUpdatesAvailable** <span
style="color: blue;">Then</span>

            MessageBox.Show(<span style="color: #a31515;">"Yeni sürüm
var lütfen uygulamayı baştan başlatın!"</span>)

        <span style="color: blue;">End</span> <span
style="color: blue;">If</span>

    <span style="color: blue;">End</span> <span
style="color: blue;">Sub</span>

**[C\#]**

        <span style="color: blue;">public</span> App()

        {

            <span style="color: blue;">this</span>.Startup += <span
style="color: blue;">this</span>.Application\_Startup;

            <span style="color: blue;">this</span>.Exit += <span
style="color: blue;">this</span>.Application\_Exit;

            <span style="color: blue;">this</span>.UnhandledException +=
<span style="color: blue;">this</span>.Application\_UnhandledException;

            <span
style="color: blue;">this</span>.**ExecutionStateChanged** += <span
style="color: blue;">new</span> <span
style="color: #2b91af;">EventHandler</span>(App\_ExecutionStateChanged);

            InitializeComponent();

        }

 

        <span style="color: blue;">void</span>
App\_ExecutionStateChanged(<span style="color: blue;">object</span>
sender, <span style="color: #2b91af;">EventArgs</span> e)

        {

            <span style="color: blue;">if</span>(<span
style="color: #2b91af;">App</span>.Current.**ExecutionState**== <span
style="color: #2b91af;">ExecutionStates</span>.**DetachedUpdatesAvailable**)

            {

                <span
style="color: #2b91af;">MessageBox</span>.Show(<span
style="color: #a31515;">"Yeni sürüm var lütfen uygulamayı baştan
başlatın!"</span>);

            }

        }

App.xaml arkasında **ExecutionStateChanged** event'ı çalıştığı anda o
anki uygulamanın ExecutionState'ini kontrol ediyoruz. Eğer
**ExecutionState** **DetachedUpdatesAvailable** olarak geliyorsa demek
ki yeni bir update var. Bu durumda kullanıcıya gerekli uyarıyı
gösterebiliriz.

**Arkaplanda neler oluyor?**

Peki nasıl oluyor da bizim Silverlight uygulaması offline çalışıyor?
Aslında konu epey basit. Herhangi bir Silverlight uygulaması Detach
edildiğinde uygulamanın XAP dosyasının bir kopyası kullanıcının
bilgisayarına alınıyor.

*C:\\Users\\KullaniciAdi\\AppData\\LocalLow\\Microsoft\\Silverlight\\Offline*
  

Yukarıda gördüğünüz yolda bulunan klasörün altına Silverlight
uygulamasının bulunduğu alan adına ait bir klasör açılır ve söz konusu
klasörün içerisinde XAP dosyası bir takım başka bilgilerle beraber
kaydedilir.

![Silverlight uygulaması diskte
saklı.](media/Silverlight_3_0_Beta_icerisinde_Out_Of_Browser_tarayici_disi_uygulamalar/26042009_14.jpg)\
*Silverlight uygulaması diskte saklı.*

Yukarıdaki ekran görüntüsünde de görebileceğiniz üzere XAP dosyamız
orada duruyor. İçerisindeki ikonlarımızdan bir **ico** dosyası
yaratılmış ve dışarıya yerleştirilmiş. Böylece işletim sisteminde tüm
kısayollarda bu ico dosyası kullanılıyor. Uygulamamızı host eden bir de
HTML var :) Bu HTML'i kim açıp bize gösteriyor kısmına birazdan geliriz.
Onun öncesinde **metadata** dosyasının içeriğine bir bakalım.

**[metadata]**

LaunchPath=C:\\Users\\KullaniciAdi\\AppData\\LocalLow\\Microsoft\\Silverlight\\Offline\\localhost.1\\index.html

CustomIcon=1

SourceDomain=localhost

**OriginalUri**=http://localhost:1559/ClientBin/SilverlightApplication29.xap

AppID=localhost.1

Description=Uygulamanın uzun uzun tanımı, açıklaması da buraya
gelecektir.

Title=Uygulama penceresinde gösterilecek metin burada!

Name=Uygulama adı uraya gelir!

Gördüğünüz gibi uygulama içerisinde bazı manifest bilgilerimiz buraya da
alınmış. Önemli noktalardan biri **OriginalUri** bilgisinde uygulamanın
orijinal adresinin saklanıyor olması. Sistem bu bilgi üzerinden yeni
sürüm kontrolü yapabiliyor. Peki tüm bunları kim çalıştırıyor?
Silverlight Runtime kullanıcıların bilgisayarına yüklenirken beraber bir
de **sllauncher.exe** adında bir program yükleniyor. Bu program aldığı
parametreye göre bilgisayarda yüklü Silverlight uygulamalarını birer
masaüstü uygulamasıymış gibi çalıştırabiliyor.

**Hmm bu Adobe AIR değil mi?**

Adobe tarafını takip edenlerin hemen soracakları ilk soru eminim ki "*Bu
Adobe AIR değil mi?*" olacaktır. Hayır, değil. Neden mi? İlk olarak
aradaki en büyük fark Adobe AIR için bilgisayarınıza ayrıca AIR Runtime
yüklemek zorunda olmanız. Silverlight tarafında böyle bir durum yok.
Hali hazırda yüklü olan Silverlight Runtime ile hayatınıza devam
edebiliyorsunuz. İkinci en büyük fark ise Silverlight'ın bir masaüstü
uygulaması haline dönüşse de hala tarayıcının güvenlik sınırlarında
çalışıyor olması. Yani masaüstüne alsanız da bir Silverlight uygulaması
masaüstündeki dosyalara kafasına göre erişemez, donanıma erişemez! Nasıl
ki tarayıcı içerisinden sadece OpenFileDialog vs kullanarak dosyalara
erişebiliyorsak masaüstüne alınmış bir Silverlight uygulaması da aynı
şartlara tabidir. Özellikle donanım erişimi konusunda farklı
senaryoların sertifikasyonlarla belki sağlanabileceğini söylese de
Microsoft şu ana kadar resmi bir duyuru yok. Adobe tarafında AIR
uygulamaları tam donanım erişimi ile çalıştığı için o tarafta
sertifikasyon şart oluyor ve Silverlight'ın masaüstüne alınabildiği gibi
bir tıkla kullanıcıya farklı bir deneyim sağlamak mümkün olmuyor. Diğer
yandan Adobe tarafında update mekanizması için de ayrı bir SDK paketinde
gelen sistemi kullanmak gerekiyor, oysa Silverlight 3.0 içerisinde söz
konusu sistem entegre olarak geliyor.

Sonuç olarak baktığınızda Adobe elindeki teknoloji ile bir Windows
uygulama geliştirme platformu oluşturmaya çalışırken Microsoft ise
Windows tarafında WPF gibi zaten kendini kanıtlamış ve arkasında .NET
Framework olan yapısını korurken web uygulamalarının rahatlıkla Offline
kullanıma açılmasını hedefleyen ve çok kolay kullanılan bir yapıyı
hedefliyor.

**Kapanış!**

Özünde Silverlight 3'ün bu özelliği ile çok ilginç senaryolar
üretilebilir. Online ve Offline senaryoların beraber kullanımının çok
daha rahat ve hoş bir kullanıcı deneyimi sağlayacağı kesin. Tüm bunları
yapabilmek için de birkaç satır koddan ödeye geçmenize gerek kalmıyor.

Hepinize kolay gelsin!


