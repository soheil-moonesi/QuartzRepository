
خوب توی C# میتونیم از constructor برای ساختن یا ویرایش کردن چیزی در داخل اون کلاسی که نوشتیمش استفاده میشه، اینجوری عمل میکنه که وقتی که وقتی که میخوایم یه نمونه از یک کلاسی رو بسازیم بعد از این که field ها ساخته شدن، constructor اتوماتیک اجرا میشه. constructor مثل یه متده ولی یه نکته ای که داره اینه که متدیه که خروجی نداره و حتما هم باید هم اسمه اون کلاسی باشه که داخلش داریم ازش استفاده میکنیم

ادامه شو دیگه باید با مثال بگم.

میخوایم یه کلاس Car بسازیم و داخلش از constructor استفاده کنیم:

![[{3D8C86BB-53A3-4F52-8B9B-201554E3A9EB}.png]]


خوب حالا بیایم مرحله به مرحله بررسی کنیم که وقتیکه این کلاس میخواد ساخته بشه چه اتفاقاتی میوفته

همون اول field ها ساخته میشن speed با مقدار 50 و name و بعدش constructor به صورت اتوماتیک اجرا میشه. مقدار speed میاد و overwrite میشه روی مقدار قبلی یعنی این که مقدار speed میشه 100 و بعد پارامتر carName رو مقدارش رو میگیریم و میزاریمش داخل name و بعد متد incSpeed اجرا میشه و speed رو 80 تا افزایش میده که نتیجه این میشه که speed در نهایت میشه 180

دقت کنید که وقتی که برای constructor اومدیم تعریف کردیم که ورودی carName رو داشته باشه باید موقعی که میخوایم از class نمونه بسازیم این مقدار رو فراهم کنیم:

![[{64DEB4EE-FCDB-41DD-96C7-70646EF4280F}.png]]

یا میتونیم یه مقدار پیش فرض براش تعریف کنیم اینجوری:

public Car(string carName = 'volvo');

یه نکته ی جالبی هم که وجود داره اینه که حتی میتونیم constructor ها رو هم overload ازشون استفاده کنیم دقیقا مثل متد ها، به این شکل که میتونیم چند تا constructor با ورودی های مختلف بنویسیم که هر کدوم با توجه به نوع ورودی که صدا زده میشن ، اجرا بشن.

حالا اگر بخوایم این قابلیت رو در نظر بگیریم که در موقع ساخت کلاس، متغییرمون فقط بتونه توسط constructor تغییر پیدا کنه باید اون متغییر read Only در نظر بگیریم.

private readonly string name;

حالا توی این شرایط فقط میتونیم از داخل constructor متغییر name رو تغییر بدیم و اگر بخوایم از جایی خارج از constructor مقدار name رو تغییر بدیم این ارور رو میگیریم:

Error CS0191 A readonly field cannot be assigned to (except in a constructor or init-only setter of the type in which the field is defined or a variable initializer) Constructor

مطالب نوشته شده، برداشت من از کلاس C# استاد عمران صادقی هستش. خیلی ممنونم از ایشون به خاطر تدریس عالی که داشتند.

