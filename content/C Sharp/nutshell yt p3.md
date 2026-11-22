https://www.youtube.com/watch?v=x70OWY0TMUE&list=PLN5rV4x2x5Xef7lcvrhdDBnJKVfVEw6ui&index=18

![[Pasted image 20261111160221.png]]

خوب span ها ref struct هستن و struct ها value type هستش و این ها توی stack ذخیره میشه - این ها میتونن در دل خودشون یک refrence رو به manged memory یا unmange memory اختصاص بدن 

خوب span ها view هستن - هر چند که struckt هستن و در stack ذخیره میشن 

اما میتونن refrece بدن به یه Squence ای از دیتا 

![[Pasted image 20261111163352.png]]

خوب اینجا اگر بخوایم یه عملیاتی رو روی این array string ها انجام بدیم باید بیایم یه obj جدید ایجاد کنیم که این کار باعث فشار اوردن gc  میاره برای پاک کردن ابجکت ها بلااستفاده 

ما میخوایم همینی که داریم رو به view های متفاوت ایجاد کنیم براش :

![[Pasted image 20261111163618.png]]

خوب حالا میخوایم دو تا ویو متفاوت ایجاد کنیم 

![[Pasted image 20261111163824.png]]

![[Pasted image 20261111164918.png]]

خوب چون span از نوع struckt هستش توی stack هستش و داریم میگیم که از ارایه 0 تا 3 رو برام ویوش رو درست کن 

![[Pasted image 20261111165110.png]]

خط دوم هم یه مدل دیگه از نوشتن هستش 

![[Pasted image 20261111165138.png]]


![[Pasted image 20261111165204.png]]
خوب این در دیتا خودش 0 اش میشه جایگاه 2 

![[Pasted image 20261111165300.png]]

![[Pasted image 20261111165319.png]]

این دو تا view با هم overlap دارن 

![[Pasted image 20261111165349.png]]


![[Pasted image 20261111170706.png]]

چون struckt هستش در span هستش ولی چون ref داره میتواند به یه قسمتی از مموری اشاره کند 

![[Pasted image 20261111170841.png]]

خوب این شکل بالا برای refrence 
یه lenth هم داره که داره میگه به چند تا view میتونه بره جلو و طولش چقدره 

![[Pasted image 20261111170940.png]]
نکته ای که هست اینه که این View به صورت پشت سر هم هستش 

خوب Strukt یه چیزی که داره memory safe هستش چون هر thread برای خودش stack خودش رو داره و struct ها در stack هستن 

خوب سه تا راه داریم برای این کار 
![[Pasted image 20261111173834.png]]

![[Pasted image 20261111173848.png]]

![[Pasted image 20261111173957.png]]


![[Pasted image 20261111174055.png]]

![[Pasted image 20261111174118.png]]

![[Pasted image 20261111174218.png]]


https://www.youtube.com/watch?v=V8WHyc5uKnY&list=PLN5rV4x2x5Xef7lcvrhdDBnJKVfVEw6ui&index=19

![[Pasted image 20261111181238.png]]

خوب background task / service ها به دو دسته تقسیم میشوند 

![[Pasted image 20261111181604.png]]

![[Pasted image 20261111181654.png]]

خوب ما میخوایم اون background service که توی کنسول اجرا میشه رو بتونیم توی web host هم پیاده سازی کنیم 

![[Pasted image 20261111181921.png]]


خوب زمانی که host یا webhost که تعریفش کردیم باید و excec بشه - میره و start  رو exce میکنه که میتونه بره دیتایی رو seed کنه یا کارهای دیگه 
زمانی که host بسته بشه میاد میگه که اون background service که از IHost Service ارث بری کرده رو stop اش رو call میکنه 

![[Pasted image 20261115095553.png]]

یه abstract class دیگه داریم به اسم background service که از IHost Service ارث بری کرده 
این کالاس از pattern template استفاده کرده و این که برای ما تسک های long runnig رو هندل میکنه 

![[Pasted image 20261115095910.png]]

