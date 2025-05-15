در wb میادبرای اجرا اون فایل یه dll میسازه روی سیستم و بعد بازش میکنه ، مشکلش اینه که در مرورگرهای قدیمی ساپورتتت نمیشه wb و این که ما در این جا لاجیک رو کاملا با front داریم یعنی به خاطر وجود view model و امکانات دیگه کاملا میتونیم اجرایی کنیم front 

اینجا front و back از هم جدا نیستن 

![[Pasted image 20250508175829.png]]

![[Pasted image 20250508175922.png]]

![[Pasted image 20250508180036.png]]

![[Pasted image 20250508180107.png]]


![[Pasted image 20250508183458.png]]



![[Pasted image 20250508183703.png]]

![[Pasted image 20250508183759.png]]
هم server side رو support میکنه هم client side رو 

![[Pasted image 20250508183854.png]]

اینجا توی این گزینه ها اومده هر side رو جدا کرده 

برای این که یه app server side بسازیم میایم از این template استفاده میکنیم :
چون که این template جدیده و اینطوری پروژه توسط net 8 و ورژن های بالاتر میشه ازش استفاده کرده 

![[Pasted image 20250508185407.png]]

![[Pasted image 20250508185432.png]]

حالا میایم کنار این پروژه blazor web assembly رو هم میزاریم :

![[Pasted image 20250508185515.png]]


![[Pasted image 20250508185533.png]]

![[Pasted image 20250508185551.png]]

تفاوت این دو تا :
![[Pasted image 20250508185637.png]]


![[Pasted image 20250508185649.png]]
خوب توی blzaor server دیگه index.html رو نداریم 

![[Pasted image 20250508185742.png]]

این فایل مسئول دانلود که application هستش در WB

حالا توی server 
![[Pasted image 20250508185908.png]]
اینجا میاد websocket client برای برقرای ارتباط بین client و server هست انجام میشه 

![[Pasted image 20250508190017.png]]
![[Pasted image 20250508190026.png]]

این یعنی این که ما میتونیم از template که توی یه پروژه دیگه استفاده کردیم ببریمش در یه پروژه دیگه هم ازش استفاده کنیم 

توی WB میاد یه فایل با حجم بیشتر رو دانلود میکنه و بعد برای اجراهای بعدی که سریعتر صفحه رو لود کنه میاد اون رو cache میکنه 

![[Pasted image 20250508190438.png]]

خوب توی lunchsetting میاد debuggin tools که موجود هستش رو نشون میده :

![[Pasted image 20250508191056.png]]
![[Pasted image 20250508191141.png]]
خوب IIS هم هستش ، درسته که توی تنظیمات نیستش ، ولی وقتی که روش میزنیم یه سری تنظیمات دیگه براش ایجاد میشه 

![[Pasted image 20250508191300.png]]


![[Pasted image 20250508191714.png]]
https://dotnettutorials.net/lesson/asp-net-core-launchsettings-json-file/


خوب inspectURL برای inspect کردن پروژه 

![[Pasted image 20250508191951.png]]

خوب اینجا توی خط اول داریم مسیر ارتباط client رو تعیین میکنیم و در default layout هم داریم تعیین میکنیم که layout مون چیه 

کلا router component ها وظیفه شون اینه که درخواست رو بگیرن و اون صفحه ای که درست هستش رو برای نمایش بیارن 

![[Pasted image 20250508192259.png]]
اینجا میایم dependecy ها پروژه رو مینویسیم که توی پروژه ازشون استفاده کنیم مثل این مورد :

![[Pasted image 20250508192422.png]]

خوب حالا بیایم main layout رو بررسی کنیم :

![[Pasted image 20250508192557.png]]
حالا توی main layout که میریم اونجا نوشته که از layout component base داره ارث بری میکنه 
و توی این فایل Nav menu و body داخلشه 

خوب حالا توی قسمت wwroot تمامی فایل های static پروژه مون توش هستش که مهمترینش index.html هستش 

![[Pasted image 20250508200342.png]]
این خط قابلیت این رو به ما میده که head component های html رو ادیت کنیم که این قضیه شامل Page title و  meta element ها میشه 

![[Pasted image 20250508200630.png]]

![[Pasted image 20250508200716.png]]


![[Pasted image 20250508200851.png]]

![[Pasted image 20250508200839.png]]

اینجا navigation route برای بهتر کردن مسیر یابی و ارتباطشون با role ها 

![[Pasted image 20250508202830.png]]

