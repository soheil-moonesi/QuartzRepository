
![[Pasted image 20241207212558.png]]

ما اینجا اومدیم و خارج از convention و به foreign key مون ID اضافه نکردیم و بنابراین باید بیام خودمون دستی براش تنظیم کنیم 

ولی اینجا همونطور که میبینید از convention ها استفاده کردیم 

![[Pasted image 20241207212610.png]]

خوب به این ارور برخوردیم :

More than one DbContext was found. Specify which one to use. Use the '-Context' parameter for PowerShell commands and the '--context' parameter for dotnet commands.

راه حلش برای این ارور اینه 
PM> Add-Migration TestDatabaseInit -context TestDataBase
میایم context اش رو تعیین میکنیم براش که کدوم دیتابیس رو منظورمونه که migration روش انجام بشه 



![[Pasted image 20241207212632.png]]



Unable to create a 'DbContext' of type 'TestDataBase'. The exception 'Unable to resolve service for type 'Microsoft.EntityFrameworkCore.DbContextOptions`1[HeartSite.DAL.TestDataBase]' while attempting to activate 'HeartSite.DAL.TestDataBase'.' was thrown while attempting to create an instance. For the different patterns supported at design time, see https://go.microsoft.com/fwlink/?linkid=851728



بعدش اومدیم طبق راه حلی که در stack بود یه constructor به کلاس دسترسی به دیتا بیس اضافه کردیم و مشکل حل شد اینطوری :

![[Pasted image 20241207212648.png]]

![[Pasted image 20241207212658.png]]


![[Pasted image 20241207212702.png]]