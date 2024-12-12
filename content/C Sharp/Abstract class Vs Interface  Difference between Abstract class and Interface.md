حالا میرسیم به قسمت جالب انگیز ماجرای سی شارپ که میاد مقایسه میکنه abstract class رو با interface

این مقاله از این [سایت](https://l.vrgl.ir/r?ad=1&l=https%3A%2F%2Fwww.shekhali.com%2Finterface-vs-abstract-class%2F&si=jfnebtdxxcp3&st=post&k=YPh2uPvgln8mhnR61UqviibALIo5WeCcBb2xm2UqNNo%3D) گرفته شده.

![[{B53B4CCF-2FE7-4B60-8D1B-4C634E3B4AD1}.png]]

و همونطوری که میبینید نکاتی رو هم که میگه به ۲ قسمت تقسیم میکنه یکی قبل از C# 8 و یکی بعد از c# 8

## What is Abstract class in C#?

An abstract class in C# is a class that **cannot be directly instantiated** using the `new` keyword and always acts as a **base class for other classes**.

Abstract classes are created using the **abstract keyword**. They provide a common structure for derived classes to follow. The key characteristics of [abstract classes in C#](https://l.vrgl.ir/r?ad=1&l=https%3A%2F%2Fwww.shekhali.com%2Fcsharp-abstract-class-with-examples%2F&si=jfnebtdxxcp3&st=post&k=aDbFVm70W2seYabTDHmie1JpNNiTYYdl35%2BSZW%2F2f4Y%3D) include:

- Abstract classes in C# can **contain abstract methods** without actual code implementation. These methods must be implemented in the derived classes.
- Abstract classes can also have **non-abstract methods** with actual code. Derived classes can inherit and, if needed, override these methods.
- Unlike other classes, abstract classes in C# **can’t be sealed**. It means other classes can extend them further.
- Abstract classes **can have constructors, but you can’t create objects from them directly**. Instead, objects of the abstract class are created using derived class constructors.

خوب اول میاد توضیح میده که abstract class اصلا چیه؟

تعریفش اینطوریه که کلاسیه که نمیتونیم مستقیم از طریق new ازش نمونه بگیریم و بسازیمش و همیشه مثل کلاس پایه برای بقیه کلاس ها استفاده میشه

کلاس های abstract رو با استفاده از کلمه کلیدی abstract میسازیم . این مدل کلاس ها یه ساختاری رو فراهم میکنند که کلاس های مشتق گرفته شده باید از اون ساختار پیروی کنند.

مشخصاتشون اینه :

کلاس های abstract میتونن حاوی abstract method ها باشن که هیچ پیاده سازی کدی براشون تعیین نشده که این یعنی این که این متد ها باید در کلاس های مشتق شده باید پیاده سازی شوند.

کلاس های abstract میتونن حاوی non-abstract method که پیاده سازی هم داخلشون انجام شده، باشند و کلاس های مشتق شده ازشون هم میتونن از این متد ها ارث بری کنند و اگر لازم بود این متد ها رو override کنند.

برخلاف کلاس های عادی، کلاس های abstract بسته نمیشن ، به این معنی که کلاس های دیگه میتونن بهش extend بشن. ( جلوتر توضیح بهتر میده)

کلاس های abstract میتونن constructor داشته باشن ولی ما نمیتونیم مستقیما ازشون آبجکت درست کنیم. باید از طریق constructor کلاس هایی که ازش مشتق گرفته شدن برای ساختن آبجکت استفاده کنیم.

```csharp
using System;
 // Define an abstract class called 'Shape' 
abstract class Shape { 
// An abstract method for calculating area, to be implemented by derived classes.
 public abstract double CalculateArea(); 
// A non-abstract method with a default implementation.
 public void DisplayArea() { 
       Console.WriteLine('Area: ' + CalculateArea()); }
 } 
// Create a derived class 'Circle' that inherits from 'Shape'
 class Circle : Shape {
 private double radius; 
// Constructor to initialize the radius 
public Circle(double r) {  
      radius = r; }
 // Implement the abstract method to calculate the area of a circle.
 public override double CalculateArea() { 
return Math.PI * radius * radius; } 
} 
class Program { 
static void Main() {
 // Create an instance of the 'Circle' class
 Circle circle = new Circle(5.0);
 // Calculate and display the area of the circle  
   circle.DisplayArea(); } 
}
```

Copy

**Code Explanation:**

- We define an abstract class `Shape` with an abstract method `CalculateArea()` that should be implemented by derived classes. It also has a non-abstract method `DisplayArea()` with a default implementation.
- We create a derived class `Circle` that inherits from `Shape`. It provides an implementation for the `CalculateArea()` method.
- In the `Main` method, we create an instance of the `Circle` class, set its radius, and then call the `DisplayArea()` method to calculate and display the area of the circle.

توضیح کد :

اینجا اومدیم یه کلاس abstract تعریف کردیم به اسمه shape با یه abstract method به اسمه calculatedArea که این متد باید در کلاسی که از این کلاس پایه مشتق گرفته میشه، پیاده سازی بشه

حالا یه متد non-abstract هم به اسم displayArea تعریف کردیم که پیاده سازیش به صورت معمولی انجام شده (یعنی کدش رو داخل همون کلاس نوشتیم).

تو مرحله بعد اومدیم یه مشتق از کلاس پایه shape گرفته شده به اسم circle که از shape ارث بری میکنه ، حالا توی این قسمت مجبور میشیم که متد calculatedArea رو پیاده سازی کنیم داخل کلاس circle.

در مرحله ی بعد اومدیم توی قسمت main از کلاس circle یه نمونه گرفتیم بهش مقدار شعاع رو دادیم و بعد هم از متد displayArea استفاده کردیم برای محاسبه و نمایش مساحت دایره.

## What is Interface in C#?

An interface in C# is a blueprint for defining **a contract that specifies a set of methods, properties, events, or indexers a class must implement**.

Unlike abstract classes, an **interface contains only method and property signatures but no method implementations**.

Here are the key characteristics of an [interface in C#](https://l.vrgl.ir/r?ad=1&l=https%3A%2F%2Fwww.shekhali.com%2Fcsharp-interface%2F&si=jfnebtdxxcp3&st=post&k=VbQz1XA8p9a9Vybf7o58RmSP3aedGq7E%2FQH%2Bqpgbcwo%3D):

- **Purely Abstract:** Interfaces contain only method signatures, properties, events, or indexers without implementations.
- **Multiple Inheritance:** A class can implement multiple interfaces, which allows inheriting behaviors from several sources.
- **Contract Enforcement:** When a class implements an interface, it’s bound to fulfill a contract by providing members (method, properties etc.) implementation with the correct signatures.
- **Polymorphism:** Interfaces enable polymorphism, allowing objects of different classes to be treated as instances of the interface type.

حالا میرسیم به توضیح interface ها ، interface ها یه جورایی میشه قراردادی که برای تعیین متد ها و پراپرتی ها و ایونت ها و کلاس هایی که باید پیاده سازی بشن.

برخلاف کلاس های abstract ، اینترفیس ها شامل فقط امضا متد ها و پراپرتی ها هستند ولی هیچ پیاده سازی متد ای داخلش نداریم.

مشخصات اینترفیس ها:

فقط داخلش امضا متد ها ، پراپرتی ها ، ایونت ها هستش، بدون پیاده سازیشون.

ارث بری چند تایی: یه کلاس میتونه از چند تا اینترفیس ارث بری کنه

وقتی که یه کلاس از یه اینترفیس ارث بری میکنه به این معنی هستش که باید به قرارداد هایی که توسط اون اینترفیس تعیین شده باید عمل کنه.

```csharp
using System;
 // Define an interface named 'IDrawable'
 interface IDrawable {
 void Draw();
 } 
// Create a class 'Circle' that implements the 'IDrawable' interface
 class Circle : IDrawable { 
 public void Draw() {       
 Console.WriteLine('Drawing a circle');
 } 
} 
  class Program {
  static void Main() { 
  Circle circle = new Circle();     
  circle.Draw();
  // Calls the 'Draw' method implemented in the 'Circle' class.
  IDrawable drawable = circle; 
 // Polymorphism: Treating 'circle' as an 'IDrawable'.        
 drawable.Draw();
 // Still calls the 'Draw' method in the 'Circle' class. 
} 
}
```



و در اینجا اومدیم اینترفیسی استفاده کردیم به اسم IDrawable که داخلش void Draw رو قرار دادیم و بعد اومدیم و بعد اومدیم به کلاس circle رو از اینترفیس IDrawable ارث بری کردیم، به این معنی که در کلاس circle باید متد Draw پیاده سازی شود.

حالا در کلاس program میایم با استفاده از new یک نمونه از Circle میسازیم و بعد میایم از متد draw داخلش استفاده میکنیم.

نکته :

`IDrawable drawable = circle;`

اینجا با توجه به ویژگی polymorphisim اومدیم circle رو داخل متغییری از جنس IDrawable که یک اینترفیس هست ریختیم و همچنان هم میتونیم از متد draw استفاده کنیم.

![[{5E4528A1-0559-4FCC-9E49-83F3020D7B38}.png]]

## اینترفیس ها همه اعضای داخلشون باید public باشن ولی abstract ها میتونن دسترسی های متفاوت داشته باشن.

اینترفیس ها نمیتونن constructor داشته باشن ولی abstract ها میتونن

اینترفیس ها قابلیت چند ارث بری دارند ولی abstract ها ندارن

اینترفیس ها داخلشون نمیتونیم پیاده سازی انجام بدیم ( این قابلیت از C# 8 به بعد تغییر کرده) ولی داخل کلاس های abstract میشه .

اعضای داخل اینترفیس ها نمیتونن abstract , virtual , static , sealed داشته باشن ولی کلاس های abstract این قابلیت رو دارن.

اینترفیس ها نمیتونن داخلشون field داشته باشن( این قابلیت توی C# 8 به بعد تغییر کرده)

  

  

## **Important Key Points About An Interface In C# 8.0**

- the Interface can implement code for methods, properties, events, or indexers .An interface can have only the declarations part that is no longer true. AfterC# 8.0
- .In C# 8, interface members can have access modifiers such as **private**,**public**,**protected**,**internal**,**virtual**,**abstract**,**override**,**static**, and **sealed**
- In C# 8, the Interface can have fields, but only if they are static.
- In C# 8, An interface can have default methods but the derived class inherited by the Interface does not know anything about the existence of the default methods also class does not contain the implementation code of the default method defined in the Interface.
- The default interface members are not inherited in the derived class in C# 8.

دقت ، مهم ، نکته ی امتحانی

ببینید از C# 8 به بعد کلا یه بیل زدن به این قسمت interface ها و یه تغییرات یا بهتره بگم یه سری فیچر جدید بهش اضافه کردن

خوب یه قابلیت جدیدیش اینه که میتونید متد و پراپرتی و ایونت و ... رو داخلش پیاده سازی کنید ، ولی قبلا فقط میشد داخل اینترفیس معرفی شون کنیم.

قابلیت بعدی اینه که اعضای اینترفیس ها میتونن access modifires داشته باشن ، قبلا فقط میتونستن public باشن

قابلیت بعدیش اینه که اینترفیس ها میتونن فیلد هم داشته باشن البته به شرطی که static باشه.

حالا این 2 تا آخری رو دقیق متوجه نشدم ، برای همین دوباره مراجعه کردم به سایتش و براش یه مثال زده که اون رو میزارم اینجا و بعد با هم تحلیلش میکنیم:

### Default Interface Methods Introduced In C# 8.0

The Default interface method which is also known as the virtual [extension method](https://l.vrgl.ir/r?ad=1&l=https%3A%2F%2Fwww.shekhali.com%2Fc-extension-methods%2F&si=jfnebtdxxcp3&st=post&k=Bf11OO3GB%2FKpgtO2SDfZumdsvret3TPZGqfN95nwID0%3D) is a new feature introduced in C# 8.0

It allows an Interface to add a method with implementation without breaking the existing functionality

```csharp
using System;
namespace DefaultInterfaceMethodDemo
{
// Default Interface Method In C# 8.0
interface IDefaultInterface
{
// This 'ShowMessage' method is having only the declaration part.
void ShowMessage(string text);
// Default interface method with both declaration and definition
//(Implementation).
//Now Interface members can be public, private, or protected
public void DefaultInterfaceMethod()
{
Console.WriteLine('Default method of interface!');
}
}
// A class that implements
// the 'IDefaultInterface' interface.
class MyClass : IDefaultInterface
{
// Providing implementation
// part of the 'ShowMessage' method
void IDefaultInterface.ShowMessage(string text)
{
Console.WriteLine(text);
}
}
class Program
{
static void Main()
{
IDefaultInterface myClass = new MyClass();
// Calling default interface method
myClass.DefaultInterfaceMethod();
myClass.ShowMessage('Hello World!');
Console.ReadLine();
}
}
}
// Output
// Default method of interface!
// Hello World!
```


خوب ببینید اینجا یه قابلیت جالبی به اینترفیس ها اضافه شده اینه میتونیم یه متدی رو توی اینترفیس پیاده سازی کنیم ولی این متد لزوما میتونه توی کلاس هایی که دارن استفاده میکنند پیاده سازی نشه و فقط وقتی که میخوایم ازش استفاده کنیم بیایم و call اش کنیم.

خوب اینجا متد defaultInterfaceMethod رو داخل اینترفیس IDefaultInterface پیاده سازی کردیم ولی همونطوری که میبینید توی کلاس MyClass که از این اینترفیس داره استفاده میکنه ولی متد defaultInterfaceMethod داخلش پیاده سازی نشده ، حالا میخوایم از این متد استفاده کنیم ، چی کار کنیم؟

دقت ، باید بیایم بعد این که از کلاس نمونه میسازیم بریزیمش داخل متغییر با تایپ اون اینترفیسی که میخوایم از اون متد داخلش استفاده کنیم :

`IDefaultInterface myClass = **new**` `MyClass();`  

نکته : میتونیم از اینترفیس در ورودی متد هامون یا همون آرگومان متدمون ازش استفاده کنیم، اینطوری:

static void Draw( IShape shape){ }

باز هم نکته : ما میتونیم از اینترفیس ها برای صدا زدن یک متد با تایپ های مختلف استفاده کنیم، مثال:

```csharp
Circle c = new Circle();
IShape1 shape1 = c;
IShape2 shape2 = c;

shape1.Draw();
shape2.Draw();
------
public class Circle :IShape1,IShape2 {
void IShape1.Draw(){
Console.WriteLine('shape 1');}
Void IShape2.Draw(){
Console.WriteLine('shape 2');}
}
Void Draw(){ Console.WriteLine('shape');} }
------
public interface IShape1 {
void Draw();}
public interface IShape2 {
 void Draw();}
```


این رو به خاطر داشته باشید که کلاس Circle از هر دو تا اینترفیس داره استفاده میکنه .

خوب همونطوری که میبینید متد Draw رو اومدیم توی 2 تا اینترفیس معرفی کردیم. حالا اومدیم با پیاده سازی اختصاصی متد Draw برای هر کدوم از اینترفیس ها به این شکل عمل کردیم. یعنی هر کدوم از متد ها با توجه نوع تایپ و اینترفیسی که براش تعیین کردیم صدا زده میشه.

دیگه نکته ی آخره :

خوب حالا فرض کنید که یه متد general هم داریم که اون هم Draw هستش حالا چطوری از ازش استفاده کنیم؟

اینطوری:

c.Draw()

حالا فرض کنید که به صورت اختصاصی IShape 2 رو پیاده سازی نکرده باشیم . در این حالت هم میاد متد general رو صدا میکنه.