![[Pasted image 20241204184533.png]]

![[Pasted image 20241204184544.png]]

![[Pasted image 20241204184651.png]]

![[Pasted image 20241204184655.png]]
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
                new Category { Id =1 , Name="mobile"},  
                new Category { Id =2 , Name="Laptop"},  
            };  
  
  
            List<Product> products = new List<Product>()  
            {  
                  new Product { Id =1 , Name ="Iphone Se" , CategoryId = 1},  
                  new Product { Id =2 , Name ="Sumsoung G8" , CategoryId = 1},  
                  new Product { Id =3 , Name ="Asus" , CategoryId = 2},  
                  new Product { Id =3 , Name ="hp" , CategoryId = 2}  
            };  
            var datajoin = products.Join(categories, p => p.CategoryId, c => c.Id, (product, category) =>  
              new  
              {  
                  ProducId=product.Id,  
                  ProductName= product.Name,  
                  ProductCategry=category.Name  
              });  
  
  
            foreach (var item in datajoin)  
            {                Console.WriteLine($"{item.ProductName}  {item.ProductCategry}");             
            }  
  
            Console.WriteLine($"________________________________");  
  
            var groupJoinResult = categories.GroupJoin(products, c => c.Id, p => p.CategoryId  
            , (category, product) =>  
            new  
            {  
                prod = product,  
                cat = category,  
            });  
  
  
            foreach (var item in groupJoinResult)  
            {            Console.WriteLine($" __ Category :{item.cat.Name}" );  
  
                foreach (var p in item.prod)  
                {                    Console.WriteLine($"{p.Name}");  
  
                }  
            }  
            Console.ReadLine();  
        }    }   
    public class Category  
    {  
        public int Id { get; set; }  
        public string Name { get; set; }  
    }  
    public class Product  
    {  
        public int Id { get; set; }  
        public int CategoryId { get; set; }  
        public string Name { get; set; }  
    }}
```