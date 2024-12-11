![[{F7CC69C0-EB32-4383-BA9F-A9F68C1EF1F6}.png]]

خوب اول یه توضیحی راجع به این موضوع داشته باشیم. ببینید توی هر برنامه ای موقعیت های خارج از انتظاری اتفاق میوفته که این ها ممکنه باعث بشن کل برنامه به فنا بره و ما برای این که جلو این اتفاق رو بگیریم و یه جورایی برنامه رو پایدار نگهداریم باید یه سری کارها رو انجام بدیم.

خوب exception handling اصلی یعنی چی؟ یعنی این که یه مکانیزمی رو طراحی کنیم که اگر خطایی رخ داد بتونیم اون رو تشخیص بدیم و بعد بتونیم اون خطا در صورت امکان رفع کنیم.

خوب حالا چرا این کار انقدر مهمه؟

چون باعث میشه که برنامه مون پایداریش بیشتر بشه ، پیام های خطایی که میده باعث میشه user experience بهتری داشته باشیم و جلوی crash کردن برنامه رو میتونیم بگیریم.

نگهداری و خطایابی توی کدمون راحت تر میشه.

### Understanding the Exception Class in C#

The System.Exception Class

توی سی شارپ exception ها آبجکت هایی هستند که از کلاس system.exception ارث بری کردند.

این کلاس چندین تا متد و پراپرتی داره که کمکمون میکنه اطلاعات راجع به exception بدست بیاریم.

مثل error message , source , stack trace

### Commonly Used Exception Classes

- `System.NullReferenceException`
- `System.ArgumentException`
- `System.DivideByZeroException`
- `System.IndexOutOfRangeException`
- `System.IO.FileNotFoundException`

### Implementing C# Exception Handling

The Try-Catch Block

خوب این یه block پایه برای همین بحث error handling هستش .

کدی که داخل try اجرا میشه اگر exception براش به وجود بیاد کدی که داخل catch هستش اجرا میشه.

```csharp
try{  
   // Code that might throw an exception
 int result = 10 / 0; } 
catch (DivideByZeroException ex) { 
    // Handle the exception 
   Console.WriteLine('Error: ' + ex.Message); }
```

The Finally Block

خوب قسمت finally آپشناله و هر چی داخلش بنویسیم همیشه اجرا میشه حالا این یعنی این که چه exception اتفاق بیوفته چه نیوفته اون قسمت اجرا میشه.

```csharp
try{   
  // Code that might throw an exception
} 
catch (Exception ex) {  
   // Handle the exception
} 
finally{
     // This code will always execute
    Console.WriteLine('Finally block executed.'); 
}
```

Nested Try-Catch Blocks

خوب این بلوک های try catch رو تو در تو هم میتونیم ازشون استفاده کنیم و زمانی هم به کار میاد که بخوایم توی قسمت های مختلفی از برنامه بخوایم exception handling انجام بدیم.

```csharp
try {    
 // Outer try block
 try    {     
    // Inner try block  
  }   
  catch (ArgumentException ex)     {    
     // Handle ArgumentException  
  } } 
catch (Exception ex) {     
// Handle all other exceptions
}
```

The Throw Statement

خوب با استفاده از Throw میتونیم خودمون دستی یه exception رو فعال کنیم. یا وقت هایی که بخوایم یه exception رو برای یه سناریویی که داریم فعال کنیم.

```csharp
try{  
   // Check for an invalid condition 
if (someCondition)     {     
    throw new InvalidOperationException('Invalid operation.');     } } catch (InvalidOperationException ex) { 
    // Handle the exception 
   Console.WriteLine('Error: ' + ex.Message); }
```

C# Exception Handling Best Practices

Using Specific Exceptions

خوب یه راهی که داریم برای exception handling اینه که بیایم ارور ها رو به صورت مشخص شده catch کنیم اینطوری میدونیم دقیقا چه خطایی رخ داده و چه پیامی رو باید براش درنظر بگیریم.