به طور مثال وقتی که تعداد اون counter تغییر میکنه یه بار دیگه render میشه و تعداد جدید رو نشون میده 

![[Pasted image 20250508202957.png]]

اینجا به جای ul اومدیم از nav استفاده کردیم 

![[Pasted image 20250508205333.png]]

تغییر میدیمش به :
![[Pasted image 20250508205426.png]]
![[Pasted image 20250508205452.png]]

![[Pasted image 20250508205512.png]]

بعد چون پوشه layout رو پاک کردیم و محتواش رو ریختیم توی shared اومدیم اینجا import اش کردیم 

بعد میایم یه فولدر به اسم component میسازیم و بعد میایم یه razor page توش میسازیم :

![[Pasted image 20250508210455.png]]


![[Pasted image 20250508210547.png]]

![[Pasted image 20250509005656.png]]


![[Pasted image 20250509005745.png]]

![[Pasted image 20250509005840.png]]


![[Pasted image 20250509005919.png]]


![[Pasted image 20250509005940.png]]

پاک کردن تنظیمات IIS 

![[Pasted image 20250509010025.png]]

قسمت 10 ببینم

![[Pasted image 20250510173715.png]]

اینطوری میتونیم به صورت یک طرفه دیتا بفرستیم یا مثلا razor page بفرستیم اینجا چیزی که داریم component parameter هستش 

این کار رو با استفاده از routing parameter داریم انجام میدیم 

حالا برای این که از این component که داریم ازش استفاده کنیم میایم و index رو ادیت میکنیم و بهش title رو اضافه میکنیم ، اینطوری :

![[Pasted image 20250510172811.png]]

![[Pasted image 20250510172833.png]]

![[Pasted image 20250510172844.png]]

خوب اینجا هم اومده یه صفحه تعریف کرده برای counter print بعد اومده به جای این که title رو به صورت hard code بزنه براش parameter تعیین کرده 
![[Pasted image 20250510173032.png]]

بعد اومده توی صفحه پدر که میشه counter از اون صفحه counter print استفاده کرده و اومده توی صفحه والد یا پدر به title هم مقدار داده 

![[Pasted image 20250510173109.png]]
حالا ما میخوایم وقتی که یه صفحه داریم میسازیم و داریم از component child داریم استفاده میکنیم میخوایم بهمون یه warning بده که این پارامتری که داخل اون child هستش نیاز داره که مقدار دهی بشه ، و برای این کار میایم از این راه استفاده میکنیم :

![[Pasted image 20250510174912.png]]

![[Pasted image 20250510174941.png]]

اینجا هم داره warning میده که اره این title اینجا مقدار دهی بشه 

arbitary paramiter

![[Pasted image 20250510175121.png]]

خوب حالا میخوایم کاری کنیم که هم بشه عکس رو عوض کرد و هم متن رو ، برای این کار میایم این کار رو میکنیم :

![[Pasted image 20250510175350.png]]
اینطوری میایم ازش استفاده میکنیم :
![[Pasted image 20250510175427.png]]


بعد برای این که dynamic بودنش رو تست کنیم :
![[Pasted image 20250510175629.png]]

خوب cascading paramiter 

یه موقع هایی میخوایم که از parent component یه مقدار یا چیزی رو بفرستیم به تمام child component 
دو راه داره با name و با type 

![[Pasted image 20250510180004.png]]

![[Pasted image 20250510180057.png]]

![[Pasted image 20250510180216.png]]

خوب توی تصویر بالا ما یه مورد داریم که اون رو هم تعریف کردیم که این مقدارش رو دریافت میکنه از سمت parnet به صورت cascade 

حالا اگر چند تا مورد رو بخوایم از سمت parent بفرستیم ، باید یه obj بفرستیم و اسمش by type فرستادنه که یه سری شرط داره 

اول این که attribute که لازمه داشته باشه اینه که cascading parameter رو داشته باشه و بعد این که set باید داشته باشه :
![[Pasted image 20250510180510.png]]
باید public باشه و بعد این که از همون نوعی باشه که در parent هست :

![[Pasted image 20250510180646.png]]

حالا یه راه دیگه اش ارسال با name هستش : توی cascading value ما اومدیم نوشتیم name و بعد اون اسم رو تعیین کردیم heading color 

![[Pasted image 20250510180832.png]]

![[Pasted image 20250510180949.png]]


![[Pasted image 20250510181002.png]]

خوب میرسیم به قسمت Debugging 

![[Pasted image 20250510184058.png]]