خوب اگر تسک long runnig بود میایم از background service ارث بری میکنیم و بعد میایم توی host یا webhost خودمون  تعریفش میکنیم 

اینجا دیگه ما start و stop نداریم و فقط اینجا داریم excec داریم 

![[Pasted image 20261115100250.png]]
با این دستور میتونیم این کار رو انجام بدیم که یه bacgorund service بسازیم 
![[Pasted image 20261115100355.png]]
از template میاد استفاده میکنه به اسم worker service و این رو میاد بر بستر host .net انجام میده - یعنی web host ای نیست 

![[Pasted image 20261115100454.png]]


![[Pasted image 20261115100601.png]]

![[Pasted image 20261115100624.png]]


![[Pasted image 20261115100658.png]]

![[Pasted image 20261115100727.png]]

![[Pasted image 20261115101215.png]]

خوب حالا میندازیمش توی یه حلقه :

![[Pasted image 20261115101327.png]]

خوب توی این حالت app ما run نمیشه - 

خوب چیزی که Recommend شده اینه که این تسکی که مینویسیم سریع تموم بشه وقتی که داریم از IHostService داریم استفاده میکنیم - کخ thrred برگرده برای استفاده برنامه 

![[Pasted image 20261115104803.png]]

نیتجه اینطوری میشه و app ما هنوز بالا نیومده - چون مدام توی این حلقه داره اجرا میشه یه تسک دیگه 

حالا اگر بخوایم long runnig اش کنیم : 

![[Pasted image 20261115104943.png]]


خوب اینطورری ما اومدیم اون کاری که میخوایم رو میندازیم توی یه task دیگه که اجرا بشه اینطوری long runnging میشه 

![[Pasted image 20261115105137.png]]

اینجا برنامه شروع شده و اون تسک هم در حال اجراست 

خوب حالا میخوایم از background service استفاده کنیم و اینجا همونطور که میبینید نوشته برای long runnging task ها داره استفاده میشه 

![[Pasted image 20261115111252.png]]

خوب در داخل خودش 

خوب حالا چرا template عه - اینجا اومدده گفته که شما بیاید start async رو پیاده سازی کنید و خودش در درون خودش قبل و بعد اجرای این دستور در دل خودش داره هندل میکنه 

![[Pasted image 20261115111350.png]]



![[Pasted image 20261115111705.png]]

![[Pasted image 20261115111718.png]]


عین همین رو هم میتونیم توی .net core هم داشته باشیم ولی اونجا host از نوع webhost هستش 


https://www.youtube.com/watch?v=8kmCgmKbGCY&list=PLN5rV4x2x5Xef7lcvrhdDBnJKVfVEw6ui&index=20

![[Pasted image 20261115112417.png]]

خوب اینجا یه درخواست میاد و اون میاد دیتا رو برمیداره و بعد لاگ میکنه و بعد جواب میده - خوب log کردن زمان میبره برای همین ما log رو میبریم رو یه threed دیگه یا task دیگه - که از threed اصلی جدا باشه که زمان بهتری برای پاسخ دادن ایجاد بشه 

![[Pasted image 20261115112631.png]]

خوب یا یه کار دیگه ای که میکنیم اینه که این لاگ ها رو push کنیم داخل یه queue مثل rabbit که بعدش یه process دیگه بیاد اون ها رو consume  کنه 

![[Pasted image 20261115112749.png]]

خوب برای یه برنامه کوچک منطقی نیست که بیایم rabbit رو بالا بیاریم 

میایم از Channel استفاده کنیم :

![[Pasted image 20261115112939.png]]

خوب channel میاد یه سیستم producer / consumer ایجاد میکنه که قابلیت کنترل bonded / unbounded رو بهم میده 

خوب 

![[Pasted image 20261115113052.png]]

ما queue مون 50 تا بیشتر جا نداره اگر 51 امی بیاد و هنوز 50 تا باشه و consumer اون ها رو مصرف نکرده باشه اون 51 عه wait میخوره تا زمانی که یکی از 50 تا توسط consumer استفاده بشن 

ما برای مدیریت memory از این روش استفاده میکنیم 

