خوب یه مبحث بسیار جالب دیگه هم داریم که کار با این دو تا keyword عه که آقای استاد شیخ علی توی سایتش توضیح داده و من هم میخوام از توضحیاتش استفاده کنم.

ولی قبلش معنی Delegate رو هم با هم بررسی کنیم:

نماینده، نمایندگی دادن، وکالت دادن، محول کردن به

خوب حالا شروع میکنیم:

![[{B7BAC2F8-F38E-4A20-B1D5-F82FF74D9F6B}.png]]

فکر میکنم این عکس خیلی خوبه برای توضیحش

## Events in C#

Events in C# are used to notify user actions such as _button click_, _mouse over_, _menu selection_, _On Text Changed_, etc.

**An event is an encapsulated delegate in C#**. It depends on the [delegate](https://l.vrgl.ir/r?ad=1&l=https%3A%2F%2Fwww.shekhali.com%2Fwhat-is-a-delegate-in-c-multicast-delegate-with-examples%2F&si=adgpcojxgkcj&st=post&k=oEMJOr4J59w7MUNM40tcJTYVCswjjox4Zepm9m8F0Mo%3D). The delegate specifies the event handler method’s signature for the subscriber class.

- A **publisher** is an object that holds the definition of the event and the delegate. A publisher class object raises an event and is notified to other objects.
- A **subscriber** is an object that receives the event and provides an event handler. The delegate of the publisher class invokes the event handler of the subscriber class.

ایونت : ایونت ها توی سی شارپ برای مطلع شدن از کارهای یوزر استفاده میشه مثل کلیک کردن موس و تکان دادن و این تغییر متن و این داستانا.

میگه ایونت ها داخل Delegate هست و کپسوله شدن داخلش.

حالا publisher چیه؟ یه آبجکتیه که تعریف event و delegate داخلشه. کلاس publisher وقتی که event اتفاق بیوفته بقیه آبجکت ها رو خبر میکنه

حالا subscriber چیه؟ آبجکتیه که event و میگیره و event hanlder رو هم اوکی میکنه. delegate کلاس publisher میاد event handler کلاس subscriber رو invoke میکنه .

حالا همه این ها رو وقتی که این کد ها رو بخونید یکم واضح تر میشه.

### Event Syntax:

In C#, Events are declared using the event keyword followed by the name of the delegate.  
The following is the event syntax:

event delegate_name event_name;

متن بالا داره ساختار event رو نشون میده.

### C# Events Declaration

An event can be declared in the following two steps:

- first, we need to declare a delegate.
- Then, declare a variable of **delegate** with the **event** keyword.

The following example shows how to declare an event in c# programming language.

`**public** **delegate** **void** Notify(); // delegate`

`**public** **event** Notify myEvent; // event`

متن بالا داره مراحل درست کردنه یه event رو شرح میده.

```csharp
using System;
namespace CSharp_Events_Example
{
public delegate void Notify(string name); // Delegate
public class Program
{
event Notify myEvent; // Event
public Program() // Constructor
{
// Register with an event
this.myEvent += new Notify(this.Display);
}
public void Display(string name)
{
Console.WriteLine($&quotHi: {name}&quot);
}
static void Main(string[] args)
{
Program e = new Program();
e.myEvent(&quotShekh&quot);
Console.ReadLine();
}
}
// Output: Hi: Shekh
}
```

### Events Overview

These are the characteristics of events:

- An event is a wrapper around a delegate or, in simpler terms, it’s an encapsulated delegate.
- Events are used to implement a communication mechanism between objects.
- Events have **publishers** and **subscribers**. Publishers determine when events occur, and subscribers determine what actions to take in response to events.
- We can subscribe to an event using the `+=` operator and unsubscribe from an event using the `-=` subtraction assignment operator.
- A single event may have multiple subscribers. A subscriber is capable of handling multiple **events** from multiple publishers.

خوب حالا میخوام یه مروری روی خصوصیات event ها داشته باشیم:

ایونت مثل یه wrapper دوره delegate هستش یا میشه گفت که delegate رو کپسوله کرده.

