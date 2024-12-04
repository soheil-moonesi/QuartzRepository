خوب امروز در حین کد نوشتن به یه داستان جالبی برخوردم گفتم به اشتراک بزارمش.

## Introduction to Static Constructors in C#

### The Basics of Constructors in C#

In C#, constructors are special [methods](https://l.vrgl.ir/r?ad=1&l=https%3A%2F%2Fwww.bytehide.com%2Fblog%2Fmethod-usage-csharp&si=r7hmi1elgeij&st=post&k=pM6erjJZg1pVriW%2FXdGtcafT3tjcH%2BAIRR8ScJNORWs%3D) that initialize an object when it’s created. They have the same name as the class and don’t return any value. Constructors can be overloaded, allowing you to create multiple constructors with different sets of parameters to initialize objects in various ways.

خوب همونطور که میدونید constructor های معمولی توی C# یه سری متد های خاص هستند که موقعی که میخواید یه نمونه بسازید براتون یه آبجکت رو میسازه. اسمشون هم اسمه با اسم اون کلاس و هیچ مقداری رو برنمیگردونه. constructor ها قابلیت overload شدن هم دارن به این معنی که به ازای مقادیر ورودی متفاوت میتونه کارای متفاوتی انجام بده.

### Why Use Static Constructors?

Static constructors are useful when you need to initialize static members of a class. They ensure that the static members are initialized only once, before any instance of the class is created or any static methods are called.

حالا میرسیم به static constructor ها . این مدل constructor ها زمانی میتونه استفاده بشه که بخوایم یه سری عضو بخوایم به اون کلاسمون اضافه کنیم، فقط دقت کنید که این constructor ها قبل از اجرای هر متد استاتیکی اجرا میشه و فقط هم همون ابتدای برنامه فقط و فقط یک بار اجرا میشن.

## Understanding Static Constructors

### Defining a Static Constructor

A static constructor is a constructor that doesn’t require an object instance to execute. It initializes the static members of a class and runs only once during the lifecycle of an application.

خوب تعریف static constructor ها اینجوری میشه که اینها یه سری constructor هستن که نیازی ندارن برای این که اجرا اون کلاس ازش نمونه ای ساخته بشه. این constructor میاد یه سری عضو استاتیک به این کلاس اضافه میکنه و فقط هم در طول اجرای برنامه یک بار همون اول اجرا میشه و تمام.

### Static Constructor Syntax

The syntax for defining a static constructor is straightforward:

```csharp
class ClassName
{
    static ClassName()
    {
        // Initialization code here
    }
}  
```

این بالا سینتکس یه static constructor هستش.

### initialization of Static Members

Static constructors are called automatically by the runtime, initializing static members before the class is used. This ensures that all static members have valid values before they are accessed.

این مدل constructor ها به صورت اتوماتیک توسط runtime اجرا میشن و static member ها رو قبل از این که کلاس بخواد استفاده بشه اوکیش میکنن. تمام static member ها با این حرکت قبل از این بخواد بهشون دسترسی اعمال بشه مقادیرشون آماده شده.

### Execution Order

The static constructor is called before any static member is accessed or any instance of the class is created. However, the exact order of execution is not guaranteed, so it’s best not to rely on any specific order when working with static constructors.

اینجا داره میگه که static constructor ها قبل از این که بخوایم به هر static member دسترسی پیدا کنیم اجرا میشن. البته نوشته که این ترتیب اجرا رو خیلی نمیشه روش حساب کرد، برای همین هم گفته که حواستون باشه و روی این که همه چی قراره به این ترتیب همیشه اجرا بشه حساب باز نکنید.

### Exception Handling

