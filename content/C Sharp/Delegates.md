A **delegate** in C# is a reference type variable that holds the reference to a method, similar to function pointers in C/C++. It serves as an object-oriented, secure, and type-safe way to invoke methods dynamically. Delegates are especially useful for implementing events and callback mechanisms, enabling event-driven programming. Defining a delegate's method signature guarantees type safety and enables the creation of variables capable of referencing any method that conforms to the specified signature. **Multicast delegates** enable referencing multiple methods, executing them sequentially upon invocation. Delegates in c# play a crucial role in event handling, asynchronous programming, and facilitating functional programming paradigms.

خوب delegate مثل یه متغییر reference type هستش که reference یه متد رو تو خودش نگه میداره.

با این کار یک راه type safe رو برای صدا کردن متد ها به صورت dynamically به ما میده.

برای پیاده سازی ایونت ها و callback ها و برنامه نویسی event driven به کار میاد.

یه قابلیت دیگه ای که داره multicast delegate اینه که میتونیم به مرجع چند تا متد اشاره کنیم و جداگونه اجراشون کنیم .

و این که delegate نقش خیلی مهمی داره توی برنامه نویسی asynchoronous و functional .

## Declaration of Delegates in C#

The **delegate** keyword in C# is used to declare a delegate type. Once the delegate type is defined, you can create delegate instances that refer to methods with compatible signatures. Here's the syntax for declaring a delegate:

```csharp
[modifier] delegate [return_type] [delegate_name] ([parameter_list]);
```

- **modifier:**  
    Optional access modifier, like public, private, protected, or internal.
- **return_type:**  
    The return type of the method the delegate can point to.
- **delegate_name:**  
    The name of the delegate type.
- **parameter_list:**  
    The list of parameters (if any) with their types and names. These must match the parameters of the methods the delegate can reference.


تعریف delegate:

خوب از کلمه delegate برای تعریف تایپ delegate استفاده میکنیم.

حالا بریم که یه مثال داشته باشیم :




```csharp
//Example of delegates declaration in c#
using System;

// Declaration of a delegate named MathOperation that takes two integers as //parameters and returns an integer.
delegate int MathOperation(int a, int b);

public class Calculator
{
    // A method that performs addition
    public static int Add(int a, int b)
    {
        return a + b;
    }

    // A method that performs subtraction
    public static int Subtract(int a, int b)
    {
        return a - b;
    }
}
```

## Instantiation and Invocation of Delegates

Once we declare a delegate type in C#, a delegate object needs to be created and associated with a specific method that has a matching signature. This process is called "**instantiating the delegate**". Here's the syntax for the instantiation of a delegate:

`[delegate_name] [instance_name] = new [delegate_name](calling_method_name);`

خوب میرسیم به قسمتی که میخوایم یه نمونه بسازیم از delegate یا وقتی که میخوایم invoke کنیم delegate رو باید چی کار کنیم.

خوب حالا اومدیم و یه delegate تعریف کردیم این آبجکت delegate به یک یا چند متدی که یه مدل خاصی هستن نیاز داره.

This syntax is used to create an instance of the delegate _delegate_name_ and associate it with a specific method named calling_method_name that matches the delegate's signature. Once the delegate instance is created, you can use it to invoke the associated method by calling it like a regular method, passing the required parameters.

خوب حالا میایم ازش یه نمونه درست میکنیم و بعد میتونیم متد هایی که مرتبط باهاش هستند رو call کنیم حالا اگر اون متد ها متغییر ورودی هم داشتن همون موقع بهشون میدیم.

In the above example we created an instance of the MathOperation delegate named addDelegate and associated it with the Calculator.Add method using new MathOperation(Calculator.Add). Finally, we invoked the delegate addDelegate with the arguments 5 and 3, resulting in calling the Calculator.Add method, and stored the return value in the result variable. The output will show the result of the addition.

حالا توی خوده مثال توضیحاتش اومده :

