خوب حالا میرسیم به قسمت های خیلی جالب C#

ببینید قبل این که برسیم به این که get و set چی هه؟ باید یه سری چیزهایی دیگه رو بگم که اصلا فلسفه ی وجودی get و set از کجا اومده.

بیاید از این جا شروع کنیم، میخوایم یه پروژه بنویسیم و توی اون پروژه یه کلاس به اسم person درست کنیم و بعدش توی اون کلاس یه متغییر Age داریم.

حالا میخوایم یه شرطی بزاریم که کاربر موقعی که Age یا همون سن خودش رو وارد کرد این متغییر چک بشه

به طور مثال سنی که وارد میکنه بین اعداد 1 تا 120 باشه.

خوب برای این که بخوایم این موضوع رو چک کنیم باید چی کار کنیم ؟ خوب باید دسترسی مستقیم رو حذف کنیم و به صورت private بزاریمش، چرا ؟ چون اگر public باشه میتونیم مستقیم و بدون این که سن چک بشه Age رو وارد کنیم.

خوب حالا که Age رو private کردیم فقط از داخل همون کلاس person بهش دسترسی داریم.

حالا باید برای دسترسی خارج از کلاس بیایم برای Age یه متد بنویسیم که بیاید Age رو از کاربر بگیره و بعد چکش کنه ببینه توی اون رنجی که ما میخوایم هست یا نه

![[{911DC90B-AAF7-4B13-B143-916148A9E4F6}.png]]

حالا اگر بخوایم یه جایی فقط مقدار Age رو بخونیم چی؟

اینجا باید یه متد دیگه هم بنویسیم که فقط مقدار Age رو return میکنه.

![[{53B34487-3AC8-4CD9-A202-032D632BE4D5}.png]]

حالا توی Main هم به این شکل ازش استفاده میکنیم:

![[{388201AF-6075-4F59-B576-80288ACC4FA4}.png]]

حالا بعد از این توضیحات میرسیم به get و set چی هه؟ خوب توی C# این امکان وجود داره که به جای این که این مراحل بالا رو بریم برای set کردن و get کردن دیتا از یه راه راحت تر بریم و اون راه راحت تره این شکلیه :

# C# Properties (Get and Set)

![[{2C7B4936-067C-4D9D-817E-F4C2D3AF4127}.png]]

نکته : تمام field ها رو بهتره که private تعریف کنیم و برای دسترسیشون از property استفاده کنیم

حالا بیایم از همین داستان توی یه مثال استفاده کنیم:

![[{EAEB4A3C-6D6B-4F84-8B99-7E719FF96DBE}.png]]

حالا شرح ماجرای این کد چیه؟ اینه که خوب ما اول یه کلاس به اسم NewPerson تعریف کردیم بعدش داخلش اومدیم یه متغییر age رو تعریف با دسترسی private حالا میرسیم به قسمت استفاده از property که اول سطح دسترسی شو public در نظر گرفتیم و بعد نوع خروجیش رو بر حسب چیزی که داره return میکنه تعیین کردیم که int هستش.

حالا اگر بخوایم ساده بگیم اینطوری میشه که هر کسی خارج از کلاس NewPerson بخواد به age دسترسی پیدا کنه باید از get استفاده کنه، که اینجا هم get همون مقدار رو برمیگردونه بهش.چجوری؟ اینجوری:

int i = newPerson.Age;

حالا برای set کردن هم مقداری که ما از خارج NewPerson میخوایم برای age بدیم یا همون set کنیم با متغییر value میادش و وارد set میشه، حالا ما اینجا اومدیم و براش شرط گذاشتیم که اگر بین 1 و 120 بود اونموقع میتونه مقدارش رو وارد متغییر age کنیم .

نکته ی جالب انگیز : توی visual studio وقتی میخواد property ها رو نشون بده کنارش یه آچار نشون میده. نکته : property نمیتونه هیچ چیزی رو داخل خودش نگه داره چون حافظه ای نداره، در حقیقت پراپرتی ابزاریه برای این که به قسمتی از حافظه که مقادیر ذخیره شده اند دسترسی پیدا کنیم.

حالا یه سری موارد دیگه هم هستش که باید بدونیم: یکیش اینه که میتونیم هر کدوم از این get یا set رو که نیاز داشتیم بزاریم یعنی میتونیم get یک متغییر رو حذف کنیم اینجوری دیگه نمیتونیم مقدارش رو بخونیم

مورد بعدی اینه که میتونیم سطح دسترسی get و set رو هم تعیین کنیم یعنی به طور مثال سطح دسترسی set رو private در نظر بگیریم ایجوری فقط میتونیم از داخل همون کلاس مقدار اون متغییر رو تغییر بدیم.

مورد بعدی اینه که ما راحت تر هم میتونیم از set , get استفاده کنیم ، اینجوری:

public int Age { get; set; }

اینجا یه آپشن دیگه هم که داره میتونیم مثل بالا برای متغییرمون یه مقدار پیش فرض تعیین کنیم، اینطوری:

public int Age { get; set; }=30;

یه آپشن دیگه هم داریم:

![[{EEE61E4E-5D01-4D6E-855A-F49559835901}.png]]

نکته : اگر پراپرتی رو که داریم تعریف میکنیم فقط get داشته باشه و set رو حذف کنیم اون پارامتر میشه private read only . چرا؟ چون دیگه فقط از طریق constructor میتونیم یه مقداری براش set کنیم و تمام.

یه قابلیت خیلی مهمه دیگه هم هست که باید بدونیم، اینه که میتونیم یه جور دیگه هم از کلاسمون نمونه درست کنیم و بسازیم، چجوری؟

راه قبلی اینطوریه :

![[{FE6C7CF9-C17B-423D-929C-B0347A835025}.png]]

در قسمت Main:

![[{604AB851-B2D2-4B62-8486-15799208AB9B}.png]]

خوب حالا اینجا اتفاقی که می افته اینه که وقتی میخوایم

newPerson.Role

رو مقدار بدیم بهمون ارور میده و میگه که این پراپرتی read only هستش و نمیتونی بهش مقدار بدی

حالا اینجا راه حل چیه؟

خوب میتونیم برای این که به یه پراپرتی read only مقدار بدیم بیایم از constructor استفاده کنیم، اینطوری:

public class NewPerson{

public NewPerson(string role){

Role = role }

}

حالا اینجوری موقع ساختن نمونه از کلاس باید یه مقداری رو برای role انتخاب کنیم.

اینجا میرسیم به راه و راه حل جدید :

خوب توی C# این قابلیت رو داریم که به این صورت هم از کلاس نمونه بسازیم:

![[{62E1487A-1F2C-47F1-8B37-BBBB51B8D810}.png]]

حالا ممکنه بگید پس Role چی شد ؟ حالا برای این که بتونیم Role رو از این مدل بهش مقدار بدیم باید قبلش یه چیزی رو به property اضافه کنیم، که اون چیه ؟ init

public string Role { get; init; }

بعد از این که init رو بهش اضافه کردیم میتونیم به Role از این راه مقدار بدیم :

![[{068DA116-5C78-434C-AE8C-BD54691AC419}.png]]

