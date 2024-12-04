مبحث بسیار جالب Params :

The ‘params’ keyword in C# allows a method to accept a variable number of parameters. The keyword simplifies the method signature, making it easier to read and maintain. It is particularly useful when the exact number of parameters cannot be predetermined, or when you want to provide a more flexible method for developers.

خوب Params بهمون این قابلیت رو میده که به یه متد هر چقدر که حال کردیم پارامتر بدیم، خوندن و نگهداری کد رو هم راحت تر میکنه، زمانی به کار میاد که معلوم نیست چند تا پارامتر باید تعریف کنیم یا زمانی که میخوایم متدمون منعطف باشه.

پارامز این شکلیه تعریف میشه

public static void MyMethod(params int[] numbers)

{

_// Method implementation goes here_

}

حالا ببینیم کجا استفاده میشه در عمل:

```csharp
Summing multiple integer values:
public static int Sum(params int[] numbers)
{
int sum = 0;
foreach (int number in numbers)
{
sum += number;
}
return sum;
}
```

حالا اینطوری ازش استفاده میکنیم:

int result = Sum(1, 2, 3, 4, 5);

Console.WriteLine(result); _// Output: 15_

```csharp
Concatenating multiple string values:
public static string Concatenate(params string[] strings)
{
StringBuilder sb = new StringBuilder();
foreach (string s in strings)
{
sb.Append(s);
}
return sb.ToString();
}
```

اینطور هم ازش استفاده میکنیم:

string result = Concatenate("Hello", " ", "World", "!");

Console.WriteLine(result); _// Output: Hello World!_

_فواید و مضرات استفاده از Params_

_:D_

_خوب اول از فوایدش شروع میکنیم:_

_انعطاف: زمانی که نمیدونیم متدمون قراره چند تا پارامتر ورودی بگیره_

```csharp
public static int Multiply(params int[] numbers)
{
int product = 1;
foreach (int number in numbers)
{
product *= number;
}
return product;
}
int result1 = Multiply(2, 3);
int result2 = Multiply(4, 5, 6);
Console.WriteLine(result1); // Output: 6
Console.WriteLine(result2); // Output: 120
```

_خوانایی:_

```csharp
public static void PrintStrings(params string[] strings)
{
foreach (string s in strings)
{
Console.WriteLine(s);
}
}
PrintStrings(&quotHello&quot, &quotWorld&quot, &quotC#&quot);
```

نگهداری: دیگه نمیخواد برای هر تعداد ورودی بیایم یه متد overload درست کنیم

```csharp
// With params keyword
public static int Add(params int[] numbers)
{
int sum = 0;
foreach (int number in numbers)
{
sum += number;
}
return sum;
}
// Without params keyword (multiple overloads)
public static int Add(int a, int b)
{
return a + b;
}
public static int Add(int a, int b, int c)
{
return a + b + c;
}
public static int Add(int a, int b, int c, int d)
{
return a + b + c + d;
}```

مضرات :

Performance:

Performance: Since the ‘params’ keyword uses arrays to store parameters, it can lead to performance overhead, especially when dealing with large numbers of parameters. This is because the runtime creates a new array every time a method with the ‘params’ keyword is called, even if no arguments are passed. If performance is a critical concern in your application, it might be worth considering alternative approaches, such as using method overloads or generic methods.

خوب چون params رو وقتی که استفاده میکنیم میاد از array برای ذخیره کردن پارامتر ها استفاده میکنه که همین میتونه باعث سنگین شدن سیستم و افت در اجرای برنامه مون بشه زمانی که پارامتر هایی خیلی زیاد رو بخوایم واردش کنیم. دلیل بعدی اینه که هر سری متد که params داشته باشه رو صدا میزنیم یه آرایه جدید رو میسازه(حتی اگر هیچ پارامتر رو هم نفرستیم براش این اتفاق میوفته). اگر بازدهی یا سرعت برنامه خیلی براتون مهمه بهتره که یه تجدید نظر بکنید برای استفاده از params و به جاش بیاید از overload ها یا generic method ها استفاده کنید.

```csharp
using System.Diagnostics;
public static void PrintNames(params string[] names)
{
foreach (string name in names)
{
Console.WriteLine(name);
}
}
// Measure the time taken to execute the method with 'params' keyword
Stopwatch sw = Stopwatch.StartNew();
PrintNames(&quotAlice&quot, &quotBob&quot, &quotCharlie&quot);
sw.Stop();
Console.WriteLine(&quotTime taken (ms): &quot + sw.ElapsedMilliseconds);
```

Limited to a single array: You can only use one ‘params’ array per method, which means you cannot have multiple variable-length parameter lists. This limitation can be restrictive in cases where you need to accept multiple sets of variable-length arguments. In such scenarios, you might need to use alternative solutions like passing multiple arrays or using tuples.

محدودیت که داریم اینه که فقط میتونیم از یک Params استفاده کنیم برای هر متدی ، این یعنی این که نمیتونیم چند تا آرایه با تعداد های متفاوت داشته باشیم، توی این حالت یا باید چند تا آرایه رو بفرستیم یا از tuples ها استفاده کنیم.

_// This code will result in a compilation error_

public static void InvalidMethod(params int[] numbers, params string[] strings)

{

_// Method implementation_

}

Type restriction: The ‘params’ keyword can only be used with single-dimensional arrays. While this restriction is not usually a major concern, it does limit the data structures that can be used with the ‘params’ keyword. If you need to work with more complex data structures, such as multi-dimensional arrays or collections, you may need to explore other methods for passing variable-length arguments.

محدودیت تایپ هم داریم به این معنی که فقط میتونیم آرایه های تک بعدی ارسال کنیم .

اگر بخوایم با دیتای پیچیده و چند بعدی کار کنیم باید از آرایه های چند بعدی یا کالکشن های چند بعدی استفاده کنیم .

_// This code will result in a compilation error_

public static void InvalidMethod(params int[,] matrix)

{

_// Method implementation_

}

لینک مقاله: [لینک](https://l.vrgl.ir/r?ad=1&l=https%3A%2F%2Ftutorials.eu%2Fa-guide-to-using-csharp-params-to-work-with-parameters%2F%23%3A~%3Atext%3DWhat%2520is%2520the%2520%27params%27%2520keyword%2Ceasier%2520to%2520read%2520and%2520maintain.&si=luwtg45xfxw5&st=post&k=55KLHDXsmUWm7NjjUaGS27XGrfmIKCZKnSriR1wteLM%3D)
