---
FallbackID: 3046
Title: Azure Notification Hub ve UWP ile Push Notification Kullanımı
PublishDate: 12/11/2016
EntryID: Notification_Hub_ve_UWP_ile_Push_Notification
IsActive: True
Section: software
MinutesSpent: 55
Tags: Azure Notification Hub
---
Dünkü [Azure Functions ve Notification Hub](http://daron.yondem.com/software/post/Azure_Functions_ve_TimerTrigger_Kullanimi) Binding yazısından sonra gelen birkaç soru ile farkına vardım ki aslında **Notification Hub** konusunda da bir yazı iyi olurmuş :) O nedenle gelin Azure'daki Notification Hub'a bir giriş yapalım. Azure Functions yazısı için test ortamı kurulumunu yaparken attığım adımları sizlerle paylaşarak aslında Notification Hub ile **WNS (Windows Push Notification Services)** kullanarak basit bir UWP uygulamasına Push Notification yollayacağız.