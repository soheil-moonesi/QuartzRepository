
![[{920EA970-C443-4FEB-882A-5BBD2A2187AF}.png]]

فکر میکنم برای توضیح کلاس میشه این رو گفت که میاد یک ذهنیتی رو از یک شی تعریف میکنه

مثلا توی همین عکس بالا کلاس ماشین یک کلیت و یک ذهنیت از یک ماشین رو داره بهمون نشون میده.

خوب حالا وقتی که بخوایم از این کلاس (ذهنیت یا تعریف ) بخوایم یه شی بسازیم - یعنی بخوایم یه ماشین( یا همون object) بسازیم ، باید بیایم ازش یک instance یا نمونه درست کنیم که توی C# برای این کار از New استفاده میکنیم

این شکلی:

به صورت کلی با نوشتن ()new Car

از کلاس نمونه درست کردیم ولی خوب این نمونه رو باید توی یه متغییری بریزیم که بتونیم باهاش کار کنیم و ازش استفاده کنیم

Car car = new();

Car car = new Car();

حالا یه نکته ای رو که باید در نظر بگیریم اینه که اینجا Car اولی از سمت چپ خودش یه نوع type داده است که خودمون درستش کردیم و بعدش هم که اسم متغییر هست که قراره instance کلاس Car داخلش قرار بگیره.  

حالا یه نکته ای که باید در نظر بگیرید اینه که تا قبل از این که بیایم از کلاسمون instance بگیریم هیچ فضایی رو در مموری اشغال نمیکنه (چون فقط یه ذهنیته) . وقتی که ازش instance گرفتیم میاد در مموری قرار میگیره(چون تبدیل میشه به یک object یا شی) .

مواردی که در کلاس قرار میگیره ایناست:

fields - میزان سوخت

properties - رنگ ماشین

methods - حرکت ماشین - تبدیل سوخت به حرکت

nested classes

حالا نکته ای که هست اینه که یه سری از ویژگی ها میتونن قابل تغییر باشن یه سری هم غیر قابل تغییر اند.

که برای توضیح این موضوع به این نوشته مراجعه کنید.

وقتی که متغییر یا همون filed رو در بالاترین نقطه کلاس قرار بدیم، همه میتونن بهش دسترسی پیدا کنن.


![[{0CD8755B-3365-4387-9AA6-872FB9F16206}.png]]

ایجا همونطور که میبینید اومدیم یه کلاس car تعریف کردیم و داخلش اومدیم یک filed یا همون متغییر رنگ رو تعریف کردیم و بعد برای مقدار پیش فرض رنگ قرمز رو گذاشتیم. ولی دقت کنید که ایجا نوع دسترسی private هستش و این یعنی از خارج کلاس نمشه به این متغییر دسترسی پیدا کرد.

مهم: فیلد ها رو camelCase اسم گذاری میکنیم.

حالا برای این که کلاس ها رو بیشتر بررسی کنیم میایم یه مثال مینویسیم:

اول میایم یه پروژه درست میکنیم به اسم Project

![[{F3C0781E-2A61-4985-AEC3-CD6B479D2C73}.png]]

بعد برای درست کردن کلاس

solution explorer > Project > Add > New Item > Class

بعد میایم یه کلاس Car درست میکنیم:

![[{D494B01C-4930-4A5A-81A9-583F68B3A0E6}.png]]

خوب حالا باید برای استفاده کردن از کلاس کار بیایم ازش یه نمونه درست کنیم:

Car car = new Car();

![[{8A27996F-D5CF-4775-A9D0-6219E35FE73C}.png]]

خوب همونطوری که میبینید فقط متغییر که نوع دسترسیش public بود رو میتونیم ازش استفاده کنیم.

1 و 2 و 3 هم اطلاعاتی هستش که راجع به isLock داره به ما میده که اولی داره میگه که field هستش و بعد تایپش bool هستش و در کلاس car

حالا اگر بخوایم به متغییر name که private تعریف شده دسترسی پیدا کنیم با این ارور مواجه میشیم:

Error CS0122 'Car.name' is inaccessible due to its protection level

نکته ای که وجود داره اینه که ما میتونیم با new هر چند تا که بخوایم از کلاس car نمونه درست کنیم یعنی میتونیم ماشین 1 ، ماشین 2 و ... رو بسازیم. (تنها لیمیت که داریم لیمیت مموری هستش)

حالا به طور مثال اومدیم متغییر speed رو هم public کردیم و این جا سرعت ماشین اولی رو به 120 تغییر دادیم و secondCar رو سرعتش رو به 80 تغییر دادیم.

![[{4180E3D1-7F05-484E-9166-95F49F432219}.png]]

حالا میرسیم به قسمت method یا فانکشن یا همون تابع : که تعریف یک رفتار در یک کلاس هستش. مثلا افزایش سرعت.  
یه سری موارد هستش که همین اول بدونیم بهتره. مثل این که ما از متد ها استفاده میکنیم برای این که بیایم یه بار یه کدی رو بنویسیم و بعدا بتونیم چندین بار ازش استفاده کنیم.

متد ها قابلیت این رو دارن که که یه سری دیتا واردشون کنیم که بهشون میگن پارامتر.

متد ها رو فقط زمانی که call میکنید اجرا میشن.

وقتی که از void در تابع ها استفاده میکنیم به این معنیه که این تابع هیچ خروجی نداره

public void myMethod();

زمانی که تابعی که نوشتیم خروجی داشته باشه باید بیایم تایپ نوع خروجی رو براش تعریف کنیم به طور مثال :