```csharp
try{    
 // Code that might throw an exception
}
 catch (FileNotFoundException ex) {
     // Handle FileNotFoundException
} 
catch (IOException ex) {
     // Handle other IO exceptions
}
 catch (Exception ex) {
     // Handle all other exceptions
}
```

Do Not Catch System.Exception Directly

از اینکه بخوایم کلاس system.Exception رو مستقیم catch کنیم جدا خودداری بفرمایید. جدی میفرماید؟

بله جدی. چرا؟ چون باعث ماسک شدن و یا همون پنهان شدن exception های دیگه میشه. به جاش بیاید و exception ها رو به صورت مشخص catch کنید.

Avoid Catching Exceptions You Cannot Handle

فقط exception هایی که میتونیم handle یا recover کنیم رو catch کنیم، اون هایی که نمیتونیم handle اش کنیم رو توی اون قسمت از کد ولش کنیم و بزاریم بره داخل call stack و از اونجا یه بلایی سرش میاریم.

Use ‘Using’ Statement for Cleanup

میگه جاهایی که دارید با resource هایی که اینترفیس Idisposable دارن استفاده میکنید مثل streams, database connection, network socket ها بیاید و از using استفاده کنید که بعدش درست clean up بشه.


```csharp
  using (StreamReader reader = new StreamReader('file.txt')) { 
    // Code that uses the StreamReader
} 
// The StreamReader is automatically disposed when the using block exits
```

Logging Exceptions Effectively

از جزییات exception ها log بگیریم . جزییاتی مثل پیام خطا ، مرجع خطا، stack trace برای این که بتونیم بهتر برای دیباگ کردن آنالیز کنیم.

میگه طبقه بندی درستی برای این log ها در نظر بگیریم error , warning , info بر اساس درجه اهمیتی که دارن.

C# Error Handling Techniques

خوب توی سی شارپ انواع و اقسام تکنیک های مختلف رو داریم برای error handling کردن

C# Error Handler

خوب error handler به صورت مرکزی میاد و هر exception توی برنامه اتفاق بیوفته رو handle میکنه که این قضیه شامل logging , displaying error message یا انجام دادن یه کاری بر اساس یه تایپی از exception ها هستش. ما میتونیم یه کلاس جدا یا یه متد برای handle exception درست کنیم که هر وقت exception اتفاق افتاد اون بیاد و یه کاری رو بر اساس اون exception انجام بده، به طور مثال درست کردن کلاس ErrorHandler برای log گرفتن و نمایش ارور ها به یوزر:

```csharp
public static class ErrorHandler
{  
   public static void HandleException(Exception ex) 
   { // Log the exception
      LogException(ex);     
    // Display a user-friendly error message        
    ShowErrorMessage(ex);     } 
     private static void LogException(Exception ex)    {     
    // Use your preferred logging framework to log the exception details        
    Console.WriteLine('Error: ' + ex.Message);     } 
     private static void ShowErrorMessage(Exception ex)    {   
     // Show a user-friendly error message, e.g., using a message box or a 
     custom UI element   
     Console.WriteLine('An error occurred: ' + ex.Message);
     } }
```

You can then call the `HandleException` method from your `catch` blocks:

```csharp
try{   
  // Code that might throw an exception
} 
catch (Exception ex) {     ErrorHandler.HandleException(ex); }
```

### C# Exception Error Code

با assign کردن error کد ها به یک کلاس exception میتونیم اطلاعات بهتری راجع به اون exception بدست بیاریم و trace کردنش هم راحت تر میشه .

```csharp

 public class CustomException : ApplicationException{ 
    public int ErrorCode { get; }  
    public CustomException(string message, int errorCode) : base(message) {         
 ErrorCode = errorCode;     } }
```

```csharp
try{     
// Throw a custom exception with an error code throw new CustomException('Invalid operation.', 1001); 
} 
catch (CustomException ex) { 
    // Handle the exception based on the error code    Console.WriteLine('Error Code: ' + ex.ErrorCode + ', Message: ' + ex.Message); 
}
```

این مطلب از این  https://www.bytehide.com/blog/5-good-practices-for-error-handling-in-c

گرفته شده و ترجمه تحت الفظی شده.