ولی unbounded ظرفیت تعیین نمیکنیم 

خوب channel ها thred safe هستن و fifo هستن 

![[Pasted image 20261115113338.png]]

اینها همون priducer و consumer هستن 

![[Pasted image 20261115122712.png]]

خوب ما میتونیم n تا producer و n تا consumer روی یک channel داشته باشیم 

استراتژی اولیه برای این که خارج از ظرفیت پیام میاد اینه که wait میکنه به صورت Defult هستش 

![[Pasted image 20261115122843.png]]



خوب یه استراتژی دیگه این هستش که اونی که اول صف هستش رو پاک کنه 

![[Pasted image 20261115123004.png]]

![[Pasted image 20261115123016.png]]

یا برعکسش 
![[Pasted image 20261115123032.png]]

یا یه نوع دیگه :
![[Pasted image 20261115123059.png]]

میگه اگر ما که داریم مینونیسیمیش اگر دیدم ظرفیت پره - خودمون f و بندازیم دور 

![[Pasted image 20261115123144.png]]


که بهمون یه call back میده 

![[Pasted image 20261115123750.png]]

![[Pasted image 20261115123832.png]]

همیشه reader کند تر از writer هستش 

![[Pasted image 20261115124046.png]]

خوب اینجا یه نکته ای هست اینه که writer 99  رو نوشته ولی reader داره 75 رو میخونه این به این معنیه که از 76 تا 99 الان توی queue هستش 

و اینجا معلوم میشه که writer سریع تر از reader داره کار میکنه 

خوب حالا میایم capacity رو کم میکنیم میایم از 50 به 2 تغییرش میدیم : 

![[Pasted image 20261115134137.png]]


![[Pasted image 20261115134153.png]]

![[Pasted image 20261115134228.png]]

خوب وقتی که میخواد 2 رو بنویسه میبیه که ظرفیت پره و وایمیسته 

خوب حالا دقیقا وقتی که 0 خونده میشه 2 وارد میشه 

![[Pasted image 20261115134407.png]]

حالا میخواد 3 رو بنویسه باز نمیتونه چون 1 و 2 داخل هستند 

![[Pasted image 20261115134547.png]]


![[Pasted image 20261115134612.png]]


حالا استراتژی های متفاوت داریم :

![[Pasted image 20261115135256.png]]


![[Pasted image 20261115135324.png]]

خوب این single reader یعنی این که فقط یک reader دیتا رو میخونه - چون چند تا reader همزمان میتونن بخونن 

![[Pasted image 20261115135448.png]]

در writer هم همین رو داریم 


![[Pasted image 20261115135645.png]]


![[Pasted image 20261115135715.png]]


![[Pasted image 20261115135817.png]]

خوب اینجا میاد قدیمی تره رو پاک میکنه که اینجا 0 هستش - پاکش میکنه که 2 رو write کنه 

![[Pasted image 20261115135917.png]]


![[Pasted image 20261115135936.png]]



خوب این هایی که دارن پاک میشن رو ما از یه طریفی میتونیم ببینیم :

![[Pasted image 20261115140054.png]]

خوب اینجا وقتی که ما داریم تایپ رو تعریف میکنیم که string هستش دیگه نیازی به اون String بالایی نداریم:

![[Pasted image 20261115140204.png]]


![[Pasted image 20261115143021.png]]

![[Pasted image 20261115143107.png]]

خوب حالا میخوایم ببینیم که میتونیم این قسمت رو 
![[Pasted image 20261115143315.png]]
ببریم توی background task 

و هر جایی هم که میخواستیم write کنیم اون backgroun task شروع کنه به خوندنش 

![[Pasted image 20261115143640.png]]


خوب حالا چطوری این رو inject اش کنیم ؟

سری پیش اینطوری ساختیمش و اصلا به service collection نفهموندیمش - ولی اینجا لازمه 

![[Pasted image 20261115143803.png]]

خوب توضیحات 
![[Pasted image 20261115144105.png]]
اینجا اول reader رو معرفی کردیم - بعدش اومدیم در خط بعدیش channel درست  کردیم و بعد با get service اومدیم اون channel رو گرفتیم 

