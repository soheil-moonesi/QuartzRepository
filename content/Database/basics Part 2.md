خوب حالا برای ساختار بندی میایم یک هارد رو اختصاص میدیم به سیستم عامل و  نرم افزاهای مربوطه و sql server یک هارد دیگه رو اختصاص میدیم به  mdf ها و یک هارد هم اختصاص میدیم به ldf ها و یک هارد هم برای بک آپ گیری ، اینی که این هارد بک آپ هم داخل همین سرور هستش برای بک داشتن اطلاعات و تغییراتی و خرابی هایی که ممکنه برنامه نویس ها به وجود بیارن بهتر اینه که بک آپ ها در یک سرور دیگه قرار بگیرند 

خوب Sql وقتی که عملیات create delete update میخواد انجام بشه قبلش میاد یه نسخه از اون دیتا رو از mdf برمیداره بعد انتقالش میده روی فایل LDF بعد یه transaction داخل اون فایل LDF باز میکنه و بعد عملیات مد نظر که از جنس همون 3 تای اون بالا هست رو انجام میده بعد از این که کار کامل و درست انجام شد commit میشه و بعد دیتاهایی که تغییر کردن یک کپیشون از ldf برداشته میشه و انتقال داده میشه به MDF 

در LDF تمامی تاریخچه و تمامی عملیاتی که روی دیتا ها انجام میشه اونجا قرار میگیره و نتیجه ی عملیات هم دیتاش داخل LDF هستش 

اگر Recovery از نوع full back up باشه اگر قسمتی از فایل mdf نابود شده باشه میتونیم با استفاده از ldf بیایم و اطلاعات رو برگردونیم ، اینطوری که میاد از اون قسمتی که اطلاعات از دست رفته میاد یکی یکی اطلاعات رو طبق LDF  تغییر میده و اطلاعات رو کامل میکنه 

![[{8DD91565-C436-46B6-A412-9F6E167A9EF4}.png]]

![[{E0880A91-9BD0-4E9A-96E9-7D60D70C8C88}.png]]

https://www.sqlservertutorial.net/sql-server-administration/sql-server-backup-types/

حالا میرسیم به قسمت file group ها 

![[{51F8A172-ACB7-47B5-9E26-3C5C83F42412}.png]]

همونطوری که میبینید file group برای LDF قابل انجام نیست ولی برای MDF میشه انجام داد 

![[{1F1C4D19-BFE0-4F3A-9271-DE76316785CD}.png]]
نکته هایی که در عکس بالا هستش اینه که اولین دیتابیس پسوندش mdfهستش و بعدی ها همه میشن ndf به خاطر این که میتونیم n تا MDF داشته باشیم پس میشه NDF 

این هایی که در filegroup های متفاوت در جاهای مختلفی میتونن ذخیره بشن مثلا برای primery میشه هارد hdd اول درایو d و برای filegroup 1 میشه هارد دوم داریو E

میتونیم به هر تعدادی که میخوایم فای های mdf درست کنیم ولی LDF فقط یه دونه است.
![[{9A4EE7E1-3145-4484-BDA8-B55E6C32B331}.png]]

خوب file type ها از این پنججره قابل تعیین کردنه 
![[{634E58A6-8424-4ABD-87F4-D9A0D1E0BBBC}.png]]

که  row data میشه MDF  و log میشه LDF و file stream هم اصا داستانش جداست

خوب حالا میتونیم دو تا file group تعیین کنیم 

![[{917DA6F5-927C-4B30-9836-2ADC9ED37B78}.png]]

یکی primery و یکی secondry که بهتره که در دو درایو جدا ذخیره سازی بشن 

حالا وقتی که میخوایم این file group رو تغییر بدیم اینطوری عوش میکنیم :
![[{461D914C-E473-43B1-9F83-9FD324746C72}.png]]

فقط دیتاهایی که حساس هستند مثل پسور رو میایم encript میکنیم و بعد ذخیره میکنیم در دیتابیس

به صورت دیفالت هم یه فایل گروپ تعیین شده 

disk managment 
دلیل این که میایم فایل گروپ های مختلف میسازیم و دیتاها رو در هارد های متفاوت ذخیره میکنیم اینه که ممکنه حجم یک هارد برای ذخیره سازی برای یک هارد ممکنه زود تموم میشه و بهتره که این جدوال رو در هارد های مختلف ذخیره کنیم 

