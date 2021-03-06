---
FallbackID: 2396
Title: Silverlight 3.0 için Trigger Action Behavior'ları geliştirmek.
PublishDate: 24/8/2009
EntryID: Silverlight_3_0_icin_Trigger_Action_Behaviorlari_gelistirmek
IsActive: True
Section: software
MinutesSpent: 0
Tags: Expression Blend, Silverlight 3.0
old.EntryID: 635a040f-cf75-43c4-8cf6-c1541ab6c907
---
Blend içerisinde kullanılabilecek Behavior çeşitlerinden biri de
Trigger'lı Behavior'lar. Bu tip Behavior'lara genelde Action da
denebiliyor. Normal Behavior'lardan farklı olarak Trigger'lar da kendi
içlerinde yaratılırken Inherit ettikleri sınıfa göre değişebilirler. Bu
yazımızda **TriggeredAction** Behavior'larına göz atacağız.

**Ne işe yarar?**

TriggeredAction behaviorları sonuç itibari ile normal Behavior'lar gibi
bir aksyon almayı hedefler fakat bu aksyon yine kullanıcı tarafından
belirlenen bir durumu takiben işleme alınır. Normal şartlarda bir
TriggeredAction kendi Parent kontrolünü hedef alarak onun herhangi bir
event'ı çalıştığında çalışacak şekilde kenarda durur.

Örneğimizde basit bir MessageBox gösteren TriggerAction tanımlayacağız.
Diyelim ki herhangi bir kontrole tıklandığında veya farklı durumlarda
MessageBox'lar göstermek istiyoruz. Normalde yapmamız gereken kesinlikle
kod tarafına geçip uygun kodu yazmak olurdu. Oysa hazırlayacağımız
**TriggerAction** herhangi bir kod yazmadan tasarımcının istediği event
ve zaman için istediği mesajı MessageBox ile gösterebilmesini
sağlayacak.

Her zamanki gibi yeni bir Silverlight projesi yarattıkta sonra
**System.Windows.Interactivity.dll**'i referans olarak alıyoruz.
Projemize ekleyeceğimiz yeni bir VB/CS dosyasının içerisinde
Behavior'ımızı tanımlayacak sınıfı yazarken **TriggerAction** sınıfnı da
inherit ediyoruz.

**[VB]**

<span style="color: blue;">Public</span> <span
style="color: blue;">Class</span> MsgBoxTrigger

    <span style="color: blue;">Inherits</span>
Interactivity.TriggerAction(<span style="color: blue;">Of</span>
UIElement)

 

    <span style="color: blue;">Protected</span> <span
style="color: blue;">Overrides</span> <span
style="color: blue;">Sub</span> Invoke(<span
style="color: blue;">ByVal</span> parameter <span
style="color: blue;">As</span> <span style="color: blue;">Object</span>)

 

    <span style="color: blue;">End</span> <span
style="color: blue;">Sub</span>

<span style="color: blue;">End</span> <span
style="color: blue;">Class</span>

