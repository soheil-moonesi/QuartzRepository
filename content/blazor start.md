https://www.youtube.com/watch?v=AKiGGtBj1go

![[Pasted image 20251105223100.png]]
اولییش سمت server هستش که crud توش پیاده سازی میکنیم و دومی میشه clinet و سومی هم share بین این ها ست 


``` c# error
PM> Add-Migration init
Add-Migration : The term 'Add-Migration' is not recognized as the name of a cmdlet, function, script file, or operable program. Check the spelling of the 
name, or if a path was included, verify that the path is correct and try again.
At line:1 char:1
+ Add-Migration init
+ ~~~~~~~~~~~~~
    + CategoryInfo          : ObjectNotFound: (Add-Migration:String) [], CommandNotFoundException
    + FullyQualifiedErrorId : CommandNotFoundException
```


![[Pasted image 20251106075949.png]]

![[Pasted image 20251106080041.png]]

https://learn.microsoft.com/en-us/answers/questions/1287896/getting-an-error-add-migration-the-term-add-migrat


برای Sqlite 

```
{
  "ConnectionStrings": {
    "DefaultConnection": "Data Source=.\\app.db;Pooling=True;"
  },
  
```


