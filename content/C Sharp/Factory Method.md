![[{2FE87168-FCD1-4B18-B9D7-C8818CEFE229}.png]]خوب برای این که بفهمیم دیزاین پترن فکتوری چیه، باید اول ببینیم چه مشکلی داریم و اون مشکل رو چجوری توسط این دیزاین پترن حل میکنیم.

مشکل:

خوب فرض کنید که شما یه اپلیکشین مدیریت logistic ساختید که توی نسخه ی اولش فقط میتونه نقل و انتقالات رو با وانت انجام بده و همه یه قسمتی زیادی از کدی که برای این برنامه نوشتید توی کلاس truck هستش. بعد فرض کنید که این اپلیکیشن شما بازار و پوکوند و همه اومدند و میخوان ازش استفاده کنن حتی شرکت های کشتیرانی هم میخواد از سرویس های شما استفاده کنه.

![[{2B1F65AA-024E-423C-89BD-B7D831E74A20}.png]]
این خبر خوبیه برای شرکت شما، ولی مشکلی که هست اینه که آیا زیرساخت لازم برای برای اضافه کردن کشتی و قایق رو به این کد داریم؟ خوب طبیعتا تمام کدی که در حال حاضر نوشتیم وابسته است به کلاس truck و برای اضافه کردن قایق به این کد باید کل ساختار کد تغییر پیدا کنه.

و حالا مشکلی که ممکنه بعدا هم پیش بیاد اینه که از شرکت های دیگه با نوع دیگه همه نقل هم بخوایم بعدا به برنامه اضافه کنیم، اونوقت باید چی کار کنیم؟

حالا راه حل ، همونطور که درست حدس زدید ، راه حلش میشه استفاده از پترن فکتوری

The Factory Method pattern suggests that you replace direct object construction calls (using the `new` operator) with calls to a special _factory_ method. Don’t worry: the objects are still created via the `new` operator, but it’s being called from within the factory method. Objects returned by a factory method are often referred to as _products._

_پترن فکتوری پیشنهاد میده که به جای این که بیایم مستقیم آبجکت رو بسازیم ( توسط new ) بیایم با_ special _factory_ method آبجکت رو بسازیم. نکته ای که هست اینه که همچنان ابجکت با new ساخته میشه ولی توسط متد factory. ابجکت هایی که توسط method factory درست میشن رو معمولا بهشون میگن product ، که خیلی جالبه .

![[{3852FB9D-A9CA-44EA-B988-C37DDF96EA7F}.png]]

At first glance, this change may look pointless: we just moved the constructor call from one part of the program to another. However, consider this: now you can override the factory method in a subclass and change the class of products being created by the method.

خوب به نظرتون شاید یه کار بی فایده داریم انجام میدم که اومدیم constructor رو از یه جای بردیم به یه جای دیگه برنامه ولی این رو در نظر بگیرید که الان میتونیم روی متد فکتوری توی زیر کلاس ها بیایم override انجام بدیم و کلاس product ساخته شده رو تغییر بدیم.

There’s a slight limitation though: subclasses may return different types of products only if these products have a common base class or interface. Also, the factory method in the base class should have its return type declared as this interface.

فقط یه محدودتی که داریم اینه که زیرکلاس ها میتونن product های متفاوتی باشن ولی در صورتی مشخصات کلاس پایه یا اینترفیسشون با هم اشتراک داشته باشه.

همچنین این که متد فکتوری که توی کلاس پایه هست باید return type مشخص شده بر اساس اینترفیس رو داشته باشه.( توی عکس فکر میکنم توضیحش بهتره )

![[{846BBDF1-2DCB-40C7-BCA3-5A8EDBF1ACF2}.png]]

For example, both `Truck` and `Ship` classes should implement the `Transport` interface, which declares a method called `deliver`. Each class implements this method differently: trucks deliver cargo by land, ships deliver cargo by sea. The factory method in the `RoadLogistics` class returns truck objects, whereas the factory method in the `SeaLogistics` class returns ships.

به طور مثال هر دو کلاس قایق و وانت باید اینترفیس transport رو که برای متد deliver هست رو پیاده سازی کنند . هر کلاسی پیاده سازیش رو متفاوت انجام میده : نقل انتقالات زمینی با وانت انجام میشه و نقل انتقالات دریایی با قایق و به همین ترتیب factory method در کلاس road logistics میاد وانت رو به عنوان آبجکت بهمون میده و factory method در کلاس sealogistic میاد قایق رو بهمون میده.

این مقاله با توجه به توضحیات و تدریس آقای مهندس سهیل محسنی نوشته شده است و قسمتی از متن هم این [سایت](https://l.vrgl.ir/r?ad=1&l=https%3A%2F%2Frefactoring.guru%2Fdesign-patterns%2Ffactory-method&si=ezeb0smkclpz&st=post&k=NzgviRP4YoTFJY0S8Qxcxamd31OY7jOSkI6wNpHGbvM%3D) ترجمه شده است.

[لینکدین](https://l.vrgl.ir/r?ad=1&l=https%3A%2F%2Fwww.linkedin.com%2Fin%2Fsoheil-mohseni-41b008239&si=qskl7dvyahg9&st=post&u=jztho14segjr&k=Uazxe5nvZdu4L1R1CE1ZTqe0abyyeKcTbkxpQtWfHmE%3D) سهیل محسنی

[ویرگول](https://virgool.io/@m_64171772) سهیل محنسی