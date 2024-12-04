If you have a set of functionally important and unchanged values, Enums are useful for developers.

Enums' key benefit is to make it possible in the future to adjust values.

اگر یه قسمت مهمی از کدتون مقادیرش تغییر نمیکنه اون موقع enum ها به کارتون میاد .

یکی از مهمترین ویژگیهاش اینه که این قابلیت رو به ما میده که بعدا مقدارش رو عوض کنیم.

خوب برای درست کردن enums میایم اول یه کلاس درست میکنیم و بعدش میایم به این شکل تعریفش میکنیم:

![[{1A860E7D-8E79-4AAA-88D6-7067B2D8E08A}.png]]

و اینطور هم ازش استفاده میکنیم برای تعیین مقدار پیش فرض برای GridSpotStatus

public Enums.GridSpotStatus Status { get; set; } = Enums.GridSpotStatus.**Empty**;

خوب بعد از این که این کار کردیم میبینیم که چه قابلیت هایی رو میتونیم استفاده کنیم:

![[{BF43F565-59D7-4E6D-9739-C887E2F829AB}.png]]

حالا بیایم ادامه قابلیت ها را همچنان از سایت مرجع دنبال کنیم:

![[{6F0E917E-F8BB-47FA-80DE-1F47123D625D}.png]]

خوب به این مطلب توجه داشته باشید که به صورت دیفالت مقدار شروع شونده برای enum ها از 0 هستش و این یعنی این که مقدار car میشه 0 و بعد اومدیم به bike مقدار 3 رو دادیم، حالا در این حالت میاد و مقادیر بعدی رو به صورت افزایشی و به صورت اتوماتیک مقدار دهی میکنه یعنی مقدار truck میشه 3 و مقدار taxi میشه 4.

Get the value of an Enum

![[{97F33ED1-C62A-4079-83F1-D7082A76E46C}.png]]

Output:

![[{1A4ED086-B482-432B-B60F-50A0A2A1A25A}.png]]

خوب همونطوری که میبینید اینجا میتونیم به مقادیر enum ها هم دسترسی پیدا کنیم

در حالت اول اومدیم و مقدار vehicleEnum.car رو cast کردیم به int برای این که مقدارش رو بگیریم

در حالت دوم برای این که به اسم خوده اون enum برسیم اومدیم از toString برای vehicle.Bike استفاده کردیم و Bike رو رو گرفتیم.

حالا یه حالت سومی هم داره که اینطوریه :

![[{7129A634-5550-407E-B5A0-B5292045A406}.png]]

اینطوری در خروجی Bike چاپ میشه.

## Conclusion

The advantages of using enums are that they are very easy to use and represented as strings but processed as integers. Enums are easy to maintain and improve code readability because they provide symbolic named constants, which means you need to remember the names, not the integer values.

لینک مطالب نوشته شده : [لینک](https://l.vrgl.ir/r?ad=1&l=https%3A%2F%2Fwww.loginradius.com%2Fblog%2Fengineering%2Fenum-csharp%2F%23%3A~%3Atext%3DC%2523%2520Enum%2Cand%2520less%2520vulnerable%2520to%2520mistakes.&si=erd8fosdbar7&st=post&k=fLs9Ospa4JgvABgVcn6KjMd%2FuIHgY%2BKf%2F998D4%2BXsCw%3D)