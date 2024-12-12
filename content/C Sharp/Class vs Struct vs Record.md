به نظرم دونستن تفاوت های و شباهت های این ها میتونه خیلی کمک کننده باشه برای همین اومدم از این مقاله رو خوندم: [لینک](https://l.vrgl.ir/r?ad=1&l=https%3A%2F%2Fwww.shekhali.com%2Fclass-vs-struct-vs-record-in-csharp%2F&si=ubuxlfcxlg77&st=post&k=tn4YF0zlbPXVIv7R7ld%2BHC9F0pLtf07ft%2FCb0OLu7Sk%3D)

Classes are reference types that store data on the heap. They are well-suited for creating complex objects that may require features like inheritance, polymorphism, and encapsulation.

Structs are value types that store data directly on the stack. They are suitable for efficiently storing small and simple data types, making them a good choice when performance is a priority.

Records, like classes, are reference types that store data on the heap. However, records are specifically designed to represent immutable data structures. Immutable means that it cannot be changed once the data is set. Records provide built-in functionality for comparing and hashing objects, making them useful for scenarios where data integrity is important.

کلاس ها : refrence type هستن و دیتا ها رو توی heap ذخیره میکنن. برای درست کردن آبجکت های پیچیده که نیاز داره از ارث بری ، polymorphisim و encapsulation داره میتونیم استفاده کنیم.

نوع struct که دیتا ها رو روی stack ذخیره میکنه و خیلی مناسبه برای دیتای ساده و کوچک و خیلی به سرعت اجرا هم کمک میکنه (یعنی سرعت اجراش سریع تره)

نوع records مثل کلاس ها refrence type هستش و دیتا ها رو روی heap ذخیره میکنه ولی record ها برای این ساخته شدن که دیتای داخلشون تغییر پیدا نکنن و immutable باشن. یعنی وقتی که set میشن دیگه قابل تغییر نیستن. داخل record ها هم یه سری فانکشن های از پیش ساخته شده هست برای مقایسه و موراد دیگه که میشه روی آبجکت ها ازشون استفاده کرد. جاهایی که یکپارچگی دیتا ها مهمه از record بهتره استفاده بشه

![[{7901D0B3-9379-4B3E-ABBC-88E6C18C4661}.png]]

