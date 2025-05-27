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