اینجا اومدیم inject اش کردیم و داریم read میکنیم روی اون channel 

![[Pasted image 20261115144211.png]]

و اینجا هم داره write میکنه 
![[Pasted image 20261115144302.png]]

![[Pasted image 20261115144401.png]]

![[Pasted image 20261115144447.png]]

خوب حالا میخوایم benchmark بگیریم :
![[Pasted image 20261115144531.png]]



خوب ددو تا سناریو داریم - اولwrite و بعد read و سناریو دوم برعکسش

![[Pasted image 20261115144624.png]]


![[Pasted image 20261115144737.png]]



https://www.youtube.com/watch?v=MB9xEpkRTWk&list=PLN5rV4x2x5Xef7lcvrhdDBnJKVfVEw6ui&index=21

![[Pasted image 20261115153704.png]]

بقیه از مشتقات این ها هستند  
خوب ما چند تا int رو میزاریم توی یه ارایه - حالا میخوایم توش پیمایش کنیم - از کدوم انیدکس شروع کنیم و به کدوم ایندکس تموم میشه - برای این که بتونیم iterate کنیم یا پیمایش کنیم 
ما برای این کار ها نیاز به یک اشاره گر داریم 
![[Pasted image 20261115153948.png]]

ساده ترین ارایه و ساده ترین پیمایش 

خوب چه نیازی به inmerable , ienumerator داریم ؟
اگر بخوایم فرمولی بریم جلو و هر کاری دیگه بکنیم - توی همین for میتونیم انجامش بدیم 

![[Pasted image 20261115154218.png]]

![[Pasted image 20261115154232.png]]

خوب ما کوئری زدیم به دیتابیس و دیتا ها رو اوردیم اونجا که درخواست زدیم گفتیم 100 تا رکورد بهمون بده - ولی ایا مطمئن هستیم که اون 100 تا رو بهمون میده ؟

خوب برای همین قضیه - ما دیتا ها رو اوردیم و بعد میشموریمشون - بعدش یه arrry درست میکنیم و دونه دونه اون دیتاهایی که اوردیم رو میرزیم توش  و بعد شروع کنیم توش iterate کردن 

ساده ترین و پایه ترین پروتکلی که میتونیم یک iterate رو پیاده سازی کنیم میگیم IEnumerator 

خوب move next که از نوع bool هستش داره میگه که بعد از من دیتایی وجود داره یا نه 
خوب حالا میخوایم movement رو عوضش کنیم 

![[Pasted image 20261115154840.png]]

میتونیم نوع های مختلفی از پیمایش رو داشته باشیم 

حالا چطوری میتونیم به یه ارایه بچسبونمشون 

خوب حالا داستان اینه که فقط این نیست که بخوایم با array ها کار کنیم چون درد سر دارن - چون اول باید ببینیم چند تا است از دیتا بیس میاد - بعد بریم به همون اندازه ارایه درست کنیم و دودونه دیتا ها رو توش بزاریم 

و این که ایا این ارایه قراره بزرگتر بشه در طول برنامه یا کوچکتر بشه و .... - خوب .net یه سری colletction ؤو به ما میدنه

خوب حالا میشه که یه arry نامحدود ساهت 

منظور از coolentink اینه که دیتا ها رو یه جوری کنار هم بچسبونیم که این دیتا ها 



![[Pasted image 20261115155607.png]]

پایه ترین نوع طراجی collection میشه IEnumerable 

 ![[Pasted image 20261115155807.png]]
خوب ما یه لیست دارم به اسم xlist و میخوایم هر سری از یه نوع از پیمایش ها که در سمت راست هستن برای پیمایش داخلش ازشون استفاده کنیم 

خوب اینجا چند تا قابلیت داره - کسی که از IEnnumberable  استفاده میکنه - باید یکی یکی پایش کنیم و هیچ تغییری نمیتنیم توش بدیم 

برای حل مشکل این قضیه این اومد 
![[Pasted image 20261115160537.png]]


