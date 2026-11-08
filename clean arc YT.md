https://www.youtube.com/watch?v=CLQzLZUTMqU&list=PLN5rV4x2x5XcRubBzzDQ_WApzFBPAgnoh&index=6

![[Pasted image 20261108152549.png]]

![[Pasted image 20261108152634.png]]
حل مشکل وابستگی به دیتا 
![[Pasted image 20261108152708.png]]

بهش میگن port and adapter
یا hexaconal 

![[Pasted image 20261108152744.png]]

هر ضلع از اون آبیه میتونه برای ارتباط با اجزای دیگه ارتباط برقرار کنه

![[Pasted image 20261108152825.png]]

![[Pasted image 20261108153232.png]]

![[Pasted image 20261108153252.png]]

خوب دو تا قسمت اصلی داریم - primary که درخواست میاد بعد وارد app core میشه و بعد میره دیتا رو میاره از secondery 

![[Pasted image 20261108154935.png]]

خوب onion هم شبیه همونه - ولی داخل app core رو هم لایه بندی کرده و تمرکر بر روی جریان وابستگی هاست 

![[Pasted image 20261108155156.png]]


خوب اینطوری میشه که از app service به domain service و بعد domain میره 

هدف اینه که هر جا دققه وابستگی داشتیم توی هر لایه - ببریمش اون رو یه لایه بالاتر 

![[Pasted image 20261108155434.png]]

اینجا domian و domain service در یک لایه هستش 

خوب اینجا repo هر entity رو هم کنارش میزاریم و حتی unit of work 

![[Pasted image 20261108160128.png]]

حالا اگر بخوایم از infra استفاده کنیم میایم اینترفیسش رو توی app درست میکنیم و پیاده سازیش رو توی infra میکنیم 

![[Pasted image 20261108160255.png]]

حالا همون فضای infra رو میتوینم به دو بخش تقسیم کنیم یکی persistance و یکی external 

اگر بخوایم به یه webservice وصل بشیم دقیقا اینترفیس رو توی app پیاده میکنیم و خوده پیاده سازی اصلی رو توی infr قسمت external 

اگر با orm خواستیم کار کنیم اینترفیس app و پیاده سازی prsitance infra 

جریان مبتنی بر di هستش 

دغدغه تکنولوژی رو  هم سپرد به di 

![[Pasted image 20261108162107.png]]

خوب وظیقه این لایه اینه که تمام infra رو بیاد inject کنه به app 

تمامی registration ها و di ها توی web ui انجام میشه 

نه app و نه infra نمیدونن که کی قراره کجا از امکاناتشون استفاده بشه 

![[Pasted image 20261108163143.png]]

![[Pasted image 20261108163154.png]]

![[Pasted image 20261108170145.png]]

![[Pasted image 20261108170240.png]]

![[Pasted image 20261108170432.png]]

![[Pasted image 20261108170601.png]]

اینجا onion به وجود اومد چون اومد app رو لایه بندی کرد 
حالا در Clean اومده domain model رو با domain service یکی کرده و اسمش رو گذاشته domain layer و لایه بالاترش میشه app layer  

و این که به primery وظیفه مدیریت injection ها داده شده - یعنی تمامی اظلاع رو 

خوب command query handler که در لایه App هستش و توی عکس هم هست 

اون هایی که داخل اظلاغ هستن میشن port که میرن به اون چیزا وصل میشن که adapter هستش 



