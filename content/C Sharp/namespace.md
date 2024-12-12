Namespaces are used to organize the classes. It helps to control the scope of methods and classes in larger **[.Net](https://l.vrgl.ir/r?ad=1&l=https%3A%2F%2Fwww.geeksforgeeks.org%2Fc-net-framework-basic-architecture-component-stack%2F&si=my5urycupf4e&st=post&k=3B%2FTcI%2FVyp1wwJSOxwJAwHrpGkRJ0Wkp67vo5eH4LHE%3D)** programming projects. In simpler words you can say that it provides a way to keep one set of names(like class names) different from other sets of names. The biggest advantage of using namespace is that the class names which are declared in one namespace will not clash with the same class names declared in another namespace.

خوب به طور خلاصه از namespace ها برای سازماندهی کردن کلاس ها استفاده میشه. بزارید با مثال بریم جلو

فرض کنید که دو کلاس NormalCar و RacingCar داریم و داخل هر دو این ها میخوایم یک کلاس Break تعریف کنیم

![[{5578722C-0887-4663-8C8A-A183B40F7D2E}.png]]

این جا با این ارور مواجه میشیم :

Duplicate definition 'Project.Break'. Possibly missing keyword 'partial'

که میگه توی namespace - Project دو تا کلاس Break تعریف شده که همین باعث ارور شده و برای راه حل احتمالی هم گفته که اگر از partial استفاده کنید اوکی میشه.

ولی اگر منظور این باشه که این دو کلاس کاملا از هم جدا هستند و مرتبط به هم نیستند باید بیایم و اسم namespace یکی رو تغییر بدیم، اینطوری ارور برطرف میشه.

![[{89623A7F-0AF3-44F7-A98D-F7C28AC2C29F}.png]]

حالا مورد بعدی اینه اگر بخوایم جداگانه از هر کدوم از اینها استفاده کنیم باید چی کار کنیم ؟ باید اسم namespace با . استفاده کنیم. اینطوری:

![[{B923F9A2-BEA8-4920-A5EE-183B230919DF}.png]]

یک قابلیت دیگه هم که داریم اینه که میتونیم namspace های تو در تو یا nested داشته باشیم.

![[{C423AF62-12B9-4236-8DBD-05AED80E2360}.png]]

همین مورد بالا رو هم میتونیم با . هم بنویسیم :

![[{6648E60C-1D5E-481A-8734-7853B2F5DBAA}.png]]

نکته : میتونیم به جای این که هر جایی بخوایم از یک namespace دیگه ای استفاده کنیم از . استفاده کنیم بیایم در بالای کد با نوشتن using و بعد نوشتن اون namespace کار خودمون رو راحت کنیم.

پیشنهاد میشه که اسم گذاری 3 بخشی انجام بشه بخش اول اسم کمپانی، بخش دوم اسم پروژه و بخش سوم سرویسی که داریم براش کد میزنیم مثلا سرویس LOGIN