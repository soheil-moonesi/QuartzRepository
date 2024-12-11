میرسیم به اصل open closed

![[{D62F5739-5240-4215-AE9D-F6AA8A1EB44D}.png]]

## Defining the Open/Closed Principle (OCP)

The Open/Closed Principle, introduced by **Bertrand Meyer**, states that software entities (such as classes, modules, and functions) should be open for extension but closed for modification. In other words, developers should be able to add new functionality to a class without changing its existing implementation. This can be achieved through **abstraction**, **inheritance**, and **polymorphism**.

خوب این اصل داره میگه که هر entity توی برنامه شامل کلاس ماژول ، فانکشن، هر چی باید برای اضافه کردن و گسترش دادن باز باشه و برای تغییر بسته. برنامه نویس ها باید بتونن به کلاس قابلیت های جدید اضافه کنن بدون این که قسمت های دیگه ای که پیاده سازی شده رو تغییر ندن. این کار با استفاده کردن از abstraction, inheritance , polymorphsim پیاده میشه .

## Why is the Open/Closed Principle Important?

Adhering to the OCP promotes a more maintainable, flexible, and scalable codebase. By ensuring that classes are open for extension and closed for modification, developers can add new functionality without altering existing code, minimizing the risk of introducing bugs or breaking existing features. This principle encourages the use of abstractions and promotes a modular architecture that is easier to understand, test, and refactor.

خوب برای این مهمه که برنامه نویس ها بتونن راحت قابلیت های جدید اضافه کنن بدون این که باگ های ناخواسته ایجاد کنن یا بزنن بقیه جاهای برنامه رو بپوکونن. خوب این قانون خیلی تشویق به این میکنه که از abstraction استفاده کنیم طراحی و ساختار ماژولار داشته باشیم که بعدا بتونیم راحت تست بنویسیم و ریفکتور کنیم.

### Abstraction

Abstraction is a technique that allows developers to hide the internal implementation details of a class and expose only its essential features. By using abstraction, developers can create flexible and extensible designs that are less susceptible to change.

خوب abstraction چیه داستانش ؟ اینه که یه تکنیکیه که برنامه نویس ها برای مخفی کردن جزییات و پیاده سازی هایی که توی کلاس شده، و اینطوری فقط مواردی که لازمه رو میان و نشون میدن. با این کار کد منعطف تره و گسترش دادنش هم راحت تر میشه.

### Inheritance and Polymorphism

Inheritance is a mechanism in C# that allows one class to inherit the properties and [methods](https://l.vrgl.ir/r?ad=1&l=https%3A%2F%2Fwww.bytehide.com%2Fblog%2Fmethod-usage-csharp&si=k8meyxh01uli&st=post&k=ksNBExPitaW8EE%2BiV1op0l126Y9JNnJtas9QAZys6Ps%3D) of another class, [while](https://l.vrgl.ir/r?ad=1&l=https%3A%2F%2Fwww.bytehide.com%2Fblog%2Fwhile-loop-csharp&si=k8meyxh01uli&st=post&k=5vq7LpmsOwE3LQyqRJkuEXho7dqxv%2BviCmSX59DQjT0%3D) polymorphism enables a class to have multiple implementations based on the context. These concepts play a crucial role in achieving the Open/Closed Principle, as they allow developers to extend classes without modifying their existing implementation.

ارث بری و polymorphism که به یه کلاس قابلیت این رو میده که از یه کلاس دیگه پراپرتی و متد به ارث ببره و polymorphism به ما قابلیت این رو میده که یه کلاس multiple implementations داشته باشه بر اساس context. این دو تا قضیه خیلی مهمه برای این که برسیم به قضیه open/closed .

Open/Closed Principle C# Example

Let’s consider an example to demonstrate the Open/Closed Principle in C#. Suppose we have a `Shape` class and a `AreaCalculator` class that calculates the area of different shapes:

خوب بیاید اینجا کلاس shape و کلاس areaCalculator رو در نظر بگیریم که مساحت اشکال رو محاسبه میکنه.

![[{AA407F09-7BF6-4958-8354-AACFC0CE0A81}.png]]

In this example, the `AreaCalculator` class can only calculate the area of rectangles. If we want to add support for other shapes, such as circles and triangles, we would need to modify the existing implementation of the `AreaCalculator` class, which violates the Open/Closed Principle.

خوب توی areaCalculator ما فقط میتونیم مساحت مربع رو محاسبه کنیم، حالا اگر بخوایم مساحت اشکال دیگه رو هم محاسبه کنیم باید بیایم و کلاسمون رو تغییر بدیم که این خلاف اصل باز / بسته بودنه.

To adhere to the OCP, we can use abstraction and inheritance to create separate classes for each shape type and provide a consistent method for calculating the area:

خوب برای این کار میتونیم کلاس های جدا تعریف کنیم و یه متد هم تعریف کنیم که بیاد و مساحت رو در هر کدوم استفاده کنه.

![[{708C58EC-6BFA-4BD2-9B6C-2E305214904B}.png]]

Now, the `AreaCalculator` class adheres to the Open/Closed Principle, as it can support new shapes without modifying its existing implementation.

خوب حالا با این کار هم از اصل باز /بسته پیروی کردیم و هم میتونیم اشکال دیگه رو هم اضافه کنیم بدون این که بخوایم تغییری ایجاد کنیم.

Strategies for Implementing the Open/Closed Principle in C#

Using Abstract Classes

Abstract classes can be used to define a base class with common functionality and provide a consistent interface for derived classes. By creating abstract methods, developers can enforce that each derived class implements its own version of the method, allowing for extensibility without modifying the base class.

خوب حالا چجوری پیاده سازیش کنیم؟ میتونیم از کلاس ها abstract استفاده کنیم و به عنوان کلاس base ازشون استفاده کنیم که باعث میشه بتونیم اینترفیس های یکسان توی کلاس های فرزند و مشتق شده داشته باشیم. با استفاده کردن از متد های abstract کلاس های مشتق شده نسخه ی خودشون از اون متد رو باید پیاده سازی کنن و این باعث میشه که بتونیم کد رو گسترش بدیم بدون این که بخوایم کلاس base رو تغییر بدیم.

### Applying the Strategy Pattern

The Strategy Pattern is a behavioral design pattern that enables selecting an algorithm at runtime. It can be used to implement the Open/Closed Principle by encapsulating different algorithms within separate classes and providing a common interface for them.

لینک مطلب : [لینک](https://l.vrgl.ir/r?ad=1&l=https%3A%2F%2Fwww.bytehide.com%2Fblog%2Fopen-closed-principle-in-csharp-solid-principles&si=k8meyxh01uli&st=post&k=mDXZYoPixmVbQ3ZvwDI6WRKOrzQ4t5sG%2FRLJQFZ4ASE%3D)