ایونت ها برای پیاده سازی یه مکانیزمی برای ارتباط بین آبجکت های مختلف طراحی شده.

ایونت ها publisher و Subscriber دارن. publisher ها تعیین میکنن که چه زمانی قراره event اتفاق بیوفته و subscriber ها تعیین میکنن که قراره چه کار یا عملی انجام بشه بعد از اون که اون اتفاق افتاد.

حالا یه قابلیتی که داره اینه که میتونیم با =+ میتونیم subscribe کنیم و با =- میتونیم unsuscribe کنیم.

یه دونه ایونت میتونه چندین تا subscriber داشته باشه. یه دونه subscriber هم این قابلیت رو داره که چند تا event رو از چند تا publisher مختلف handle کنه.

## C# event handler with example

To respond to an event, an event receiver must define an **event handler** method. The signature of this method must match the signature of the delegate for the event it handles.  
The event handler method contains the code that gets executed in response to a specific event that occurs in an application such as button clicks, mouse hover, menu selections, etc.  
Now that we are clear on what an event handler is, let us write a simple syntax for an Event handler method as follows:

حالا این قضیه event handler رو با مثال بیایم بررسی کنیم.

برای پاسخ دادن به یه event باید اون event یه متد event handler رو داشته باشه. مدل اون متده باید مثل مدل delegate برای اون event باشه، برای این که بتونه handle اش کنه

اون متد event handler باید شامل کدی باشه که میخواد در پاسخ به یه event اجرا بشه، مثل کلیک کردن رو یه دکمه موس و هاور کنی و ... .

`**public** **delegate** **void** sampleEventHandler(**int** num1, **int** num2);`

The delegate declaration above has a basic operation that points to an event-handling method that accepts two parameters of integer type.

توی خط بالا این delegate داره به یه متد event handle اشاره میکنه.

#### Example: EventHandler

The following example shows the event handler methods named  Add  &  Substract  that match the signature of the EventHandler delegate. These methods subscribe to the event named “MyEvent”.

خوب الان مثالی که میخوایم این پایین بنویسیم این قضیه رو داره نشون میده که متد های Add و subtract که event handler هستند با مدل یا امضا EventHandler Delegate میخونن.

```csharp
using System;
namespace CSharp_Event_Handler_Example
{
// Declare delegate
public delegate void sampleEventHandler(int num1, int num2);
class Program
{
// Declare event
public static event sampleEventHandler MyEvent;
static void Main()
{
// Register event handler methods with an event
MyEvent += new sampleEventHandler(Add);
MyEvent += new sampleEventHandler(Substract);
MyEvent.Invoke(20,10);
Console.ReadLine();
}
// Event Handler methods
static void Add(int num1, int num2)
{
Console.WriteLine( $&quot Addition: {num1} + {num2} = {num1 + num2} &quot);
}
static void Substract(int num1, int num2)
{
Console.WriteLine($&quot Substraction: {num1} - {num2} = {num1 - num2} &quot);
}
}
}
```

![[{E6CFC870-4D8F-44D4-AC68-E2C4590C58D2}.png]]

[لینک عکس](https://l.vrgl.ir/r?ad=1&l=https%3A%2F%2Fwww.c-sharpcorner.com%2FUploadFile%2Fefa3cf%2Funderstanding-delegates-in-C-Sharp%2F&si=adgpcojxgkcj&st=post&k=g3NLOOMp4Tu%2Bupg4nKbmQego4dauq%2FcH8qaxpSdvSyQ%3D)

البته این رو بهتون بگم که من یک سری از کلاس آقای صادقی این ها رو یادگرفتم و برای تکمیل کردنش میایم یه مقاله مرتبط رو ترجمه میکنم. خیلی ممنونم از ایشون بخاطر تدریس عالی که داشتن.

لینک مقاله: [لینک](https://l.vrgl.ir/r?ad=1&l=https%3A%2F%2Fwww.shekhali.com%2Fcsharp-events%2F&si=adgpcojxgkcj&st=post&k=RgXsnLIQNjA5Ad5wCPwJUtG2dMQMtdzSWdMn7MtYKyU%3D)

