
![[Pasted image 20241211165249.png]]

اون دو تا باکس قرمز ها جفشتون دارن یه کار میکنن و دومی مدل fluent هستش که ازش میخوایم استفاده کنیم

![[Pasted image 20241211165258.png]]

![[Pasted image 20241211165303.png]]

این قسمت هم داخل همین قسمت بالاییه 

![[Pasted image 20241211165315.png]]

خوب حالا اصلا چرا این کار رو داریم میکنیم ؟

![[Pasted image 20241211165322.png]]

چون میتونیم اینطوری ازش استفاده کنیم

![[Pasted image 20241211165330.png]]

برای حالت اول :

![[Pasted image 20241211165336.png]]

خوب حالا برای این که کانفیگ ها رو در جای جداگونه بنویسیم میایم این کار رو میکنیم :

![[Pasted image 20241211165345.png]]

ممکنه در معماری های مختلف جای این متفاوت باشه 
لایه دامین و entity باید مستقل از هر چیزی باشند 
خوب دلیل این که این ها باید از entity جدا باشند اینه که اینجا اگر ما بخوایم entityi هایی که داریم رو به یه دیتا بیس دیگه وصل کنیم ، اگر این config ها کنار خوده entitty باشه ، یعنی بهش وابسته باشه دیگه نمیتونیم به راحتی این کار رو انجام بدیم برای همین entity ها رو همیشه چدا مینویسیم و کانفیگ ها در DAL به صورت جداگانه مینویسیم 

خوب حالا میایم اینطوری کافیگ ها رو جدا میسازیم 


![[Pasted image 20241211165353.png]]

خوب اینجا این یعنی چی؟ IentityTypeConfiguration توی قسمت بعدیش میایم کانفیگ اون entity که میخوایم درست کنیم رو مینویسیم ، خوب وقتی که بزنیم اتوماتیک متذ هاشو درست کنه بهمون  void configure رو میده که اونجا همونطوری که میبینید اون پارامتر builder از نوع و تایپ entityTypeBuilder هستش که میشه همون شبیه model builder که توی دیتا بیس ازش استفاده کردیم 

![[Pasted image 20241211165359.png]]

و بعد اینطوری میتونیم ازش استفاده کنیم :

![[Pasted image 20241211165406.png]]

اینجا اومدیم از همون دستوراتی که توی data annotation استفاده کردیم اینجا هم استفاده کردیم 
یعنی اومدیم گفتیم که اسم جدولی که این entity توی دیتابیس میسازی tbl_product هستش و بعد براش اسکیما prod رو هم تعیین کردیم 

خوب حالا نکته ی آخر اینه که ما حالا اومدیم این کانفیگ رو انجام دادیم چجوری ببریم به برنامه بگیم که وقتی که میخوای دیتابیس رو بسازی بیا و از این کانفیگ استفاده کن ؟

![[Pasted image 20241211165420.png]]

اینطوری که توی شکل بالا گفته ، فقط دقت کنید که برای استفاده کردن ازش باید یادمون باشه که new بزنیم و از ApplyConfiguration استفاده کنیم و اون کلاسی که توش کانفیگ رو درست کردیم بدیم بهش

یه روش دیگه هم هست که اسمش reflection که بعدا یادش میگیریم

![[Pasted image 20241211165430.png]]

خوب ما میتونیم فیلد مورد نظرمون رو بیایم در دیتا بیس reqierd کنیم 

![[Pasted image 20241211165443.png]]

خوب حالا میتونیم از onModelCreating هم استفاده کنیم ولی یکم متفاوته 
توی اونجا دیگه ما کانفیگی که میخوایم بنویسیم فقط برای یک entity نیستش . این یعنی این که توی عکس بالا میبینید که کافیگی که درست کردیم فقط برای product هستش ولی وقتی که توی OnModelCreating هستیم یعنی به کل دیتا بیس دسرتسی داریم و توی این حالت باید تعیین کنیم که به کدوم entity میخوایم وصل بشیم و اونجا اون پراپرتی که میخوایم رو reqired کنیم