```csharp
using System;
delegate int MathOperation(int a, int b);
public class Calculator
{
    // A method that performs addition
    public static int Add(int a, int b)
    {
        return a + b;
    }

    // A method that performs subtraction
    public static int Subtract(int a, int b)
    {
        return a - b;
    }
}

public class Program
{
    static void Main()
    {
        // Create an instance of the MathOperation delegate and associate 
        //  it with the Add method.
        MathOperation addDelegate = new MathOperation(Calculator.Add);

        // Invoke the delegate, which in turn calls the Add method.
        int result1 = addDelegate(5, 3); //

        // Create another instance of the MathOperation delegate and //associate it with the Subtract method.
  MathOperation subtractDelegate = new MathOperation(Calculator.Subtract);

        // Invoke the delegate, which in turn calls the Subtract method.
        int result2 = subtractDelegate(8, 2);
        Console.WriteLine(result1);
        Console.WriteLine(result2);
    }
}
```

خروجی میشه 8 و 6

## C# Delegates Multicasting

**Multicasting of a delegate** in C# allows you to combine multiple methods into a single delegate instance. When you invoke the delegate, all the associated methods are called in the order they were added to the delegate. This feature is useful when you want to execute multiple methods sequentially through a single delegate call.

این قابلیت multiCasting اینطوریه که میتونیم چند تا متد رو توی یه نمونه ساخته شده از delegate بچپونیم.

وقتی که اون delegate رو invoke میکنیم تمام اون متد هایی توش ریخته بودیم با همون ترتیبی هم که توش ریخته بودیم call میشن. زمانی به کار میاد که بخوایم چند تا متد جداگانه رو با یه delegate اجرا کنیم.

Multicasting delegates are especially useful when you want to perform multiple operations through a single callback or event handler. They provide a convenient way to implement event notification systems, where multiple subscribers can register their methods with a single delegate, and all subscribers receive notifications when the event is raised.

زمانی که بخوایم چند تا کار رو با یه callback یا یه event handler انجام بدیم.

```csharp
using System;

// Declare a delegate type that takes an integer parameter and returns void.
delegate void MyDelegateType(int value);

class Program
{
    // Method1: Sample method to be associated with the delegate
    static void Method1(int value)
    {
        Console.WriteLine($'Method1: {value}');
    }

    // Method2: Another sample method to be associated with the delegate
    static void Method2(int value)
    {
        Console.WriteLine($'Method2: {value}');
    }

    static void Main()
    {
        // Create an instance of the MyDelegateType delegate and associate it with Method1.
        MyDelegateType myDelegate = Method1;

        // Multicasting: Add Method2 to the delegate.
        myDelegate += Method2;

        // Invoke the delegate, which will call both Method1 and Method2.
        myDelegate(42);
    }
}
```

**Output:**

```csharp
Method1: 42 Method2: 42
```

`مثال بعدی:`

```csharp
using System;

// Declare a delegate for arithmetic operations
delegate double ArithmeticOperation(double x, double y);

class Calculator
{
    // Method to perform addition
    static double Add(double x, double y)
    {
        return x + y;
    }

    // Method to perform subtraction
    static double Subtract(double x, double y)
    {
        return x - y;
    }

    // Method to perform multiplication
    static double Multiply(double x, double y)
    {
        return x * y;
    }

    // Method to perform division
    static double Divide(double x, double y)
    {
        if (y == 0)
        {
            throw new ArgumentException('Cannot divide by zero.');
        }
        return x / y;
    }

    static void Main()
    {
        // Create delegate instances and assign methods to them
        ArithmeticOperation addDelegate = Add;
        ArithmeticOperation subtractDelegate = Subtract;
        ArithmeticOperation multiplyDelegate = Multiply;
        ArithmeticOperation divideDelegate = Divide;

        // Perform arithmetic operations using delegates
        double x = 10;
        double y = 5;

        double resultAdd = addDelegate(x, y);
        double resultSubtract = subtractDelegate(x, y);
        double resultMultiply = multiplyDelegate(x, y);
        double resultDivide = divideDelegate(x, y);

        // Display the results
        Console.WriteLine($'Addition: {x} + {y} = {resultAdd}');
        Console.WriteLine($'Subtraction: {x} - {y} = {resultSubtract}');
        Console.WriteLine($'Multiplication: {x} * {y} = {resultMultiply}');
        Console.WriteLine($'Division: {x} / {y} = {resultDivide}');
    }
}
```


https://www.scaler.com/topics/csharp/delegate-in-csharp/


