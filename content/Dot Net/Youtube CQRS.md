میخوایم این منطق رو سوار بر clean arc کنیم 
![[Pasted image 20251003002330.png]]

![[Pasted image 20251003002346.png]]

![[Pasted image 20251003002430.png]]

چک لیست برای سفر میخوایم داشته باشیم 

![[Pasted image 20251003002515.png]]

اول میایم یه blank soultion میسازیم 

![[Pasted image 20251003010200.png]]

```
dotnet new -n Final_SophieTravelManagment
```

بعدش میایم یه کلاس درست میکنیم 
```
dotnet new classlib -n Final_SophieTravelManagment.Domain
```

![[Pasted image 20251003010521.png]]

13:34

خوب در نظر داشته باشیم که توی این چک لیسته یه سری چیزا واجب و ضروریه مثل پاسپورت  

![[Pasted image 20251003020410.png]]

خوب ما میخوایم از بیرون کسی نتونه به این مقادیر دسترسی پیدا کنه که میایم اون رو private میکنیم ولی اینطوری درست نمیشه ، چرا ؟ چون که نمیتونیم برای id بیایم و private اش کنیم 

چون یه سری مشکل برامون به وجود میاره : 
مشکلات :

![[Pasted image 20251003021312.png]]

![[Pasted image 20251003021410.png]]

پس چی کار کنیم که کپسوله کنیمش ؟

خوب اگر بیایم و private رو برداریم و برای این که بخوایم کاری روی این entity انجام بدیم توی conroller این کار رو انجام بدیم 

ولی مشکل اینه که oop از بین میره و seperation of concerns درست که داریم ولی چون مبتنی بر oop نیست ، اشتبااااهههه اشتباه آقای کلاهدوزان میگه 

خوب راه حل اینه که از یه سری obj دیگه برای کامل کردن enitity مون استفاده کنیم ، که مهمترینشون value object ها هستن

میخوایم مشکلات enitity رو در Doimian با value obj حل کنیم 

کلی راه و روش دیگه هست که میتونیم ازشون استفاده کنیم 

حوبvalue object خودش مثل Enitit هستش ولی به تنهایی ارزشی نداره 

مثلا آدرس این رو داریم و میتونیم به هر Entity که دوست داریم بچسبونمیش ولی خودش هیج ارزشی به تنهایی نداره و نه id داره و نه کاری میشه باهاش کرد  

تایم 28

خوب توی کد از یه سری تبدیل های implicit  استفاده شده بود که اومدیم برای یادگیریش از deepseek کمک گرفتیم 

```C#
using System;
namespace LearnImplicitOperators

{
    // A custom ID class that wraps an integer
    public record UserId
    {
        public int Val { get; }
        public UserId(int InputValue)

        {
            if (InputValue <= 0)
                throw new ArgumentException("User ID must be positive");

            Val = InputValue;
        }

         // IMPLICIT OPERATOR: UserId → int (automatic conversion)

         public static implicit operator int(UserId userId) => userId.Val;
        // // EXPLICIT OPERATOR: int → UserId (requires cast)

         public static explicit operator UserId(int SomeValue) => new(SomeValue);
        // Factory method

        public static UserId CreateNew() => new(new Random().Next(1, 1000));

    }
    
    class Program
    {
        static void Main(string[] args)

        {

            Console.WriteLine("=== LEARNING IMPLICIT OPERATORS ===\n");
            // Create a UserId
            UserId userId = UserId.CreateNew();
            Console.WriteLine($"1. Created UserId: {userId.Val}");
            // // DEMO 1: Implicit conversion (UserId → int)

            // Console.WriteLine("\n--- IMPLICIT CONVERSION ---");

             int regularInt = userId; // ← MAGIC! No cast needed!

             Console.WriteLine($"UserId automatically converted to int: {regularInt}");

            // // DEMO 2: Using in methods that expect int

            // Console.WriteLine("\n--- USING IN METHODS ---");

             DisplayUserId(userId); // Pass UserId directly to method that expects int!

  

            // // DEMO 3: Using in calculations

            // Console.WriteLine("\n--- USING IN CALCULATIONS ---");

            int nextId = userId + 1; // Can do math directly!

             Console.WriteLine($"Next ID would be: {nextId}");

  

            // // DEMO 4: Using in collections

             Console.WriteLine("\n--- USING IN COLLECTIONS ---");

             var userDictionary = new Dictionary<int, string>();

             userDictionary[userId] = "John Doe"; // Automatic conversion!

             Console.WriteLine($"User in dictionary: {userDictionary[userId]}");

  

            // // DEMO 5: Explicit conversion (int → UserId)

            // Console.WriteLine("\n--- EXPLICIT CONVERSION ---");

             int someNumber = 42;

             UserId newUserId = (UserId)someNumber; // ← Requires explicit cast

             Console.WriteLine($"Created UserId from int: {newUserId.Val}");

  

            // // DEMO 6: Comparison

            // Console.WriteLine("\n--- COMPARISON ---");

             bool isEqual = userId == 123; // Works due to implicit conversion

            // Console.WriteLine($"Is userId equal to 123? {isEqual}");

  

            // // DEMO 7: Real-world scenario

            // Console.WriteLine("\n--- REAL-WORLD SCENARIO ---");

             ProcessUserOrder(userId, "Laptop");

        }

  

        // Method that expects regular int

        static void DisplayUserId(int id)

        {

            Console.WriteLine($"Displaying user ID: {id}");

        }

  

        // Simulate database operation

        static void ProcessUserOrder(UserId userId, string product)

        {

            // Note: We can use userId directly in string interpolation

            // because it implicitly converts to int!

            Console.WriteLine($"Processing order - User: {userId}, Product: {product}");

            // Simulate database call that needs int

            SaveToDatabase(userId, product); // Automatic conversion!

        }

  

        static void SaveToDatabase(int userId, string product)

        {

            Console.WriteLine($"SAVED to DB - UserId: {userId}, Product: {product}");

        }

    }

}
```