مشکلی که داره اینه که نمیتونیم به صورت رندوم بیایم هر جایی در ارایه insert کنیم - add میتونیم بکنیم ولی insert نه 

برای حلش : 

![[Pasted image 20261115163641.png]]


![[Pasted image 20261115163726.png]]


![[Pasted image 20261115163759.png]]


خوب IEnumerable فقط زمانی که یک بار میخوایم توش iterate کنیم سرعتش بالاتر از Ilist هستش 

چرا ؟ چون توی IEnumerable دیتا کاملا روی memory نیست و اگر بخوایم دوباره iterate کنیم دوباره فرایند از اول انجام میشه 

![[Pasted image 20261115165318.png]]

اون دایره ها link list , hash set هستند 

![[Pasted image 20261115165414.png]]


یک آرایه داره به صورت 4 خونه ای - برای این که دیتا ها رو توی خودش نگه داره -


![[Pasted image 20261115165527.png]]

خوب اینجا داره میگه که اگر اون چیزی که میخوایم Add کنیم سایزش کمتر از اون ظرفیتی که داریمه - که اوکیه انجام میشه - ولی اگر نه میگه addwithresize 

![[Pasted image 20261115165645.png]]


![[Pasted image 20261115165657.png]]

این رو چقدر رشد میده برای این که مثلا w رو واردش کنه 

![[Pasted image 20261115165725.png]]


![[Pasted image 20261115171221.png]]

و هر بار که میخواد زیادش کنه 2 برابرش میکنه 

https://www.youtube.com/watch?v=y_xZy2i0H6o&list=PLN5rV4x2x5Xef7lcvrhdDBnJKVfVEw6ui&index=22

![[Pasted image 20261115171443.png]]

اینجا ما اول یه isntance ساختیم و بعد از متدش استفاده کردیم و اینطوری بهش میگن instace method 

![[Pasted image 20261115171553.png]]

خوب حالا اون متد هایی که static هستند رو از خوده کلاس باید بهشون برسیم و ازشون استفاده کنیم برای همین بهش میگن class method 

وقتی که از class میایم instance میگیریم refre میاد در stack ذخیره میشه و دیتای اصلی میره توی heap 

![[Pasted image 20261116095731.png]]


![[Pasted image 20261116095819.png]]

خوب توی heap یه جایی رو داریم به اسم HFH میایم Static ها رو اونجا ذخیره میکنیم

![[Pasted image 20261116095947.png]]

خوب وقتی که instance میسازیم میره یه جای دیگه رو توی heap بهش اختصاص میده 

![[Pasted image 20261116100101.png]]


خوب وقتی که بخوایم اطلاعاتی رو بین تمامی instance ها و یا بین تمام thread های برنامه Share اش کنیم میایم از Static استفاده میکنیم 

![[Pasted image 20261116100416.png]]

https://www.youtube.com/watch?v=rkL10_bBg6Y&list=PLN5rV4x2x5Xef7lcvrhdDBnJKVfVEw6ui&index=23

![[Pasted image 20261116100821.png]]

خوب اینجا اگر قانون عوض بشه برای حقوق کارمند ما باید بیایم همون جا تغییر بدیم 

![[Pasted image 20261116101047.png]]
خوب برای این که بهترش کنیم میایم جداش میکنیم - محاسبه حقوق رو از salery 

![[Pasted image 20261116101154.png]]

خوب حالا ما یه جا این محاسبه حقوق رو تعییر میدیم و همه جا تغییر میکنه 

![[Pasted image 20261116101223.png]]

خوب حالا hr گفت با یه فرمول دیگه میخواد محاسبه بکنه - ما باید بیام و ورودی تابع رو تغییر بدیم 

خوب برای همین قضیه میایم یه متد به صورت plug in میزاریم و به salery میگیم که اون رو call کن 

برای این که مثلا اگر یه فرمول اضافه بشه نخوایم هی else if بزاریم 

![[Pasted image 20261116102540.png]]

خوب ما اینجا میخوایم plug in اش کنیم 

![[Pasted image 20261116102922.png]]


![[Pasted image 20261116103819.png]]

