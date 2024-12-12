خوب به مبحث واقعا کاربردی رسیدیم، خوب این مبحث قراره به کدوم سوال ما پاسخ بده؟

این سوال: آیا قابلیتی توی C# هستش که بتونیم یک تیکه از کدی که نوشتیم فقط توی حالت Debug اجرا بشه و توی Release اجرا نشه و یا برعکس یه تیکه کد توی Release اجرا بشه و توی Debug اجرا نشه .

جواب کوتاه : آره داریم همچین قابلیتی رو.

حالا جواب بلند اینه که چجوری ؟ اینجوری :

```csharp
#if (DEBUG)
            Console.WriteLine(&quotit is debug mode&quot);
#else 
return false;
 #endif
```

برای این که توی release اجرا بشه:

```csharp
#if (!DEBUG)    
         Console.WriteLine(&quotit is release mode&quot);
 #else  return false; 
 #endif
```