backup managment 
اینطوری در نظر بگیریم که اگر از فایل گروپ ها استفاده نکنیم یه جدول ممکنه داشته باشیم 20 تراباییت و حال ا میخوایم ازش بک آپ بگیریم حالا اتفاقی که میوفته اینه که دقیقا یه هارد دیگه 20 ترابیایتی برای ذخیره سازی بک آپمون نیاز دارم  

خوب حالا برای مدیریت این که فاصله زمانی هر بک آپ چقدر باشه هم میونیم از file group استفاده کنیم مثلا فایل گروپ 1 سالی یکبار ازش بک آپ گرفته بشه و فایل گروپ 2 ماهی یکبار 

optimization 
پردازش موازی و ذخیره سازی و لود دیتا ها به صورت همزمان در ترد های متفاوت برای همین میام فایل گروپ ها رو درست میکنیم چون برای هر هارد یک مقدار از resourse و thread در نظر گرفته میشه و بعد در صورت انجام عملیت به صورت موازی سریع تر و بهتر عمل میکنه که البته این خودش trade of هایی داره 

archiving 
میتونیم حتی دیتای داخل یک جدول رو بیایم در هارد ها و یا جاهای دیگه قرار بدیم ، مثلا بیایم بر اساس شهر ها دیتا ها رو در هارد های متفاوت قرار بدیم

 انواع مدل ساختن دیتابیس 
نوع اول
یک دیتابیس واحد 
جدول 1400 و جدول 1401

برای گزارش گیری باید هر سری اسم جدول هارو عوض کنیم برای هر سال 
دیتا یکجاست که خوب نیست

نوع دوم 
دیتابیس 1 - جدول سال 1400
دیتابیس 2 - جدول سال 1401
دیتابیس های جدا جدا
محصول شماره 1 میشه مثلا خودکار در سال 1400 
محصول شماره 1 در سال بعدی مثلا اگر بشه صندلی 
قابلیت این رو داره که دیتابیس های قدیمی رو آرشیو کنیم

نوع سوم 
دیتابیس با یک جدول و فیلد سال 
جامعیت دیتا دارم ولی امنیتش پایینه 

پارتیشن بندی
![[{3937E41D-2676-44A3-9132-0FB438585374}.png]]

![[{DD2F0CE7-DE88-4A2E-ACA0-F1DEA9307A3C}.png]]


https://questdb.io/glossary/database-partitioning/

![[{E4159046-1076-433E-9740-BC8D68340683}.png]]
![[{50A6EF33-30AB-44F2-ABAE-D399C17E07A6}.png]]

خوب برای این کار رو انجام بدیم اول باید بیایم دیتاهمون رو پارتیشن بندی کنیم :
![[{4F888A7B-785B-4CDE-8F1B-51982967471F}.png]]
بعد از اون باید بیایم تعیین کنیم که هر کدوم از این پارتیشن ها به کدوم از فایل گروپ ها وصله بشه :
![[{F5249C83-C457-4CBE-9627-198368991F30}.png]]

خوب اگر از اول پارتیشن بندی نکردی هم میشه این کار و کرد  وقتی که میخوایم این کار رو انجام بدیم انتفال اطلاعات به صورت اتوماتیک انجام میشه به طور مثال وقتی که از اول دیتابیسمون بدون پارتیشن بوده و بعد میایم براش توی هارد های مختلف فایل گروپ درست میکنیم بعد انتقال اطلاعات و جابه جایی شون رو اتوماتیک انجام میشه 


در دیتا بیس ما دستور های create ساختن  و alter تغییر و ویرایش , drop پاک کردن 

![[{B1A17182-660A-4CCB-AEA5-8E451896FFD6}.png]]

خوب حالا میرسیم به انجام مراحل 
اول یه دیتابیس میسازیم و بعد میایم 3 تا فایل از جنس ndf درست میکنیم بعد میایم اسم فایل های ndf رو تعیین میکنیم و بعد میایم file group هاش رو تعیین میکنیم و بعد میایم جاهایی که باید ذخیره بشن رو تعیین میکنیم 
![[{EB6A73DD-5870-43E1-9909-7A36FA51D0EE}.png]]

