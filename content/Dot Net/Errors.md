این اروری بود که وقتی که میخواستم add migration رو انجام بدم بهش برخوردم و بعد برای رفع ارور گفته شده که به جای پکیج sqlite.core بیایم و پیکج sqlite رو نصب کنیم و این مشکل رو حل کرد 
Unable to create a 'DbContext' of type ''. The exception 'You need to call SQLitePCL.raw.SetProvider().  If you are using a bundle package, this is done by calling SQLitePCL.Batteries.Init().' was thrown while attempting to create an instance. For the different patterns supported at design time, see https://go.microsoft.com/fwlink/?linkid=851728

![[Pasted image 20250428133854.png]]



![[Pasted image 20250428134011.png]]

![[Pasted image 20250428134039.png]]


error:
Unable to create a 'DbContext' of type ''. The exception 'The entity type 'MeetingLinkUser' requires a primary key to be defined. If you intended to use a keyless entity type, call 'HasNoKey' in 'OnModelCreating'. For more information on keyless entity types, see https://go.microsoft.com/fwlink/?linkid=2141943.' was thrown while attempting to create an instance. For the different patterns supported at design time, see https://go.microsoft.com/fwlink/?linkid=851728

اینجا یه کلاس داریم که دو تا کلاس دیگه رو داره به هم وصل میکنه برای روابط چند به چند داره ازش استفاده میشه برای همین دو تا primery key داریم که باید تعریفش کنیم توی کلاس های دیگه چون از id استفاده کردیم به صورت اتوماتیک اومده اون رو pk در نظر گرفته است.

![[Pasted image 20250428143227.png]]

اینجا اومدیم و با دستور hasKey براش pk رو تعریف کردیم و ارور حل شد 