برای تابع

f(x) = x + 5;

![[{0B84BE32-F27D-4CF9-A621-520A434ABD53}.png]]

توی حالتی که خروجی برای تابع تعریف کردیم حتما باید داخلش حداقل یک پارامتر رو return کنیم.

متد ها رو با PascalCase اسم گذاری میکنیم.

خوب حالا میخوایم یه مثال هم از متد داشته باشیم

حالا میخوام توی کلاس Car بیایم یه متد تعریف کنیم :


![[{C00BC05D-305F-4150-BA6C-57ADF6310371}.png]]

حالا میتونیم از این متد چندین بار استفاده کنیم به این صورت


![[{5A1643E4-01AB-43CF-9D79-2A6174A0AEB1}.png]]

حالا یه مرحله میریم جلوتر و یه متد دیگه به اسم IncSpeed تعریف میکنیم که سرعت ماشین رو 20 تا بیشتر میکنه :

![[{BA4FB273-7FFC-4154-A85B-27A497AB5A1A}.png]]

برای دیدن تغییرات speed میایم در کد یه breaking point تعریف میکنیم و در حالت debug کد رو اجرا میکنیم که به تمام متغییرهای فرآیند دسترسی داشته باشیم و ببینیمشون.

![[{8423D5A8-ECDF-4883-9EA2-0D92114E65DD}.png]]

خوب همونطور که میبینید بعد از اجرا شدن IncSpeed سرعت ماشین از 5 به 25 تغییر کرد.

نکته جانبی: عکسی که میبینید از برنامه rider هستش که خیلی حجمش کمتره برای دانلود و اجرا. روی سیستم هایی که سخت افزار ضعیف تری دارند بهتر عمل میکنند.

با shortcut F12 میتونیم برسیم به مرجع اون متغییر یا متد یا هر چیزی که روش کلیک کنیم

go to defination

حالا میخوایم این قابلیت رو ایجاد کنیم که مقدار افزایش سرعت رو خودمون تعیین کنیم. برای این کار باید برای تابع IncSpeed یک پارامتر ورودی تعیین کنیم به این شکل:

![[{004B3753-2E42-431E-B213-5B1FF9B10F92}.png]]

یه مورد دیگه اینه که ما میتونیم به متدمون چندین تا پارامتر ورودی بدهیم.

![[{F1552AD2-1AC8-4E1E-88A1-31B5A02307AA}.png]]

حالا برای استفاده کردن ازش باید به این شکل نوشت:
![[{1E757050-7A2A-4E0C-A97B-21615016EF0C}.png]]
مورد جالبی که وجود داره اینه که فانکشن ها یا متد ها به شکل یک مکعب بنفش نشون داده میشن

کلاس ها هم با رنگ سبز نشون داده میشن

حالا باز هم میخوایم یه مثال دیگه با یه ساختار دیگه تعریف کنیم :

![[{8CBD5701-5EC5-49D8-A7B0-6E88929C4BF5}.png]]

حالا یه کلاس جدید به اسم MyClass میسازیم:

![[{5DF70F19-B4AB-4C19-85E9-36DF635FC605}.png]]

حالا اینجا که میخوایم چند تا نکته در دل این این مثال بگیم، یکیش این که ما میتونیم به متغییر های ورودی متد ها یک مقدار پیش فرض بدیم، اینجوری:

public void MyMethod1(string name,string lastName='rezayi')

این جا برای lastName اومدیم مقدار پیش فرض rezayi رو وارد کردیم، یعنی این که اگر کسی فامیلیشو وارد نکنه به صورت پیش فرض ما فامیلیشو rezayi در نظر میگریم

MyMethod1('soheil');

یعنی نتیجه این متد این شکلی میشه:

soheil rezayi

حالا نکاتی که باید اینجا در نظر داشته باشیم اینه که همیشه متغییر هایی رو که میخوایم بهشون مقدار پیش فرض بدیم باید آخر باشن یعنی توی این مثال نمیتونیم اینطوری بنویسیم:

public void MyMethod1(string name='reza',string lastName)

نمیتونیم مقدار اولیه رو با پیش فرض و مقدار دومی رو بدون پیش فرض در نظر بگیریم.

حالا برای این که بخوایم name هم مقدار پیش فرض بگیره باید برای lastName هم مقدار پیش فرض در نظر بگیریم،

public void MyMethod1(string name='reza',string lastName='rezayi')


![[{023EE3AF-0839-46DE-A5FD-82386183DFB6}.png]]

یه نکته ی دیگه ای که هست اینه که حالا اگر توی این حالت بیایم اسم سبحان رو بنویسیم

MyMethod1('sobhan')

سبحان میاد روی name که از قبل reza بود overwrite میشه و نتیجه میشه :

sobhan rezayi

خوب حالا همونطوری که میبینید برای MyMethod1 مقادیر پیش فرض رو داره بهمون داخل براکت نشون میده [ ] .

باز هم نکته: میتونیم وقتی که داریم متغییر ها رو مینویسیم عنوانش رو هم بنویسیم تا از تداخل های احتمالی جلوگیری کنیم، به طور مثال این جا اومدیم فقط به متغییر lastName مقدار دادیم و name رو به پیش فرض در نظر گرفتیم.

MyMethod1(lastName= ' majidi ' )

reza majidi

مطالب نوشته شده، برداشت من از کلاس C# استاد عمران صادقی هستش. خیلی ممنونم از ایشون به خاطر تدریس عالی که داشتند.

[[C Sharp]]