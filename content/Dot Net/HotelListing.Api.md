![[{8DC6B2E2-FD3C-4C25-9949-290DD9547CDC}.png]]
اینجا وقتی که تعیین کردیم که route  روی controller باشه ، اینطوری میشه که هر وقت درخواستی با اسم اون کنترلر بیاد اون فعال میشه و یه پاسخی رو برمیگردونه اینجا اسم کنترلرمون weatherForcast هستش 

![[{74307FCE-A30B-4314-B14C-AD4BE5A421D3}.png]]
حالا اگر بزنیم weatherForcast/GetWeatherForcast این متد فعال میشه و یه دیتایی رو برای ما برمیگردونه 

نکته : lunch setting همونطوری که از اسمش پیداست یعنی چیزهایی که نیازه برای این که پروژه رو اجرا کنیم و راه بندازیم :
![[{24BCA30C-B9C9-4292-A282-623B7CE2C9B7}.png]]
ولی appSetting  چیزهایی هستش که ما برای develpment میخوایم استفاده کنیم 

![[{08112018-2DF0-4718-A2E4-6805348C7F9D}.png]]


نکته اگر بخوایم سرویسی رو تعریف کنیم میایم اون ها رو بین builder و builder.build تعریفشون میکنیم :

![[{321A5994-5A0B-4F97-8390-2A43D0E8FEE5}.png]]

 و نکته ی بعدی اینه که اگر بخوایم middleware رو تعریف کنیم میایم بین app و app.run تعریفش میکنیم :

![[{E3633229-AA58-4B6A-B107-80B4291DCA75}.png]]
خوب اون builder که داره سرویس ها و چیزهایی که برنامه میخواد ازشون استفاده کنه قبل از این که app.build بشه رو فراهم و آماده میکنه برای همین بهش میگن IOC Controller یا همون inverstion of control container 

خوب وقتی که به app میشه دیگه ما میایم middleware ها رو اضافه میکنیم که این به request pipline تاثیر میزاره 
![[{F0FC4EAE-AA02-4073-A493-3A9FA2DE71AD}.png]]

خوب یاینجا به طور مثال داره میگه اگر روی ماشین خودمون و در حالت development داریم کد رو اجرا میکنیم بیاید و از این ها استفاده کنه و اون ها رو اجرا کنه swagger و swaggerUI  

![[{2842B87B-E931-450B-BFFD-EFD1ACA9C33B}.png]]
این برای اینه که همیشه از https استفاده کنیم 

خوب model ها برای این هستند که دیتا چه شکلی باید باشن 
![[{179277C6-F119-4C1D-95AB-3F2EC2249014}.png]]

 
تعریف cors  این برای این هستش که client های مختلفی که روی سرور من نیستند هم بتونند به این api دسترسی داشته باشند 

![[{C7357C4C-82A3-4A19-8267-96C5A7A6EC4A}.png]]

https://www.bytehide.com/blog/cors-aspnet-core

In this guide, we’ll unravel the core principles of Cross-Origin Resource Sharing (CORS) in ASP.NET Core. We will cover its role in web applications, provide practical examples and highlight some common mistakes to avoid.

Let’s dive in!


## Introduction to CORS

Ever wondered about the invisible rules that keep your website interactions safe and secure? That’s where CORS, or Cross-Origin Resource Sharing, comes in. This primer will help us understand its importance in our web applications.

### Understanding CORS and Its Importance

CORS or Cross-Origin Resource Sharing is the guardian angel that allows or restricts external domains to access resources from your domain. Imagine you’re hosting a party (your website), and CORS is the bouncer deciding who gets in (requests) based on the guest list (rules you’ve set). Oh, and that party? It’s one thrilling and secure online experience!

![[{83307703-5432-4163-B21F-FC7DDD5AEF47}.png]]

### How Does CORS Work

Once you send a request from a client to a server in the dance of web communication, the server responds with access control headers. These headers decide who gets to dance along to the beat (the resources). But hey, let’s not only talk in riddles, let’s dive deeper into CORS’s working mechanism in ASP.NET Core context in the next sections.

![[{776E9F6D-C9A2-4273-8439-04072A19A9F5}.png]]

### Step-by-step Guide to Enabling CORS in Web API NET Core


![[{2ECEFB75-2CE5-4BF0-9860-7E18176D4E63}.png]]

### Understanding NET Core Allow CORS Methods

![[{F5D7D3D8-9557-4D6E-A39F-076451A5B267}.png]]



![[{0AC37B19-B5F4-4423-8472-CAC35F4D4F33}.png]]

https://www.bytehide.com/blog/cors-aspnet-core


بعدا  کامل مطالعه شود

