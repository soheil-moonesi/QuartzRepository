برای scaffold کردن میایم از این کامند در package manager استفاده میکنیم :

Scaffold-DbContext -Connection "server= esme server; Database=esme database; User = esme user ; Password=password ke gozashtim ; TrustServerCertificate = True" -provide Microsoft.EntityFrameworkCore.SqlServer -OutputDir Models -Tables jadvali ke mikhaym 1 , jadvali ke mikhaym 2 

خوب server اسم سرور یا همون server name که روی sql server هستش رو مینویسیم
مورد بعدی data base هستش که اسم database رو مینویسیم
مورد بعدی user که اون یوزری که داریم باهاش به دیتابیس وصل میشیم رو مینویسم 
بعدش password که داریم رو میزنیم 
بعدش میایم اون trusted رو true میکنیم که ارور نده 
بعدش میگیم که ما این scaffold که میخوایم انجام بدیم رو هدف یا اون دیتابیسی که میخواد روش انجام بشه از نوع sql server هستش که تعیین کردیم 
بعد هم با output داریم میگیم که خروجی رو بریز توی models 
بعدش میایم و table هایی که میخوایم رو جدا جدا بهش میگیم که این ها رو بیاره

چون اگر کلش رو بزنیم ممکنه که کرش و هنگ کنه 

خوب حالا نکته ای که هست اینه که اگر بخوایم چیزی اضافه کنیم به این ساختار با -force انجام میدیم 


پیکیج های لازم »
entityframworkcore 
entityframworkcore.design 
entityframeworkcore.sqlserver
entityframeworkcore.tools
swashbuckle.aspcore.swagger
newtonjson