نکته ای که هست اینه که وقتی که توی کلاسمون یکی پارامتر داریم اوکیه ولی وقتی که چند تا باشن نمیشه ، مگر اینه که فقط برامون مهم باشه که با اون یدونه پارامتر اصلی مثلا id بخوایم کار کنیم 

کدی که خودم نوشتم برای یادگیری:

```C#
using System;

using System.Collections.Generic;

namespace Final_SophieTravelManagment.Domain.ValueObjects

{

    public record TravelerCheckListId

    {  

        public Guid Value { get; }

        public TravelerCheckListId(Guid value)

        {

            if (value == Guid.Empty)

            {

                throw new ArgumentNullException();
 

            }


            Value = value;

        }

        public static implicit operator TravelerCheckListId(Guid id) => new(id);

        public static implicit operator Guid(TravelerCheckListId id) => id.Value;


    }


    class Program

    {

        static void Main(string[] args)

        {

  

            // TravelerCheckListId Test = new(Guid.NewGuid());

  

            TravelerCheckListId Test = Guid.NewGuid();

  

            Guid MyGuid = Test;

  

            Console.WriteLine(Test.Value);

  

            //Guid GuidValue = Guid.Parse(Test.Value.ToString());

  
  
  

        }

    }

}
```


![[Pasted image 20251003111124.png]]

![[Pasted image 20251003111241.png]]

![[Pasted image 20251003111301.png]]

این مطالب بالا رو جدا کردم 

![[Pasted image 20251003094746.png]]

![[Pasted image 20251003094808.png]]

این قسمت بالا رو بعدا باید جدا کنم ببرم توی قسمت csharp چون که بیسیک هستش 

![[Pasted image 20251003111908.png]]

![[Pasted image 20251003111922.png]]


خوب حالا برای این که کار قشنگ تر بشه به جای این که همینطوری بیایم و یه exception رو بفرسیتم بالا میایم یه فولدر میسازیم به اسم exception 

30

![[Pasted image 20251004110745.png]]

![[Pasted image 20251004110922.png]]
این جا میاد message رو به کلاس parent پاس میده 
how to handle parent paramiter in child class in Csharp 

خوب حالا ما هر جایی توی سیستم که ex داشته باشیم اون میاد از این کلاسه که ساختیم استفاده میکنه 

![[Pasted image 20251004111315.png]]

خوب حالا میخوایم بیایم توی domian و ex های که اونجا اتفاق میوفته رو بنویسیم 

![[Pasted image 20251004111427.png]]

این میاد فقط ex هایی که مرتبط با id هستش رو پیدا میکنه 
![[Pasted image 20251004111558.png]]

![[Pasted image 20251004111631.png]]

میرسیم به value object ها 

![[Pasted image 20251004111939.png]]

![[Pasted image 20251004112034.png]]

![[Pasted image 20251004112053.png]]

![[Pasted image 20251004112132.png]]

![[Pasted image 20251004112454.png]]
![[Pasted image 20251004112705.png]]


![[Pasted image 20251004112817.png]]

![[Pasted image 20251004113040.png]]

![[Pasted image 20251004113117.png]]


خوب این رو اضافه میکنیم :

![[Pasted image 20251004122820.png]]


![[Pasted image 20251004122958.png]]

![[Pasted image 20251004123019.png]]
تا دقیقه 46
