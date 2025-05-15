خوب اینجا قسمت fluent assertion هستش که میاد چک ها رو انجام میده 
![[Screenshot_2025-04-09-14-16-37-137_com.appzoom.zoomplayerclassic.jpg]]
قبلا جور دیگری انجام میشد 
![[Screenshot_2025-04-09-14-18-15-107_com.appzoom.zoomplayerclassic.jpg]]

![[Screenshot_2025-04-09-14-21-49-746_com.appzoom.zoomplayerclassic.jpg]]



![[Screenshot_2025-04-09-14-30-55-293_com.appzoom.zoomplayerclassic.jpg]]
![[Screenshot_2025-04-09-14-31-36-344_com.appzoom.zoomplayerclassic.jpg]]


خوب نکته ای که هست اینه که اگر یه کلاسی به اسم user داریم بیایم برای چک کردنش بیایم یه کلاس به اسم user validator درست کنیم که از fluent validator ارث بری کرده باشه
![[Screenshot_2025-04-09-14-41-37-682_com.appzoom.zoomplayerclassic.jpg]]

خوب در عکس بالا اومدیم برای فیلد های username, password در نظر گرفتیم که خالی نباشند 

![[Screenshot_2025-04-09-14-47-17-491_com.appzoom.zoomplayerclassic.jpg]]

خوب اینجا اومدیم اول یه new از validator و بعد اومدیم در خط پایین تر instance رو برابر user قرار دادیم 

در خط بالاتر یه new از user درست کردیم

خوب اتفاقی که میوفته اینه که اگر results is valid برابر باشه با false اتفاقی که میوفته اینه که results.error یه کالکشنی داره که میایم با foreach داخلش رو چاپ می کنیم.

![[Screenshot_2025-04-12-14-25-26-186_com.appzoom.zoomplayerclassic.jpg]]


![[Screenshot_2025-04-09-15-12-58-179_com.appzoom.zoomplayerclassic.jpg]]

اینجا اومدیم از not null استفاده کردیم و بعد اومدیم یه کد خطا با یه نوشته کل خطا رو درست کردیم که ازش استفاده کنیم
خوب req ها قبل از این که وارد action شوند میشه که چک شوند
![[Screenshot_2025-04-12-14-29-31-139_com.appzoom.zoomplayerclassic 1.jpg]]