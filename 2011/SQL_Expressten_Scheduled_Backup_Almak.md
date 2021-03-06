---
FallbackID: 2693
Title: SQL Express'ten Scheduled Backup Almak
PublishDate: 10/9/2011
EntryID: SQL_Expressten_Scheduled_Backup_Almak
IsActive: True
Section: software
MinutesSpent: 0
Tags: SQL Server 2008
---
Blogu yazarkenki hikayalerim bitmiyor değil mi? :) Eh uzun süredir rahat
rahat her noktasındaki taktiklerden bahsedebileceğim kendimce özgür bir
proje yazdım :) Genelde müşterilere yapınca projelerin içlerinden
birşeyler paylaşmak mümkün olmuyor. Neyse gelelim konumuza. Şimdi benim
blog arkada bir SQL 2008 R2 Express kullanıyor. SQL'in Express sürümleri
ile beraber bir Agent yapısı gelmiyor ve Schedulede Backup almak doğal
olarak dert oluyor. Bunun için ufak bir takniği devreye alıp Windows'un
kendi Scheduler'ını kullanabiliriz aslında. Nasıl mı?

**[T-SQL]**

<span style="color:blue;">declare</span> <span
style="color:teal;">@DBFileName</span> <span
style="color:blue;">varchar</span><span
style="color:gray;">(</span>256<span style="color:gray;">)</span>  \
\
<span style="color:blue;">set</span> <span
style="color:teal;">@DBFileName</span> <span
style="color:gray;">=</span> <span
style="color:red;">'C:\\backups\\myblog\\'</span> <span
style="color:gray;">+</span> <span
style="color:magenta;">datename</span><span
style="color:gray;">(</span><span style="color:teal;">dd</span><span
style="color:gray;">,</span> <span
style="color:magenta;">getdate</span><span
style="color:gray;">())</span> <span style="color:gray;">+</span> <span
style="color:magenta;">\
        datename</span><span style="color:gray;">(</span><span
style="color:teal;">m</span><span style="color:gray;">,</span> <span
style="color:magenta;">getdate</span><span
style="color:gray;">())</span> <span style="color:gray;">+</span> <span
style="color:magenta;">datename</span><span
style="color:gray;">(</span><span style="color:teal;">yy</span><span
style="color:gray;">,</span> <span
style="color:magenta;">getdate</span><span
style="color:gray;">())</span> <span style="color:gray;">+</span> <span
style="color:red;">'-MyBlog.bak'</span>\
<span style="color:blue;">select</span> <span
style="color:teal;">@DBFileName</span>\
                       \
<span style="color:blue;">BACKUP</span> <span
style="color:blue;">DATABASE</span> <span
style="color:teal;">myblog</span> <span
style="color:blue;">TO</span>  <span
style="color:blue;">DISK</span> <span style="color:gray;">=</span> <span
style="color:teal;">@DBFileName</span> \
<span style="color:blue;">WITH</span> <span
style="color:blue;">RETAINDAYS</span> <span
style="color:gray;">=</span> 30<span style="color:gray;">,</span> <span
style="color:teal;">NAME</span> <span style="color:gray;">=</span> <span
style="color:red;">N'Blog Backup'</span><span
style="color:gray;">,</span> <span style="color:blue;">SKIP</span>\
\
<span style="color:blue;">GO</span>

İlk olarak yukarıdaki gibi bir T-SQL komutunu bir text dosyasına yazıp
diskte güzel bir yere yerleştiriyoruz. Bu T-SQL içerisindeki komut ile
veritabanından bir full backup alınacak diskte uygun klasöre tarih
bilgisi dosya adı olarak atanarak yerleştiriliyor. Ben çılgınlık yapıp
günlük backup alıyorum :) Backup file'ların ayrı ayrı olmasını istedim
çünkü başka bir scheduled task bu dosyalardan her gün yaratılan ayrı bir
FTP sunucuya atıyor. Dediğim gibi eğer bu kodu ayrı bir dosyaya
kaydettiyseniz sıra geldi eski tarz bir BAT dosyası yaratmaya.

**[BAT]**

"C:\\Program Files\\Microsoft SQL
Server\\100\\Tools\\Binn\\SQLCMD.EXE" -S .\\SQLExpress -i
C:\\backups\\backup.sql

Bat dosyamız içerisindeki komut SQL Server ile beraber gelen
SQLCMD.EXE'ye instance adını ve çalıştırılacak T-SQL komutlarının
bulunduğu dosyanın adresini veriyor. Böylece bu komut çalıştırıldığında
bizim SQLExpress'te biraz önce kaydettiğimiz dosyadaki T-SQL
çalıştırılarak istediğimiz yere backup alınmış olacak. Şimdi sıra geldi
bu BAT dosyasının Windows Scheduler ile ayarlanmasına.

Server'da **Task Scheduler** diye aratırsanız hemen bulup ayar ekranını
karşınıza getirebilirsiniz. Task Scheduler Library içerisindeki sağ
panelden "Create Task" diyerek aşağıda ekrana ulaşabiliyoruz.

![Task'ı Login olmasak da çalışacak hale
getirelim.](media/SQL_Expressten_Scheduled_Backup_Almak/scheduler_1.png)\
*Task'ı Login olmasak da çalışacak hale getirelim.*

Task'ın ayarlarının bulunduğu ilk "General" sekmesinde "**Run whether
user is logged or not**" diyerek logon olmuş olmasak da taskın
çalıştırılmasını sağlıyoruz. Bu task artık sizin kullanıcı adınız ve
şifrenizi de kaydederik sizin kullanıcınızın hakları ile login olmasanız
da çalışacak.

![Task'ımızın ne zaman çalışacağına karar
verelim.](media/SQL_Expressten_Scheduled_Backup_Almak/scheduler_2.png)\
*Task'ımızın ne zaman çalışacağına karar verelim.*

Ayarlar kısmında ikinci sekme olan "Triggers"a girdiğimiz hemen "New"
düğmesine basıp yeni bir tetikleyici ayarlayabiliyoruz. Burada ne zaman
ve ne aralıklarla taskın çalıştırılacağını belirtebilirsiniz. Eğer siz
de benim gibi günlük backup alacaksanız sitenizin en az ziyaret aldığı
bir saat aralığını seçmenizde fayda var.

![Task ne
yapacak?](media/SQL_Expressten_Scheduled_Backup_Almak/scheduler_3.png)\
*Task ne yapacak?*

Son olarak artık taskımızın ne yapacağına karar vermemiz gerek.
Çalıştırılacak program olarak BAT dosyamızı diskten taskımıza
gösteriyoruz. Böylece belirlediğimiz aralıklarda BAT dosyamız çalışacak
ve T-SQL'imiz de backup'ı almış olacak. Tüm yapmanız gereken bu kadar.
Artık Scheduled bir backup process'iniz var hem de ücretsiz SQL Express
ile ;)

Hepinize kolay gelsin.