![[{D429724E-2B2D-4EF8-AB5A-3B154D732EF6}.png]]

خوب حالا ما این رو توی service ها اضافه کردیم حالا میرسیم به این که اضافه اش کنیم به pipeline  تا ازش استفاده کنیم 

![[{38E8593B-49BD-4505-A71B-A7CC09666173}.png]]

اینطوری میایم اسم اون policy که اون بالا تعریف کردیم رو میاریم و اینجا استفاده میکنیم 

![[{BEC0CEC1-94D9-424B-991E-E013928256BE}.png]]

توضیحات بیشتر 
https://andrewlock.net/making-authenticated-cross-origin-requests-with-aspnetcore-identity/

بعدا مطالعه شود 


خوب حالا میرسیم به serilog 

https://virgool.io/dotnetzoom/%D8%A8%D8%B1%D8%B1%D8%B3%DB%8C-%D9%88-%D9%BE%DB%8C%D8%A7%D8%AF%D9%87-%D8%B3%D8%A7%D8%B2%DB%8C-centerilzed-logging-system-%D8%AF%D8%B1-asp-net-core-%D8%A8%D8%A7-%D8%A7%D8%B3%D8%AA%D9%81%D8%A7%D8%AF%D9%87-%D8%A7%D8%B2-serilog-%D9%88-elasticsearch-%D9%88-kibana-jbevdsvooran

خوب logging توی پروژه خیلی مهمه ، مخصوصا برای api  ها چون توی api ها ما هیچ اینترفیسی نداریم که داره دقیقا چه اتفاقی میوفته برای همین یه موقع هایی که مثلا  client میگه که من فلان کار رو کردم و فلان ارور خوردم برای ما خیلی مشکل میشه که بخوایم track کنیم و مشکل رو پیدا کنیم 

خوب برای همین میخوایم یه چیزی رو ستاپ کنیم که log ها رو generate کنه و بهمون نشون بده که چه اتفاقاتی داره میوفته در هر روز و هدف بعدی اینه که بیایم همه این log رو ذخیره کنیم  

میایم این رو نصب میکنیم :
![[{7F1C122E-7E8B-40E5-9EFB-E23F7C8D8845}.png]]
خوب همچنین یه مفهمومی داریم به اسم sinks که میاد اون فایل خروجی رو بیاد کجا و به چه صورت ذخیره و Save کنه 

![[{76368DE9-4472-40D6-8362-ACB16BA0C7D5}.png]]

که برای این پروژه میایم و seq رو نصب میکنیم و ازش استفاده میکنیم 

![[{394FE2CA-5C77-4837-89B3-E36197043464}.png]]
https://satyampushkar.medium.com/serilog-logging-to-console-seq-elasticsearch-file-using-dotnet6-d9536b534209

این رو نصب میکنیم :
![[{6A340A69-7C4B-4FD1-9DE0-51DEA9798CC7}.png]]

بعدش میایم serilog expression رو نصب میکنیم برای cofig کردن در پروژه 
![[{B37EEF02-B429-4BE0-A872-39ABECA6E022}.png]]

و در csProj نشون میده که چیا نصب کردیم :
![[{47809D7B-E788-4CAE-AF56-D3D21CD82971}.png]]

خوب این نکته هستش که وقتی که اسم این پکیج ها اینجا باشه خوده vsisual studio میره اون ها رو دانلود میکنه و میاره برای اجرای پروژه 

![[{0058E461-C9B3-4431-8FA7-D1EB02D73626}.png]]

https://andrewlock.net/exploring-dotnet-6-part-2-comparing-webapplicationbuilder-to-the-generic-host/

خوب اینجا نوشته که قبلا فقط مشید برای web/http استفاده بشه ولی تیم .net اومده کاری کرده که از worker service ها بتونیم استفاده کنیم برای message queus و grpc , windows serivce 

این کار با هدف این که web app با قابلیت configureation و loggig و di رو با برنامه هایی با type های دیگه دراه هم بتونیم انجام بدیم 


![[{04BCE564-E63A-4606-B530-DE3E729E08CF}.png]]

https://andrewlock.net/exploring-dotnet-6-part-2-comparing-webapplicationbuilder-to-the-generic-host/

![[{2FB91A21-9909-4808-9BDC-C24D74A0664A}.png]]

![[{5430D2FE-8085-4E60-8783-2CF94850900E}.png]]



![[{EE7EBB0D-D652-41FA-A0D6-8C8AF0CE9FC0}.png]]


![[{7119B74B-6856-45D7-9537-0B694187F8A9}.png]]

![[{CBD0F245-F562-424A-89C6-ED285EB8F3FF}.png]]

