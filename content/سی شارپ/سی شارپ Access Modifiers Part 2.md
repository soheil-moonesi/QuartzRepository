![[Pasted image 20241113025431.png]]

این عکس از این سایت گرفته شده : [لینک](https://l.vrgl.ir/r?ad=1&l=https%3A%2F%2Fraw.githubusercontent.com%2Fgist%2Fmichail-peterlis%2F67ab9f81f16cd2fb074d8ea9c8008653%2Fraw%2F1b41929acf1cab64b4cb386966659e079a9edef5%2Faccess_modifier.svg&si=gfba0fuzkkpq&st=post&k=dUOS%2BY885DOxaEM5A9cIiueuQOV%2BZJVlibC4aqN3Sps%3D) که لایو دمو هم داره و خیلی جالبه حتما یه سر بهش بزنید


In C#, if you don't specify an access modifier for a class, it will be given the default access modifier, which is `internal`. This means that the class will be accessible only within the same assembly (a compiled unit of code). It will be private to code outside of that assembly.


توی C# وقتی که هیچ دسترسی خاصی رو برای کلاس تعریف نکنیم به صورت default کلاس internal در نظر گرفته میشه .

خوب حالا اینجا میخوام یه مثال ی بزنم از اون ماشینی که توی تعریف کلاس توی این نوشته کردم

ببنید برای سرنشین یا کاربر پدال گاز public هستش ولی عملکرد موتور و این که چه اتفاقاتی در موتور میفته وقتی که داریم پدال گاز رو فشار بدیم رو سرنشین نمیدونه، که در این حالت میشه private

خوب یه موردی رو که باید دقت کنیم اینه که همه متد ها رو نباید public بزاریم. چرا؟

مثلا در نظر بگیرید که خوده راننده باید بیاد و میزان بنزینی رو که باید به موتور برسه رو دستی خودش تنظیم، خوب همونطوری که خودتون میدونید این خودش یه نقص و مشکل محسوب میشه پس برای همین موضوع باید حواسمون به نوع دسترسی ها در کلاس ها و متد ها باید باشه.

خوب حالا public میشه سطح دسترسی که همه بهش میتونن دسترسی پیدا کنن.

سطح private میشه زمانی که فقط اعضای داخلی میتونن بهش دسترسی پیدا کنن.

در نسخه های سی شارپ 7.2 به بعد private protected اضافه شده است.

سطح internal فقط در داخل همون پروژه ای که استفاده شده قابل دسترسی هست(در همون اسمبلی)