ما میتونیم قبل از این جدولی داشته باشیم بیایم یه partition function رو داشته باشیم بعدا به هر جدولی این partion function رو بدیم میاد اون عملیات رو براش اجرا میکنه مثلا طوری نوشتیمش که بیاید بر اساس سال پارتیشن بندی رو انجام بده هر وقت که این partion function رو وصل کنیم به table که سال داره اون میاد این کار ها رو براش انجام میده 

این پایین تمام مشخصات رو نشون میده که نوع دیتابیس جیه و با چه یوزی هستم و اسم دیتابیسمون چیه 

![[{0ADC43C2-F46F-40A9-97CF-38CC3B97456B}.png]]

خوب برای تنظیم پارتیشن ها از این روش استفاده میکنیم :
![[{3B0A9C4D-4584-4AFB-B840-7B6080F5E58E}.png]]

خوب اونجایی که نوشتیم int این data type که برای تقسیم بندی میخوایم استفاده کنیم از چه نوع داده ای هستش 

نکته ای که هست اینه که به تعداد +1 بیشتر از تعداد تقسیم ها میشه تعداد پارتیشن ها یعنی به طور مثال 1385 و 1386 رو داریم که میشه 2 تا نقطه تقسیم پس در نتیجه ما 3 تا جای پارتیشن براش نیاز داریم  


برای این که تعیین کنیم که range مون از راسته یا چپ از طریق شکل زیر عمل میکنیم 

![[{C350E154-BE1D-49AA-8025-E57F1245263D}.png]]

![[{A9133440-845B-432C-BFF7-36DE25F17FD4}.png]]
left 

![[{7E97ACCD-3660-48BC-8BE0-529392773BAC}.png]]
right


بعد از اجرای دستور 

![[{B504D900-3D11-4FFF-87E3-4E0BB0387FAA}.png]]

طریقه ی کامنت گزاری :
![[{DE32BA96-4FC2-44EB-B888-A1134DA0CF4F}.png]]

خوب برای وصل کردن پارتیشن ها به فیل گروپ ها از این کد استفاده میکنیم :
![[{461C833E-6E72-4B55-A7BF-2194CE8502CD}.png]]
که میایم یه schme به اسم PS1 درست میکنیم و بعد میگیم که اون پارتیشن فانشکن رو بگیر و وصلشون که به این 3 تا فایل گروپ

بعد میایم table رو درست میکنیم 

![[{D7BCD8A8-C57F-480E-85F9-E51D205B0D60}.png]]

بعدش میایم روی جدولی که درست کردیم قسمت properties و اونجا regular data space specifiction رو میزاریم روی Partition scheme

![[{98307D1E-1BF3-463D-873E-1A7B6D99F329}.png]]

بعدش باید تعیین کنیم که اسم اون schema چیه؟ که چون یکی schema داریم همون رو به صورت اتوماتیک قرار داده 

![[{656CD091-F8C4-4FD9-BBDD-667ECDF1914D}.png]]


بعدش میایم تعیین میکنیم که پارتیشن بر چه اساسی انجام بشه ، میزنیم روی  partition column list و از اونجا میبینیم طبق کدی که زدیم باید این قسمت از نوع int باشه و میاد دیتا تایپ هایی که از نوع int هستن در اون جدول رو بهمون نشون میده 

![[{9D7EE549-27C7-4919-9C5D-18EFB6AABEE9}.png]]

و از اونجا میایم و year رو انتخاب میکنیم 


بعد میایم به صورت دستی توی جدول دیتا وارد میکنیم 
![[{76E107A2-BE55-47EE-A27B-5127739ACFB7}.png]]

![[{18031F0A-2FBD-47C1-83D6-4280C7A6B328}.png]]

الان اینجا 3 تا دیتا داریم که قراره بره توی 3 تا پارتیشن مختلف 

برای گرفتن ریپورت هم اینطوری عمل میکنیم :
![[{96A76928-63D2-4686-B92D-F422B2300BC1}.png]]

اینطوری ریپورتش رو نشون میده :

![[{2C5599C0-070C-4B77-BF09-3AD43505C78E}.png]]

رفع باگ :
 باگ
![[{B9042AE2-87B1-4E8F-85EE-86698C77B942}.png]]

![[{E36A1574-4205-4B27-8699-87CE3380B7D1}.png]]
تیک perevent saving رو غیر فعال کنیم و بعد سیوش کنیم باگ برطرف میشه 

