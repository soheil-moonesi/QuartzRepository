![[Pasted image 20250430214338.png]]
![[Pasted image 20250430214422.png]]

![[Pasted image 20250430214302.png]]
خوب توی این پروژه اومدیم از mapperly به جای Auto mapper استفاده کردیم :

![[Pasted image 20250504180121.png]]



![[Pasted image 20250504164818.png]]
خوب برای استفاده ازش میایم یه کلاس میسازیم به اسم User Mapper 
نکته اینه که باید از partial استفاده کنیم 
دلیل استفاده از partial اینه که میاد کلاس های اصلی رو extend میکنه و یعنی قسمتی از کلاس های اصلی هستتش 
بعد attribute رو مینویسیم mapper


![[Pasted image 20250504170446.png]]

![[Pasted image 20250504181151.png]]

خوب حالا میخوایم بگیم که بیا و userAddDto رو تبدیل که به user که در تصویر بالا هستش
از name of هم به جای magic string ها استفاده کردیم که اگر تغییرش دادیم ارور بده و متوجه بشیم 
خوب توی User Add dto to user هم ورودی رو با توجه به Dto میگیریم که اینجا تعیین کردیم فقط email باشه و بعد mapperly میاد map اش میکنه به user و اینطوری میتونیم بریزیمش توی database

![[Pasted image 20250512213719.png]]


![[Pasted image 20250512213707.png]]

اون هایی که مرتبطه با bootstrap رو پاک مکینیم و اون هایی که برای mud blazor هستش رو اضافه میکنیم :
![[Pasted image 20250512214222.png]]

https://www.youtube.com/watch?v=IhA_dE4XF9o&t=288s&ab_channel=NaveenBommidiTechSeeker


نکته ای که داره اینه که اگر بخوایم api و front رو به هم وصل کنیم این دو تا موقع compile شدن میرن توی همدیگه و با هم build میشن و این درست نیست برای همین میایم و یک class library رو بینشون میزاریم و بهش refrence میدیم 

error
``` c#
Unable to create a 'DbContext' of type ''. The exception 'The entity type 'IdentityUserLogin<string>' requires a primary key to be defined. If you intended to use a keyless entity type, call 'HasNoKey' in 'OnModelCreating'. For more information on keyless entity types, see https://go.microsoft.com/fwlink/?linkid=2141943.' was thrown while attempting to create an instance. For the different patterns supported at design time, see https://go.microsoft.com/fwlink/?linkid=851728
```

![[Pasted image 20250529135428.png]]

![[Pasted image 20250529135341.png]]
وقتی که بعد از تنظیم کردن jwt میخوایم migration بزنیم این ارور میومد ، بعدش که درستش کردیم migration انجام شد 

دقت کنیم که بعد از این عملیات هستش که یه سری جدول رو میاد توی دیتابیس برای identity درست میکنه 

![[Pasted image 20250529135613.png]]

![[Pasted image 20250529135631.png]]


![[Pasted image 20250529135644.png]]



![[Pasted image 20250529135716.png]]

![[Pasted image 20250529135732.png]]

![[Pasted image 20250529135748.png]]


![[Pasted image 20250529135801.png]]

