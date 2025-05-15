![[Screenshot_2025-04-12-14-29-31-139_com.appzoom.zoomplayerclassic.jpg]]![[Screenshot_2025-04-12-14-43-34-412_com.appzoom.zoomplayerclassic.jpg]]

اینجا میاد خوده null و null string رو تشخیص میده

![[Screenshot_2025-04-12-14-54-15-113_com.appzoom.zoomplayerclassic.jpg]]

خوب اینجا اومدیم با روش post و check validator میخوایم کار کنیم
ورودی اینجا models users user است
خوده دات نت چیزی داره برای validation به اسم model state 
ما میخوایم قبل از این که req وارد controller بشه ، چک بشه 
![[Screenshot_2025-04-12-15-03-58-327_com.appzoom.zoomplayerclassic.jpg]]
خوب اینجا باز هم از start up استفاده کردیم و این یعنی این که بره کل پروژه رو میگرده و هر جایی که از validator استفاده شده میاد اون ها رو register میکنه 
خوب قسمت localization برای چند زبانگی پروژه استفاده میشه 
مورد دوم automatic validation enable برای این که قبل از این که درخواست به کنترلر برسه 

خوب مورد بعدیimplicitly validation children property که یعنی برای پراپرتی های که nested هستند بیاد چک رو انجام بده برای لول یک و لول دو و بقیه موارد که nested هستند 
بهتره که درخواست های که از سمت کاربر میاد اون شی از نوع فلت باشه یعنی این که nested نباشه 

خوب مورد بعدی که ازش استفاده شده برای چک کردن خوده شی هستش یعنی این که مثلا تعدادش زوج باشه سا حتکا شامل بدهکار و بستانکار باشه ، اگر بخوایم کالکشنی از اشیا رو ارسال کنیم باید این مورد رو فعال کنیم 
مورد اخر هم همون model state که دات نت داره که برای اطمینان فعالش میکنیم

![[Screenshot_2025-04-12-15-41-27-006_com.appzoom.zoomplayerclassic.jpg]]
خوب اینجا پیامی که داره میده اینه که اول null چک شده و بعد پیام داده و بعد empty میاد چک میکنه و بعد پیام میده 

![[Screenshot_2025-04-18-16-56-44-146_com.appzoom.zoomplayerclassic.jpg]]

![[Screenshot_2025-04-12-15-51-28-278_com.appzoom.zoomplayerclassic.jpg]]
خوب توی این حالت وقتی که به ارور میخوریم یا از قبل به ارور میخوره دیگه متوقف میشه

این یعنی این که در ۲ عکس بالاتر دو تا ارور نوشته شده ولی در این حالت مثلا وقتی که به ارور اولی میخوره دیگه دومی چک نمیشه و متوقف میشه 

![[Screenshot_2025-04-18-17-06-49-108_com.appzoom.zoomplayerclassic.jpg]]

اینجا به جای دستی خودمون بنویسیم user name اومدیم و از property name استفاده کردیم که اینجوری میاد اتوماتیک همون user name رو برمیگردونه 
![[Screenshot_2025-04-18-17-10-16-965_com.appzoom.zoomplayerclassic.jpg]]

خوب یه نکته ای که هست اینه که اگر‌ ما بخوایم اسمی که توی property name نشون میده با اسم اون property فرق داشته باشه به طور مثال به جای user name بخوایم توس پیام نشون بدیم نام کاربری ، از این استفاده میکنیم 
![[Screenshot_2025-04-18-17-13-14-476_com.appzoom.zoomplayerclassic.jpg]]
اینجا باید از with name استفاده کنیم

![[Screenshot_2025-04-18-17-16-26-660_com.appzoom.zoomplayerclassic.jpg]]
اینجا تابعی تعریف کردیم که بیاد چک کنه ببینه که تمام حروف وارد شده از نوع کاراکتر باشند

اول میاد چک می‌کنه که value وارد شده خالی نباشه 
بعد میاد اون مقدار رو میگیره و اگر توش space باشه میاد به جاش string empty رو میزاره 
و بعد داره چک می‌کنه که تمامی مقادیر اژ نوع کارکتر هستند یا خیر

![[Screenshot_2025-04-18-17-28-04-092_com.appzoom.zoomplayerclassic.jpg]]