![[Pasted image 20241211165453.png]]

خوب حالا کارهای دیگه ای که میتونیم انجام بدیم یکیش اینه که میتونیم یه پراپرتی که داریم توی یک entity و نمیخوایم توی دیتا بیس ذخیره بشه رو میتونیم تعیین کنیم با استفاده از ignore

![[Pasted image 20241211165504.png]]

خط بعدی که نوشته شده که از hasColumnName استفاده کرده برای اینه که زمانی که ما بخوایم اسم یه پراپرتی که میخوایم توی دیتا بیس ذخیره کنیم با اسم اون پراپرتی یکسان نباشه و اسمش رو بخوایم برای ذخیره در دیتا بیس تغییر بدیم ازش استفاده میکنیم:

![[Pasted image 20241211165512.png]]


دقت کنید که تمام این کارهای بالا رو میتونستیم با data annotation ها انجام بدیم مثلا برای این که پرارپتی ذخیره نشه میتونستیم از not mapped استفاده کنیم


![[Pasted image 20241211165520.png]]

با دستور بالا میتونیم تایپی که میخوایم رو تعیین کنیم

![[Pasted image 20241211165531.png]]

خوب یه چیزی که باید دقت کنیم اینه که ما هر کافیگی که بخوایم روی entity و دیتا بیسمون بخوایم اعمال کنیم باید از ApplyConfiguration استفاده کنیم

![[Pasted image 20241211165540.png]]

حالا ما یه entity دیگه هم ساختیم 

![[Pasted image 20241211165546.png]]

میخوایم کد اصلی رو براش تعیین کنیم چون اسمش keyId هستش و Id نیست و اتوماتیک تشخیص داده نمیشه 

![[Pasted image 20241211165558.png]]

![[Pasted image 20241211165559.png]]

خوب حالا فرض کنید که بخوایم دو تا کلید اصلی داشته باشیم 

![[Pasted image 20241211165608.png]]

![[Pasted image 20241211165610.png]]

اینطوری مثل عکس بالا عمل میکنیم

خوب حالا اگر بخوایم اسم کلید اصلی رو تغییر بدیم اینطوری عمل میکنیم

![[Pasted image 20241211165620.png]]

خوب ما یه مفهومی داریم به اسم alternate key که میشه همون کاره کلید اصلی رو داره میکنه مثلا اینجا به طور مثال میشه از کد ملی استفاده کرد 

![[Pasted image 20241211165628.png]]

خوب حالا میتونیم چند تا alternate key هم داشته باشیم / اینطوری:

![[Pasted image 20241211165637.png]]

![[Pasted image 20241211165641.png]]

دقت کنید که برای کد ملی indexable فعال هستش که نمایانگره اینه که به عنوان کلید alternate در نظر گرفته شده 

حالا البته اینجا رو ببینید ما یه تغییراتی دادیم و حالا میخوایم توی دیتا بیس ببینیم که چجوری میشه :

![[Pasted image 20241211165651.png]]

![[Pasted image 20241211165653.png]]

خوب حالا ما برای این که بخوایم جست و جوی سریع تر و بهتر داشته باشیم میخوایم شماره تلفن رو هم ایندکس کنیم برای این کار میایم اینجوری کد میزنیم:

![[Pasted image 20241211165701.png]]

![[Pasted image 20241211165704.png]]

اینجوری هم میشه برای کد ملی و شماره تلفن این کار رو کرد

![[Pasted image 20241211165712.png]]

![[Pasted image 20241211165714.png]]

ما نمیتونیم یه entity رو که هیچ کلید اصلی براش در نظر نگرفتیم رو بریزیم توی دیتا بیس 
البته اینجا توی این پیام ارور داده و گفته که اگر میخواید این کار رو بکنید از has no key استفاده کنید

![[Pasted image 20241211165722.png]]

![[Pasted image 20241211165724.png]]

![[Pasted image 20241211165727.png]]

از ef core 2 به بعد این امکان اضافه شده 

