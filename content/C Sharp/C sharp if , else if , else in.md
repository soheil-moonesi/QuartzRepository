![[Pasted image 20241113022407.png]]

خوب حالت کلی رو که باید در نظر بگیرید اینه که اول if و شرط رو تعیین میکنیم و بعد اگر نیاز داشتیم حالت های دیگه رو هم چک کنیم میایم از else if استفاده میکنیم و در آخر هم اگر هیچ کدوم از شرط هایی که تعیین کردیم چک شد و با هیچ کدوم جور نشد، کد داخل else اجرا میشه.

```csharp

string day = Console.ReadLine();
if (day == "sunday")
{ Console.WriteLine("today is sunday"); }
else if (day == "monday")
{ Console.WriteLine("today is monday"); }
else
{ Console.WriteLine("i just know sunday and monday :D "); }
```