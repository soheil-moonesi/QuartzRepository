ترتیب اجرای sql 
اول from هستش 
بعد قسمت on توی join ها و بعد خوده join ها و بعد where condition ها و بعدیش group by و بعدیش having و بعدیش دستور select و بعدی distinct و بعدی order by  و بعدی limit هستش 

![[Pasted image 20250102085948.png]]

[SQL Queries Execution Order - JigNect Technologies Pvt Ltd SQL Queries Execution Order](https://jignect.tech/sql-queries-execution-order/)

![[Pasted image 20250102091759.png]]

اینجا در مورد دومی اومدیم اول اون هایی که بیشتر از 1 یکی کتاب دارند رو جدا کنه و بعد ادامه ی مطالب 
در کد اولی این کار در مرحله ی آخر انجام میشه

خوب sub query ها  نوع 1 بهمون یک تک مقدار تولید میکنه و بهش نمیتونیم اسم بدیم 

خوب top قبلش Distinct قرار میگیره : 
![[Pasted image 20250102093329.png]]

![[Pasted image 20250102093543.png]]


![[Pasted image 20250102093523.png]]

[SQL SELECT LIMIT, TOP, FETCH FIRST (With Examples) (programiz.com)](https://www.programiz.com/sql/limit-top-fetch-first)

![[Pasted image 20250102093657.png]]

![[Pasted image 20250102093712.png]]

خوب with ties همیشه با دستور order by  میاد 

![[Pasted image 20250102093843.png]]

![[Pasted image 20250102093903.png]]

![[Pasted image 20250102093923.png]]

ما دو تا 100 داشتیم 

![[Pasted image 20250102094004.png]]

خوب اول top 1 میره یک جوابی میاره و بعد with ties میره دیتاهایی که شبیه به top 1 بود رو هم میاره 

![[Pasted image 20250102094126.png]]

![[Pasted image 20250102094145.png]]

![[Pasted image 20250102094153.png]]

![[Pasted image 20250102094328.png]]

نکته order by کوئری رو میپوکونه و برای بهتر شدنشون باید براشون index تعیین کنیم 


![[Pasted image 20250102101126.png]]

 ![[Pasted image 20250102101330.png]]

شماره ایندکس از 0 شروع میشه 

خوب offset مشخص کننده ی این هستش که از کجا شروع کنه دیتا رو بیاره 

خوب fetch هم به تعدادش از اونجا میره دیتا ها رو میاره 

![[Pasted image 20250102101511.png]]

توی صفحه ی بعدی offset میشه 5 

![[Pasted image 20250102101637.png]]

در جلوتر به صورت فانکشن میتونیم این کار رو انجام بدیم 

در oracle ما top نداریم و باید از offset , fetch استفاده کنیم 

![[Pasted image 20250102102614.png]]

![[Pasted image 20250102104325.png]]

![[Pasted image 20250102104345.png]]

![[Pasted image 20250102104353.png]]

![[Pasted image 20250102104409.png]]

![[Pasted image 20250102104501.png]]

![[Pasted image 20250102104520.png]]

![[Pasted image 20250102104816.png]]


![[Pasted image 20250102113744.png]]

فانکشن هایی که خوده sql دارن خیلی سریع هستند ، این ها از سال 2008 به بعد اضافه شدن 

![[Pasted image 20250102113959.png]]

![[Pasted image 20250102114147.png]]

![[Pasted image 20250102121212.png]]

این مورد دومش میشه sub query نوع سوم 

![[Pasted image 20250102121334.png]]

