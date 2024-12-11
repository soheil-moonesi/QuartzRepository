![[{CA76E8B9-EC63-48C3-B1C6-91B534D3F7C9}.png]]

## Importance of LSP

The LSP is vital because it ensures that the **inheritance hierarchy** is correctly designed and implemented, promoting **code reusability** and **maintainability**. Adhering to LSP leads to a robust and flexible system architecture that can easily accommodate changes in requirements.

خوب میرسیم به ال که میشه همون اصل LSP که حالا چرا انقدر مهمه؟ برای این که به ما این اطمینان رو بده که سلسله مراتب ارث بری درست طراحی و پیاده سازی شده و پایداری و نگهداری کد هم راحت تر میشه. پیاده سازی درستش همچنین باعث میشه معماری سیستمی که داریم منعطف باشه.

## Examples of Violating LSP

### Incorrect Hierarchy

An incorrect class hierarchy violates the LSP when the **derived class** does not correctly represent the **base class**. This often happens when the inheritance relationship is based on implementation details rather than a true “is-a” relationship.

سلسله مراتب اشتباه: این کار باعث نقض قانون LSP میشه، اگر کلاس مشتق شده یا کلاس فرزند به اشتباه داره کلاس base رو نمایش میده (یعنی نمایش درستی از والد نیست). این اتفاق زمانی میوفته که ما روابط ارث بری رو صرفا فقط برای نوشتن کد و پیاده سازی داریم استفاده میکنیم و این پیاده سازی بر اساس روابط درستی پایه گذاری نشده. حالا این یعنی چی ؟ یعنی به جای این که قبل از این که بخوایم کد رو بنویسیم بیایم کلاس ها رو درست تعریف کنیم و روابط رو درست بنویسیم و طراحی کنیم، اومدیم فقط شروع کردیم به کد نوشتن و طی مسیر هر جایی که برای پیاده سازی کدمون لازم داشتیم رو نوشتیم توی کلاس های مختلف و ارث بری کردیم و ... که همین کار در ادامه باعث سردرگمی و پیچیدگی کد میشه.

### Violating Method Signatures

When a derived class changes the [method](https://l.vrgl.ir/r?ad=1&l=https%3A%2F%2Fwww.bytehide.com%2Fblog%2Fmethod-usage-csharp&si=xqsrkodhn4xq&st=post&k=utjzthJdLDVQnz7bkz0tFcGyrsrFSfl08O0YT%2FtCcXI%3D) signature or return type of a base class method, it violates the LSP as the derived class can no longer be substituted for the base class without causing issues.

تناقض در مدل متد ها : وقتی که کلاس های مشتق شده بیان و مدل متد یا تایپ اون چیزی رو که قراره return کنه رو در کلاس پایه رو تغییر بدن قانون LSP رو نقض کردن. یعنی اگر در کلاس های مشتق شده بیایم یه متدی رو مدلش رو تغییر بدیم یا تایپی رو که برمیگردونه رو تغییر بدیم قانون LSP رو نقض کردیم.

### Misuse of Inheritance

Using inheritance to reuse code rather than establish a true “is-a” relationship is another way to violate LSP. When the derived class only inherits the base class for code reuse and not to represent a proper relationship, it can lead to design issues and decreased maintainability.

اگر ما داریم فقط از ارث بری برای این استفاده میکنیم که صرفا کدی رو که قبلا نوشتیم رو در یه جا دیگه از کد استفاده کنیم به جای این که ببینیم این واقعا یه ارتباط هستش ، این کار یاعث نقض قانون میشه.

## LSP in C#: Key Concepts

To understand the LSP in C#, let’s first explore some key concepts:

### Base Class

A **base class** is a general class that acts as a foundation for more specific classes, known as derived classes. The base class defines common properties and methods that the derived classes will inherit.

### Derived Class

**Derived classes** are specialized versions of the base class, inheriting its properties and methods. They can also override or extend the functionality provided by the base class.

### Method Overriding

**Method overriding** is the process by which a derived class provides a new implementation for a method declared in its base class. This allows the derived class to customize the behavior of the inherited method without changing the base class’s code.

خوب مفاهیم اصلی که توی این قانون هستش ایناست:

کلاس base: این کلاس میشه پایه و اساس یه سری از کلاس های دیگه که ازش مشتق شده اند. کلاس پایه یه سری از پراپرتی ها و متد هایی که در تمامی این کلاس ها مشترک هستند رو در خودش داره.

کلاس مشتق شده: این ها یه سری کلاس هایی هستند که از کلاس base ارث بری کردند و یه سری متد و پراپرتی هایی رو که مخصوص به خودشون هست رو دارن، و میتونن override , extend کنن functionality که توسط کلاس پایه فراهم اومده.

متد overriding: توی این پروسه کلاس مشتق میاد یه پیاده سازی جدیدی رو از متدی که در کلاس پایه هست رو انجام میده که با این کار میتونه بدونه این که به کد کلاس پایه دست بزنه و تغییر بده یه مدل جدیدی از اون متد رو که برای کار خودش لازم هست پیاده سازی کنه.

![[{C632A2E6-6FF2-4A61-95C3-2F7A557D54DE}.png]]

خوب ببینید در کد بالا نمونه درستی از پیاده سازی LSP هستش ، همونطوری که میبنید توی کلاس پایه اومده متدی Area رو تعریف کرده و بعد اومده توی مستطیل فرمول و پراپرتی هایی که مرتبط باهاش هست رو تعریف کرده و بعد اومده توی کلاس مربع که از مستطیل ارث بری کرده و متد area رو استفاده کرده ولی اومده override اش کرده به منظور استفاده مشخص خودش ، این جا ارث بری ها درست انجام شده .

C# LSP: Best Practices

### Design by Contract

When designing classes and their relationships, ensure that derived classes fulfill the **contract** established by the base class. This includes adhering to method signatures, return types, and any specified behavior.

وقتی که میخوایم ارتباطات بین کلاس ها رو تنظیم کنیم حتما این رو در نظر بگیریم که یه سری قرارداد ها بین کلاس پایه و کلاس مشتق شده انجام بشه، که این قضیه شامل مدل متد ها، return type ها و هر رفتار دیگه میشه.

### Favor Composition over Inheritance

Instead of relying heavily on inheritance, consider using **composition** to achieve code reuse and flexibility. This can help avoid LSP violations and other design pitfalls associated with inheritance.

اگر درست متوجه شده باشیم منظورش اینه که به جای این که خیلی از ارث بری استفاده کنیم بیایم از ترکیب کردن استفاده کنیم ، یعنی بیایم با استفاده از چندین تا کلاس بیایم یه کاری رو انجام بدیم و پیاده سازی کنیم.

### Use Interface-Based Programming

Implementing **interfaces** rather than inheriting from concrete classes can help enforce LSP adherence, as interfaces define contracts that must be fulfilled by any implementing class.

وقتی که داریم ارث بری میکنیم بیایم و از اینترفیس ها هم استفاده کنیم.

[لینک](https://l.vrgl.ir/r?ad=1&l=https%3A%2F%2Fwww.bytehide.com%2Fblog%2Fliskov-substitution-principle-in-csharp-solid-principles&si=xqsrkodhn4xq&st=post&k=WTkN4GrbJyT51lqANUTdxhW77%2B7EArTPifbiry%2FOCik%3D)