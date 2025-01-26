![[Pasted image 20241204184237.png]]https://www.sharpencode.com/article/Linq/projection-operators

![[Pasted image 20241204184253.png]]


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
        {  
            List<Category> categories = new List<Category>()  
            {  
                new Category { Id =1 , Name="mobile" , Products = new List<Product>()  
                {  
                  new Product { Id =1 , Name ="Iphone Se" , CategoryId = 1 , InsertDate= DateTime.Now.AddYears(-5)},  
                  new Product { Id =2 , Name ="Sumsoung G8" , CategoryId = 1, InsertDate= DateTime.Now.AddYears(-8)},  
                }},  
                new Category { Id =2 , Name="Laptop" , Products = new List<Product> ()  
                {  
  
                  new Product { Id =3 , Name ="Asus" , CategoryId = 2, InsertDate= DateTime.Now},  
                  new Product { Id =3 , Name ="hp" , CategoryId = 2, InsertDate= DateTime.Now.AddYears(-15)}  
                }},  
            };  
  
            var data = categories.SelectMany(c => c.Products  
             .Where(p => p.InsertDate.Year < 2020)  
             .Select(s => new   
{  
                 Year = s.InsertDate.Year,  
                 Productname = s.Name,  
                 Category = c.Name,  
  
             }));  
  
            foreach (var item in data)  
            {                Console.WriteLine($"{item.Productname}      {item.Category}   {item.Year}");   
            }    
Console.ReadLine();  
        }    }   
    public class NewListdto  
    {  
        public int Id { get; set; }  
        public string Name { get; set; }  
        public string Category { get; set; }  
    }  
  
    public class Category  
    {  
        public int Id { get; set; }  
        public string Name { get; set; }  
        public List<Product> Products { get; set; }  
    }  
    public class Product  
    {  
        public int Id { get; set; }  
        public int CategoryId { get; set; }  
        public string Name { get; set; }  
        public DateTime InsertDate { get; set; }  
    }}
```

[[LINQ]]