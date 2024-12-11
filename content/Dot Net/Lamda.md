![[Pasted image 20241211170328.png]]
![[Pasted image 20241211170331.png]]

red cube is mean extension method

![[Pasted image 20241211170340.png]]

![[Pasted image 20241211170344.png]]


use delegate : 

![[Pasted image 20241211170346.png]]
using lamda 


![[Pasted image 20241211170414.png]]

![[Pasted image 20241211170416.png]]![[Pasted image 20241211170421.png]]

```csharp
// See https://aka.ms/new-console-template for more information  
namespace lamda  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {         
           List<Company> companies = new List<Company>()  
            {  
            new Company() {Id= 1, Name ="Benz" },  
            new Company(){Id = 2,Name = "BMW"},  
            new Company() {Id = 3,Name = "VW"}  
            }; 
         var result = companies.Where(company => company.Name.StartsWith("B"));  
            foreach (var company in result)  
            {          Console.WriteLine($"Id: {company.Id}, Name{company.Name}");  
            }    
                }   
                 }  
    class Company  
    {  
        public int Id;  
        public string Name;  
    }}
```

![[Pasted image 20241211170601.png]]

![[Pasted image 20241211170604.png]]