![[{FEEBAE53-4C1A-43FF-8580-5F81F96B31F4}.png]]

![[{83741ADB-E354-4BF9-B34C-E77D4CBD3309}.png]]

خوب اینجا توی app setting میبینیم که فرآیند logging به صورت دیفالت تعریف شده و ما برای این که بخوایم از serilog استفاده کنیم میایم این رو پاک میکنیم 
![[{488CC388-C9E9-4877-A85A-7B07AFD6BFBE}.png]]

![[{E0F8AE85-571B-411D-A11B-2BF7B3842D37}.png]]

![[{BFC8AA6A-6A55-4439-8AE5-9F6B8DE56D01}.png]]

![[{0F33D5CD-B1A5-457E-9A91-35271EE21FF3}.png]]

![[{E5C2ACC1-E655-48CC-AD13-7966AB17A503}.png]]


![[{418B2DD3-28D8-44A1-9C41-88A542B3C4D1}.png]]

خوب ما اومدیم اول روی سیستم warning ماکروسافت اومدیم override کردیم اون تنظیماتی رو که میخواستیم و بعد اومدیم تعیین کردیم که کجا save بشه اطلاعاتمون و بعد هم اومدیم گفتیم که میخوایم از seq برای ذخیره سازی اطلاعات استفاده کنیم 

خوب برای استفاده از Seq میریم و دانلودش میکنیم از سایتش فقط این مورد هستش که سایتش از اونور مارو تحریم کرده 


![[{664277DA-5647-4DE2-BE1B-F499DEBAF12F}.png]]

![[{7C128989-266A-4381-808C-84BBBB6703E3}.png]]

![[{2F25AFE6-5FEE-4FF2-89BE-ABCAC145112F}.png]]

![[{80A1F5B7-4835-4563-B156-3F68D412846F}.png]]

خوب ما به طور مثال شاید بخوایم یه مدل customiziation رو انجام بدیم برای نمایش لاگ هامون برای همین میایم از یه middlewate استفاده میکنیم 

![[{670336C6-F713-47D0-A601-981A99BFE06A}.png]]

قبل از useHttpsRedirection میزاریمش 

حالا میریم سراغ data base 

![[{A9ECC6D1-60B3-4111-B9A6-17C2B8501189}.png]]


![[{E9BC9406-CA09-48C3-9FCD-43E96B21E3E4}.png]]

اینجا میتونیم ببینیم که با اون پکیجی که نصب کردیم چه چیزهای دیگه ای باهاش نصب شدن 

![[{BF249DE3-9F95-49F3-96D6-68C0902DF56B}.png]]


خوب حالا اینجا میتونیم تعیین کنیم و بنویسیم که اسم سرورمون چیه 
![[{80304695-19F7-45F3-915D-046309DFB668}.png]]
اگر سرور روی سیستم خودمونه که local میشه اگر روی سیستم دیگه است که ip اش رو میدیم ، اگر توی یه instace دیگه روی سیستمون هست ، اسم اون رو مینویسیم 

![[{FDC3AE05-0E2C-4357-87E7-E469887101D5}.png]]

 خوب اینجا trusted connection رو true گذاشتیم که بگیم connection که داریم مورد اطمینان هستش و مورد بعدی که multipleActiveResultSets هم این قابلیت رو بهمون میده که به صورت همزمان از چند جا به این app وصل بشیم 

خوب حالا ما این رو اینجا تعیین کردیم حالا باید بریم توی program و به برنامه بگیم که از این استفاده کنه برای ef Core 

![[{E7180978-2409-4832-8899-50451985327C}.png]]
خوب اینجا یه var رو تعریف میکنیم و بعد میریم اون connection string رو میاریم و میریزیم داخل متغییر ConnectionString برای این که وقتی که خواستیم از دیتابیس استفاده کنیم این رو بهش بدیم 

بعد اومدیم سرویس AddDbContext رو اضافه کردیم و با استفاده از option بهش گفتیم که داریم از sql server استفاده میکنیم و بعد هم بهش connection string رو دادیم  

![[{BAE7574A-CEA9-42C4-B56D-8E0A764F6DDA}.png]]
خوب اینجا ما اومدیم توی کلاسی که ساختیم توی constructor اش اومدیم از DbContextOption در آرگمان ورودیش استفاده کردیم که اون options که اونجا هستش در حقیقت از همون options که در program نوشتیم داره میاد  

![[{CDAD541D-F1DC-4ABC-8182-2A140606E1DB}.png]]

بعد از این که options رو گرفتیم میاریم پاسش میدیم به base چون context به این option برای initilize شدن به این روش نیاز داره 