If an exception is thrown in a static constructor, the runtime will not catch it, and the type will become unusable for the lifetime of the application domain. It is crucial to handle [exceptions](https://l.vrgl.ir/r?ad=1&l=https%3A%2F%2Fwww.bytehide.com%2Fblog%2F5-good-practices-for-error-handling-in-c&si=r7hmi1elgeij&st=post&k=FpBLtUgb7fUjAH4ubomvyqd%2BvEgnTRytdqz2JGT77M8%3D) in a static constructor to prevent the application from crashing.

آها یه داستان دیگه ای هم که داره اینه که اگر exception یهویی پیش بیاد runtime نمتونه اون ها رو catch منه و میگه که اون تایپ کلا به فنا میره وقتی که این اتفاق میوفته برای همین خیلی مهمه که با یه سری راه های دیگه این exception ها رو handle کنیم که برنامه crash نکنه و به فنا نره .

## Static Constructor vs. Instance Constructor

### Key Differences

Static constructors initialize static members, [while](https://l.vrgl.ir/r?ad=1&l=https%3A%2F%2Fwww.bytehide.com%2Fblog%2Fwhile-loop-csharp&si=r7hmi1elgeij&st=post&k=Vk15JsekDMqIubRJsbgYEqUhSShIwblVkt0IF7uSJQ8%3D) instance constructors initialize instance members.

Static constructors are called only once, whereas instance constructors are called every time a new object is created.

Static constructors do not have access [modifiers](https://l.vrgl.ir/r?ad=1&l=https%3A%2F%2Fwww.bytehide.com%2Fblog%2Faccess-modifiers-csharp&si=r7hmi1elgeij&st=post&k=Jg%2BmGTdQ5QSH5F%2BVFzRYC%2B9Ar%2BoCiD9GqIgALcGoCQk%3D) or parameters.

خوب حالا فرق static constructor ها با constructor های معمولی چی هه؟

اینه که static constructor ها میان static member ها رو درست میکنن. ولی constructor های معمولی instance member ها رو میسازن.

و این که static constructor ها access modifire ندارن .

## Practical Examples of Static Constructors

### Singleton Design Pattern

The [Singleton](https://l.vrgl.ir/r?ad=1&l=https%3A%2F%2Fwww.bytehide.com%2Fblog%2Fsingleton-design-pattern-csharp&si=r7hmi1elgeij&st=post&k=pKJYHk1c1%2FOFnzVYI3XUIATk0LkKoYPrewCSWJIXe4M%3D) design pattern ensures that only one instance of a class exists in an application. A static constructor can be

used to implement this pattern:

اینجا همنطور که میبنید میتونیم از static constructor ها برای پیاده سازی دیزاین پترن singleton استفاده کنیم.

اینجا اومده new که باهاش میان از کلاس یه نمونه میسازن رو توی static constructor تعریف کرده، و این یعنی این که فقط همون شروع برنامه یه نمونه از این کلاس درست میشه و تمام.
```csharp
public class Singleton
{
    private static readonly Singleton _instance;

    static Singleton()
    {
        _instance = new Singleton();
    }

    private Singleton() { }

    public static Singleton Instance
    {
        get { return _instance; }
    }
}
```

## Common Pitfalls and Best Practices

### Be Mindful of Execution Order

Since the execution order of static constructors is not guaranteed, avoid relying on a specific order when working with multiple static constructors.

### Avoid Complex Initialization Logic

Keep the initialization logic in static constructors simple and straightforward. Complex logic may lead to unforeseen issues and make the code harder to maintain.

خوب حالا گفته ممکنه چه خطاهای پیش بیاد.

اولیش گفته که زیاد روی ترتیب اجرا این داستان ها حساب باز نکنید

دومیش هم گفته که زیاد منطق پیچیده ای رو داخل شون پیاده سازی نکنید چون بعدا ممکنه به یه سری خطاهای عجیب غریب بر بخورید.

این هم مقاله ای که ازش استفاده کردم: [لینک](https://l.vrgl.ir/r?ad=1&l=https%3A%2F%2Fwww.bytehide.com%2Fblog%2Fstatic-constructor-csharp&si=r7hmi1elgeij&st=post&k=iC7HS0FG3VVZh%2FUjXNtaAyWfE6pQ8zld%2BPOQVjO%2B98M%3D)