جلسه دوم 
![[Screenshot_2025-04-06-15-01-41-086_com.appzoom.zoomplayerclassic.jpg]]


![[Screenshot_2025-04-06-15-03-20-147_com.appzoom.zoomplayerclassic.jpg]]

![[Screenshot_2025-04-06-15-03-36-867_com.appzoom.zoomplayerclassic.jpg]]

این جا میخوایم با استفاده از اینترفیس ilogger بیایم و کلاس logger رو وارد کلاس someClass کنیم

![[Screenshot_2025-04-06-15-16-13-011_com.appzoom.zoomplayerclassic.jpg]]

خوب پارامتر اولی رو read only کردیم 
نکته ای که هست اینه که میتونیم توی constructor بهش مقدار اولیه بدیم 

توی اینترفیس اومدیم و اسم تابع و نوع ورودیش رو تعیین کردیم و بعد در کلاس logger اومدیم و نوع پیاده سازیش رو نوشتیم و بعد ازش در someClass ازش استفاده کردیم 
![[Screenshot_2025-04-07-11-35-41-197_com.appzoom.zoomplayerclassic.jpg]]

![[Screenshot_2025-04-07-11-38-50-957_com.appzoom.zoomplayerclassic.jpg]]

خوب توی این حالت اومدیم از protect استفاده کردیم و با فقط نوشتن get اومدیم اون فیلد رو read only کردیم 
![[Screenshot_2025-04-07-12-26-25-157_com.appzoom.zoomplayerclassic.jpg]]

خوب حالا عکس پایین:
اینجا اول اومدیم logger رو از جنس اینترفیس پدرش تعریف کنیم بعد اومدیم new کردیم و logger رو به تزریق کردیم
![[Screenshot_2025-04-07-12-32-26-179_com.appzoom.zoomplayerclassic.jpg]]
خوب در mvc core میخوایم وقتی که به طور مثال یه کلاس رو new کنیم که یه اینترفیسی در ورودیش داره ، بهشون میفهمونیم که در این مورد بیاد و یه کلاس رو بسازه

خوب حالا چطوری این کار رو انجام بدیم؟ 
اینطوری 
اول میایم و service رو با استفاده از service collection درست میکنیم و بعد با استفاده از services میایم و build service provider رو درست میکنیم 

مورد بعدی اینه که اگر ورودی کلاسی ، کلاس some class بود خودش بیاد و از some class یه کلاس بسازه و inject کنه 

![[Screenshot_2025-04-07-13-04-20-950_com.appzoom.zoomplayerclassic.jpg]]

اینجا اومدیم گفتیم که هر جایی که ورودیش ilogger بود بیا و از کلاس logger یکی بساز و بهش تزریق کن

خوب بعدش provider خودمون رو درست کردیم 

![[Screenshot_2025-04-07-13-11-53-283_com.appzoom.zoomplayerclassic.jpg]]

خوب حالا اینجا اتفاقی که افتاده اینه که با استفاده از service provider میایم و create scope میکنیم و میریزیم توی scope 

حالا با استفاده از scope میایم و get required service رو استفاده میکنیم 

نکته scope رو در mvc core نداریم 
خوب scope با استفاده از service provider میاد کمک میکنه در تولید کردن کلاس ها و inject کردنشون

با استفاده از get required service یه شی برامون بسازه که اون شی میشه some class خوب نکته ای که اینجا هستش اینه که باید ببینیم که اون کلاس توی service ها تعیین شده یا نه که توسط 
Services add transient  
انجام شده است 

خوب حالا داستانش اینه که خوده کلاس some class هم توی ورودیش از ilogger استفاده شده است که اون هم باید توی service ها ثبت شده 
![[Screenshot_2025-04-07-13-52-30-067_com.appzoom.zoomplayerclassic.jpg]]

خوب اون قسمت کامنت شده روش قدیمی هستش 
حالا با استفاده از شی ساخته شده میایم از تابع do something استفاده میکنیم 

![[Screenshot_2025-04-07-14-27-16-213_com.appzoom.zoomplayerclassic.jpg]]

در دات نت به ازای هر نفری که وارد سایت میشه یه thread ساخته و اختصاص داده میشه 

در Singleton میاد اولین نفری که به سرور درخواست میزنه میاد یه دونه از اون شی میسازه و بعد همون شخص و نقرات بعدی هم از همون شی استفاده میکنند


دقیقه ۲۰

خوب scope به این شکل هستش برای هر یوزر که یک thread اختصاص داده میشه و به ازای هر یوزر یک شی درست میشه

خوب transient به ازای هر درخواست اون شی رو میسازه 

خوب توی قسمت های بالا برای console app اومدیم dependency injection رو توضیح دادن 

از این جا میرسیم به وب 

![[Screenshot_2025-04-07-15-20-18-010_com.appzoom.zoomplayerclassic.jpg]]

![[Screenshot_2025-04-07-15-20-34-609_com.appzoom.zoomplayerclassic.jpg]]

خوب توی پروژه های mvc core به صورت پیش فرض nuget dependency injection نصب هستش 

![[Screenshot_2025-04-08-07-46-52-711_com.appzoom.zoomplayerclassic.jpg]]

![[Screenshot_2025-04-07-15-29-25-701_com.appzoom.zoomplayerclassic.jpg]]

خوب توی عکس بالا اومدیم و ilogger رو inject کردیم و با استفاده از Singleton اومدیم یه بار ساختیمش تا بتونیم ازش استفاده کنیم