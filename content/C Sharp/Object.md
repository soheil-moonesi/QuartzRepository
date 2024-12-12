مرجع: [سایت](https://l.vrgl.ir/r?ad=1&l=https%3A%2F%2Fwww.geeksforgeeks.org%2Fc-sharp-object-class%2F&si=zomctsmeckku&st=post&k=7IIIvI51vdFQIF8vxhLwKGiPYrfC14cVEXlbqTDh4UY%3D)

خوده آبجکت یک سری متد داره که ما میتونیم ازشون استفاده کنیم:

![[{8E7D4DD2-AA2B-4DDC-A9E9-18AED38B7960}.png]]

این رو به عنوان یه توضیح ابتدایی گذاشتیم و جلوتر میایم یکی یکی بررسیشون میکنیم.

There are two types in C# i.e **[Reference types and Value types](https://l.vrgl.ir/r?ad=1&l=https%3A%2F%2Fwww.geeksforgeeks.org%2Fc-data-types-2%2F&si=zomctsmeckku&st=post&k=3fGVYowM3ieWsZscP7Nn6GrmecHbtl1TdTgGCEAStXg%3D)**. By using System.ValueType class, the value types inherit the object class implicitly. System.ValueType class overrides the virtual methods from Object Class with more appropriate implementations for value types. In other programming languages, the built-in types like int, double, float, etc. do not have any object-oriented properties. To simulate the object-oriented behavior for built-in types, they must be explicitly wrapped into the objects. But in C#, we have no need for such wrapping due to the presence of value types that are inherited from the System.ValueType that is further inherited from System.Object. So in C#, value types also work similarly to reference types. Reference types directly or indirectly inherit the object class by using other reference types.

![[{4F1B6AC1-2E50-4E19-B18F-5B05B6903D98}.png]]

تمام شی ها در آخر از کلاس Object ارث بری میکنند.

```csharp
public class Object {
public Object();
public static bool equals(Object? objA,Object? objB);
public static bool RefrenceEquals(Object? objA,Object? objB);
public virtual bool Equals(object? obj);
public type GetType();
public virtual string?ToString();
protected Object MemberWiseClone();
}
```

Copy
به این مثال دقت کنید:

```csharp
int i = 5; 
string Name='soheil'
Car car = new Car();
Console.WriteLine(i);
Console.WriteLine(Name);
Console.WriteLine(car);
```

Copy
خوب اینجا دقت کنید ، اتفاقی که افتاده اینه که برای متد WriteLine از قبل overload های مختلفی در نظر گرفته شده ، یعنی وقتی که string میفرستیم داخلش متد WriteLine که آرگومان استرینگ میگیره کال میشه و وقتی که تایپ ورودی از نوع کلاس (آبجکت) باشه متد با آرگومان ورودی آبجکت کال میشه.

نکته: زمانی که این آرگومان ها داخل متد WriteLine میشن، به طور اتومات از تابع ToString استفاده میشه.

خروجی کد بالا به این شکل هستش:

![[{977507FF-5502-4746-A4B3-7B0E7FBA0AFC}.png]]

از این تابع بالا استفاده شده و همنطور که میبینید چون virtual تعریف شده پس ما میتونیم override کنیم روش.

قبل از این که override اش کنیم باید بگیم که عملکرد معمولی این تابع به این صورته که وقتی که آبجکت رو واردش میکنیم میاد و namespace و بعد اسم اون آبجکت رو در خروجی چاپ میکنه : project1.Car حالا ما میخوایم override کنیم که عملکردش رو تغییر بدیم به اون چیزی که خودمون میخوایم.

حالا میایم داخل کلاس Car این overriding رو به این شکل انجام میدیم :

```csharp
namespace Project1
{
public class Car
{
public string Name{ get; set; }
public override string ToString()
{
return $' car name is : {Name} '
}
}
}
```

Copy

حالا به این شکل اول به طور مثال به Name مقدار میدیم و بعد نتیجه رو میبینیم :

![[{8E1E7DD7-4E4B-4F99-B95F-AD3B44636A6C}.png]]

حالا در خروجی کلمه benz چاپ میشه .