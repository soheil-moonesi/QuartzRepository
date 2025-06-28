استفاده از litebus برای پروژه 
از marvin جای mediateR استفاده کنیم 
از Mapperly به جای auto mapper
پکیج brighter هم خیلی خوبه 

![[Pasted image 20250422145909.png]]

خوب داره میگه که از Command برای CQRS استفاده میشه و با استفاده از DI این کار انجام میشه و وقتی که T هم میزاریم دیگه میتونیم درخواستمون از هر نوعی باشه input و out put میتونه باشه 

![[Pasted image 20250422145936.png]]

![[Pasted image 20250422145954.png]]

![[Pasted image 20250422150019.png]]

این تعریف بهتری داده :
![[Pasted image 20250422150253.png]]

![[Pasted image 20250422151825.png]]
این کلاس هستش که میاد منطق درست کردن کلاس user رو hangle میکنه ، ورودی میاد Create User Command رو میگیره و بعد خروجی User میده 
![[Pasted image 20250422151908.png]]

![[Pasted image 20250422152040.png]]

![[Pasted image 20250422154445.png]]

![[Pasted image 20250422154507.png]]

![[Pasted image 20250422154545.png]]


دقیقا همین داستان ها رو هم برای query داریم 

![[Pasted image 20250422154613.png]]

![[Pasted image 20250422154936.png]]


![[Pasted image 20250422160948.png]]

![[Pasted image 20250422165005.png]]

https://mehmetozkaya.medium.com/cqrs-abstraction-layer-on-mediatr-in-net-8-microservices-f63304992a3f

![[Pasted image 20250422165139.png]]

![[Pasted image 20250422170741.png]]

https://code-maze.com/cqrs-mediatr-fluentvalidation/

![[Pasted image 20250422170956.png]]

خوب برای استفاده از mediatR میایم و از اینترفیس IRequest استفاده میکنیم که هم command و هم query رو داره انجام میده 

برای استفاده ازش میایم و دو تا abstraction جدا ازش میسازیم 

![[Pasted image 20250422171257.png]]

![[Pasted image 20250422171415.png]]

خوب بعد میایم TRespose رو از نوع generic type رو تعریف میکنیم و بعد از out استفاده میکنیم

بعد میایم دو تا abstraction جدا هم برای handlers ها تعریف میکنیم 

![[Pasted image 20250422171710.png]]


![[Pasted image 20250422171732.png]]


خوب چرا میایم این interface ها رو تعیین میکنیم آیا اینترفیس های mediatR به اندازه کافی خوب نیست >؟
با درست کردن این abstraction ها ما انعطاف بیشتری داریم برای تغییر و اضافه کردن قابلیت های جدید 


![[Pasted image 20250422173305.png]]

اینجا تعریفی که کرده اینه که ما میخوایم تمامی command ها idempotent باشند یعنی فقط یک بار اجرا بشه 

خوب ما میتونیم ICommand inteface رو extent کنیم و یه IIdempotent Command Interface رو درست کنیم 

![[Pasted image 20250422173813.png]]


![[Pasted image 20250422180340.png]]

https://code-maze.com/cqrs-mediatr-fluentvalidation/


خوب توی کد بالا میاد یه اینترفیس درست میکنه که خوده اون میاد و از اینترفیس mediatR ارث بری کرده و بعد گفته که TCommand باید بیاد و ICommand TResponse رو پیاده سازی کنه 

![[Pasted image 20250423160248.png]]


![[Pasted image 20250423160324.png]]
خوب اینجا اول اومده از IRequest TResponse ارث بری کرده که یعنی میخواد اون رو extend کنه و ICommand داره میگه که خروجی هم از نوع TResponse هستش 

بعد اومده از همین اینترفیسی که درست کردیم و قراره custumize اش کنیم در خط پایین استفاده کرده اومده از این اینترفیس برای یک کلاس abstract استفاده کرده و همین به ما این قابلیت رو میده که برای پیاده سازی Command و استفاده از logic اش در جاهای دیگه ازش استفاده کنیم 

![[Pasted image 20250423160852.png]]




![[Pasted image 20250424105921.png]]

https://medium.com/@90mandalchandan/cqrs-architecture-how-it-works-5f18a36886ea

![[Pasted image 20250424112042.png]]

https://codewithmukesh.com/blog/cqrs-and-mediatr-in-aspnet-core/

![[Pasted image 20250424112106.png]]

### Registering MediatR

As we have already installed the required package to our application, let’s register MediatR handlers to the application’s DI Container. Open up `Program.cs` file.
```
builder.Services.AddMediatR(cfg => cfg.RegisterServicesFromAssembly(Assembly.GetExecutingAssembly()));
```


![[Pasted image 20250424142038.png]]

![[Pasted image 20250424143820.png]]

خوب اینجا یه سری قابلیت جدید اضافه شده :
https://learn.microsoft.com/en-us/ef/core/modeling/relationships/many-to-many

![[Pasted image 20250424150907.png]]

![[Pasted image 20250424170125.png]]
https://medium.com/@susithapb/understanding-singleton-scoped-and-transient-in-net-core-b7efede6c513#:~:text=A%20scope%20represents%20a%20certain,shared%20within%20a%20specific%20context.

error :
Unhandled exception. System.IO.FileNotFoundException: Could not load file or assembly 'System.Runtime, Version=10.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a'.

![[Pasted image 20250424175034.png]]

اونجا باید 64 win-X رو بنویسیم ارور حل میشه 

![[Pasted image 20250426113915.png]]

