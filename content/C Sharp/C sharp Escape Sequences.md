![[Pasted image 20241113023835.png]]

خوب در حالت عادی اگر بخواید مثلا یه سری کارها رو روی string انجام بدید میتونید از escape sequence ها استفاده کنیم.

مثلا به طور مثال اگر بخوایم توی متنی که نوشتیم بخوایم از \ استفاده کنیم باید اینطوری بنویسیمش \\

یا اگر بخوایم داخل string که خودش داخل double quotation هست از double quotation استفاده کنیم باید اینطوری بنویسیم "\

```csharp

Console.WriteLine("soheil \t moonesi");
soheil   moonesi

Console.WriteLine("soheil \n moonesi");
soheil
 moonesi

Console.WriteLine("soheil \v moonesi");
soheil
 moonesi
 
Console.WriteLine("soheil \\ moonesi");
soheil \ moonesi

Console.WriteLine("soheil \" moonesi");
soheil " moonesi

Console.WriteLine("soheil \' moonesi");
soheil ' moonesi
```