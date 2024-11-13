```csharp
class Program
{
    static void Main()
    {
        MathHelperExe();
    }

    public static class MathHelper
    {
        public static int Add(int a, int b)
        {
            return a + b;
        }
    }

       static void MathHelperExe()
    {
        int result = MathHelper.Add(2, 3);
        Console.WriteLine(result);
    }
}
```

خوب همونطوری که میبینید در قسمت بالا ما اومدیم از static برای کلاسمون استفاده کردیم.

وقتی که از static استفاده کردیم دیگه نمیتونیم در قسمت های دیگه ی از اون کلاس instance درست کنیم با new پس میایم و مستقیم از خوده کلاس و متد داخلش برای محاسبات استفاده میکنیم. که مزایاش میتونه این باشه که نمیایم فقط برای این که از یه متد داخل یه کلاس میخوایم استفاده کنیم بیایم از کل اون کلاس یه instance بگیریم و بعد بیام از اون متد استفاده کنیم.


```csharp
class Program
{
    static void Main()
    {
        MathHelperNonStatic mathHelper = new MathHelperNonStatic();
        int result =  mathHelper.Add(1, 2);
        Console.WriteLine(result);
    }

    public class MathHelperNonStatic
    {
        public int Add(int a, int b)
        {
            return a + b;
        }
    }
}
```

##### Key differences

There are a few key differences between static classes and normal (non-static) classes in C#:

1. **Instance**: A static class cannot be instantiated using the “new” keyword, while a normal class can.
2. **Members**: A static class can only contain static members, while a normal class can contain both static and instance members.
3. **Inheritance**: A static class cannot be inherited by other classes, while a normal class can be inherited.
4. **Accessibility**: A static class can only be accessed through its static members, while a normal class can be accessed through both its static and instance members.
5. **Use cases**: Static classes are typically used to hold utility methods and other functionality that is not specific to a particular instance of an object. On the other hand, normal classes are used to represent objects that have a specific state and behavior.


کلاس های استاتیک فقط میتونن اعضای استاتیک داشته باشن. ولی در کلاس معمولی اعضا میتونن استاتیک یا معمولی باشن

کلاس های استاتیک نمیتونن توسط کلاس های دیگه ارث بری بشن.

دسترسی به کلاس استاتیک فقط از طریق اعضای استاتیک امکان پذیره.

خب حالا میرسیم به توضیحات بیشتر:

اینجا فرض کنید که یه کلاس person داریم که پراپرتی هایی مثل اسم و فامیل داره، حالا فرض کنید توی همین کلاس یه پراپرتی داریم به اسم جمعیت که میشه مجموع این person ها، خوب طبعتا این پراپرتی نمیتونه متعلق به یک شخص یا person باشه و یک پراپرتی کلی تر هستش، توی این موارد ما میایم پراپرتی رو به صورت static تعریفش میکنیم و به این شکل این پراپرتی تبدیل به یک پراپرتی global میشه.

یه نکته ی جالبی که همیشه یادتون باشه اینه که Console.WriteLine هم دقیقا به صورت static پیاده سازی شده برای همین ما میتونیم اینطوری ازش استفاده کنیم.

```csharp
Singleton.instance;
```

```csharp
Singleton.instance;
```