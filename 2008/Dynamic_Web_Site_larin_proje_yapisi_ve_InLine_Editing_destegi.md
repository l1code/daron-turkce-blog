---
FallbackID: 2214
Title: Dynamic Web Site'ların proje yapısı ve InLine Editing desteği.
PublishDate: 13/10/2008
EntryID: Dynamic_Web_Site_larin_proje_yapisi_ve_InLine_Editing_destegi
IsActive: True
Section: software
MinutesSpent: 0
Tags: ASP.NET 3.5, ASP.NET
old.EntryID: 780ceee6-8011-4b82-981d-5e3bddeb30c9
---
Bir [önceki
yazımda](http://daron.yondem.com/tr/post/a562c8ca-165a-41ba-b82b-0996aa8ea267)
yeni bir Dynamic Data Web Site'ın nasıl oluşturulabileceğine göz
atmıştık. Aynı proje üzerinden devam ederek Dynamic Data Web Site'larda
otomatik olarak karşımıza çıkan sayfaların yapılarını, nerelerden
geldiklerini ve yönlendirme sistemlerini inceleyeceğiz.

Tamamen boş, yeni bir Dynamic Data Web Site yarattığınızda aslında
Visual Studio sizin için birçok gerekli dosyayı projenize otomatik
olarak ekliyor. Tüm bu otomatik eklenen dosyalar proje içerisinde
DynamicData adında bir klasörün altında saklı.

![DynamicData klasöründeki SAKLI
GÜÇ](media/Dynamic_Web_Site_larin_proje_yapisi_ve_InLine_Editing_destegi/12102008_1.png)\
*DynamicData klasöründeki SAKLI GÜÇ*

Dynamic Data klasöründeki farklı yapıların amaçlarını hızlıca
açıklayalım. **Content** klasörü altındaki içerik genelde diğer
UserControl ve sayfalarda kullanılan içeriği taşır. Bu klasörde resimler
veya harici UserControll'ler bulunabilir. Varsayılan ayarlarla gelen iki
UserControl'den biri olan **FilterUserControl** bizim örneğimizde
Kategorilerin filtreleme amaçlı olarak kullanıldığı yerlerde nasıl
gözükeceğini ve çalışacağını belirler. **FilterUserControl**.**ascx'in**
içindeki kod baktığımızda aşağıdaki manzara ile karşılaşıyoruz.

<span style="background: #ffee62;">\<%</span><span
style="color: blue;">@</span> <span
style="color: #a31515;">Control</span> <span
style="color: red;">Language</span><span
style="color: blue;">="VB"</span> <span
style="color: red;">CodeFile</span><span
style="color: blue;">="FilterUserControl.ascx.vb"</span> <span
style="color: red;">Inherits</span><span
style="color: blue;">="FilterUserControl"</span> <span
style="background: #ffee62;">%\></span>

 

<span style="color: blue;">\<</span><span
style="color: #a31515;">asp</span><span
style="color: blue;">:</span><span
style="color: #a31515;">DropDownList</span> <span
style="color: red;">ID</span><span
style="color: blue;">="DropDownList1"</span> <span
style="color: red;">runat</span><span
style="color: blue;">="server"</span> <span
style="color: red;">AutoPostBack</span><span
style="color: blue;">="true"</span> <span
style="color: red;">EnableViewState</span><span
style="color: blue;">="true"</span> <span
style="color: red;">CssClass</span><span
style="color: blue;">="droplist"\></span>

    <span style="color: blue;">\<</span><span
style="color: #a31515;">asp</span><span
style="color: blue;">:</span><span
style="color: #a31515;">ListItem</span> <span
style="color: red;">Text</span><span style="color: blue;">="All"</span>
<span style="color: red;">Value</span><span
style="color: blue;">=""</span> <span style="color: blue;">/\></span>

<span style="color: blue;">\</</span><span
style="color: #a31515;">asp</span><span
style="color: blue;">:</span><span
style="color: #a31515;">DropDownList</span><span
style="color: blue;">\></span>

Bu kodda gördüğünüz DropDownList'i farklı bir kontrol ile
değiştirirseniz doğrudan tüm proje içerisinde Filtreleme işlemlerinde bu
kontrol kullanılacaktır. Sanırım yavaş yavaş Dynamic Data Web Site
yapısının avantajlarını da hissetmeye başladık. Tabi bu gibi
özelleştirme konularının detaylarına ileride daha derinlemesine
gireceğiz.

DynamicData klasörümüzün içeriğine geri dönmek gerekirse sırada
**FieldTemplates** klasörü vardı. Hatırlarsanız bir önceki makalemizde
veritabanındaki tabloların Field'lerinin veri tipine göre farklı
kontrollerin sahneye geldiğini görmüştük. Yerine göre MultiLine bir
Textbox veya **Chechbox** gelebiliyordu. İşte FieldTemplates klasörü
altında farklı veri tiplerine için sahneye gelecek olan UserControl'ler
bulunuyor. Örneğin **Boolean.ascx**'i açarak karşımıza bir Checkbox
gelecektir.

<span style="background: #ffee62;">\<%</span><span
style="color: blue;">@</span> <span
style="color: #a31515;">Control</span> <span
style="color: red;">Language</span><span
style="color: blue;">="VB"</span> <span
style="color: red;">CodeFile</span><span
style="color: blue;">="Boolean.ascx.vb"</span> <span
style="color: red;">Inherits</span><span
style="color: blue;">="BooleanField"</span> <span
style="background: #ffee62;">%\></span>

 

<span style="color: blue;">\<</span><span
style="color: #a31515;">asp</span><span
style="color: blue;">:</span><span
style="color: #a31515;">CheckBox</span> <span
style="color: red;">runat</span><span
style="color: blue;">="server"</span> <span
style="color: red;">ID</span><span
style="color: blue;">="CheckBox1"</span> <span
style="color: red;">Enabled</span><span
style="color: blue;">="false"</span> <span
style="color: blue;">/\></span>

Yine bu dosya içerisinde yapılan herhangi bir değişiklik tüm projede
Boolean Field'lerin gösteriminde etkili olacaktır.

Son olarak bizi yakından ilgilendiren klasörlerden biri de
**PageTemplates** klasörü. Bu klasör içerisinde veri kaynağımızdaki tüm
tablolarla dinamik olarak çalışabilecek şekilde hazırlanmış ve CRUD
işlemlerini yapmayı hedefleyen farklı ASPX sayfaları bulunuyor. Bu
sayfalar bizim örneğimizde de hem Kategoriler hem de Ürünler tablosunu
düzenlerken kullanılıyordu.

![Dynamic Data Web Site'ın URL
yapısı.](media/Dynamic_Web_Site_larin_proje_yapisi_ve_InLine_Editing_destegi/12102008_2.png)\
*Dynamic Data Web Site'ın URL yapısı.*

Yukarıdaki ekran görüntüsünde de görebileceğiniz gibi Kategorilers
adındaki LINQ serisini düzenlerken düzenlediğimiz tablonun / nesnelerin
adı URL içerisinde belirdikten sonra doğrudan **List.aspx** adında bir
dosya çağrılıyor. Bu dosya hali hazırda **PageTemplates** içerisinde
bulunan dosyanın ta kendisi. Bunun gibi **Edit** düğmesine
tıkladığımızda da **Edit.aspx** ve tüm diğerleri de uygun işlemlerde
tablo isminin ardından geliyorlar. Tabi ki
[URLRewriting](http://daron.yondem.com/tr/post/7d7a31e7-5427-4186-bf42-7797634fb037)'den
bahsediyoruz ama konumuz o olmadığı için detaylara girmeyeceğim.

PageTemplates içerisinde herhangi bir dosyanın görselliğini veya
yapısını değiştirdiğiniz anda projenizdeki tüm tablolarla ilgili
işlemlerde gözükür hale gelecektir. Unutmayın tüm tablolar için bu
dosyalar kullanılıyor. Peki bu durumu nasıl değiştirebiliriz?

**Farklı tablolara farklı sayfalar?**

Aslında tüm bu yönlendirme işlemlerinin yapıldığı yer projenin
Global.asax dosyası. Global.asax içerisinde kodlar tabloların ne şekilde
hangi dosyalarla işlem yapacağına karar veriyor.

**[VB]**

    routes.Add(<span style="color: blue;">New</span>
DynamicDataRoute(<span
style="color: #a31515;">"**{table}/{action}**.aspx"</span>) <span
style="color: blue;">With</span> { \_

        .Constraints = <span style="color: blue;">New</span>
RouteValueDictionary(<span style="color: blue;">New</span> <span
style="color: blue;">With</span> {.Action = <span
style="color: #a31515;">"List|Details|Edit|Insert"</span>}), \_

        .Model = model})

**[C\#]**

        routes.Add(<span style="color: blue;">new</span> <span
style="color: #2b91af;">DynamicDataRoute</span>(<span
style="color: #a31515;">"**{table}/{action}**.aspx"</span>) {

            Constraints = <span style="color: blue;">new</span> <span
style="color: #2b91af;">RouteValueDictionary</span>(<span
style="color: blue;">new</span> { action = <span
style="color: #a31515;">"List|Details|Edit|Insert"</span> }),

            Model = model

        });

Yukarıdaki gördüğünüz kod Global.asax içerisinde hazır olarak bulunuyor
ve List, Details, Edit, Insert işlemlerinin hepsini **tablo adı /
aksiyon adı .aspx** şeklinde yönlendiriyor. Aslında Dynamic Web Site
yapısına gelen bir diğer özellik de tüm bu CRUD işlemlerinin tek bir
sayfada yapılacak şekilde düzenlenmesi. Yani verileri ekleme, çıkarma ve
düzenleme işlemlerinin hepsini tek bir sayfada halledebilecek şekilde
hazırlanmış bir şablon da DynamicData klasöründeki PageTemplates
içerisinde duruyor : **ListDetails.aspx**.

Bu dosya içerisindeki bir GridView Inline Editin sağlarken
DetailsView'de detayların gösterilmesi ve yeni kayıt eklenmesini
sağlıyor. Peki yönlendirmeyi nasıl değiştirebiliriz? Bu işlemin kodu de
Global.asax içerisinde pasif bir şekilde duruyor. Tek yapmanız gereken
yukarıdaki kodu pasif hale alıp aşağıdaki aktif hale getirmek.

**[VB]**

        routes.Add(<span style="color: blue;">New</span>
DynamicDataRoute(<span
style="color: #a31515;">"{table}/ListDetails.aspx"</span>) <span
style="color: blue;">With</span> { \_

            .Action = PageAction.List, \_

            .ViewName = <span
style="color: #a31515;">"ListDetails"</span>, \_

            .Model = model})

 

        routes.Add(<span style="color: blue;">New</span>
DynamicDataRoute(<span
style="color: #a31515;">"{table}/ListDetails.aspx"</span>) <span
style="color: blue;">With</span> { \_

            .Action = PageAction.Details, \_

            .ViewName = <span
style="color: #a31515;">"ListDetails"</span>, \_

            .Model = mod

**[C\#]**

        routes.Add(<span style="color: blue;">new</span> <span
style="color: #2b91af;">DynamicDataRoute</span>(<span
style="color: #a31515;">"{table}/ListDetails.aspx"</span>)

        {

            Action = <span
style="color: #2b91af;">PageAction</span>.List,

            ViewName = <span
style="color: #a31515;">"ListDetails"</span>,

            Model = model

        });

 

        routes.Add(<span style="color: blue;">new</span> <span
style="color: #2b91af;">DynamicDataRoute</span>(<span
style="color: #a31515;">"{table}/ListDetails.aspx"</span>)

        {

            Action = <span
style="color: #2b91af;">PageAction</span>.Details,

            ViewName = <span
style="color: #a31515;">"ListDetails"</span>,

            Model = model

        });

Kodlarda da yer aldığı üzere toplam iki yönlendirme yapıyoruz. Birincisi
"**List**" işleminin **tablo adı / ListDetails.aspx** sayfasında
yapılacağı ile ilgili diğer ise **Details** görünümünün de aynı şekilde
yapılacağı ile ilgili. Edit ve Insert işlemlerini yönlendirmemize gerek
yok çünkü zaten onlar artık ListDetails içerisinde hallediliyor olacak.

![ListDetails ile herşey aynı sayfada
halloluyor.](media/Dynamic_Web_Site_larin_proje_yapisi_ve_InLine_Editing_destegi/12102008_3.png)\
*ListDetails ile herşey aynı sayfada halloluyor.*

Yukarıdaki ekran görüntüsünde ListDetails.aspx'i görüyorsunuz. GridView
artık kendi içerisinde InlineEdit destekliyor ve bizim kategori kolonu
da gördüğünüz gibi **Edit** modunda bir **DropDownList** olarak
beliriyor.

Peki bizim esas konumuz neydi? Biz farklı bir tabloyu farklı bir dosya
ile göstermek istiyorduk. Gelin örneğimizdeki **Urunler** tablosunun
**ListDetails** ile gösterilmesini ayarlarken geri kalanların normal bir
şekilde ayrı ayrı dosyalarla düzenlenmesini sağlayalım.

**[VB]**

        routes.Add(<span style="color: blue;">New</span>
DynamicDataRoute(<span
style="color: #a31515;">"**Urunlers**/ListDetails.aspx"</span>) <span
style="color: blue;">With</span> { \_

            .Action = PageAction.List, \_

            .ViewName = <span
style="color: #a31515;">"ListDetails"</span>, \_

**            .Table =** <span
style="color: #a31515;">"**Urunlers"**</span>**, \_**

            .Model = model})

 

        routes.Add(<span style="color: blue;">New</span>
DynamicDataRoute(<span
style="color: #a31515;">"**Urunlers**/ListDetails.aspx"</span>) <span
style="color: blue;">With</span> { \_

            .Action = PageAction.Details, \_

            .ViewName = <span
style="color: #a31515;">"ListDetails"</span>, \_

**            .Table =** <span
style="color: #a31515;">"**Urunlers"**</span>**, \_**

            .Model = model})

 

        routes.Add(<span style="color: blue;">New</span>
DynamicDataRoute(<span
style="color: #a31515;">"{table}/{action}.aspx"</span>) <span
style="color: blue;">With</span> { \_

            .Constraints = <span style="color: blue;">New</span>
RouteValueDictionary(<span style="color: blue;">New</span> <span
style="color: blue;">With</span> {.Action = <span
style="color: #a31515;">"List|Details|Edit|Insert"</span>}), \_

            .Model = model})

**[C\#]**

        routes.Add(<span style="color: blue;">new</span> <span
style="color: #2b91af;">DynamicDataRoute</span>(<span
style="color: #a31515;">"**Urunlers**/ListDetails.aspx"</span>)

        {

            Action = <span
style="color: #2b91af;">PageAction</span>.List,

            ViewName = <span
style="color: #a31515;">"ListDetails"</span>,

**            Table =** <span
style="color: #a31515;">"**Urunlers"**</span>,

            Model = model

        });

 

        routes.Add(<span style="color: blue;">new</span> <span
style="color: #2b91af;">DynamicDataRoute</span>(<span
style="color: #a31515;">"**Urunlers**/ListDetails.aspx"</span>)

        {

            Action = <span
style="color: #2b91af;">PageAction</span>.Details,

            ViewName = <span
style="color: #a31515;">"ListDetails"</span>,

            **Table =** <span
style="color: #a31515;">"**Urunlers"**</span>,

            Model = model

        });

 

        routes.Add(<span style="color: blue;">new</span> <span
style="color: #2b91af;">DynamicDataRoute</span>(<span
style="color: #a31515;">"{table}/{action}.aspx"</span>)

        {

            Constraints = <span style="color: blue;">new</span> <span
style="color: #2b91af;">RouteValueDictionary</span>(<span
style="color: blue;">new</span> { action = <span
style="color: #a31515;">"List|Details|Edit|Insert"</span> }),

            Model = model

        });

Yukarıdaki kodlar **Urunlers** tablosunun **ListDetails.aspx** ile
gösterilmesini ve geri kalan tüm tabloların standart bir şekilde **tablo
adı / aksiyon adı.aspx** ile düzenlenmesini sağlayacaktır. Burada önemli
olan noktalardan biri kodumuzun içerisindeki istisnai durumların yani
bizim örneğimizde **Urunlers** tablosunun durumunun kod sırasında daha
önde tanımlanmış olmasının şart olması. Aksi halde sistem istediğimiz
gibi çalışmayacaktır.

Bu yazıda Dynamic Web Site yapısının nasıl çalıştığını ve proje yapısını
incelemekle beraber web sitelerini özelleştirme dünyasına da ufak bir
giriş yaptık. Sonraki yazılarımda derin detaylara yolculuğumuz devam
edecek.

Hepinize kolay gelsin.