خوب بعدش یه کلاس میسازیم و فیلد id رو براش تعیین میکنیم ، وقتی که ef core این پترن رو میبینه متوجه میشه که id فیلدیه PK هست و  auto inctimental هستش  

![[{08684993-A53B-4747-BE3A-54D49EE2D866}.png]]
هم به شکل بالا متوجه میشه و هم به این شکل 
![[{5C602456-CE4B-4541-8308-8671E60279D3}.png]]


![[{516A24FB-A101-41C0-B6D3-DA7F59B681A0}.png]]


![[{C6D5EB6B-BB66-4FB6-864E-C284C654B97B}.png]]

![[{1877ED9B-00BA-43CD-94B6-942B4BA05FB3}.png]]
به هر دو حالت میتونیم بنویسیم ولی مزیت پایینی اینه که دقیقا اسم همون فیلدی رو که میخوایم رو بهمون به شکل string بهمون میده و هر وقت که اسم اون فیلد رو تغییر بدیم بهمون ارور میده ولی در مورد بالایی اینطور نیست و هیچ اروری نمیگیرم و بعدا در برنامه دچار مشکل میشیم 


![[{FF820F0D-8838-41D3-9B6E-706E91D146CF}.png]]

![[{CBF41238-C265-4DCC-9B9C-7770010E0DB7}.png]]

![[{6E734EF8-8FB1-4BF7-BC3A-20B4FCD8617F}.png]]

  

خوب اینجا ما تعیین کردیم که CountryId به عنوان FK و اینجا ef با توجه به convention که هست متوجه میشه که این FK متعلقه به Country چون CountryId نوشتیم Country + Id

 ![[{AB606B1A-542B-4D26-8091-48A756997690}.png]]

![[{75CC9229-696E-4F56-ABB0-46E75EA48F9C}.png]]

و اینجا ما یک ارتباط یک به چند و چند به یک داریم 

خوب حالا بعد از اینها 

![[{41D8BF77-EB79-457F-85FA-D98C126E62AA}.png]]
به ارور این که این فیلدها نمیتونن null باشن برمیخوریم و برای رفع این ارور میایم 

![[{06B5700F-D7E3-412F-B125-C9FBE57F02C8}.png]]
میایم و nullable رو disable میکنیم 

بعد میایم و توی کلاس که رابط با دیتابیسمون رو ساختیم کلاس هایی که میخوایم ازشون استفاده کنیم رو معرفی میکنیم ، اینطوری:
![[{0ADC3D03-E2E4-455D-BE85-DE9B1ECCD49A}.png]]

![[{EDF8279A-F172-41E9-B202-1EC1D19D62A9}.png]]

![[{B770FA17-AF20-4051-AE41-46633AAABBCC}.png]]

خوب اینجا به این ارور برخوردیم وقتی که Add-Migration InitialMigration رو زدیم:

![[{6279A3E1-A3EF-40CD-A644-3873D016D3E8}.png]]

توی خط آخر نکته ای که گفته مشکل ما رو حل میکنه ، این که باید Options رو به base  بدیم 

![[{ECD6557E-29A0-4DC3-B230-7FAE4377DA81}.png]]

خوب اینجا در فایل migration این ها رو میبینیم 

![[{9EB80C27-84E5-4E74-A507-62CE3E2CF3F1}.png]]

به طور مثال میتونیم cascade رو تغییر بدیم ، معنی cascade در اینجا اینه که اگر Hotels رو پاک کنیم دیتاهای County هم پاک میشه 

خوب اینجا یه بخشی داریم به اسم up که یعنی اون کاری که میخوایم انجام بدیم و اعمال کنیم و قسمت down میشه قسمتی که بخوایم undo کنیم تغییراتی که اعمال کردیم 

![[{6A45DB36-9830-4BCC-8DAD-71369B460935}.png]]

![[{D93C743F-A74F-402D-9701-9C0C981621F5}.png]]
![[{8B8B0584-0FB8-42FC-B652-888F3B997653}.png]]
یه راه دیگه هم برای دیدن دیتابیس استفاده از 

![[{64294517-1D2B-4789-AAAE-14C1C93AB70F}.png]]

![[{037A9A90-040A-42BD-BA85-E93BA2E52941} 1.png]]

توی قسمت server مینویسیم localdb/mssqllocaldb 

حالا میخوایم دیتابیسمون رو  seed  کنیم :

![[{D54DC356-D8A2-4B1F-8E9D-66D9ED50A77D}.png]]

![[{B8DF8384-B44B-48E0-9051-41B9DC5EF9B9}.png]]

![[{D3E24E34-533C-429A-89C9-7618267CC425}.png]]

![[{A18E1E82-0DC8-4559-8670-3746F4A49CE2}.png]]

