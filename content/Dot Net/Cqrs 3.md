خوب قسمت سوم auto mapper ![[Screenshot_2025-04-08-08-03-02-624_com.appzoom.zoomplayerclassic.jpg]] 
خوب وقتی که از base استفاده میکنیم namespace و اسم پروژه رو برامون مینویسه 

خوب در نظر بگیرید که ورودی action یک dto هستش که اون باید تبدیل بشه به command و بعد اون تبدیل بشه به model و بعد تبدیل بشه به viewmodel و بعد return بشه 

![[Screenshot_2025-04-08-08-27-58-772_com.appzoom.zoomplayerclassic.jpg]]

خوب اینجا اومدیم پراپرتی های person رو برابر person view model قرار میدیم 
![[Screenshot_2025-04-08-08-57-16-324_com.appzoom.zoomplayerclassic.jpg]]

خوب در عکس بالا اومدیم تنظیمات auto mapper رو تنظیماتش رو درست میکنیم 
دلیل استفاده از automapper اینه که اگر ما یه پراپرتی به person اضافه کردیم و یادمون رفت به person view model اضافه کنیم یا همین مورد در مورد کم کردنش هم هست 

توی عکس بالا چیزی که تعریف کردیم اینه توی config  بیا یه مپ ایجاد کن از person به person view model

خوب از همون config که ایجاد کردیم میایم اینجا استفاده میکنیم و میگیم که حالا بیا مپ رو ایجاد کن با config . Create mapper و بعد داریمم میگیم که اون شی که به عنوان source بهش دادیم رو بیاد و مپ کنه به person view model و این کار در پشت با استفاده از تکنیک های reflection انجام میشود

![[Screenshot_2025-04-09-08-42-55-895_com.appzoom.zoomplayerclassic.jpg]]
 
خوب حالا اینجا جاشون رو برعکس کردیم و بعد به این ارور پایین خوردیم 
![[Screenshot_2025-04-09-08-50-20-398_com.appzoom.zoomplayerclassic.jpg]]

![[Screenshot_2025-04-09-10-46-49-794_com.appzoom.zoomplayerclassic.jpg]]


![[Screenshot_2025-04-09-10-49-26-961_com.appzoom.zoomplayerclassic.jpg]]

![[Screenshot_2025-04-09-10-51-04-362_com.appzoom.zoomplayerclassic.jpg]]

![[Screenshot_2025-04-09-11-05-00-763_com.appzoom.zoomplayerclassic.jpg]]

خوب اینجا اومدیم هم از person view model به person و هم برعکسش عملیات مپ کردن رو انجام دادیم 

خوب حالا میدونیم که در person پارامتر display full name وجود نداره

خوب ما میخوایم بعد از مپ شدن تکلیف display full name تعریف شود

خوب برای این کار وقتی که داریم person رو به person view model تعریف کنیم میای از for member استفاده میکنیم و بعد هم با استفاده از map from استفاده میکنیم و بعد میگیم اسم کامل طرف رو در کنسول بنویسن
![[Screenshot_2025-04-09-11-09-20-115_com.appzoom.zoomplayerclassic.jpg]]


خوب دو تا استراتژی برای استفاده از auto mapper هستش یا همه رو توی یک کلاس بنویسیم یا به ازای هر کلاس که میخوایم ازش استفاده کنیم بیایم اون رو بنویسیم 

![[Screenshot_2025-04-09-12-17-21-039_com.appzoom.zoomplayerclassic.jpg]]



خوب اینجا در ابتدا وقتی که service رو میزنیم بعدش چون که add auto mapper یک extension method هستش باید اون بالا using اش رو بزنیم

حالا اونجا که نوشته شده startup به این شکل کار میکنه میره کل پروژه رو میگرده و  که هر کدوم از کلاس هایی که از auto mapper profile ارث بری کرده رو پیدا میکنه و mapping هایی که داخلشون در constructor نوشتیم رو اجرا میکنه 

![[Screenshot_2025-04-09-12-30-35-266_com.appzoom.zoomplayerclassic.jpg]]

اینطوری ازش استفاده میکنیم

خوب اینکته هستش که زمانی که میخواد این کنترلر ساخته بشه میاد و di انجام میشه 

