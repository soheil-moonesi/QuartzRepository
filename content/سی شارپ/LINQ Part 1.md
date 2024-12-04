خوب میرسیم به مبحث بسیار بسیار و بازم بسیار مهمه LINQ

حالا قبل هر چیز بیایم ببینیم که اصلا معنی LINQ چی هه ؟! اصلا مخففه چیه ؟

Language Integrated Query

![[{B050818F-5C2F-4BB7-B5C9-C55FB3A16295}.png]]

Before the introduction of LinQ, querying and manipulating data in C# was an arduous and disjointed task. Developers had to grapple with multiple querying languages and approaches, such as SQL for databases, XPath for XML data, and custom solutions for other data types.

خوب اینجا داره تاریخی بررسی میکنه، میگه که قبل از این که linq بیاد برنامه نویس ها برای این که بخوان query بزنن و تغییراتی بخوان روی دیتا انجام بدن باید از انواع اقسام ابزار ها و زبان ها باید استفاده میکردند تا کار رو دربیارن.

These disparate [methods](https://l.vrgl.ir/r?ad=1&l=https%3A%2F%2Fwww.bytehide.com%2Fblog%2Fmethod-usage-csharp&si=r4hkfw5ujlwj&st=post&k=5BCDt3MKan6QZES3Dx%2FACA7FjLoNOv%2B2nM0QdsPRUs0%3D) lacked integration with C#, which hindered productivity and resulted in overly complex and error-prone code.

خوب همین راه هایی که بالاتر هم گفتیم زیاد با C# همخونی چندانی نداشتن و برای همین راه حل ها و کارهایی که برنامه نویس ها انجام میدادن خیلی پیچیده شد و کارایش هم پایین میومد.

Recognizing the need for a unified querying language, the creators of C# set out to develop a powerful, flexible, and integrated solution that could cater to a wide range of data sources.

خوب برای همین هم نیاز به یک رویکرد جدید و همسان سازی برای C# ایجاد شد و بعد هم سازندگان C# هم اومدن و یه راه حلی رو برای این داستان ساختن.

### Birth of LinQ: C# 3.0 and its game-changing features

In November 2007, Microsoft released C# 3.0 and the .NET Framework 3.5, which introduced multiple groundbreaking features, including extension methods, anonymous types, [lambda expressions](https://l.vrgl.ir/r?ad=1&l=https%3A%2F%2Fwww.bytehide.com%2Fblog%2Flambda-expressions-csharp&si=r4hkfw5ujlwj&st=post&k=m%2Fi0MC%2FlrnMOFLjLtvy%2FsT9LMriEzb%2FOTtsd9tu86Fk%3D), and, most importantly, LinQ. These innovations were critical in enabling LinQ to deliver on its promise as a seamless, expressive, and unified querying framework.

خوب بعدش اومدن و extention method , anonymous type , lamda expression ها و مهمتر از همه Linq رو درست کردن.

قبل از این که linq بیاد برای این که بخوایم دیتا های توی یه کالکشنی رو ببینیم باید میومدیم و foreach استفاده میکردیم.

```csharp
List<int> numbers = new List<int> { 1, 2, 3, 4, 5, 6, 7, 8, 9, 10 }; List<int> evenNumbers = new List<int>();
  foreach (int number in numbers) {  
   if (number % 2 == 0)     {  
       evenNumbers.Add(number);     } }

```

حالا after و before رو میبینیم، بعد از اومدن linq:

```csharp
List<int> numbers = new List<int> { 1, 2, 3, 4, 5, 6, 7, 8, 9, 10 };  IEnumerable<int> evenNumbers = from number in numbers                                 where number % 2 == 0 select number;
```

it has opened the door for exciting advancements and enhancements, such as async queries, asynchronous streaming, and parallelism in the LINQ to Objects provider.

میگه که درهای جدیدی رو باز کرد این قضیه، مثله : async queries , asynchronous streaming , parallelism و این ها قابلیت های جدیدی بود برای C#

حالا entity framework هم اومد دیگه این قابلیت رو کامل تر کرد.

### LinQ Namespace and Assemblies

LinQ is available in various namespaces within the .NET Framework. The primary namespaces you’ll be interacting with are:

- `System.Linq`: Contains basic LinQ extension methods for enumerable collections
- `System.Data.Linq`: Offers LinQ-to-SQL components
- `System.Xml.Linq`: Houses LinQ-to-XML functionalities

خوب حالا میگه که شما برای هر کدوم از کاراهایی که میخواید انجام بدید از این namespace های linq میتونید استفاده کنید مثلا برای sql میشه از system.data.linq استفاده کنیم.

Expressions, delegates, and anonymous methods are essential components that underpin LinQ’s functionality.

و این که expressions , delegate , anoymous method ها عضو های اصلیه linq هستند.

#### Expressions

Expressions are C# code blocks that produce a value. A LinQ query often involves filtering or manipulating data using predicate expressions, which are conditions that return either `true` or `false`. Due to their concise and expressive nature, lambda expressions (introduced in C# 3.0) are commonly used in these scenarios.

خوب expressions ها کد بلاک هایی هستند که نتایج و مقادیر رو درست میکنند. linq query ها معمولا توشون فیلتر کردن یا ایجاد تغییرات روی دیتا ها انجام میشه. predicate expressions ها مثل شرط هستند که جوابشون true یا false هستش، جلوتر مثال گفته:

### Example of a simple predicate expression:

```csharp
Func<int, bool> isEven = x => x % 2 == 0;
```

In this example, the expression `x => x % 2 == 0` is a lambda expression that represents a predicate that checks if a given integer is even.

اینجا مثلا isEven داره به ما میگه که عدد داده شده زوجه یا فرده

#### Delegates

Delegates are type-safe function pointers that encapsulate references to methods. They are crucial for LinQ because they provide the flexibility needed when working with methods in queries. Methods can be assigned to delegates, which in turn can be used as arguments to other methods, effectively providing a way to “plug in” functionality.

This allows LinQ queries to utilize custom methods for operations such as filtering, sorting, or grouping according to different criteria.

خوب همونطوری هم که قبلا گفتیم delegate ها مثل یه type safe function pointer عمل میکنن که میان و مرجع متد ها رو توی خودشون نگه میدارن. اتفاقا خیلی هم توی linq مهم و کاربردی هستن برای این که به ما قابلیت های مهم و انعطاف پذیری از متد های مختلف در query ها رو به ما میدن.

```csharp
public delegate bool IsEvenDelegate(int number); 
 public static bool IsEven(int number){ 
    return number % 2 == 0; }  
IsEvenDelegate isEvenDel = IsEven; 
List<int> numbers = new List<int> { 1, 2, 3, 4, 5 }; 
 IEnumerable<int> evenNumbers = numbers.Where(n => isEvenDel(n));
```

n this example, we created a custom delegate `IsEvenDelegate` and a method `IsEven()` that checks if a number is even. We then assigned the method to the delegate and used it within our `Where` clause to filter out even numbers from a list.

خوب برای توضیحات کد بالا به نظرم یکم باید بریم جلو تر.

#### Anonymous Methods

Anonymous methods, primarily expressed as lambda expressions in modern C#, enable more concise and expressive syntax for defining inline functions. These functions are called “anonymous” because they don’t require an [explicit](https://l.vrgl.ir/r?ad=1&l=https%3A%2F%2Fwww.bytehide.com%2Fblog%2Fcsharp-explicit-conversion&si=r4hkfw5ujlwj&st=post&k=y1%2BE4sNpFiAbq9jNlCf6qnWSbHJRMZJn0lE1d%2B1uYNE%3D) method name.

This conciseness is particularly important when writing LinQ queries, as it significantly reduces verbosity and enhances code readability.

Consider this example that demonstrates the use of an anonymous method through a lambda expression in LinQ:

متد های ناشناس در حالت عادی در lambda expression ها مورد استفاده قرار میگیره و یه راه خیلی خوب برای تعریف یک function هستش.

خلاصه نوشتن در نوشتن linq query ها خیلی مهمه چون پیچیدگی کد رو کم میکنه و خوانایی کد رو میبره بالا.

### Starting Strong: Writing Your First LinQ Queries in C#

Basic LinQ Query Syntax and Structure

خوب میرسیم به داستان linq ، همونطوری که میدونید با کلمه from میتونیم دیتاستی که قراره باهاش کار کنیم رو انتخاب کنیم بعدش از query operator هایی مثل where ,select, group , order استفاده کنیم برای این که بتونیم دیتا ها رو فیلتر کنیم یا تغییرشون بدیم.

```csharp
 // Query syntax example
 var results = from student in students 
               where student.Age > 18
               orderby student.Name ascending 
               select student.Name;
```

Implicitly Typed Local Variables (var) in C# and LinQ

میرسیم به این که اینجا میتونیم از var هم استفاده کنیم. چرا؟ چون اینجا دیگه میتونیم فقط تمرکزمون رو بزاریم برای نوشتن کد و query ها و بزاریم کامپایلر بیاد و تایپ ها رو خودش تعیین کنه اینجوری کارمون راحت تر میشه.

```csharp
// Using var with LinQ 
var studentsWithHighScores = from student in students                               
                             where student.Score > 80 
                             select student;
```

### From, Select, and Where Keyword Usage

حالا داستان هر کدوم از keyword ها چیه؟

کلمه from تعیین کننده مرجع و منبع دیتاهامون هستش

کلمه select مشخص میکنه که دقیقا شما چه دیتایی رو میخواین واکشی کنین از دیتابیس مثلا شاید بخواین اسم دانشجو ها رو فقط بدست بیارید اینطوری مینویسید : select student.Name

کلمه where میاد بر اساس یه سری شرط یه سری فیلتر های رو دیتامون اعمال میکنه.

```csharp
// Using from, select, and where
 var names = from student in students
             where student.Age > 18
             orderby student.Name ascending 
             select student.Name;
```

حالا فرض کنید که بخوایم فقط دانشجو های خانم رو جدا کنیم:

```csharp
// Using from, select, and where with a different condition
 var femaleNames = from student in students
                   where student.Gender == &quotFemale&quot 
                   orderby student.Name ascending 
                   select student.Name;
```

Filter, Projection, and Transformation Operations

خوب حالا بخوایم یه سری تغییرات توی دیتاهمو اعمال کنیم چی کار کنیم؟ خوب قبل از این کار بیایم ببینیم که چه کارهایی رو میتونیم انجام بدیم و یه اصطلاحات مربوط بهش رو یادبگیریم:

خوب اصطلاح filtering همونطوری که مشخصه از اسمش برای این که دیتامون رو بخوایم یه سری شرط روش اعمال کنیم میایم ازش استفاده میکنیم ، از where هم برای این کار استفاده میکنی.

اصطلاح projection میاد ساختار یا فرمت دیتامون رو تبدیل میکنه برای این کار از select استفاده میکنیم.

اصطلاح transformation برای group ,orderby و join و set oprator و موارد پیشرفته تر استفاده میشه .

```csharp
var highScoreNames = from student in students 
                      where student.Score > 80 
                      orderby student.Age  
                      select student.Name;
```

حالا فرض رو بر این بزارید که بخوایم یه سری از دانشجو ها رو بر اساس کلاسشون گروه بندی کنیم.

```csharp
var studentsByClass = from student in students  
                     group student by student.Class into studentGroup                       
          select new { Class = studentGroup.Key, Students = studentGroup };
```

حالا اینجا همونطوری که میبینید اومده از group برای دسته بندی دیتاهای دانشجو ها انجام داده و گروه بندیشون رو بر اساس کلاس که داخلش هستن انجام داده. بعد اومده از select استفاده کرده و نتیجه این عملیات رو ریخته توی یه anonymous type که حاوی کلاس و یه کالکشن از دانشجو ها هستش. خوب اینجا با استفاده از select اومدیم اصلا ساختار دیتامون رو به یه شکل دیگه تبدیل کردیم.

  

مرجع این مقاله: [لینک](https://l.vrgl.ir/r?ad=1&l=https%3A%2F%2Fwww.bytehide.com%2Fblog%2Flinq-csharp&si=r4hkfw5ujlwj&st=post&k=B1Fx%2FJHe4FcfoHlwIeXjwdur3My7QkrsJtnRrc9L3so%3D)


