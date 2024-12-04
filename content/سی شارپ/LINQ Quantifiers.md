![[Pasted image 20241204184355.png]]

وقتی که میخوایم چیزی رو چک کنیم در لیستمون برای افزاریش کارایی میتونیم از any استفاده کنیم

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
        {            List<Product> products = new List<Product>()  
            {                new Product { Name = "Asp.Net Core", Price = 10000 },  
                 new Product { Name = "C-Shart", Price = 15000 },  
                 new Product { Name = "C++", Price = 5000 },  
                 new Product { Name = "PHP", Price = 25000 },  
                 new Product { Name = "Java", Price = 8000 },  
            };  
            Console.WriteLine("__________ALL___________");  
            var allResult = products.All(p => p.Price > 9000);  
            Console.WriteLine(allResult);  
  
  
            Console.WriteLine("__________Any___________");  
            var anyResult = products.Any(p=> p.Price > 9000);  
  
            //var countResult = products.Count(p => p.Price > 9000);  
            //if(countResult>= 1)            //{            //    ///--------            //}            Console.WriteLine(anyResult);  
  
  
            Console.WriteLine("__________Contains___________");  
            var ContainsResult = products.Where(p => p.Name.Contains("C"));  
            foreach (var item in ContainsResult)  
            {                Console.WriteLine($"{item.Name}");  
  
            }  
            Console.ReadLine();  
        }    }  
    public class Product  
    {  
        public string Name { get; set; }  
        public int Price { get; set; }  
    }  
  
  
}
```