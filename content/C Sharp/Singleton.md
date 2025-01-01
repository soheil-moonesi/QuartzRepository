
![[{658BCA67-0AF4-4361-8D8E-BFD79E3784EA}.png]]

**Singleton** is a creational design pattern, which ensures that only one object of its kind exists and provides a single point of access to it for any other code.

خوب تعریف singleton میشه دیزاین پترنی که میاد یه کاری میکنه که شما فقط یه دونه از یک آبجت رو فقط داشته باشید و فقط هم از یک راه بتونید بهش دسترسی پیدا کنید . حالا توضیحات بیشترش رو باید بخونیم.

**Usage examples:** A lot of developers consider the Singleton pattern an antipattern. That’s why its usage is on the decline in C# code.

میگه خیلی از برنامه نویسی ها singleton به نوعی antipattern میدونن و برای همین توی C# کمتر استفاده میشه.

**Identification:** Singleton can be recognized by a static creation method, which returns the same cached object.

اینطوری singleton رو میتونیم بشناسیم توسط یک متد static درست میشه و مقدار cached شده آبجکت رو return میکنه.

```csharp
 using System;

namespace RefactoringGuru.DesignPatterns.Singleton.Conceptual.NonThreadSafe
{
    // The Singleton class defines the `GetInstance` method that serves as an
    // alternative to constructor and lets clients access the same instance of
    // this class over and over.

    // EN : The Singleton should always be a 'sealed' class to prevent class
    // inheritance through external classes and also through nested classes.
    public sealed class Singleton
    {
        // The Singleton's constructor should always be private to prevent
        // direct construction calls with the `new` operator.
        private Singleton() { }

        // The Singleton's instance is stored in a static field. There there are
        // multiple ways to initialize this field, all of them have various pros
        // and cons. In this example we'll show the simplest of these ways,
        // which, however, doesn't work really well in multithreaded program.
        private static Singleton _instance;

        // This is the static method that controls the access to the singleton
        // instance. On the first run, it creates a singleton object and places
        // it into the static field. On subsequent runs, it returns the client
        // existing object stored in the static field.
        public static Singleton GetInstance()
        {
            if (_instance == null)
            {
                _instance = new Singleton();
            }
            return _instance;
        }

        // Finally, any singleton should define some business logic, which can
        // be executed on its instance.
        public void someBusinessLogic()
        {
            // ...
        }
    }

    class Program
    {
        static void Main(string[] args)
        {
            // The client code.
            Singleton s1 = Singleton.GetInstance();
            Singleton s2 = Singleton.GetInstance();

            if (s1 == s2)
            {
                Console.WriteLine(&quotSingleton works, both variables contain the same instance.&quot);
            }
            else
            {
                Console.WriteLine(&quotSingleton failed, variables contain different instances.&quot);
            }
        }
    }
}
```

خوب اول این که اینجا اومده کلاس singleton رو از نوع sealed تعریف کرده، که به این معنیه که هیچ کلاسی دیگه نمیتونه از این کلاس ارث بری کنه.

**private** Singleton() { }

بعد اومده constructor این کلاس رو هم private کرده که کسی نتونه با استفاده از new این کلاس رو نمونه برداری کنه و بسازه .

**private** **static** Singleton _instance;

و بعد اومده instance رو با تایپ Singleton و static و با درسترسی private تعریف کرده(اینجا اشاره شده که این مدل تعریف کردن اصلا مناسب با multithreading نیست که من در حال نمیدونم چرا).

GetInstance

حالا اومده و متد getInstance رو تعریف کرده و داخلش اینطوری تعریف کرده که اگر instance برابر با null بود بیاد و یه نمونه از کلاس Singleton رو میسازه و میریزه داخل متغییر instance با آندر لاین که این یعنی بار بعدی که این متد getInstance فراخوانی بشه به دلیل این که دیگه instance دیگه null نیستش، همون آبجکت instance به خروجی ارسال میشه.

و این پیاده سازی کد بالا یه نماینگر کلی از دیزاین پترن singleton هستش.

خوب حالا singleton چه مشکلی رو حل میکنه؟

**Ensure that a class has just a single instance**. Why would anyone want to control how many instances a class has? The most common reason for this is to control access to some shared resource—for example, a database or a file.

خوب به نظرتون چرا باید یه کاری کنیم که فقط بشه از یک کلاس فقط یدونه نمونه توی کل برنامه داشته باشیم؟

خوب یه دلیل منطقیش اینه که بخوایم دسترسی به منابعی که share هستند مثل دیتابیس رو کنترل کنیم.

**Provide a global access point to that instance**. Remember those global variables that you (all right, me) used to store some essential objects? While they’re very handy, they’re also very unsafe since any code can potentially overwrite the contents of those variables and crash the app.

Just like a global variable, the Singleton pattern lets you access some object from anywhere in the program. However, it also protects that instance from being overwritten by other code.

فراهم آوردن دسترسی global به اون نمونه ، خوب طبیعتا ما یه سری آجکت داریم که توی کل برنامه مورد استفاده قرار میگیره و ما در اینجا میایم اون ها رو میریزم داخل این متغییر global ، حالا درسته که در این حالت دسترسیمون خیلی راحت شده ولی خیلی هم این کار باعث ایجاد خطاهای احتمالی در کد میشه چرا؟ چون ممکنه توسط یه قسمتی از کد این اطلاعات در متغییر global بیاد overwrite بشه و باعث crash app بشه .

استفاده از singleton pattern ها هم شبیه به عملکرد متغییر global هستش ولی اینجا فرق که داره اینه که دیگه اینجا مشکل ایجاد خطا به خاطر overwrite شدن رو نداریم.

این مقاله با توجه به توضحیات و تدریس آقای مهندس سهیل محسنی نوشته شده است و قسمتی از متن هم این [سایت](https://refactoring.guru/design-patterns/singleton/csharp/example#example-0) ترجمه شده است.

[لینکدین](https://l.vrgl.ir/r?ad=1&l=https%3A%2F%2Fwww.linkedin.com%2Fin%2Fsoheil-mohseni-41b008239&si=qskl7dvyahg9&st=post&k=ekYT2M3WlDY%2B8O%2B3%2F0%2BM0IS5UsXKnwaSRJ0QYvbftlE%3D) سهیل محسنی

[ویرگول](https://virgool.io/@m_64171772) سهیل محنسی