خوب instance ها و obj ها و delegate ها میدوندد که چجوری متد ها رو call بکنن 

![[Pasted image 20261116103915.png]]

خوب حالا مال پشت این Delegate میتونیم متد هایی رو ارسال کنیم خروجی int باشه و ورودش int باشه 

![[Pasted image 20261116103956.png]]

دیگه دققه ی if و condition رو نداریم 
![[Pasted image 20261116104334.png]]

خوب حالا میخوایم hr رو محاسبه کنیم - دیگه نیمخواد بریم condition اضافه کنیم 

![[Pasted image 20261116104423.png]]


https://www.youtube.com/watch?v=B42CSczVmK4&list=PLN5rV4x2x5Xef7lcvrhdDBnJKVfVEw6ui&index=24

خوب قبلا اینطوری مینوشتن 

![[Pasted image 20261116105315.png]]

ولی الان invoke رو هم نزاریم اوکیه 

![[Pasted image 20261116105627.png]]

دیگه ما اینجا دققه ی این رو نداریم که یه رفتار جدید یا یه شرط جدید ایجاد بشه 

ایا delegate ها میتونن به صورت genetic باشن ؟

![[Pasted image 20261116105826.png]]
 
مثل عکس بالاا میتونیم generic اش کنیم و ورودی و خروجیش یکسان هستش 


خوب اینجا مشکلی که پیش میاد - اینه که ورودیمون یه چیزی باشه خروجیمون یه چیز دیگه 

![[Pasted image 20261116110202.png]]


![[Pasted image 20261116110709.png]]


![[Pasted image 20261116110755.png]]

![[Pasted image 20261116110824.png]]

تا 16 تا overload رو پیاده سازی کردن - یعنی 16 تا ورودی و اخرینش میشه خروجی 

![[Pasted image 20261116110920.png]]

خوب دیگه ما نیازی نداریم از اون بخش کامنت شده استفاده کنیم و از همین امکانات .net استفاده میکنیم 

خوب func نوعی از delegate generic هستش که حتما خروجی داره 

خوب حالا Action جیع ؟ این فرقش با بالایی اینه که دیگه خروجی نداره و خروجیش void هستش 

![[Pasted image 20261116111111.png]]


https://www.youtube.com/watch?v=lt0-w6vxk5Q&list=PLN5rV4x2x5Xef7lcvrhdDBnJKVfVEw6ui&index=25

خوب delegate ها ابجکت هایی هستن که میدودنن که چطوری باید متد ها رو call کنن 

![[Pasted image 20261116112400.png]]


![[Pasted image 20261116112541.png]]


خوب با استفاده از delegate ها میتونیم multi cast کنیم 

![[Pasted image 20261116112710.png]]

![[Pasted image 20261116113942.png]]

اگر خروجی void باشه این کار رو میکنیم 

![[Pasted image 20261116114028.png]]



خوب حتی میتونیم action رو هم ننویسیسم و فقط var بنویسیم 

![[Pasted image 20261116114151.png]]

بر اساس این که ما داریم singiture متد رو بهش میدیم خودش action در نظرش میگیره در کامپایلر

https://www.youtube.com/watch?v=4-QazqN36TY&list=PLN5rV4x2x5Xef7lcvrhdDBnJKVfVEw6ui&index=26

![[Pasted image 20261116115033.png]]

خوب حالا میخوایم ببینیم که کجا ها باید interface ها استفاده کرد 

![[Pasted image 20261116115210.png]]


![[Pasted image 20261116115249.png]]

خوب 3 تا حالت هستش که بخوایم از delegate استفاده کنیم یا از interface 

زمانی که multicast داریم نمیتوانیم از interface ها استفاده کنیم 
به ازای هر رفتار و فرمول داریم کلاس های متفاوت درست میکنیم - یعنی رفتار یکی ولی متفاوت پیاده سازی شده است - در این صورت نیازی نیست از interface استفاده بشه 

https://www.youtube.com/watch?v=uf691MK762Q&list=PLN5rV4x2x5Xef7lcvrhdDBnJKVfVEw6ui&index=27

