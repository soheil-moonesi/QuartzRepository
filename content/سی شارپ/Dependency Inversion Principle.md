![[{ACB63ED6-A431-4913-A269-2A27C350B3C1}.png]]

The **Dependency Inversion Principle (DIP)** is a fundamental principle of the **[SOLID](https://l.vrgl.ir/r?ad=1&l=https%3A%2F%2Fwww.bytehide.com%2Fblog%2Fsolid-principles-in-csharp&si=h3qdcdkmnax4&st=post&k=QvFjVQMCk95BA%2BDF6pe59%2FrwUzMiRdH7vm04jqxs9c0%3D) design principles** that is crucial for building maintainable and extensible software systems in **C#**. By adhering to the DIP, developers can decouple the high-level components of their applications from the low-level implementation details, resulting in code that is easier to modify and test.

The main idea behind DIP is that higher-level modules should not depend on lower-level modules; instead, they should both depend on abstractions.

میگه ایده کلی این قانون اینه که ماژول های higher level نباید وابستگی داشته باشن به ماژول های lower level به جاش هر دو اینا باید به abstraction ها وابسته باشن.

## Dependency Inversion Principle in C# – The Basics

To implement the Dependency Inversion Principle in C#, you should focus on creating **abstractions** (interfaces or abstract classes) and making both high-level and low-level modules depend on them. By doing so, you can avoid direct dependencies between high-level and low-level modules.

خوب برای اجرای این قانون واجبه که بیشتر بر روی abstraction ها که میشن همون اینترفیس ها یا کلاس های abstract و کاری کنیم که ماژول های high lelev , low level به اون ها وابستگی داشته باشن و از هرگونه وابسته سازی مستیم بین ماژول های high level , low level اجتناب کنیم.

### Without Dependency Inversion Principle

Imagine you have an email notification system that sends notifications to users. The `EmailNotification` class has a `Send` [method](https://l.vrgl.ir/r?ad=1&l=https%3A%2F%2Fwww.bytehide.com%2Fblog%2Fmethod-usage-csharp&si=h3qdcdkmnax4&st=post&k=fE2kmeKDdew3Iv5%2FnF6yZhq0428YxIIi%2BKQfe%2BAEd3w%3D) which directly depends on the `SmtpClient` class to send the email.

خوب اینجا میخوایم مثالی رو بررسی کنیم که این قانون توش رعایت نشده. کلاس emailNotification یه متد send داره که به smtpClient وابسته است

### Implementing Dependency Inversion Principle

To implement the Dependency Inversion Principle, you’ll introduce an abstraction that both the `EmailNotification` class and the `SmtpClient` class will depend on. This abstraction will be an interface called `IEmailSender`.

خوب حالا مشکلی که بالاتر گفتیم رو چجوری حل کنیم؟ بیایم از abstraction ها جوری استفاده کنیم که هر دو اینا وابسته به اون abstraction بشن. خوب برای این کار هم میایم یه اینترفیس به اسم IEmailSender درست میکنیم.

```csharp
public interface IEmailSender{  
   void Send(string emailAddress, string message); 
}
```

Refactoring the Example with Dependency Inversion Principle

  

خوب حالا میایم اول smptClient رو وابسته به اینترفیس IEmailSender میکنیم

```csharp
public class SmtpClient : IEmailSender{  
   public void Send(string emailAddress, string message)    { 
        // Implementation of email sending using SMTP    }
 }
```

Next, modify the `EmailNotification` class to depend on the `IEmailSender` interface instead of the `SmtpClient` class. You’ll do this by passing an instance of `IEmailSender` to the constructor of the `EmailNotification` class.

بعدش میایم EmialNotification رو وابسته میکنیم به IEmailSender ، برای این کار هم میایم توی constructor کلاس EmailNotification میایم IEmailSender رو قرار میدیم به عنوان تایپ ورودی.

جالا دیگه اینجوری هیچ کدوم از این ها به هم وابسته نیستند و هر دو به یک اینترفیس وابستگی دارن واینطوری اگر بخوایم بخوایم توی مکانیزم ارسال ایمیل هم تغییری به وجود بیاریم فقط کافیه که یه کلاس جدید بسازیم که اون کلاس هم اینترفیس IEmailSender رو پیاده سازی کنه.

Dependency Inversion Principle and Interfaces

اینترفیس ها نقش بسیار مهمی در این قانون دارند چون باعث میشن ماژول های رده بالا و رده پایین هر دو از طریق اینترفیس ها با هم ارتباط داشته باشن و همین باعث میشه که کد انعطاب بیشتری داشته باشی و کوپل شدگی کمتری داشته باشه.

Dependency Inversion Principle and Dependency Injection

**Dependency Injection (DI)** is a technique used to decouple classes by providing their dependencies from external sources. It is often used in conjunction with the Dependency Inversion Principle to achieve even better decoupling and testability.

تزریق وابستگی تکنیکیه که برای فراهم آوردن مواردی که یه کلاس میخواد از یه منبع خارجی بدون کوپل شدگی. برای استفاده از این تکنیک بهتره که از DIP استفاده کنیم

Dependency Injection Techniques  
There are three common techniques for implementing Dependency Injection

- **Constructor Injection**: Injecting dependencies through the constructor of a class.
- **Property Injection**: Injecting dependencies through public properties of a class.
- **Method Injection**: Injecting dependencies as parameters of a method.

[لینک](https://l.vrgl.ir/r?ad=1&l=https%3A%2F%2Fwww.bytehide.com%2Fblog%2Fdependency-inversion-principle-in-csharp-solid-principles&si=h3qdcdkmnax4&st=post&k=vIfnIaRkN1h2tqdEdhtnbpRs0EglYabmf3WcaSTNYBA%3D)