خوب میخوایم برنامه ای بنویسیم که مساحت اشکال مختلف هندسی رو محاسبه کنه.

در ابتدای کار باید بیایم یه کلاس پایه درست کنیم، اسمش رو میزاریم shape خوب shape رو طبیعتا باید به شکل abstract تعریفش کنیم چرا که shape یه تعریف کلی هستش و نیازی نیست که ازش بخوایم با new نمونه بسازیم.

حالا بعدش میایم دو تا کلاس دیگه تعریف میکنیم که هر دو از shape ارث بری میکنند به اسم های Rectangle و circle .

```csharp
     public class Rectangle:Shape
   {
        public int Width { get; set; }
        public int Height { get; set; }
    }

public class Circle:Shape    {  
       public doubele R { get; set; }
        }

   public abstract class Shape
{
        public void CalcArea(Circle c){       }
 public void CalcArea(Rectangle r){       }
    }
```

خوب در این حالت مشکلی که هست اینه که برای هر شی یا شکل هندسی که میخوایم اضافه کنیم باید بیایم متد محاسبه مساحت رو در کلاس پایه shape اضافه کنیم.

حالا بیاید در نظر بگیریم که این کلاس پایه shape داخل یک library درست شده و ما میخوایم ازش استفاه کنیم و حالا اتفاقی که میوفته اینه که ما میخوایم یه شکل هندسی جدید که داخل اون کتابخونه نیست رو مساحتش رو بدست بیاریم، حالا باید چی کار کنیم؟

راه حل اول :

![[{147D9694-12FD-4699-A293-87D7E7376609}.png]]

و بعدش اگر دلمون خواست میریم داخل هر کدوم از کلاس اشکال و override میکنیم :

```csharp
public class Rectangle:Shape    {    
     public int Width { get; set; }   
      public int Height { get; set; }

public override double CalcArea(){
return base.CalcArea();
}
     }
```

خوب حالا اینجا مشکلی که پیش میاد اینه که ما ممکنه بیایم و اشتباهی از متد CalcArea که داخل کلاس پایه shape هستش استفاده کنیم. حالا برای رفع این مشکل چی کار کنیم؟ بیایم متد رو هم از نوع abstract تعریف کنیم.

![[{F434C5C3-D17F-4886-A41E-68EE55A98B60}.png]]

نکته ای که وجود داره اینه که متد abstract باید داخل کلاس abstract باشه و اگر نه به ارور برمیخوریم.

حالا این به چه کاری میاد - این کار باعث این میشه که ما هر کلاسی که از کلاس shape ارث بری کرده باشه ، الان دیگه باید متد CalcArea رو داخلش پیاده سازی کنه.

نکته ای که وجود داره همین کارهایی که برای متد کردیم رو هم میتونیم برای پراپرتی ها هم انجام بدیم.

حالا برای این که موارد بیشتر و کارایش رو بهتر متوجه بشیم همون مثال قبل رو ببریم جلو تر

```csharp
public abstract class Shape {       
    public abstract double CalcArea();  
 }
 }
public abstract class Shape2 : Shape
{
}```

حالا دقت کنید که اینجا با این که کلاس shape2 از کلاس shape ارث بری کرده ولی بدون این که متد CalcArea رو پیاده سازی کنیم اروری نداریم و دلیلش هم اینه که کلاس shape2 خودش از نوع abstract هستش.

خوب حالا اینجا میتونیم یه کار جالب تر دیگه هم بکنیم اینه که میتونیم یه سری متد رو هم به صورت abstract در shape2 بنویسیم و اینطوری کلاسی که از shape2 ارث بری میکنه هم باید متد های های abstract داخل shape رو پیدا سازی کنه و هم متد های abstract کلاس shape2 رو :

البته اینجا به جای متد اومدیم یه پراپرتی اضافه کردیم.


```csharp
public abstract class Shape {  
          public abstract double CalcArea();    
 }
 public abstract class Shape2 : Shape { 
        public abstract double Perimeter { get; set; }
}
public class Final  : Shape2{
public override double Perimeter { get; set; }
public override double CalcArea(){
return 0;
}
}
```

حالا بیایم و یه ویژگی دیگه این abstract ها رو ببینیم:

```csharp
    public abstract class Shape
    {
        public abstract int Side{get; set;}
    public abstract double CalcArea();
}
public abstract class Shape2 : Shape
{
        public override int Side => 5;
     public abstract double Perimeter { get; set; }
 }
 public class Final : Shape2
{
    public override double Perimeter { get; set; }
        public override int Side { set => throw new NotImplementedException(); }
        public override double CalcArea()
        {
            return 0;
        }
}
```

اینجا توی کلاس final دیگه نیازی نیست که side رو مقدار دهی کنیم چون داخل کلاس shape2 بهش مقدار دادیم.
