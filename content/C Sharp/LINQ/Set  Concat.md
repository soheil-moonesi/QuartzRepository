![[Pasted image 20241204145706.png]]https://www.sharpencode.com/article/Linq/set-operators-in-linq

با استفاده از union هم تجمیع انجام میشه و هم اعداد تکراری حذق میشه .

![[Pasted image 20241204145731.png]]

فرق concat اینه که دیگه تکراری باشه یا نه براش فرقی نداره.

```csharp
using System;  
using System.Collections;  
using System.Collections.Generic;  
using System.Diagnostics.CodeAnalysis;  
using System.Linq;  
using System.Security.Cryptography;  
  
namespace LinqProject  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {            List<User> users = new List<User>()  
            {  
                 new User { Name = "Ehsan"},  
                 new User { Name = "Maysam"},  
                 new User { Name = "Nader"},  
                 new User { Name = "Sadegh"},  
                 new User { Name = "Ehsan"},  
            };      
              
List<User> user2 = new List<User>()  
            {  
                 new User { Name = "Ehsan"},  
                 new User { Name = "Maysam"},  
                 new User { Name = "Nahid"},  
                 new User { Name = "Elham"},  
                 new User { Name = "Samira"},  
                 new User { Name = "negin"},  
            };  
  
            var userDistinc = users.Distinct(new userComparer());  
  
            foreach (var item in userDistinc)  
            {                Console.WriteLine(item.Name);  
  
            }              
Console.WriteLine("_______________Except______________");  
  
            var userExcept = users.Except(  user2,new userComparer());  
  
            foreach (var item in userExcept)  
            {                Console.WriteLine(item.Name);  
  
            }              
              
Console.WriteLine("_______________Intersect______________");  
  
            var userIntersect = users.Intersect(  user2,new userComparer());  
  
            foreach (var item in userIntersect)  
            {                Console.WriteLine(item.Name);  
  
            }              
Console.WriteLine("______________Union______________");  
  
            var userUnion = users.Union(  user2,new userComparer());  
  
            foreach (var item in userUnion)  
            {                Console.WriteLine(item.Name);  
  
            }              
              
Console.WriteLine("______________Union______________");  
  
            var userConcat = users.Concat(user2);  
  
            foreach (var item in userConcat)  
            {                Console.WriteLine(item.Name);  
  
            }  
  
            Console.ReadLine();  
        }    }  
    public class User  
    {  
        public string Name { get; set; }  
    }  
    public class userComparer : IEqualityComparer<User>  
    {        public bool Equals([AllowNull] User x, [AllowNull] User y)  
        {            if (x.Name == y.Name)  
                return true;  
  
  
            return false;  
        }  
        public int GetHashCode([DisallowNull] User obj)  
        {            return obj.Name.GetHashCode();  
        }    }  
}
```


برای این که بتونیم مقایسه بین string ها انجام بدیم باید بیایم برایش یه متد جدا با یه اینترفیس به اسم IEqualityComparer بسازیم که این اینترفیسه برای این که اوکی بشه خودش دو تا متد دیگه رو باید براش پیاده سازی کنیم اولیش Equals هستش و بعدیش GetHashCode هستش 


 public bool Equals([AllowNull] User x, [AllowNull] User y)  
        {            if (x.Name == y.Name)  
                return true;  
  
  
            return false;  
        } 


خوب equals میاد دو تا عضو میگیره و بعد طبق اون شرطی که براش تعریف کردیم میاد مقایسه رو انجام میده.

بعدیش هم GetHashCode که فکر میکنم برای سرعت بیشتر در اجرا استفاده میشه.

بعد از اون داستانا هم میایم اینجوری ازش استفاده میکنیم:

            var userDistinc = users.Distinct(new userComparer());  

![[Pasted image 20241204145854.png]]

[[LINQ]]