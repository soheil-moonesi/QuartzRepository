![[{713909F9-2B4B-4E94-8B43-F54A4745DEE6}.png]]

فکر میکنم این مبحث خیلی جالب و کاربردیه پس شروع میکنیم به بررسیش.

بیایم با مثال شروع کنیم :

![[{B4055E1A-31DD-49E1-B639-A1F4CC8FA286}.png]]

حالا این جا خروجی در کنسول به ما نشون میده، خالیه چون اصلا Name در car2 مقدار دهی نشده.

حالا بیایم car1 رو توی car2 قرار بدیم، اینطوری:

![[{F05CE085-4BD6-4F02-89EB-5EC92BCD6492}.png]]

حالا اتفاقی که میوفته اینه که در کنسول Benz نمایش داده میشه.

چرا؟ دلیلش اینه که در اینجا reference متغییر car1 داره توی متغییر car2 قرار میگیره، که این معنی رو میده که هر اتفاق و تغییری که روی car1 انجام بشه، car2 داره بهش اشاره میکنه

خوب حالا برای درک بیشتر بیایم از چند تا عکس مثال استفاده کنیم:

![[{DDE32BA2-1419-4BC4-A8E6-D4316ACDA8DA}.png]]

خوب در رابطه با این عکس بالا باید بگم که این عکس از این [مقاله](https://l.vrgl.ir/r?ad=1&l=https%3A%2F%2Fwww.codeproject.com%2FArticles%2F1263638%2FA-Re-Introduction-to-Csharp-References-Post-Csharp%23fromHistory&si=ohlramolbje2&st=post&k=xQGmFyE7YxwoL3vi2FvJL3dzrQh03GfdgOezIpkcqGA%3D) در سال 2018 بهترین مقاله توی اون سایت تشخیص داده شده ، ترجمه تحت الفظی شده. فقط نکته ای که هست یکی از نفراتی که عضو این سایت بوده اومده یه اشکال به این عکس گرفته که دلیلش رو در حال متوجه نشدم ولی اینجا گذاشتمش:

In your diagram you show "dynamic" as a type but it isn't. "dynamic" is just an indication to the compiler to generate dynamic code. This is best demonstrated by creating a class with a dynamic field and then using reflection. The field will be found to be of type System.Object.

که بعدا راجع بهش تحقیق کنم که dynamic دقیقا چیه . ممکنه بگید که چرا از نوشته که سال 2018 نوشته شده استفاده کردم، خوب به نظرم این بود که خیلی خوب و با حوصله وقت گذاشته بود و تصاویر و شکل های خوبی رو گذاشته بود و مورد بعدی این که به نظرم مفاهیم اصلی و کلی C# خیلی تغییر نکردند.

Primitive types are those, which the compiler supports directly, along with a range of operators and casting between them. They map to framework types, e.g.:

- `int` maps to `System.Int32`
- `float` maps to `System.Single`

#### خوب primitive type ها چی هستن؟ type هایی هستن که خود کامپایلر مستقیم پشتیبانیشون میکنه به همراه عملگرهاشون و عملیات casting بینشون. مثل int , float و ...

حالا میخوایم value type ها رو بررسی کنیم

![[{91082F40-F064-4BF5-8979-D768D224E044}.png]]

If you edit the copy made of a file, the changes do not affect the original file.

توی value type ها اگر ما روی نسخه ای که copy شده تغییرات اعمال کنیم ، این تغییرات روی نسخه ی اصلی اعمال نمیشه.

ایجا اتفاقی که افتاده اول اومدیم مقدار orginalint رو که 0 هست ریختیم توی متغییر copiedint خوب واضح هستش که وقتی که کنسول بگیریم هر دو مقدارشون 0 هستش

در مرحله بعد میایم به copiedint مقدار 500 رو اضافه میکنیم ، خوب اینجا اتفاقی که میوفته اینه که فقط متغییر copiedint مقدارش تغییر میکنه و orginalint هیچ تغییری نمیکنه و همچنان مقدارش 0 باقی میمونه


![[{377ED19D-B060-4B9A-BB90-91879BEF6D54}.png]]

نکته»

- The ‘`value`’ stored in a value type is the actual data.
- The default behaviour passing it around, is that we are making copies of this value.
- They support interfaces but there is no inheritance.

مقدار value که در value type هستند مقادیر واقعی هستند (جلوتر واضح تر میشه این تعریف)

وقتی که داریم از value type ها استفاده میکنیم و مقادیرشون رو توی متغییر دیگه قرار میدیم به این معنیه که مقدارشون کپی کردیم و ریختیم داخل متغییر جدید.

خوب value type ها interface ها رو پشتیبانی میکنن ولی ارث بری رو خیر.

حالا میرسیم به reference type ها :

![[{9118CF9D-3BCA-4B9D-A1E4-61532EF2AB33}.png]]

خوب در نظر بگیرید که ما یه لینکی که مرتبط با یه فایل هستش رو برای تام و کیت میفرستیم، بعد تام روی اون لینکه میزنه و میره داخلش و فایل رو تغییر میده ، بعد کیت میزنه روی لینک و شروع میکنه به خوندن فایل و اونجا تغییراتی که تام داده رو میبینه .

**A reference type still has a value – it’s just that the ‘value’ is a memory location where the actual data is.**

**خوب refernce type ها هم value دارن داخلشون ولی value که دارن آدرسیه که داره به یه قسمتی از حافظه داره اشاره میکنه که توی اون آدرس دیتا اصلی وجود داره ، خیلی باحال توضحیش داده .**

![[{455831B5-40D0-4A9D-B9F6-8B8B6ACFEFC4}.png]]

![[{60276A9B-B034-4604-ADE6-A53496C3210F}.png]]

خوب همونطوری که میبینید اینجا یک کلاس simpleObject تعریف کردیم با یک پراپرتی Number که بعد اومدیم موقعی که ازش نمونه میسازیم مقدارش رو 100 گذاشتیم و ریختیم داخل orginal ، بعد اومدیم orginal رو ریختیم توی copied ، در مرحله بعد اومدیم مقدار داخل کپی رو 500 تا افزایش دادیم، خوب اینجا اتفاقی که میوفته اینه که حالا هر دو مقدار orginal و کپی هر دو مقدار 600 رو نشون میدن چون هر دو دارن به یک آدرس از حافظه اشاره میکنن و وقتی که مقدار داخل اون آدرس هست تغییر میکنه ، هر دو همون رو نشون میدن.

حالا میخوایم این مثال رو بررسی کنیم

![[{2BD836BA-EF5B-413C-82ED-0ADC566E33A5}.png]]

حالا ممکنه بگید عه چرا پس اینجا مقدار orginal با copied فرق داره، یکیشون شده 300 اون یکیشون شده 100 ، خوب ببینید برای توضیحش از یه عکس دیگه استفاده میکنیم:

![[{230F8EBD-02A2-4D6E-B375-22778AC5AF9F}.png]]

خوب حالا در نظر بگیرید که این سری یه لینک برای تام و کیت فرستادیم که توش فایل با مقدار 100 هستش، خوب حالا تام از این فایل که مقدارش 100 هستش خوشش نمیاد و حال نمیکنه ، بعدش میاد یه فایل جدید درست میکنه با مقدار 300 و لینک اولی رو که گرفته بود رو هم تغییر میده به این فایل کپی جدید که خودش درست کرده ، ولی لینکی که برای کیت فرستادیم همچنان همونه و کیت همون فایل مقدار 100 رو میبینه .

![[{ECD441AC-AB2B-4028-B46B-E399A16DB058}.png]]

حالا بخوایم همین رو از روی کد هم توضیح بدیم اینجوری میشه که ما اول یه نمونه از simpleObject با مقدار 100 ساختیم و آدرسش رو در orginal گذاشتیم (فرض کنید که آدرس نمونه ساخته شده 1000 هستش و آدرس orginal هستش 1004 .

و بعد آدرسی که در orginal هستش که میشه 1000 رو در copied قرار دادیم(فرض کنید که آدرس copid هستش 1018) که این به این معنی هستش که در این حالت هر دو دارن به یک آدرس حافظه که توش مقدار 100 هست دارن اشاره میکنن.

خوب حالا مرحله ی بعد میایم یه نسخه دیگه از simpleObject رو با مقدار 300 میسازیم که به طور مثال در نظر بگیرید آدرسش 1008 هستش رو میریزیم داخل متغییر Orginal با آدرس 1004 این یعنی که آدرس جدیدی که داره بهش اشاره میکنه به مقدار 300 رو جایگزین آدرسی که داشت اشاره میکرد به مقدار 100 کردیم. یعنی 1008 رو جایگزین 1000 کردیم.

، حالا چه اتفاقی سره copied میوفته ، خوب طیبعتا copied همچنان داخلش اون آدرسی هستش که داره به مقدار 100 اشاره میکنه یعنی 1000 ، پس همچنان مقدارش 100 میمونه .

امیدوارم که تونسته باشم درست بفهمم و درست مطلب رو نوشته باشم.

Passing to a Method by Value

خوب حالا میرسیم به مبحث پاس دادن value به یک متد

private static void One(int[] intArray)

این که واضح هستش

حالا میرسیم به قسمتی که میخوایم به متد یه رفرنس بفرسیتم :

![[{8913342B-B76E-435F-A800-62CE5A86215D}.png]]

خوب همونطوری که میبینید اینجا اومدیم مقدار i رو با رفرنسش فرستادیم توی متد ChangeNumber و بعد مقدارش رو به 2 عوض کردیم، حالا اتفاقی که میوفته اینه که وقتی که میخوایم توی کنسول چاپش کنیم مقدار 2 رو نشون میده.

بزارید اینجوری توضیحش بدیم: وقتی که ref i مینویسیم همون موقع میاد یک قسمت جدید حافظه در stack درست میشه و مقدار int i =1 یعنی 1 رو برمیداره کپی میکنه و میریزه توی ref i و اگر عملیات ریاضی رو هم روی این متغییر انجام بدیم هیچ تاثیری روی int i نمیزاره چون محل ذخیره سازیشون در حافظه متفاوت هست.

#### Behaviour with Value types

If you pass a value type by reference, there is no copying and the called method is able to make changes to the data, which will be visible to the caller.

خوب نکته ای که وجود داره اینه که ما int رو که یه Value type هستش رو با رفرنس میفرستیم دیگه خبری از کپی کردن نیستش و متدی که کالش کردیم میتونه اون دیتا رو تغییر بده ، اگر ما اینجا از ref استفاده نکنیم مقداری که در کنسول چاپ میشه 1 هستش.

**Misconception**: Passing a value type by reference causes boxing to occur. **Wrong!** Boxing occurs when you convert a value type to a reference type. Passing a value type by reference simply creates an alias, meaning we’d have two variables representing the same memory location.

کژ فهمی: آیا وقتی که یه value type رو با refrence میفرستیم باعث میشه boxing اتفاق بیوفته؟ غلطه

خوب حالا سوالی که هست اینه اصلا boxing چیه؟ boxing زمانی اتفاق میوفته که ما میخوایم یه value type رو به یک refrence type تبدیل کنیم.

وقتی که ما یه Value type رو با رفرنس میفرستیم باعث میشه alias میشه که معنیش میشه این که دو تا متغییر نشان دهنده یه قسمت مشخص و یکسان از حافظه هستند.

Behaviour with Reference Types

حالا در نظر بگیرید که به جای value type ها میخوایم با refrence type ها این کار ها رو بکنیم. یعنی یه refrence type رو با ref بفرستیم داخل متد.

![[{13AE9C5F-975F-4939-8EFF-7451D1AC889C}.png]]

مثل همیشه بیایم با این عکس توضیح این کد رو بدیم:

![[{13208022-9342-421D-AB68-F36A497E40AA}.png]]

خوب توضیح عکس اینه که به جای این که لینک رو مستقیم بفرستیم به تام و کیت ، میایم لینک رو میزاریم توی یه صفحه وب و بهشون آدرس وب رو میدیم. بعدش کیت وارد سایت میشه میزنه رو لینک و فایل رو میبینه ، بعد اونموق چون میدونه تام همچین مقداری رو نمیخواد (مثلا) میاد مقدار رو به 300 تغییر میده و بعد لینک قبلی رو پاک میکنه و لینک جدید رو برای دسترسی به فایل جدید جایگزین میکنه. در مرحله بعد تام صفحه وب سایت رو باز میکنه و میزنه روی اون لینک و مقدار رو میبینه . این سری ما لینک رو نیومدیم کپی کنیم، بلکه اومدیم دسترسی به اون فایل رو لینکش رو share کردیم.

Instead of passing Tom and Kate copies of my link, I gave them access to the link itself. So as before, they both see changes to the file; but now also, if one of them changes the link to a new file, they both see that too.

این سری به جای این که کپی لینک ها رو برای کیت و تام بفرستیم اومدیم خوده لینک رو بهشون دادیم و هر کدومشون که روش تغییری ایجاد کنن اون یکی هم میبینه.

So, using the `ref` keyword is kind of telling the compiler not to dereference / fetch the data from the memory location, but instead, pass the address itself, analogous to creating an alias.

استفاده کردن از ref رو ایجوری میشه معنی کرد که به کامپایلر بگیم که که دیتا رو از memory نیاره، و بیاد فقط اون آدرس که توی متغییر هست رو برداره.

حالا بیاید این رو توی کدی که بالاتر نوشته شده توضیح بدیم. خوب اولش میایم یه نمونه از simpleObject میسازم و آدرس حافظه که اطلاعات درونش ساخته شده رو داخل orginal قرارش میدیم. حالا مرحله بعد میایم مقدار خوده orginal رو برمیداریم و میزاریم داخل copied حالا این به چه معنیه یعنی این که copied تبدیل میشه به یک اشاره گر به orginal

مرحله بعدی میایم یه نمونه جدید درست میکنیم با مقدار 300 که یک آدرس جدید داره و بعد این آدرس جدید رو میریزیم توی copied و این تغییر بر روی orginal هم اعمال میشه

هر اتفاقی که داخل خوده orginal بیوفته و هر تغییر آدرسی که داخلش اتفاق بیوفته رو copied هم اعمال میشه و بلعکس، اگر ما تغییری در copied ایجاد کنیم یعنی مستقیما روی orginal تغییر ایجاد کردیم.

نکته ای که وجود داره اینه که اگر در اون آدرسی که هر دو اینها دارن اشاره میکنن تغییری در اون آدرس حافظه ای که این دو دارن اشاره میکنن، اتفاق بیوفته ، اون دو تا میبینند.

out (C# Reference)

You can use the out keyword in two contexts:

As a parameter modifier, which lets you pass an argument to a method by reference rather than by value.

In generic type parameter declarations for interfaces and delegates, which specifies that a type parameter is covariant.

از استادم آقای عمران صادقی هم تشکر میکنم به خاطر تدریس عالی که داشتن.