هدف این مطلب توضیح این سه تاست و این که چه تفاوت هایی با هم دارند.

این متن از این [سایت](https://l.vrgl.ir/r?ad=1&l=https%3A%2F%2Fwww.codeproject.com%2FArticles%2F816448%2FVirtual-vs-Override-vs-New-Keyword-in-Csharp%23fromHistory&si=h0y2n9lcf9nw&st=post&k=rkf2jeXmgi5iIssRyxOsyYe3ajze9VGRhwGCA2EICyU%3D) گرفته شده و ترجمه شده.

Virtual Keyword

`Virtual` keyword is used for generating a virtual path for its derived classes on implementing method overriding. `Virtual` keyword is used within a set with `override` keyword. It is used as:

خوب حالا بیایم برای توضیح این متن بالا با مثال شروع کنیم.

ولی قبلش یه توضیح ای که باید بدم اینه که drived class یعنی کلاسی که از کلاس پایه درست شده و مشتق شده.

![[{C04E1C79-D3FC-4D24-9FA3-EFD78E1AFB60}.png]]

خوب کلاس A رو فرض کنید کلاس پایه است.

### Override Keyword

`Override` keyword is used in the derived class of the base class in order to override the base class method. `Override` keyword is used with `virtual` keyword, as:

![[{6822C94A-D5DC-43DB-9F91-35C69A428494}.png]]


اینجا کلاس ‌B میشه کلاس مشتق شده از کلاس A . خوب همونطوری که میبینید توی کلاس اصلی و پایه اومدیم از virtual استفاده کردیم و توی کلاس مشتق شده از override استفاده کردیم. چرا؟ جلوتر میفهمیم.

#### آها، قبلش ولی New Keyword رو هم یه مثال براش بزنیم:

`New` keyword is also used in polymorphism concept, but in the case of method overloading So what does overloading means, in simple words we can say procedure of hiding your base class through your derived class.

It is implemented as:

![[{DB2E96EB-8AD9-4870-A70A-248C6685F313}.png]]

حالا بریم سره اصل قضیه :

![[{DAE8A2B8-144D-47E2-8943-20AF2B197BD6}.png]]

خوب یه بررسی کنیم از اول این کد: اول اومدیم کلاس A رو ساختیم ، بعد اومدیم کلاس B رو از کلاس A ساختیم و مشتق گرفتیم. بعد هم اومدیم هر کدوم این ها رو یه نمونه ازشون درست کردیم و بعد از متد show برای چاپ در کنسول استفاده کردیم.

فقط یه نکته ای اینجا هستش :

![[Pasted image 20241204193959.png]]

اینجا اومدیم یه نمونه از کلاس B درست کردیم و ریختیمش داخل a2 که از نوع کلاس A هستش. مگه میشه ؟ آره میشه. توی C# میشه مقدار کلاس مشتق شده رو داخل متغییر از نوع و تایپ کلاس پایه ریخت. ولی اتفاقی که اینجا میوفته اینه که دیگه توی این حالت به متد ها و اجزای داخل کلاس ‌B دسترسی نداریم (یعنی به متد something هم دسترسی نداریم) و فقط به کلاس A دسترسی داریم. در این حالت هیچ خطایی دریافت نمیکنیم ولی یه warning داریم :

The keyword 'new' is required on 'show' because it hides method 'void Virgol.A.show()'

اینجا virgol اسمه namespace هستش و داره میگه که برای رفع این warning باید از کلمه new استفاده کنید. برای رفع warning میایم توی کلاس B به این شکل مینویسیم:

public new void show()

در دو حالت خروجی که داریم به این ترتیبه :

Hello: Base Class!

Hello: Derived Class!

Hello: Base Class!

حالا سوالی که برای خودم پیش اومده اینه که خوب که چی؟ چرا اینجا از override و virtual استفاده نشد. خوب طبیعتا برای این که بفهمیم که این دو تا چی کار میکنن، باید قبلش ببینیم ببینیم که بدون این ها چطوری داره کار میکنه و بعدش چطوری کار میکنه.

#### حالا دیگه جدی میرسیم به

Virtual & Override Keywords | Method Overriding


![[{B43E60B0-2689-4B61-8C3A-0CC7CD654ABB}.png]]

خوب حالا بررسی کنیم خروجی رو :

Hello: Base Class!

Hello: Derived Class!

Hello: Derived Class!

همونطوری که میبینید خروجی a2.show تغییر کرده و شده Hello: Derived Class چرا؟

برای این که ما بخوایم متدی رو override کنیم باید اون متد در کلاس پایه virtual تعریف شده باشه.

خوب ما این کار رو انجام دادیم که هر وقت که اومدیم یه نمونه از کلاس B ساختیم و خواستیم اون رو داخل متغییری از کلاس A ریختیم همچنان بتونیم از متدی که داخل کلاس B هستش استفاده کنیم.

فقط نکته ای که هست ما فقط به متدی که override شده میتونیم دسترسی پیدا کنیم و همچنان متد something وقتی که میخوایم از a2 استفاده کنیم از دسترس خارجه.

یه مثال دیگه :

Overriding + Hiding | Together

![[{5B03698F-8857-44E2-B5FA-E47A2A454F8D}.png]]

![[{8BFD211D-1D63-42EB-9102-FBDB198CE616}.png]]

حالا خروجی به این شکل میشه :


![[{96E17233-C5FF-46CC-801F-5D795D9BF7C6}.png]]

خوب حالا بیایم بررسی کنیم:

![[{3A32F1D7-3CC1-4AD7-9A22-87A739BCE3C8}.png]]

اینجا چون متد show رو override کردیم طبیعتا این خروجی رو به ما میده

![[{A07F8656-60E0-4413-A260-C2862B780C51}.png]]

توی مورد بالا اومدیم کلاس C که خودش مشتق شده کلاس B هستش و در کلاس B اومدیم متد show که در کلاس A به صورت virtual تعریف شده رو override کردیم.

![[{48AC4659-F680-4FD1-86E2-EB45578A9054}.png]]

اینجا هم اومدیم کلاس C رو که مشتق گرفته شده از کلاس B هستش رو داخل متغییر با تایپ B ریختیم.