اگر بخوایم جای فایل ها رو عوض کنیم باید دیتابیس رو از engine جدا کنیم و بعد فایل هاش رو دستی  به جایی که میخوایم جابه جاش کنیم ببریم و بعد وقتی که میخوایم دوباره بچسبونیمش باید یه سری کار ها رو انجام بدیم   

![[{7AD713A0-5E5E-4851-B827-CE31CF13D96B}.png]]

![[{7D848BAF-A10D-4BB0-868F-FD2941DC6FFE}.png]] 

خوب اینجا همونطوری که میبینید فایلی که به فایل گروپ primery وصل باشه نمیتونه read only بشه 

حالا به طور مثال میایم fg1 رو read only میکنیم 

ارور :
![[{09E90FA7-F4E8-406C-85DB-67E8BABC51A3}.png]]

راه حل راحتش اینه که یه بار کل برنامه رو ببندیم و بعد بازش کنیم 

خوب حالا وقتی که fg2 رو Read only کردیم وقتی که میخوایم توی table اش دیتا وارد کنیم با این ارور مواجه میشیم 

![[{544E5919-3C2D-4FE5-93B6-1520A73D6323}.png]]


![[{4C75EE01-260E-473E-9B27-7D420054A443}.png]]

ویرایش و حذف و هر کار دیگه رو دیگه رو نمیشه روشون انجام داد و این که فایل هایی که read only میشن سرعت دسترسی شون میره بالا 

 خوب حالا برای این که فایل گروپ رو از حالت دیفالت از روی primery بخوایم تغییر بدیم 
 ![[{1C0DBCAB-2E3F-4D9A-BAD1-621ABAF3E824}.png]]

![[{905EC722-A075-48EE-8553-4E227A2AC13C}.png]] 

اینجا دیفالت روش هستش و از اینجا تغییرش میدیم 

![[{10550D6F-95F0-4507-8B59-F27202FE909D}.png]]

خوب حالا وقتی که میخوایم یه فایل گروپ جدید بسازیم بهمون میگه دیفالت کدومه 

![[{98A0D4A3-FE76-4951-896B-F413E3EEDB3E}.png]]

اول ما عملیات پارتیشن بندی برای دیتاهامون در جدول انجام میدیم و بعد میایم با partition scheme  تعیین میکنیم که هر کدوم از اون partisition هایی که در مرحله قبل درست کردیم به کدوم file group وصل بشه 

در نظر بگیریم که اگر در ابتدا فقط windows authentication رو انتخاب کردیم ولی بعدش میخوایم عوضش کنیم ، حالا میخوایم عوضش کنیم (در حالتی که mix mode رو انتخاب نکرده بودیم )   

![[{BDE81CED-AF92-46BE-AC93-862EE3C20329}.png]]

بعد میریم توی قسمت security اونجا sql server and windows auth رو انتخاب میکنیم 

بعد میریم توی Services 

![[{379071CA-AE65-46F9-8E2F-14B87D76F856}.png]]

![[{BD61C480-AF1C-4A27-88BE-3FAC3396F5DF}.png]]

بعدش میریم توی این قسمت و میزنیم روی sa :

![[{12ADA363-7BB6-4DEB-8D5E-6AF1A994C1D4}.png]]

![[{176BDA33-1420-4C56-9679-C21796E95003}.png]]
براش پسورد رو هم تعیین میکنیم 

![[{FB93A75B-CF42-4555-9058-B222173540EA}.png]]


برای درست کردن user جدید 
![[{5715B856-3E24-43C6-91E4-59DCB512E562}.png]]

![[Pasted image 20241130155352.png]]

بعدش میزنیم روی advance و اونجا میزنیم روی find now و از اونجا یوزرمون رو انتخاب میکنیم 

برای ساختن user sql ای هم اینطوری عمل میکنیم :

![[{C535C96D-5891-44F8-A77E-1A31F49F61CE}.png]]

خوب pasword policy چک میکنه میزان امن بودن  پسورد انتخابی رو 

بعدیش expiration بعد از یک ماه پسوردش باطل میشه 

بعدیش هم change password هستش که بعد از اولین لاگین نفری که باهاش وارد شده پسوردش رو خودش تعیین میکنه  

[[SQL Server]]