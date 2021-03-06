---
FallbackID: 1735
Title: Internet Explorer ve Flash'lardaki Çerçeve (Aktivasyon) Sorunu
PublishDate: 28/4/2007
EntryID: Internet_Explorer_ve_Flashlardaki_Cerceve_Aktivasyon_Sorunu
IsActive: True
Section: software
MinutesSpent: 0
Tags: HTML, JavaScript
old.EntryID: b359c340-e08c-4466-a49b-4e304438824f
---
Bu konuyu uzun süre önce, daha Türkçe blog sitemi açmadığım zamanlarda
(17 Nisan 2006) İngilizce blog sitemde incelemiştim. İngilizce makaleye
[buradan](http://daron.yondem.com/en/post/5e86a2ff-9d03-431f-8759-e643bad1bdcc)
ulaşabilirsiniz. **Mayasoft Bilişim Akadem**i'sinde vermekte olduğum
**Web Tasarım** dersinde öğrencilerimden biri bu konuya değinince
sorunla ilgili çözümü Türkçe blog siteme de yazmam gerektiğini düşündüm.
Halen çok sayıda eski ve yeni yapılan web sitesinde Flash animasyonlar
ve Internet Explorer arasındaki sorun devam ediyor. İlk önce sorun nedir
ve nerden çıktı, ona bakalım.

Güncel bir örnek olarak bugünlerde ziyaret edeceğim
[EducaTurk](http://www.educaturk.com/educaturk/index.asp) fuarının yeni
web sitesini ele alabiliriz. Siteye girdikten sonra online davetiye
almak için tıklamam gereken görsel link Flash ile hazırlanmış. Fakat
gerekli düzenlemeler yapılmadığı için Internet Explorer ile siteye giriş
yaptığımda düğmeye iki kere tıklamam gerekiyor. Birinci tıklamayı Flash
animasyonunu aktive etmek için, ikinciyi de aktive edilmiş animasyona
tıklayabilmek için yapmam gerekiyor.

![](media/Internet_Explorer_ve_Flashlardaki_Cerceve_Aktivasyon_Sorunu/27042007_1.png)

Bu sorun sadece **Internet Explorer** için geçerli. **11 Nisan 2006**
tarihinde Microsoft tarafından bir
[yama](http://support.microsoft.com/?scid=kb%3Btr%3B912945&x=11&y=13)
çıkarıldı ve tüm Windows'lara Windows Update aracılığı ile yüklendi.
Microsoft, **ActiveX** objelerinin Internet Explorer'daki çalışma
yapısını değiştirmek durumunda kaldı. Bu durum da sayfalarımıza
eklediğimiz Flash objelerini etkiledi. Peki Microsoft neden bunu yaptı?
Özetle patent sorunları diyebiliriz. Konuyla ilgili [makaleyi
(İngilizce)
buradan](http://www.vnunet.com/vnunet/news/2153137/eolas-patent-case-prompts)
inceleyebilirsiniz. [Eolas](http://www.eolas.com/) ve [California
Üniversite](http://www.universityofcalifornia.edu/)'ine ait patent
nedeniyle web sayfaları içerisine ActiveX ile dinamik içerik, animasyon
eklenmesini sağlayan Microsoft 521m\$ cezaya çarptırıldı. Sonuç olarak
yukarıdaki manzara ortaya çıktı.

Peki bu sorundan nasıl kurtulabiliriz? Çözüm basit sayfanın içerisine
direk ActiveX objeleri eklemeyeceğiz. Ekleme işlemini **JavaScript** ile
istemci tarafında yapacağız. Bunun için Flash objemizi sayfaya
yerleştirecek olan HTML kodunu JavaScript ile sayfaya yazan bir
JavaScript fonksiyonu tanımlayarak harici bir JavaScript dosyasına
yerleştirmemiz gerekiyor.\

<span style="color: blue;"> function</span><span> GetLogo()</span>\
 <span> {</span>\
 <span> <span style="">   </span> document.write(<span
style="color: rgb(163, 21, 21);">'\<object
classid="clsid:d27cdb6e-ae6d-11cf-96b8-444553540000"
codebase="http://fpdownload.macromedia.com/pub/shockwave/cabs/flash/swflash.cab\#version=8,0,0,0"
**width="786" height="241"** id="logo" align="middle"\>\<param
name="allowScriptAccess" value="sameDomain" /\>\<param name="movie"
value="**banner.swf**" /\>\<param name="quality" value="high" /\>\<param
name="bgcolor" value="\#ffffff" /\>\<embed src="**banner.swf**"
quality="high" bgcolor="\#ffffff" **width="786" height="241"**
name="logo" align="middle" allowscriptaccess="sameDomain"
type="application/x-shockwave-flash"
pluginspage="http://www.macromedia.com/go/getflashplayer"
/\>\</object\>'</span>);</span>\
 <span> }</span>

Yukarıdaki JavaScript fonksiyonu HTML kodunu **document.write()**
JavaScript metodu ile sayfaya yazıyor. Bu fonksiyonu **flash.js** adında
bir metin dosyasına kaydediyoruz. Flash animasyonu kullanacağımız sayfa
ile aynı klasöre koyuyoruz. Kod içerisinde yer alan HTML kodundaki flash
animasyon dosyasına ait dosya adını ve boyut bilgilerini kendi sitenize
uygun şekilde değiştirebilirsiniz. Sıra geldi içerisinde yukarıdaki
fonksiyonumuzun yer aldığı dosyayı sayfamıza eklemeye.\

<span style="color: blue;"> \<</span><span
style="color: rgb(163, 21, 21);">head</span><span
style="color: blue;">\></span>\
 <span> <span>  </span> <span style="color: blue;"> \<</span><span
style="color: rgb(163, 21, 21);">meta</span> <span style="color: red;">
http-equiv</span><span style="color: blue;">="Content-Type"</span> <span
style="color: red;"> content</span><span
style="color: blue;">="text/html; charset=utf-8"</span> <span
style="color: blue;"> /\></span></span>\
 <span> <span>  </span> <span style="color: blue;"> \<</span><span
style="color: rgb(163, 21, 21);">script</span> <span
style="color: red;"> language</span><span
style="color: blue;">="javascript"</span> <span style="color: red;">
type</span><span style="color: blue;">="text/javascript"</span> <span
style="color: red;"> src</span><span
style="color: blue;">="**flash.js**"</span><span
style="color: blue;">\></span></span><span><span
style="color: blue;">\</</span><span
style="color: rgb(163, 21, 21);"></span></span><span><span
style="color: blue;"></span><span
style="color: rgb(163, 21, 21);">script</span></span><span><span
style="color: blue;">\></span></span>\
 <span> <span>  </span> <span style="color: blue;"> \<</span><span
style="color: rgb(163, 21, 21);">title</span><span
style="color: blue;">\></span>Örnek Sayfa <span style="color: blue;">
\</</span><span style="color: rgb(163, 21, 21);">title</span><span
style="color: blue;">\></span></span>\
 <span style="color: blue;"> \</</span><span
style="color: rgb(163, 21, 21);">head</span><span
style="color: blue;">\></span>

Yukardaki şekli ile sayfamızın Header kısmına JavaScript dosyamızı
linkledik. Böylece dosya içerisinde fonksiyonları sayfamızda
kullanabileceğiz. Hazırladığımız fonksiyonun adı <span>**GetLogo**
şeklindeydi. Flash animasyon sayfada nereye eklenecekse oraya aşağıdaki
kodu yazmamız gerekiyor.</span>

<span><span>   </span><span style="color: blue;">\<</span><span
style="color: rgb(163, 21, 21);">script</span><span style="color: red;">
language</span><span style="color: blue;">="javascript"</span><span
style="color: red;"> type</span><span
style="color: blue;">="text/javascript"\></span>GetLogo()<span
style="color: blue;">\</</span><span
style="color: rgb(163, 21, 21);">script</span><span
style="color: blue;">\></span></span>

Sayfamızın tam kodu aşağıdaki şekilde olacaktır.

<span style="color: blue;">\<!</span><span
style="color: rgb(163, 21, 21);">DOCTYPE</span><span><span
style="color: red;"> html </span><span
style="color: red;">PUBLIC</span><span style="color: blue;">
"-//W3C//DTD XHTML 1.0 Transitional//EN"</span><span
style="color: blue;">"http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd"\></span></span>\
<span style="color: blue;">\<</span><span
style="color: rgb(163, 21, 21);">html</span><span><span
style="color: red;"> xmlns</span><span
style="color: blue;">="http://www.w3.org/1999/xhtml"\></span></span>\
<span style="color: blue;">\<</span><span
style="color: rgb(163, 21, 21);">head</span><span
style="color: blue;">\></span>\
<span><span> </span><span style="color: blue;">\<</span><span
style="color: rgb(163, 21, 21);">meta</span><span style="color: red;">
http-equiv</span><span style="color: blue;">="Content-Type"</span><span
style="color: red;"> content</span><span
style="color: blue;">="text/html; charset=utf-8"</span><span
style="color: blue;">/\></span></span>\
<span><span> </span><span style="color: blue;">\<</span><span
style="color: rgb(163, 21, 21);">script </span><span
style="color: red;">language</span><span
style="color: blue;">="javascript"</span><span style="color: red;">
type</span><span style="color: blue;">="text/javascript"</span><span
style="color: red;"> src</span><span
style="color: blue;">="flash.js"\>\</</span><span
style="color: rgb(163, 21, 21);">script</span><span
style="color: blue;">\></span></span>\
<span><span> </span><span style="color: blue;">\<</span><span
style="color: rgb(163, 21, 21);">title</span><span
style="color: blue;">\></span>Örnek Sayfa<span
style="color: blue;">\</</span><span
style="color: rgb(163, 21, 21);">title</span><span
style="color: blue;">\></span></span>\
<span style="color: blue;">\</</span><span
style="color: rgb(163, 21, 21);">head</span><span
style="color: blue;">\></span>\
<span style="color: blue;">\<</span><span
style="color: rgb(163, 21, 21);">body</span><span
style="color: blue;">\></span>\
<span><span> </span><span style="color: blue;">\<</span><span
style="color: rgb(163, 21, 21);">div</span><span style="color: red;">
style</span><span style="color: blue;">="position: absolute; left: 20px;
top: 50px;"\></span></span>\
<span><span>   </span><span style="color: blue;">\<</span><span
style="color: rgb(163, 21, 21);">script </span><span
style="color: red;">language</span><span
style="color: blue;">="javascript"</span><span style="color: red;">
type</span><span
style="color: blue;">="text/javascript"\></span>GetLogo()<span
style="color: blue;">\</</span><span
style="color: rgb(163, 21, 21);">script</span><span
style="color: blue;">\></span></span>\
<span><span> </span><span style="color: blue;">\</</span><span
style="color: rgb(163, 21, 21);">div</span><span
style="color: blue;">\></span></span>\
<span style="color: blue;">\</</span><span
style="color: rgb(163, 21, 21);">body</span><span
style="color: blue;">\></span>\
<span style="color: blue;">\</</span><span
style="color: rgb(163, 21, 21);">html</span><span
style="color: blue;">\></span> 

Yukarıdaki örnek içerisinde bir katman (div) içine flash animasyonumuzu
yerleştiriyoruz. Gerekli HTML kodunun belgenin o kısmına yerleştirilmesi
için önceden hazırlamış olduğumuz JavaScript fonksiyonunu
çalıştırıyoruz. Tabi ki bir JavaScript fonksiyonu çalıştırabilmek için
komutumuzu script tagları arasına koymalıyız.

Çözümümüz tamamlandı fakat yukarıdaki sistem farklı durumlarda sorun
çıkartabilir. Örneğin hedef internet tarayıcı JavaScript desteklemiyorsa
sistem çalışmayacaktır. Tüm tarayıcılara uygun bir sistem için aşağıdan
indirebileceğiniz Adobe'a ait JavaScript dosyasını kullanabilirsiniz.
Söz konusu dosyayı makalenin sonundaki download paketinde
bulabilirsiniz. Dosyanın adı **AC\_RunActiveContent.js** şeklinde.
Yukarıdaki, bizim hazırladığımız JavaScript dosyası yerine bu dosyayı
sitemize ekleyeceğiz. Ekledikten sonra da aşağıdaki JavaScript kodu ile
animasyonu sayfamıza yazdıracağız.

<span>   <span style="color: blue;">\<</span><span
style="color: rgb(163, 21, 21);">script</span><span style="color: red;">
type</span><span
style="color: blue;">="text/javascript"\></span></span>\
<span>AC\_FL\_RunContent(<span
style="color: rgb(163, 21, 21);">'codebase'</span>,<span
style="color: rgb(163, 21, 21);">
'http://download.macromedia.com/pub/shockwave/cabs/flash/swflash.cab\#version=9,0,28,0'</span>,\
<span style="color: rgb(163, 21, 21);"> 'width'</span>,<span
style="color: rgb(163, 21, 21);">'**786**'</span>,<span
style="color: rgb(163, 21, 21);">'height'</span>,<span
style="color: rgb(163, 21, 21);">'**241**'</span>,<span
style="color: rgb(163, 21, 21);">'src'</span>,<span
style="color: rgb(163, 21, 21);">'**banner**'</span>,<span
style="color: rgb(163, 21, 21);">'quality'</span>,<span
style="color: rgb(163, 21, 21);">'high'</span>,<span
style="color: rgb(163, 21, 21);">'pluginspage'</span>,\
<span style="color: rgb(163, 21, 21);">
'http://www.adobe.com/shockwave/download/download.cgi?P1\_Prod\_Version=ShockwaveFlash'</span>,\
 <span style="color: rgb(163, 21, 21);">'movie'</span>,<span
style="color: rgb(163, 21, 21);">'**banner**'</span> );<span
style="color: green;">//end AC code</span></span>\
<span>   <span style="color: blue;">\</</span><span
style="color: rgb(163, 21, 21);">script</span><span
style="color: blue;">\></span></span>

Kullandığımız JavaScript fonksiyonu Adobe tarafından hazırlanmış bir
fonksiyon. Sayfamıza eklediğimiz **AC\_RunActiveContent.js** dosyası
içerisinde bulunuyor. Fonksiyonun aldığı parametreler arasında kalın
yazılmış olanlara dikkat etmekte fayda var. Bunlar Flash animasyonun
yüksekliği, genişliği ve dosya adını içeriyor. Adobe tarafından
hazırlanmış olan bu fonksiyonu farklı tarayıcılarla ilgili uyumluluk
sorunlarını halledecektir. Son olarak JavaScript desteklemeyen
tarayıcılar için de aşağıdaki kodu sayfamıza yerleştireceğiz. Fakat
unutmamakta fayda var, eğer tarayıcının JavaScript desteği kapatılmışsa
maalesef Internet Explorer'da Flash animasyonlarda aktivasyon talebi
devam edecektir.

<span>   <span style="color: blue;">\<</span><span
style="color: rgb(163, 21, 21);">noscript</span><span
style="color: blue;">\></span></span>\
<span>     <span style="color: blue;">\<</span><span
style="color: rgb(163, 21, 21);">object </span><span
style="color: red;">classid</span><span
style="color: blue;">="clsid:D27CDB6E-AE6D-11cf-96B8-444553540000"</span><span
style="color: red;"> codebase</span><span
style="color: blue;">="http://download.macromedia.com/pub/shockwave/cabs/flash/swflash.cab\#version=9,0,28,0"</span></span>\
<span>       <span style="color: red;">width</span><span
style="color: blue;">="786" </span><span
style="color: red;">height</span><span
style="color: blue;">="241"\></span></span>\
<span>       <span style="color: blue;">\<</span><span
style="color: rgb(163, 21, 21);">param</span><span style="color: red;">
name</span><span style="color: blue;">="movie"</span><span
style="color: red;"> value</span><span
style="color: blue;">="banner.swf"/\></span></span>\
<span>       <span style="color: blue;">\<</span><span
style="color: rgb(163, 21, 21);">param</span><span style="color: red;">
name</span><span style="color: blue;">="quality"</span><span
style="color: red;"> value</span><span
style="color: blue;">="high"/\></span></span>\
<span>       <span style="color: blue;">\<</span><span
style="color: rgb(163, 21, 21);">embed</span><span style="color: red;">
src</span><span style="color: blue;">="banner.swf"</span><span
style="color: red;"> width</span><span
style="color: blue;">="786"</span><span style="color: red;">
height</span><span style="color: blue;">="241"</span><span
style="color: red;"> quality</span><span style="color: blue;">="high"
</span><span style="color: red;">pluginspage</span><span
style="color: blue;">="http://www.adobe.com/shockwave/download/download.cgi?P1\_Prod\_Version=ShockwaveFlash"</span></span>\
<span>         <span style="color: red;">type</span><span
style="color: blue;">="application/x-shockwave-flash"\>\</</span><span
style="color: rgb(163, 21, 21);">embed</span><span
style="color: blue;">\></span></span>\
<span>     <span style="color: blue;">\</</span><span
style="color: rgb(163, 21, 21);">object</span><span
style="color: blue;">\></span></span>\
<span>   <span style="color: blue;">\</</span><span
style="color: rgb(163, 21, 21);">noscript</span><span
style="color: blue;">\></span></span>

Sonuç olarak tam çözümümüzün kodu aşağıdaki şekilde sonlanıyor.

<span style="color: blue;">\<!</span><span
style="color: rgb(163, 21, 21);">DOCTYPE</span><span><span
style="color: red;"> html</span><span style="color: red;"> PUBLIC
</span><span style="color: blue;">"-//W3C//DTD XHTML 1.0
Transitional//EN"</span><span
style="color: blue;">"http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd"\></span></span>\
<span style="color: blue;">\<</span><span
style="color: rgb(163, 21, 21);">html</span><span><span
style="color: red;"> xmlns</span><span
style="color: blue;">="http://www.w3.org/1999/xhtml"\></span></span>\
<span style="color: blue;">\<</span><span
style="color: rgb(163, 21, 21);">head</span><span
style="color: blue;">\></span>\
<span><span> </span><span style="color: blue;">\<</span><span
style="color: rgb(163, 21, 21);">meta</span><span style="color: red;">
http-equiv</span><span style="color: blue;">="Content-Type"</span><span
style="color: red;"> content</span><span
style="color: blue;">="text/html; charset=utf-8"</span><span
style="color: blue;">/\></span></span>\
<span><span> </span><span style="color: blue;">\<</span><span
style="color: rgb(163, 21, 21);">title</span><span
style="color: blue;">\></span>Untitled 1<span
style="color: blue;">\</</span><span
style="color: rgb(163, 21, 21);">title</span><span
style="color: blue;">\></span></span>\
<span><span> </span><span style="color: blue;">\<</span><span
style="color: rgb(163, 21, 21);">script </span><span
style="color: red;">language</span><span
style="color: blue;">="javascript"</span><span style="color: red;">
type</span><span style="color: blue;">="text/javascript"</span><span
style="color: red;"> src</span><span
style="color: blue;">="**AC\_RunActiveContent.js**"\>\</</span><span
style="color: rgb(163, 21, 21);">script</span><span
style="color: blue;">\></span></span>\
<span style="color: blue;">\</</span><span
style="color: rgb(163, 21, 21);">head</span><span
style="color: blue;">\></span>\
<span style="color: blue;">\<</span><span
style="color: rgb(163, 21, 21);">body</span><span
style="color: blue;">\></span>\
<span><span> </span><span style="color: blue;">\<</span><span
style="color: rgb(163, 21, 21);">div</span><span style="color: red;">
style</span><span style="color: blue;">="position: absolute; left: 20px;
top: 50px;"\></span></span>\
<span style="color: blue;"> </span>\
<span><span>   </span><span style="color: blue;">\<</span><span
style="color: rgb(163, 21, 21);">script</span><span style="color: red;">
type</span><span
style="color: blue;">="text/javascript"\></span></span>\
<span>AC\_FL\_RunContent(<span
style="color: rgb(163, 21, 21);">'codebase'</span>, <span
style="color: rgb(163, 21, 21);">'http://download.macromedia.com/pub/shockwave/cabs/flash/swflash.cab\#version=9,0,28,0'</span>,
<span style="color: rgb(163, 21, 21);">'width'</span>,<span
style="color: rgb(163, 21, 21);">'786'</span>,<span
style="color: rgb(163, 21, 21);">'height'</span>,<span
style="color: rgb(163, 21, 21);">'241'</span>,<span
style="color: rgb(163, 21, 21);">'src'</span>,<span
style="color: rgb(163, 21, 21);">'banner'</span>,<span
style="color: rgb(163, 21, 21);">'quality'</span>,<span
style="color: rgb(163, 21, 21);">'high'</span>,<span
style="color: rgb(163, 21, 21);">'pluginspage'</span>, <span
style="color: rgb(163, 21, 21);">'http://www.adobe.com/shockwave/download/download.cgi?P1\_Prod\_Version=ShockwaveFlash'</span>,
<span style="color: rgb(163, 21, 21);">'movie'</span>,<span
style="color: rgb(163, 21, 21);">'banner'</span> );<span
style="color: green;">//end AC code</span></span>\
<span><span>   </span><span style="color: blue;">\</</span><span
style="color: rgb(163, 21, 21);">script</span><span
style="color: blue;">\></span></span>\
<span style="color: blue;"> </span>\
<span><span>   </span><span style="color: blue;">\<</span><span
style="color: rgb(163, 21, 21);">noscript</span><span
style="color: blue;">\></span></span>\
<span><span>     </span><span style="color: blue;">\<</span><span
style="color: rgb(163, 21, 21);">object</span><span style="color: red;">
classid</span><span
style="color: blue;">="clsid:D27CDB6E-AE6D-11cf-96B8-444553540000"</span><span
style="color: red;"> codebase</span><span
style="color: blue;">="http://download.macromedia.com/pub/shockwave/cabs/flash/swflash.cab\#version=9,0,28,0"</span></span>\
<span><span>       </span><span style="color: red;">width</span><span
style="color: blue;">="786" </span><span
style="color: red;">height</span><span
style="color: blue;">="241"\></span></span>\
<span><span>       </span><span style="color: blue;">\<</span><span
style="color: rgb(163, 21, 21);">param</span><span style="color: red;">
name</span><span style="color: blue;">="movie"</span><span
style="color: red;"> value</span><span
style="color: blue;">="banner.swf"</span><span
style="color: blue;">/\></span></span>\
<span><span>       </span><span style="color: blue;">\<</span><span
style="color: rgb(163, 21, 21);">param</span><span style="color: red;">
name</span><span style="color: blue;">="quality"</span><span
style="color: red;"> value</span><span
style="color: blue;">="high"</span><span
style="color: blue;">/\></span></span>\
<span><span>       </span><span style="color: blue;">\<</span><span
style="color: rgb(163, 21, 21);">embed</span><span style="color: red;">
src</span><span style="color: blue;">="banner.swf" </span><span
style="color: red;">width</span><span
style="color: blue;">="786"</span><span style="color: red;">
height</span><span style="color: blue;">="241"</span><span
style="color: red;"> quality</span><span
style="color: blue;">="high"</span><span style="color: red;">
pluginspage</span><span
style="color: blue;">="http://www.adobe.com/shockwave/download/download.cgi?P1\_Prod\_Version=ShockwaveFlash"</span></span>\
<span><span>         </span><span style="color: red;">type</span><span
style="color: blue;">="application/x-shockwave-flash"\>\</</span><span
style="color: rgb(163, 21, 21);">embed</span><span
style="color: blue;">\></span></span>\
<span><span>     </span><span style="color: blue;">\</</span><span
style="color: rgb(163, 21, 21);">object</span><span
style="color: blue;">\></span></span>\
<span><span>   </span><span style="color: blue;">\</</span><span
style="color: rgb(163, 21, 21);">noscript</span><span
style="color: blue;">\></span></span>\
<span><span> </span><span style="color: blue;">\</</span><span
style="color: rgb(163, 21, 21);">div</span><span
style="color: blue;">\></span></span>\
<span style="color: blue;">\</</span><span
style="color: rgb(163, 21, 21);">body</span><span
style="color: blue;">\></span>\
<span style="color: blue;">\</</span><span
style="color: rgb(163, 21, 21);">html</span><span
style="color: blue;">\></span>

Makale boyunca kullandığımız tüm dosyaları ve örnekleri aşağıdaki
download paketine bulabilirsiniz.

Kolay gelsin.

[27042007\_2.rar - Örnekler (12.37
KB)](media/Internet_Explorer_ve_Flashlardaki_Cerceve_Aktivasyon_Sorunu/27042007_2.rar)


