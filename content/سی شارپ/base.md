
کی و کجا باید از base استفاده کرد؟

The `base` keyword is used to access members of the base class from within a derived class. Use it if you want to:

- Call a method on the base class that has been overridden by another method.
- Specify which base-class constructor should be called when creating instances of the derived class.

کلمه کلیدی base به ما قابلیت این رو میده که از داخل کلاس مشتق شده بتونیم به اجزا کلاس base که override شده دسترسی پیدا کنیم.

چون اگر به خاطرتون باشه ما در حالت عادی به تمام اجزای کلاس بیس دسترسی داریم ولی وقتی که یه متد کلاس بیس توسط یه کلاس مشتق override کردیم باید از base استفاده کنیم تا به اجزا کلاس بیس دسترسی پیدا کنیم.

به طور مثال:

![[{66EA0428-88F8-46D1-B54F-45DC424E3FCE}.png]]

خوب حالا بیایم این مثال رو بررسی کنیم، همونطوری که میبینید اینجا متد GetInfo توسط کلاس employee اومده override شده. حالا ما میخوایم همچنان از اطلاعات اولیه کلاس بیس استفاده کنیم که برای همین توی همون متد اومدیم از base استفاده کردیم

این مطالب از این [سایت](https://l.vrgl.ir/r?ad=1&l=https%3A%2F%2Flearn.microsoft.com%2Fen-us%2Fdotnet%2Fcsharp%2Flanguage-reference%2Fkeywords%2Fbase&si=spzbmdo9w1v9&st=post&k=H%2Bl85Ay1M5LnwDC6m4N1sjvSXwYR%2FFFzjBckX2rC8s0%3D) گرفته شده است.