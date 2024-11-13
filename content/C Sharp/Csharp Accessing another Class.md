برای این که بخوایم به یه کلاس دیگه توی برنامه دسترسی داشته باشیم چند تا مورد رو باید رعایت کنیم :

1. اسم namespace هاشون یکی باشه
2. اون کلاسی که میخوایم ازش استفاده کنیم public باشه.

نمونه ای که خودم نوشتم رو این جا گذاشتم :

```csharp
namespace virgol
{
    class Program
    {
        static void Main()
        {
            UserMsg.sayGoodMorning();
        }
    }
}

//create new class 

namespace virgol
{
    public class UserMsg
    {
        public static void sayGoodMorning()
        {
            Console.WriteLine("good morning");
        }
    }
}
```

فقط نکته ای که هست اینه که مثلا اگر میخواید از یک متد داخل اون کلاس استفاده کنید اول اسم اون کلاس رو بنویسید و بعد . و بعد اسم اون متدی که میخواید ازش استفاده کنید.