این خط کد بالا داره به برنامه این رو میگه که این پروژه از نوع wb و blazor هستش و میاد browser رو به debugger مون وصل میکنه 

![[Pasted image 20250510184722.png]]

![[Pasted image 20250510184751.png]]

![[Pasted image 20250510184822.png]]


بعد میریم توی brower و میزنیم روی source 
![[Pasted image 20250510184945.png]]


![[Pasted image 20250510185014.png]]

![[Pasted image 20250510185228.png]]

خوب یه چیزی داریم به اسم partial class که میاد لاجیکمون رو از html جدا میکنه 
خوب میایم یه فایل به اسم home.razor.cs درست میکنیم که اتوماتیک تشخیص داده میشه 
![[Pasted image 20250510210008.png]]

![[Pasted image 20250510210016.png]]

![[Pasted image 20250510210104.png]]
اگر خواستیم چند تا هم کلاس partial داشته باشیم این کار رو با naming اش انجام میدیم 
![[Pasted image 20250510210159.png]]
میرسیم به قسمت render fragment 

![[Pasted image 20250510210358.png]]

![[Pasted image 20250510210425.png]]

![[Pasted image 20250510210628.png]]

حالا میایم اسم دلخواهمون رو میزاریم 

![[Pasted image 20250510210851.png]]

![[Pasted image 20250510210906.png]]

![[Pasted image 20250510210932.png]]

خوب میرسیم به life cycle ها که برای استفاده ازشون میایم و override اشون میکنیم 
اگر Action مون Async هستش میایم از life cycle async استفاده میکنیم 




![[Pasted image 20250514154008.png]]

![[Pasted image 20250514154557.png]]

https://blazorschool.com/tutorial/blazor-wasm/dotnet6/component-lifecycle-527158

![[Pasted image 20250514154038.png]]


![[Pasted image 20250510221922.png]]

قسمت 19

![[Pasted image 20250512175439.png]]


![[Pasted image 20250512175525.png]]


![[Pasted image 20250512175609.png]]

![[Pasted image 20250512175631.png]]

![[Pasted image 20250512175640.png]]

وقتی که رو counter میزنیم :
![[Pasted image 20250512175733.png]]

حالا میایم تغییر ایجاد میکنیم :

![[Pasted image 20250512175759.png]]

![[Pasted image 20250512175816.png]]

![[Pasted image 20250512175825.png]]

آپدیت ui انجام نمیشه 

![[Pasted image 20250512175940.png]]


![[Pasted image 20250512175955.png]]

![[Pasted image 20250512180341.png]]

وقتی که برمیگردیم توی home 
![[Pasted image 20250512180409.png]]

خوب حالا برای logging اول میایم اون رو پروژه اضافه میکنیم :

![[Pasted image 20250512180835.png]]

![[Pasted image 20250512180857.png]]



![[Pasted image 20250512180942.png]]


![[Pasted image 20250512180957.png]]

![[Pasted image 20250512181045.png]]


![[Pasted image 20250512181114.png]]


![[Pasted image 20250512181200.png]]



![[Pasted image 20250512181212.png]]

خوب بعدش میایم برای این که همه ی ارور ها رو بهمون نشون بده ، سطح defualt logging رو عوض میکنیم :
![[Pasted image 20250512181319.png]]

![[Pasted image 20250512181407.png]]

خوب حالا بعدش میایم توی کد هر جا که console log استفاده کردیم میایم اون رو با logger log عوض میکنیم 

![[Pasted image 20250512181524.png]]

![[Pasted image 20250512181618.png]]

خوب حالا میخوایم سطح بعدی این log ها رو ببریم توی appsetting که بعدا هر موقع که خواستیم بیایم و عوضش کنیم ، میایم و توی wwwroot این کار رو انجام میدیم 

![[Pasted image 20250512181741.png]]

![[Pasted image 20250512181822.png]]


![[Pasted image 20250512181838.png]]


![[Pasted image 20250512181904.png]]


```
Severity Code Description Project File Line Suppression State Error (active) CS0246 The type or namespace name 'EventConsole' could not be found (are you missing a using directive or an assembly reference?) BlazorAppFront C:\Web\Soheil\LinkMeetShareProject\BlazorAppFront\Pages\Home.razor 62
```


برای رفع ارور بالا میگه که باید یه چیزی رو دانلود کنید که توی پکیج RADZEN نیست و میریم از روی گیت هابش دانلود میکنیم میزاریمش توی پروژه 

![[Pasted image 20250514160208.png]]

https://forum.radzen.com/t/eventconsole-cs0246-error/9801/4