**[C\#]**

    <span style="color: blue;">public</span> <span
style="color: blue;">class</span> <span
style="color: #2b91af;">MsgBoxTrigger</span> :
System.Windows.Interactivity.<span
style="color: #2b91af;">TriggerAction</span>\<<span
style="color: #2b91af;">UIElement</span>\>

    {

        <span style="color: blue;">protected</span> <span
style="color: blue;">override</span> <span
style="color: blue;">void</span> Invoke(<span
style="color: blue;">object</span> parameter)

        {

        }

    }

Gördüğünüz üzere hemen anında Invoke adında bir de metoda sahip olduk.
TriggerAction sınıfında Invoke "MustInherit" olarak tanımlandığı için
söz konusu metodu bizim yazmamış şart. Zaten bu metod da bizim en çok
işimize yarayacak metod olacak. Herhangi bir şekilde bizim
Trigger'ımızda kullanıcı tarafından ayarlanmış event çalıştığında
buradaki Invoke metodu çalışacak. Anlayacağınız TriggerAction'ımızın tüm
işlevselliğini buraya yazacağız.

**[VB]**

    <span style="color: blue;">Private</span> PText <span
style="color: blue;">As</span> <span style="color: blue;">String</span>

    <span style="color: blue;">Public</span> <span
style="color: blue;">Property</span> MessageText() <span
style="color: blue;">As</span> <span style="color: blue;">String</span>

        <span style="color: blue;">Get</span>

            <span style="color: blue;">Return</span> PText

        <span style="color: blue;">End</span> <span
style="color: blue;">Get</span>

        <span style="color: blue;">Set</span>(<span
style="color: blue;">ByVal</span> value <span
style="color: blue;">As</span> <span style="color: blue;">String</span>)

            PText = value

        <span style="color: blue;">End</span> <span
style="color: blue;">Set</span>

    <span style="color: blue;">End</span> <span
style="color: blue;">Property</span>

**[C\#]**

        <span style="color: blue;">public</span> <span
style="color: blue;">string</span> MessageText { <span
style="color: blue;">get</span>; <span style="color: blue;">set</span>;
}

Tasarımcımızdan aynı anda MessageBox ile gösterilecek metni de almamız
gerek. O nedenle hemen bir de Property tanımlayarak sınıfımıza
ekliyoruz. Bir sonraki adımda basit bir şekilde Invoke metodunda bu
mesajı göstermemiz yeterli olacaktır.

**[VB]**

    <span style="color: blue;">Protected</span> <span
style="color: blue;">Overrides</span> <span
style="color: blue;">Sub</span> Invoke(<span
style="color: blue;">ByVal</span> parameter <span
style="color: blue;">As</span> <span style="color: blue;">Object</span>)

        MessageBox.Show(MessageText)

    <span style="color: blue;">End</span> <span
style="color: blue;">Sub</span>

**[C\#]**

        <span style="color: blue;">protected</span> <span
style="color: blue;">override</span> <span
style="color: blue;">void</span> Invoke(<span
style="color: blue;">object</span> parameter)

        {

            <span
style="color: #2b91af;">MessageBox</span>.Show(MessageText);

        }

Gördüğünüz gibi sistem epey basit. Her zamanki gibi isterseniz
**AssociatedObject'e** de ulaşarak **TriggerAction'ın** bağlı olduğu
kontrolü de bulabilirsiniz. Artık elimizdeki Behavior'ı rahatlıkla
tasarımcılar da Blend içerisinde kullanarak istedikleri durumlarda
MessageBox gösterebilirler.

![Özel TriggerAction Behavior'ımız
karşınızda.](media/Silverlight_3_0_icin_Trigger_Action_Behaviorlari_gelistirmek/23082009_1.png)\
*Özel TriggerAction Behavior'ımız karşınızda.*

XAML tarafına baktığımızda her zaman olduğu gibi tüm Trigger yapısı XML
ile tanımlanmış durumda. Gerekli XML NameSpace'ler de eklendikten sonra
hazırladığımız TriggerAction rahatlıkla kullanılabiliyor.

**[XAML]**

<span style="color: blue;">\<</span><span
style="color: #a31515;">UserControl</span>

   <span style="color: red;"> xmlns</span><span
style="color: blue;">="http://schemas.microsoft.com/winfx/2006/xaml/presentation"</span>

   <span style="color: red;"> xmlns</span><span
style="color: blue;">:</span><span style="color: red;">x</span><span
style="color: blue;">="http://schemas.microsoft.com/winfx/2006/xaml"</span>

   <span style="color: red;"> xmlns</span><span
style="color: blue;">:</span><span style="color: red;">d</span><span
style="color: blue;">="http://schemas.microsoft.com/expression/blend/2008"</span><span
style="color: red;"> xmlns</span><span
style="color: blue;">:</span><span style="color: red;">mc</span><span
style="color: blue;">="http://schemas.openxmlformats.org/markup-compatibility/2006"</span>

   <span style="color: red;"> mc</span><span
style="color: blue;">:</span><span
style="color: red;">Ignorable</span><span
style="color: blue;">="d"</span><span style="color: red;">
**xmlns**</span><span style="color: blue;">**:**</span><span
style="color: red;">**i**</span><span
style="color: blue;">**="clr-namespace:System.Windows.Interactivity;assembly=System.Windows.Interactivity"**</span><span
style="color: red;"> **xmlns**</span><span
style="color: blue;">**:**</span><span
style="color: red;">**local**</span><span
style="color: blue;">**="clr-namespace:Triggers\_VB"**</span><span
style="color: red;"> x</span><span style="color: blue;">:</span><span
style="color: red;">Class</span><span
style="color: blue;">="Triggers\_VB.MainPage"</span>

   <span style="color: red;"> d</span><span
style="color: blue;">:</span><span
style="color: red;">DesignWidth</span><span
style="color: blue;">="640"</span><span style="color: red;">
d</span><span style="color: blue;">:</span><span
style="color: red;">DesignHeight</span><span
style="color: blue;">="480"\></span>

<span style="color: #a31515;">  </span><span
style="color: blue;">\<</span><span
style="color: #a31515;">Grid</span><span style="color: red;">
x</span><span style="color: blue;">:</span><span
style="color: red;">Name</span><span
style="color: blue;">="LayoutRoot"\></span>

 

<span style="color: #a31515;">      </span><span
style="color: blue;">\<</span><span
style="color: #a31515;">Rectangle</span><span style="color: red;">
Fill</span><span style="color: blue;">="Red"</span><span
style="color: red;"> Stroke</span><span
style="color: blue;">="Black"</span><span style="color: red;">
HorizontalAlignment</span><span style="color: blue;">="Left"</span><span
style="color: red;"> Margin</span><span
style="color: blue;">="157,184,0,215"</span><span style="color: red;">
Width</span><span style="color: blue;">="159"\></span>

<span style="color: #a31515;">          </span><span
style="color: blue;">\<</span><span
style="color: #a31515;">i</span><span style="color: blue;">:</span><span
style="color: #a31515;">Interaction.Triggers</span><span
style="color: blue;">\></span>

<span style="color: #a31515;">              </span><span
style="color: blue;">\<</span><span
style="color: #a31515;">i</span><span style="color: blue;">:</span><span
style="color: #a31515;">EventTrigger</span><span style="color: red;">
**EventName**</span><span
style="color: blue;">="**MouseLeftButtonDown**"\></span>

<span style="color: #a31515;">                  </span><span
style="color: blue;">\<</span><span
style="color: #a31515;">local</span><span
style="color: blue;">:</span><span
style="color: #a31515;">**MsgBoxTrigger**</span><span
style="color: red;"> **MessageText**</span><span
style="color: blue;">="Selamlar!"/\></span>

<span style="color: #a31515;">              </span><span
style="color: blue;">\</</span><span
style="color: #a31515;">i</span><span style="color: blue;">:</span><span
style="color: #a31515;">EventTrigger</span><span
style="color: blue;">\></span>

<span style="color: #a31515;">          </span><span
style="color: blue;">\</</span><span
style="color: #a31515;">i</span><span style="color: blue;">:</span><span
style="color: #a31515;">Interaction.Triggers</span><span
style="color: blue;">\></span>

<span style="color: #a31515;">      </span><span
style="color: blue;">\</</span><span
style="color: #a31515;">Rectangle</span><span
style="color: blue;">\></span>

 

<span style="color: #a31515;">  </span><span
style="color: blue;">\</</span><span
style="color: #a31515;">Grid</span><span style="color: blue;">\></span>

<span style="color: blue;">\</</span><span
style="color: #a31515;">UserControl</span><span
style="color: blue;">\></span>

Hepinize kolay gelsin.

[Örneğe ait kaynak kodlar - 23082009\_2.rar (49,3
KB)](media/Silverlight_3_0_icin_Trigger_Action_Behaviorlari_gelistirmek/23082009_2.rar)


