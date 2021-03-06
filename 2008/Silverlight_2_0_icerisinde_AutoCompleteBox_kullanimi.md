---
FallbackID: 2252
Title: Silverlight 2.0 içerisinde AutoCompleteBox kullanımı.
PublishDate: 20/11/2008
EntryID: Silverlight_2_0_icerisinde_AutoCompleteBox_kullanimi
IsActive: True
Section: software
MinutesSpent: 0
Tags: Silverlight 2.0
old.EntryID: 611e4193-9dec-4c92-8015-67c41b9bed73
---
AutoComplete işlevselliği AJAX günlerinden alışık olduğumuz bir sistem.
Herhangi bir TextBox'a kullanıcı yazı yazarken aynı anda uygun
alternatifleri göstermek ve aslında arka planda bir arama sistemi kurmak
gibi işlemleri uzun zamandır farklı arayüz araçları kullansak da bir
şekilde programcılar olarak hazırlayabiliyoruz. Silverlight tarafında
ise Silverlight'ın görsel gücünden de faydalanarak çok ilginç çözümler
üretmek mümkün. Silverlight dünyasında AutoComplete altyapılarını
incelerken Silverlight Toolkit içerisindeki **AutoCompleteBox**
kontrolünü kullanacağız.

*Not: Silverlight Toolkit'i kullanabilmeniz için*
[*CodePlex*](http://daron.yondem.com/tr/ct.ashx?id=c7205227-d787-4df7-9e0e-fff1a9be63b4&url=http%3a%2f%2fcodeplex.com%2fSilverlight)
*üzerindeki adresten kütüphaneyi indirerek içerisindeki*
***Microsoft.Windows.Controls.dll*** *dosyasını projenize referans
olarak eklemelisiniz.*

**En hızlı şekilde AutoCompleteBox kullanımı..**

AutoCompleteBox'ın kullanımı aslında çok basit. Hemen bir **String**
**Array** veya **List** yaratarak AutoCompleteBox'a bind etmeniz yeterli
olacaktır. Tüm filtreleme ve AutoComplete işlemleri otomatik olarak
yapılacaktır.

**[VB]**

    <span style="color: blue;">Private</span> <span
style="color: blue;">Sub</span> Page\_Loaded(<span
style="color: blue;">ByVal</span> sender <span
style="color: blue;">As</span> <span style="color: blue;">Object</span>,
<span style="color: blue;">ByVal</span> e <span
style="color: blue;">As</span> System.Windows.RoutedEventArgs) <span
style="color: blue;">Handles</span> <span
style="color: blue;">Me</span>.Loaded

        <span style="color: blue;">Dim</span> Liste <span
style="color: blue;">As</span> <span style="color: blue;">New</span>
List(<span style="color: blue;">Of</span> <span
style="color: blue;">String</span>)

        Liste.Add(<span style="color: #a31515;">"ASP.NET"</span>)

        Liste.Add(<span style="color: #a31515;">"AJAX"</span>)

        Liste.Add(<span style="color: #a31515;">"Silverlight"</span>)

        Liste.Add(<span style="color: #a31515;">"WPF"</span>)

        AutoComplete1.ItemsSource = Liste

    <span style="color: blue;">End</span> <span
style="color: blue;">Sub</span>

**[C\#]**

        <span style="color: blue;">void</span> Page\_Loaded(<span
style="color: blue;">object</span> sender, <span
style="color: #2b91af;">RoutedEventArgs</span> e)

        {

                <span style="color: #2b91af;">List</span>\<<span
style="color: #2b91af;">String</span>\> Liste = <span
style="color: blue;">new</span> <span
style="color: #2b91af;">List</span>\<<span
style="color: blue;">string</span>\>();

                Liste.Add(<span
style="color: #a31515;">"ASP.NET"</span>);

                Liste.Add(<span style="color: #a31515;">"AJAX"</span>);

                Liste.Add(<span
style="color: #a31515;">"Silverlight"</span>);

                Liste.Add(<span style="color: #a31515;">"WPF"</span>);

                AutoComplete1.ItemsSource = Liste;

        }

Yukarıdaki kod ile hazırladığımız basit bir uygulamanın aşağıda da XAML
kodunu inceleyebilirsiniz.

**[XAML]**

<span style="color: blue;">\<</span><span
style="color: #a31515;">UserControl</span><span style="color: red;">
x</span><span style="color: blue;">:</span><span
style="color: red;">Class</span><span
style="color: blue;">="SilverlightApplication3.Page"</span>

  <span style="color: red;"> xmlns</span><span
style="color: blue;">="http://schemas.microsoft.com/winfx/2006/xaml/presentation"</span>

  <span style="color: red;"> xmlns</span><span
style="color: blue;">:</span><span style="color: red;">x</span><span
style="color: blue;">="http://schemas.microsoft.com/winfx/2006/xaml"</span>

  <span style="color: red;"> Width</span><span
style="color: blue;">="400"</span><span style="color: red;">
Height</span><span style="color: blue;">="300"</span><span
style="color: red;"> xmlns</span><span
style="color: blue;">:</span><span
style="color: red;">controls</span><span
style="color: blue;">="clr-namespace:Microsoft.Windows.Controls;assembly=Microsoft.Windows.Controls"\></span>

<span style="color: #a31515;">    </span><span
style="color: blue;">\<</span><span
style="color: #a31515;">Grid</span><span style="color: red;">
x</span><span style="color: blue;">:</span><span
style="color: red;">Name</span><span
style="color: blue;">="LayoutRoot"</span><span style="color: red;">
Background</span><span style="color: blue;">="White"\></span>

<span style="color: #a31515;">      </span><span
style="color: blue;">\<</span><span
style="color: #a31515;">controls</span><span
style="color: blue;">:</span><span
style="color: #a31515;">**AutoCompleteBox**</span><span
style="color: red;"> Height</span><span
style="color: blue;">="24"</span><span style="color: red;">
Margin</span><span style="color: blue;">="24,24,144,0"</span><span
style="color: red;"> VerticalAlignment</span><span
style="color: blue;">="Top"</span><span style="color: red;">
x</span><span style="color: blue;">:</span><span
style="color: red;">Name</span><span
style="color: blue;">="**AutoComplete1**"/\></span>

<span style="color: #a31515;">    </span><span
style="color: blue;">\</</span><span
style="color: #a31515;">Grid</span><span style="color: blue;">\></span>

<span style="color: blue;">\</</span><span
style="color: #a31515;">UserControl</span><span
style="color: blue;">\></span>

![Basit bir AutoComplete
örneği.](media/Silverlight_2_0_icerisinde_AutoCompleteBox_kullanimi/19112008_1.png)\
*Basit bir AutoComplete örneği.*

**AutoCompleteBox'ın özellikleri.**

**IsTextCompletionEnabled** - Bu özellik açık olduğunda kullanıcı yazı
yazdıkça sadece alternatifler gösterilmez, ek olarak en yakın alternatif
sanki yazılmış gibi TextBox içerisinde de gösterilir. Varsayılan değeri
True şeklindedir.

**SelectedItem** - Eğer kullanıcı AutoCompleteBox'ın açılan ListBox
kısmından bir öğe seçerse SelectedItemChanged çalışır ve SelectedItem
geriye bir Item döndürür. Kullanıcı ListBox içerisinde yer alan bir
Item'ın metnini elle yazmışsa SelectedItem geriye değer
döndürmeyecektir.

**SearchMode** - AutoComplete işlemi yapılırken kaynak veride ne şekilde
arama yapılacağına karar veren SearchMode özelliği varsayılan değeri
olan **StartsWith** ile gelir. İsterseniz **Contains** seçeneğini
seçerek doğrudan kaynak verinin içindeki tüm metinlerin içinde arama
yapılmasını da sağlayabilirsiniz. Eğer kendi arama sisteminizi entegre
edecekseniz **None** seçeneğini seçmeniz gerekecektir.

**MinimumPopulateDelay** - Kullanıcı yazı yazarken ne kadar süre sonra
alternatiflerin gösterileceğini belirler. Eğer veri kaynağı istemci
tarafında bir Silverlight değişkeni ise varsayılan değer olan 0 ile
herhangi bir sorun yaşamazsınız. Fakat alternatifleri sunucudan her
seferinde çekiyorsanız buradaki bekleme süresini uzatmakta büyük fayda
olacaktır.

**MinimumPrefixLength** - Alternatifler gösterilmeden önce kaç
karakterlik verinin girilmiş olması gerektiğine dair ayar bu özellik
üzerinden yapılabilir.

**Kendi filtreleme mekanizmamızı yazalım.**

Bir AutoCompleteBox'ı aslında iki şekilde veri bağlamış olabiliriz.
Bunlardan birincisi yazımızın başındaki gibi basit bir metin dizisini
AutoCompleteBox'a aktarmak ikincisi ise kendi tanımladığımız nesnelerin
bir dizisini bağlamak. Gelin her iki durumda da filtreleme işlemlerini
nasıl özelleştirebileceğimize bakalım.

Bir önceki örneğimizin üzerinden yola devam edersek zaten hali hazırda
bir String listesini alıp AutoCompleteBox'ımıza bağlamıştık.
AutoCompleteBox'ın **TextFilter** özelliğini değiştirirek filtreleme
işleminin tam olarak nasıl yapılacağına karar verebiliriz. Bizim
yapacağımız örnekte kullanıcının yazdığı metin ile başlayan değil de
biten öğeleri göstermeye çalışacağız.

**[VB]**

    <span style="color: blue;">Function</span> Filtreleme(<span
style="color: blue;">ByVal</span> Search <span
style="color: blue;">As</span> <span style="color: blue;">String</span>,
<span style="color: blue;">ByVal</span> item <span
style="color: blue;">As</span> <span style="color: blue;">String</span>)

        <span style="color: blue;">If</span>
item.ToString.EndsWith(Search) <span style="color: blue;">Then</span>

            <span style="color: blue;">Return</span> <span
style="color: blue;">True</span>

        <span style="color: blue;">Else</span>

            <span style="color: blue;">Return</span> <span
style="color: blue;">False</span>

        <span style="color: blue;">End</span> <span
style="color: blue;">If</span>

    <span style="color: blue;">End</span> <span
style="color: blue;">Function</span>

**[C\#]**

        <span style="color: blue;">public</span> <span
style="color: blue;">bool</span> Filtreleme(<span
style="color: blue;">string</span> Search, <span
style="color: blue;">string</span> item)

        {

            <span style="color: blue;">if</span>
(item.ToString().EndsWith(Search)) {

                <span style="color: blue;">return</span> <span
style="color: blue;">true</span>;

            }

            <span style="color: blue;">else</span> {

                <span style="color: blue;">return</span> <span
style="color: blue;">false</span>;

            }

        }

Yukarıdaki fonksiyonumuzu filtreleme işlemlerini yapmak için
kullanacağız. Gelen iki parametreden ilki kullanıcının TextBox içerisine
yazdığı metin, ikincisi ise o an fonksiyonumuza aktarılan ana kaynak
veriden gelen bir Item. Burada kafalar biraz karışabilir o nedenle biraz
daha detaya inelim. AutoCompleteBox filtreleme işlemini yaparken
elindeki verinin içindeki her bir öğeyi tek tek bizim filtreleme
fonksiyonumuza verecek ve söz konusu öğenin gösterilip
gösterilmeyeceğine dair bir cevap bekleyecek. Yani eğer veri kaynağında
10 adet öğe varsa bu fonksiyon 10 defa çağrılacak.

**[VB]**

    <span style="color: blue;">Private</span> <span
style="color: blue;">Sub</span> Page\_Loaded(<span
style="color: blue;">ByVal</span> sender <span
style="color: blue;">As</span> <span style="color: blue;">Object</span>,
<span style="color: blue;">ByVal</span> e <span
style="color: blue;">As</span> System.Windows.RoutedEventArgs) <span
style="color: blue;">Handles</span> <span
style="color: blue;">Me</span>.Loaded

        <span style="color: blue;">Dim</span> Liste <span
style="color: blue;">As</span> <span style="color: blue;">New</span>
List(<span style="color: blue;">Of</span> <span
style="color: blue;">String</span>)

        Liste.Add(<span style="color: #a31515;">"ASP.NET"</span>)

        Liste.Add(<span style="color: #a31515;">"AJAX"</span>)

        Liste.Add(<span style="color: #a31515;">"Silverlight"</span>)

        Liste.Add(<span style="color: #a31515;">"WPF"</span>)

 

**        AutoComplete1.TextFilter =** <span
style="color: blue;">**New**</span>
**Microsoft.Windows.Controls.AutoCompleteSearchPredicate(**<span
style="color: blue;">**Of**</span> <span style="color: blue;">
**String**</span>**)(**<span style="color: blue;">**AddressOf**</span>
**Filtreleme)**

        AutoComplete1.ItemsSource = Liste

    <span style="color: blue;">End</span> <span
style="color: blue;">Sub</span>

**[C\#]**

        <span style="color: blue;">void</span> Page\_Loaded(<span
style="color: blue;">object</span> sender, <span
style="color: #2b91af;">RoutedEventArgs</span> e)

        {

                <span style="color: #2b91af;">List</span>\<<span
style="color: #2b91af;">String</span>\> Liste = <span
style="color: blue;">new</span> <span
style="color: #2b91af;">List</span>\<<span
style="color: blue;">string</span>\>();

                Liste.Add(<span
style="color: #a31515;">"ASP.NET"</span>);

                Liste.Add(<span style="color: #a31515;">"AJAX"</span>);

                Liste.Add(<span
style="color: #a31515;">"Silverlight"</span>);

                Liste.Add(<span style="color: #a31515;">"WPF"</span>);

 

**                AutoComplete1.TextFilter =** <span
style="color: blue;">**new**</span> **Microsoft.Windows.Controls.**<span
style="color: #2b91af;">**AutoCompleteSearchPredicate**</span>\<<span
style="color: blue;">**string**</span>**\>(Filtreleme);**

                AutoComplete1.ItemsSource = Liste;

        }

Hazırladığımız filtreleme fonksiyonunu tabi ki AutoCompleteBox'ın
**TextFilter'ına** da aktarmamız gerek. Yukarıdaki kodlardaki kalın
satırlarda söz konusu aktarma işleminin nasıl yapıldığını
inceleyebilirsiniz. **TextFilter** bizden bir
**AutoCompleteSearchPredicate** istiyor, biz de kendisine istediğini
veriyoruz :)

Peki ya AutoCompleteBox'a kendi yarattığımız nesne türlerinden bir liste
bağlamış olsaydık bu filtreleme işlemini nasıl yapacaktık. Böyle bir
durumda **TextFilter** yerine **ItemFilter'ı** kullanmak zorunda
kalacaktık. Gelin ilk olarak örneğimizde ilerleyebilmek için **Kitap**
adında kendi sınıfımızı tanımlayalım.

**[VB]**

    <span style="color: blue;">Public</span> <span
style="color: blue;">Class</span> Kitap

 

        <span style="color: blue;">Private</span> PAdi <span
style="color: blue;">As</span> <span style="color: blue;">String</span>

        <span style="color: blue;">Public</span> <span
style="color: blue;">Property</span> Adi() <span
style="color: blue;">As</span> <span style="color: blue;">String</span>

            <span style="color: blue;">Get</span>

                <span style="color: blue;">Return</span> PAdi

            <span style="color: blue;">End</span> <span
style="color: blue;">Get</span>

            <span style="color: blue;">Set</span>(<span
style="color: blue;">ByVal</span> value <span
style="color: blue;">As</span> <span style="color: blue;">String</span>)

                PAdi = value

            <span style="color: blue;">End</span> <span
style="color: blue;">Set</span>

        <span style="color: blue;">End</span> <span
style="color: blue;">Property</span>

 

        <span style="color: blue;">Private</span> PFiyat <span
style="color: blue;">As</span> <span style="color: blue;">Double</span>

        <span style="color: blue;">Public</span> <span
style="color: blue;">Property</span> Fiyat() <span
style="color: blue;">As</span> <span style="color: blue;">Double</span>

            <span style="color: blue;">Get</span>

                <span style="color: blue;">Return</span> PFiyat

            <span style="color: blue;">End</span> <span
style="color: blue;">Get</span>

            <span style="color: blue;">Set</span>(<span
style="color: blue;">ByVal</span> value <span
style="color: blue;">As</span> <span style="color: blue;">Double</span>)

                PFiyat = value

            <span style="color: blue;">End</span> <span
style="color: blue;">Set</span>

        <span style="color: blue;">End</span> <span
style="color: blue;">Property</span>

 

    <span style="color: blue;">End</span> <span
style="color: blue;">Class</span>

**[C\#]**

        <span style="color: blue;">public</span> <span
style="color: blue;">class</span> <span
style="color: #2b91af;">Kitap</span>

        {

            <span style="color: blue;">public</span> <span
style="color: blue;">string</span> Adi { <span
style="color: blue;">get</span>; <span style="color: blue;">set</span>;
}

            <span style="color: blue;">public</span> <span
style="color: blue;">double</span> Fiyat { <span
style="color: blue;">get</span>; <span style="color: blue;">set</span>;
}

        }

Şimdi bu sınıflar üzerinden yola çıkarak Silverlight tarafında birkaç
kitap yaratıp AutoCompleteBox'larımıza DataBind edeceğiz.

**[VB]**

    <span style="color: blue;">Private</span> <span
style="color: blue;">Sub</span> Page\_Loaded(<span
style="color: blue;">ByVal</span> sender <span
style="color: blue;">As</span> <span style="color: blue;">Object</span>,
<span style="color: blue;">ByVal</span> e <span
style="color: blue;">As</span> System.Windows.RoutedEventArgs) <span
style="color: blue;">Handles</span> <span
style="color: blue;">Me</span>.Loaded

        <span style="color: blue;">Dim</span> Liste <span
style="color: blue;">As</span> <span style="color: blue;">New</span>
List(<span style="color: blue;">Of</span> Kitap)

        Liste.Add(<span style="color: blue;">New</span> Kitap <span
style="color: blue;">With</span> {.Adi = <span
style="color: #a31515;">"ASP.NET AJAX"</span>, .Fiyat = 25})

        Liste.Add(<span style="color: blue;">New</span> Kitap <span
style="color: blue;">With</span> {.Adi = <span
style="color: #a31515;">"ADO.NET"</span>, .Fiyat = 35})

        Liste.Add(<span style="color: blue;">New</span> Kitap <span
style="color: blue;">With</span> {.Adi = <span
style="color: #a31515;">"WPF"</span>, .Fiyat = 15})

        Liste.Add(<span style="color: blue;">New</span> Kitap <span
style="color: blue;">With</span> {.Adi = <span
style="color: #a31515;">"Silverlight"</span>, .Fiyat = 25})

 

        AutoComplete1.ItemFilter = <span style="color: blue;">New</span>
Microsoft.Windows.Controls.AutoCompleteSearchPredicate(<span
style="color: blue;">Of</span> <span style="color: blue;">
**Object**</span>)(<span style="color: blue;">AddressOf</span>
**Filtreleme**)

 

        AutoComplete1.ItemsSource = Liste

    <span style="color: blue;">End</span> <span
style="color: blue;">Sub</span>

**[C\#]**

        <span style="color: blue;">void</span> Page\_Loaded(<span
style="color: blue;">object</span> sender, <span
style="color: #2b91af;">RoutedEventArgs</span> e)

        {

 

                  <span style="color: #2b91af;">List</span>\<<span
style="color: #2b91af;">Kitap</span>\> Liste = <span
style="color: blue;">new</span> <span
style="color: #2b91af;">List</span>\<<span
style="color: #2b91af;">Kitap</span>\>();

        Liste.Add(<span style="color: blue;">new</span> <span
style="color: #2b91af;">Kitap</span>  {Adi = <span
style="color: #a31515;">"ASP.NET AJAX"</span>, Fiyat = 25});

        Liste.Add(<span style="color: blue;">new</span> <span
style="color: #2b91af;">Kitap</span>  {Adi = <span
style="color: #a31515;">"ADO.NET"</span>, Fiyat = 35});

        Liste.Add(<span style="color: blue;">new</span> <span
style="color: #2b91af;">Kitap</span>  {Adi = <span
style="color: #a31515;">"WPF"</span>, Fiyat = 15});

        Liste.Add(<span style="color: blue;">new</span> <span
style="color: #2b91af;">Kitap</span>  {Adi = <span
style="color: #a31515;">"Silverlight"</span>, Fiyat = 25});

 

        AutoComplete1.ItemFilter = <span style="color: blue;">new</span>
Microsoft.Windows.Controls.<span
style="color: #2b91af;">AutoCompleteSearchPredicate</span>\<<span
style="color: #2b91af;">**Object**</span>\>(**Filtreleme**);

 

        AutoComplete1.ItemsSource = Liste;

        }

Kodumuz içerisinde çok büyük değişiklikler yok. Bu sefer bir **String**
listesi yerine **Kitap** listesi yaratıyor ve AutoCompleteBox'ın
**ItemsSource'una** eşitliyoruz. Filtreleme işlemi için yine
**Filtreleme** adında bir metod kullanacağımız için **ItemFilter**
özeliğine de söz konusu metodu bağlıyoruz. Aradaki en önemli fark
elimizdeki **Predicate'in** artık **Object** türünü taşıyor olması.

**[VB]**

    <span style="color: blue;">Function</span> Filtreleme(<span
style="color: blue;">ByVal</span> Search <span
style="color: blue;">As</span> <span style="color: blue;">String</span>,
<span style="color: blue;">ByVal</span> item <span
style="color: blue;">As</span> <span style="color: blue;">
**Object**</span>)

        <span style="color: blue;">If</span> <span
style="color: blue;">CType</span>(item, **Kitap**).**Fiyat** \< <span
style="color: blue;">CInt</span>(**Search**) <span
style="color: blue;">Then</span>

            <span style="color: blue;">Return</span> <span
style="color: blue;">True</span>

        <span style="color: blue;">Else</span>

            <span style="color: blue;">Return</span> <span
style="color: blue;">False</span>

        <span style="color: blue;">End</span> <span
style="color: blue;">If</span>

    <span style="color: blue;">End</span> <span
style="color: blue;">Function</span>

**[C\#]**

        <span style="color: blue;">public</span> <span
style="color: blue;">bool</span> Filtreleme(<span
style="color: blue;">string</span> Search, <span
style="color: blue;">object</span> item)

        {

            <span style="color: blue;">if</span> (((<span
style="color: #2b91af;">**Kitap**</span>)item).**Fiyat** \< <span
style="color: blue;">int</span>.Parse(**Search**)) {

                <span style="color: blue;">return</span> <span
style="color: blue;">true</span>;

            }

            <span style="color: blue;">else</span> {

                <span style="color: blue;">return</span> <span
style="color: blue;">false</span>;

            }

        }

Filtreleme metodumuzun ikinci parametresi artık **Object** tipinde. Biz
aslında buradaki değişkenin bir **Kitap** nesnesi olduğunu biliyoruz
çünkü **AutoCompleteBox** tek tek kendisine verilen öğeleri bu
filtreleme fonksiyonuna iletecektir. Bu nedenle elimizde gelen objeyi
**Kitap** tipine cast edip bu sefer de kitapların fiyatları üzerinden
filtreleme yapıyoruz. Kullanıcıların **TextBox** içerisinde sayısal bir
fiyat gireceğini ve bu fiyatın altındaki kitapların listeleneceğini
varsayalım.

Bu şekilde uygulamamızı çalıştırırsak ufak bir karışıklık olacaktır.
AutoCompleteBox'a bağladığımız veri Kitap'lardan oluşuyor. Peki
**AutoCompleteBox** bu Kitap nesnelerinin hangi özelliğini ekrana nasıl
getirecek? Örneğin kitabın adını mı yoksa fiyatını mı gösterecek
**AutoComplete** esnasında? İşte bu noktada da bizim XAML tarafına geçip
birkaç işlem yapmamız gerek.

**[XAML]**

<span style="color: blue;">\<</span><span
style="color: #a31515;">UserControl</span><span style="color: red;">
x</span><span style="color: blue;">:</span><span
style="color: red;">Class</span><span
style="color: blue;">="SilverlightApplication3.Page"</span>

  <span style="color: red;"> xmlns</span><span
style="color: blue;">="http://schemas.microsoft.com/winfx/2006/xaml/presentation"</span>

  <span style="color: red;"> xmlns</span><span
style="color: blue;">:</span><span style="color: red;">x</span><span
style="color: blue;">="http://schemas.microsoft.com/winfx/2006/xaml"</span>

  <span style="color: red;"> Width</span><span
style="color: blue;">="400"</span><span style="color: red;">
Height</span><span style="color: blue;">="300"</span><span
style="color: red;"> xmlns</span><span
style="color: blue;">:</span><span
style="color: red;">controls</span><span
style="color: blue;">="clr-namespace:Microsoft.Windows.Controls;assembly=Microsoft.Windows.Controls"\></span>

<span style="color: #a31515;">  </span><span
style="color: blue;">\<</span><span
style="color: #a31515;">UserControl.Resources</span><span
style="color: blue;">\></span>

<span style="color: #a31515;">    </span><span
style="color: blue;">\<</span><span
style="color: #a31515;">**DataTemplate**</span><span
style="color: red;"> x</span><span style="color: blue;">:</span><span
style="color: red;">Key</span><span
style="color: blue;">="**DataTemplate1**"\></span>

<span style="color: #a31515;">      </span><span
style="color: blue;">\<</span><span
style="color: #a31515;">Grid</span><span style="color: blue;">\></span>

<span style="color: #a31515;">        </span><span
style="color: blue;">\<</span><span
style="color: #a31515;">**TextBlock**</span><span style="color: red;">
HorizontalAlignment</span><span style="color: blue;">="Left"</span><span
style="color: red;"> VerticalAlignment</span><span
style="color: blue;">="Top"</span><span style="color: red;">
Text</span><span style="color: blue;">="**{**</span><span
style="color: #a31515;">**Binding**</span><span style="color: red;">
**Path**</span><span style="color: blue;">**=Fiyat}**"</span><span
style="color: red;"> TextWrapping</span><span
style="color: blue;">="Wrap"/\></span>

<span style="color: #a31515;">      </span><span
style="color: blue;">\</</span><span
style="color: #a31515;">Grid</span><span style="color: blue;">\></span>

<span style="color: #a31515;">    </span><span
style="color: blue;">\</</span><span
style="color: #a31515;">DataTemplate</span><span
style="color: blue;">\></span>

<span style="color: #a31515;">  </span><span
style="color: blue;">\</</span><span
style="color: #a31515;">UserControl.Resources</span><span
style="color: blue;">\></span>

<span style="color: #a31515;">    </span><span
style="color: blue;">\<</span><span
style="color: #a31515;">Grid</span><span style="color: red;">
x</span><span style="color: blue;">:</span><span
style="color: red;">Name</span><span
style="color: blue;">="LayoutRoot"</span><span style="color: red;">
Background</span><span style="color: blue;">="White"\></span>

<span style="color: #a31515;">      </span><span
style="color: blue;">\<</span><span
style="color: #a31515;">controls</span><span
style="color: blue;">:</span><span
style="color: #a31515;">AutoCompleteBox</span><span style="color: red;">
Height</span><span style="color: blue;">="24"</span><span
style="color: red;"> Margin</span><span
style="color: blue;">="24,24,144,0"</span><span style="color: red;">
VerticalAlignment</span><span style="color: blue;">="Top"</span><span
style="color: red;"> x</span><span style="color: blue;">:</span><span
style="color: red;">Name</span><span
style="color: blue;">="AutoComplete1"</span><span style="color: red;">
**ItemTemplate**</span><span style="color: blue;">**="{**</span><span
style="color: #a31515;">**StaticResource**</span><span
style="color: red;"> **DataTemplate1**</span><span
style="color: blue;">}"/\></span>

<span style="color: #a31515;">    </span><span
style="color: blue;">\</</span><span
style="color: #a31515;">Grid</span><span style="color: blue;">\></span>

<span style="color: blue;">\</</span><span
style="color: #a31515;">UserControl</span><span
style="color: blue;">\></span>

Artık bizim AutoCompleteBox'ımızın ItemTemplate'ini değiştirmemiz ve
özelleştirmemiz gerekiyor. Böylece tam olarak gelen veriden hangi
öğelerin nerelerde nasıl gösterileceğine karar verebiliriz. Yukarıdaki
kod içerisinde AutoCompleteBox'ın **ItemTemplate** özelliğinin
değiştirildiğini görebilirsiniz. DataTemplate1 adında yarattığımız
DataTemplate'i **UserControl.Resources** içerisine koyup
kullanabiliyoruz. **DataTemplate** içerisinde ise bir Grid ve TextBlock
bulunuyor. Söz konusu **TextBlock** doğrudan **Fiyat** adında bir
Field'e DataBind edilmiş durumda. Hatırlarsanız bizim **Kitap**
sınıfımızın **Fiyat** adında bir **Property'si** vardı. Böylece
AutoCompleteBox'a kendisine verilen verilerden her birinin **Fiyat**
özelliğinin **DataTemplate** içerisindeki bu TextBlock'un **Text'ine**
bağlanmasını sağladık. Tüm bu işlemleri Visual Studio içerisinde XAML
yazarak yapabileceğiniz gibi isterseniz Expression Blend'in arayüzünden
de tabi ki daha rahatlıkla yapabilirsiniz. Tek yapmanız gereken
AutoCompleteBox'a sağ tuş tıklayıp gelen menüden "Edit Other Templates /
Edit ItemTemplate" demek. Böylece tasarım modunda Blend içerisinde de
DataTemplate'in görselliğini değiştirebilirsiniz.

Artık filtreleme işlemlerini bitirdik, filtreleme esnasından Kitapların
sadece fiyatlarının gözükmesini de sağladık. Fakat neden sadece
fiyatları gözüksün ki? Kullanıcı TextBox içerisinde 25 yazdığınzda
25YTL'den ucuz kitapların hem adı hem fiyatı yazsa? Ve bunların
arasından bir kitap seçilince fiyatı otomatik olarak TextBlock içerisine
yerleşse daha güzel olmaz mı? AutoCompleteBox'ın açılan kısmının
görselliğini ne de olsa yukarıda değiştirmiştik, gelin şimdi ikinci bir
TextBlock ekleyerek onu da **Kitap** nesnelerinin **Adi** özelliğine
bağlayalım.

**[XAML]**

<span style="color: #a31515;">    </span><span
style="color: blue;">\<</span><span
style="color: #a31515;">DataTemplate</span><span style="color: red;">
x</span><span style="color: blue;">:</span><span
style="color: red;">Key</span><span
style="color: blue;">="DataTemplate1"\></span>

<span style="color: #a31515;">      </span><span
style="color: blue;">\<</span><span
style="color: #a31515;">StackPanel</span><span style="color: red;">
HorizontalAlignment</span><span
style="color: blue;">="Stretch"</span><span style="color: red;">
VerticalAlignment</span><span
style="color: blue;">="Stretch"</span><span style="color: red;">
Background</span><span style="color: blue;">="{</span><span
style="color: #a31515;">x</span><span style="color: blue;">:</span><span
style="color: #a31515;">Null</span><span
style="color: blue;">}"</span><span style="color: red;">
Orientation</span><span style="color: blue;">="Horizontal"\></span>

<span style="color: #a31515;">        </span><span
style="color: blue;">\<</span><span
style="color: #a31515;">TextBlock</span><span style="color: red;">
Text</span><span style="color: blue;">="{</span><span
style="color: #a31515;">Binding</span><span style="color: red;">
Path</span><span style="color: blue;">=**Adi**}"</span><span
style="color: red;"> Foreground</span><span
style="color: blue;">="\#FFFF0000"</span><span style="color: red;">
Height</span><span style="color: blue;">="Auto"</span><span
style="color: red;"> Width</span><span
style="color: blue;">="Auto"/\></span>

<span style="color: #a31515;">        </span><span
style="color: blue;">\<</span><span
style="color: #a31515;">TextBlock</span><span style="color: red;">
Text</span><span style="color: blue;">="{</span><span
style="color: #a31515;">Binding</span><span style="color: red;">
Path</span><span style="color: blue;">=**Fiyat**}"</span><span
style="color: red;"> Foreground</span><span
style="color: blue;">="\#FF838383"</span><span style="color: red;">
Height</span><span style="color: blue;">="Auto"</span><span
style="color: red;"> Width</span><span
style="color: blue;">="Auto"/\></span>

<span style="color: #a31515;">        </span><span
style="color: blue;">\<</span><span
style="color: #a31515;">TextBlock</span><span style="color: red;">
Text</span><span style="color: blue;">="**YTL**"</span><span
style="color: red;"> TextWrapping</span><span
style="color: blue;">="Wrap"</span><span style="color: red;">
Foreground</span><span style="color: blue;">="\#FF838383"</span><span
style="color: red;"> Height</span><span
style="color: blue;">="20"</span><span style="color: red;">
Width</span><span style="color: blue;">="20"/\></span>

<span style="color: #a31515;">      </span><span
style="color: blue;">\</</span><span
style="color: #a31515;">StackPanel</span><span
style="color: blue;">\></span>

<span style="color: #a31515;">    </span><span
style="color: blue;">\</</span><span
style="color: #a31515;">DataTemplate</span><span
style="color: blue;">\></span>

Gördüğünüz gibi DataTemplate'i değiştirerek aslında işimizi çözmüş
olduk. Geriye tek bir sorun kalıyor. Kullanıcı herhangi bir Item'ı
**ListBox** içerisinden seçtiğinde **TextBox'ın** içine ne yazılacak?
**Kitap** nesnesinin **Adi** mı? yoksa **Fiyatı** mı? Tabi ki bizim
örneğimizde **Kitap** nesnesinin fiyatı yazılacak aksi halde filtreleme
mekanizmamızla çakışacaktır.

**[VB]**

  <span style="color: blue;">Public</span> <span
style="color: blue;">Class</span> Kitap

 

        <span style="color: blue;">Private</span> PAdi <span
style="color: blue;">As</span> <span style="color: blue;">String</span>

        <span style="color: blue;">Public</span> <span
style="color: blue;">Property</span> Adi() <span
style="color: blue;">As</span> <span style="color: blue;">String</span>

            <span style="color: blue;">Get</span>

                <span style="color: blue;">Return</span> PAdi

            <span style="color: blue;">End</span> <span
style="color: blue;">Get</span>

            <span style="color: blue;">Set</span>(<span
style="color: blue;">ByVal</span> value <span
style="color: blue;">As</span> <span style="color: blue;">String</span>)

                PAdi = value

            <span style="color: blue;">End</span> <span
style="color: blue;">Set</span>

        <span style="color: blue;">End</span> <span
style="color: blue;">Property</span>

 

        <span style="color: blue;">Private</span> PFiyat <span
style="color: blue;">As</span> <span style="color: blue;">Double</span>

        <span style="color: blue;">Public</span> <span
style="color: blue;">Property</span> Fiyat() <span
style="color: blue;">As</span> <span style="color: blue;">Double</span>

            <span style="color: blue;">Get</span>

                <span style="color: blue;">Return</span> PFiyat

            <span style="color: blue;">End</span> <span
style="color: blue;">Get</span>

            <span style="color: blue;">Set</span>(<span
style="color: blue;">ByVal</span> value <span
style="color: blue;">As</span> <span style="color: blue;">Double</span>)

                PFiyat = value

            <span style="color: blue;">End</span> <span
style="color: blue;">Set</span>

        <span style="color: blue;">End</span> <span
style="color: blue;">Property</span>

 

**       ** <span style="color: blue;"> **Public**</span> <span
style="color: blue;">**Overrides**</span> <span style="color: blue;">
**Function**</span> **ToString()** <span style="color: blue;">
**As**</span> <span style="color: blue;">**String**</span>

**           ** <span style="color: blue;">**Return**</span> <span
style="color: blue;"> **Me**</span>**.Fiyat**

**       ** <span style="color: blue;"> **End**</span> <span
style="color: blue;">**Function**</span>

 

    <span style="color: blue;">End</span> <span
style="color: blue;">Class</span>

**[C\#]**

        <span style="color: blue;">public</span> <span
style="color: blue;">class</span> <span
style="color: #2b91af;">Kitap</span>

        {

            <span style="color: blue;">public</span> <span
style="color: blue;">string</span> Adi { <span
style="color: blue;">get</span>; <span style="color: blue;">set</span>;
}

            <span style="color: blue;">public</span> <span
style="color: blue;">double</span> Fiyat { <span
style="color: blue;">get</span>; <span style="color: blue;">set</span>;
}

 

**           ** <span style="color: blue;">**public**</span> <span
style="color: blue;"> **override**</span> <span
style="color: blue;">**string**</span> **ToString()**

**            {**

**               ** <span style="color: blue;">**return**</span> <span
style="color: blue;"> **this**</span>**.Fiyat.ToString();**

**            }**

        }

Bu da ne şimdi? dediğinizi duyar gibiyim. Maalesef AutoCompleteBox'ın
**ListBox'tan** seçili öğelerin hangi özelliklerinin alınacağına dair
bir ayarı yok. Aslında arka planda AutoCompleteBox kendi içerisinde bir
öğe seçildiğinde o öğeyi **ToString**() metodu ile alıp **TextBox**
içerisine yerleştiriyor. Bu durumda bizim de **ToString** metodunu
**Override** etmemiz her şeyi çözecektir. Artık herhangi bir **Kitap**
nesnesi üzerinden **ToString** çalıştırılırsa kitabın fiyat bilgisi
verilecek.

![Özelleştirilmiş bir AutoCompleteBox
örneği.](media/Silverlight_2_0_icerisinde_AutoCompleteBox_kullanimi/19112008_2.png)\
*Özelleştirilmiş bir AutoCompleteBox örneği.*

Hepinize kolay gelsin.


