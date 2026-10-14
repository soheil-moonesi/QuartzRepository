https://www.youtube.com/watch?v=DZbvL-bE0DA&list=PLN5rV4x2x5Xef7lcvrhdDBnJKVfVEw6ui&index=2

![[Pasted image 20260722144813.png]]


![[Pasted image 20260722145156.png]]

به اون جمله میشه statement

![[Pasted image 20260722145234.png]]


خوب toplevel statements 
![[Pasted image 20260722145348.png]]
یعنی اون statement اونجا رفته اون بالا 

تایپ ها pre defind و csutom type ها ، اولی رو کامپایلر از قبل میدونه 

خوب value type , reference type

خوب primitive ها و struct ها میشن value type و بقیه هر چی که هست میشه ref type 

![[Pasted image 20260722165658.png]]


![[Pasted image 20260722165851.png]]


![[Pasted image 20260722170116.png]]

![[Pasted image 20260722170143.png]]
چون فضای stack خیلی کمه میایم فقط ادرسش رو توی stack ذخیره میکنیم 

![[Pasted image 20260722170228.png]]
خوب نکته اینجاست که struct ها توی stack هستن چون value type هستن 
و int هم value type هستش برای همین توی stack هستش ولی s که string هستش چون از نوع refrence type هستش ادرسش رو فقط توی stack نگه میداریم 
![[Pasted image 20260722170348.png]]

خوب اون رنگیا به اضای هر عضو توی کلاس struct مون ساخته میشن

stck - filo

خوب حالا چون اینطوریه - اولین چیزی که پاک میشه info هستش بعدش میشه s بعدش میشه i 


![[Pasted image 20260722170718.png]]




![[Pasted image 20260722171215.png]]

این جا هم درسته که ذات struct از جنس value type هستش ولی خوده string از جنس Refrence type هستش 

![[Pasted image 20260722171440.png]]



![[Pasted image 20260722171649.png]]


اول میاد یه لیست درست میکنه توی stack که ادرسش توی هیپه بعدش بهش یه آدرس دیگه میده که توی ادرسه مقدار string هستش 


حالا اول کد رو ببینیم و بعد بریم سراغش - توضیحاتش پایین تر نوشته شده 

![[Pasted image 20261013095651.png]]

لیسته یه رفرنس تایپپ هستش و بعدش میایم 6 تا ازش میسازیم 



![[Pasted image 20260722172901.png]]
خوب توی اون قسمت زرده یه آدرس هست که توی اون آدرسه - کلاس info ساخته شده که حالا توی همون دوباره توی قسمت name اش یه آدرس هستش که داره به یه قسمت دیگه از حافظه اشاره میکنه که اونجا codenex رو نوشته 

![[Pasted image 20260722173006.png]]


![[Pasted image 20260722173036.png]]

![[Pasted image 20260722173058.png]]


خوب ویدیو بالا تموم شد 

https://www.youtube.com/watch?v=urEn4JOsqd4&list=PLN5rV4x2x5Xef7lcvrhdDBnJKVfVEw6ui&index=3

# statics memory allocations in c#

[](https://www.youtube.com/@iCodeNext)

![[Pasted image 20261013100306.png]]

![[Pasted image 20261013100516.png]]

به cpu وقتی که به هر کدو ما زپین هاش برق وصل میکنیم بهمون 1 میده بقیه صفر - این رو ما توی default value استفاده میکنیم :



![[Pasted image 20261013100628.png]]


توی stack هستش هستش value type ها 

خوب به طور مثال اگر ما 10 رو بخوایم داشته باشیم باید توی 8 بیت بسازیمیش و برای ساختن مثلا در 8 بیت نیاز داریم دو تا 1 داشته باشیم برای همین باید بهش برق بدیم 

حالا برای کم کردن مصرف برق اینا رو دیفالت گذاشیتیم صفر 

![[Pasted image 20261013101635.png]]

خوب ما که نمیدونیم که این name رو به کجا refrence بدیم توی heap برای همین میشه null 
 

![[Pasted image 20261013101810.png]]



خوب اگر name.lenth   رو بزنیم null refrence pointer میگیریم چون در heap خالیه

هر refrence tpe رو مثل کلاس user رو اگر new اش کنیم کلا در ابتدا null هستش چون مقداری بهش assign نشده برای همین null هستش پس توی stack هستش ولی مقدارش توی heap نال هستش 


خوب rosylin داره تضمین میده که توی Casting اطلاعات از دست نمیرود 

![[Pasted image 20261013105102.png]]

اینجا اوکیه 

ولی انجا 

![[Pasted image 20261013105147.png]]

ولی اینجا داره ارور میده چون یه تایپ بزرگ رو میخواد تبدیل کنه به کوچکتر 

ولی ![[Pasted image 20261013105337.png]]

اینجا explicit نه گرانتی میده نه ضمنی هستش 

خوب اون چیزی که کامپایلر نمیفهمه و ممکنه یه اطلاعاتی رو از دست میده از explicit استفاده میکنیم 

نکته جانبی :
اینجا برامون main و program داره ساخته میشه 

![[Pasted image 20261013110304.png]]

---
![[Pasted image 20261013110444.png]]

خوب اینجا اتفاقی که میوفته اینه که کنسول 0 رو نشون میده 
خوب اول ما صفر رو میفرستیم توی متد add و اونجا در خروجی add به ما 1 رو چون توی stack یک هستش و pop میشه و بعد number که در stack هستش 0 هستش 

![[Pasted image 20261013111155.png]]


در حالت بالا اگر ما اینطوری بنویسیم درست میشه 

```
number = Add(number)

```

![[Pasted image 20261013111620.png]]


ولی هدف مورد دیگه ایه 

حالا ما میخوایم value type رو به صورت ref type بفرستیم 

![[Pasted image 20261013111644.png]]


![[Pasted image 20261013111750.png]]

ما این رو refrence ای نکردیم -  ما فقط ادرس اون رو در stack  بود فرستادیم 

خوب به کل این میگن statement 

![[Pasted image 20261013111912.png]]

سمت راست میشه expression 

![[Pasted image 20261013112244.png]]


خوب اینجا تا اون خط زرده میشه این تصویر که واضحه 

![[Pasted image 20261013112420.png]]


----


![[Pasted image 20261013112744.png]]

تفاوت اینها چیه ؟

خوب تفاوتش اینه که 

![[Pasted image 20261013113215.png]]

اینجا وقتی که یه کلاس ساخته میشه اول توی stack یه آدرس میخورده که به یک آدرسی توی heap داره اشاره میکنه - که اونجا یه چیز دیگه ای هم هست به اسم metadata که اون تو داره اشاره میکنه به جایی که متد قرار داره و اگر یه instance دیگه بسازیم دوباره همین مراحل اتفاق میوفته 

![[Pasted image 20261013113537.png]]

خوب وقتی که چیزی رو میخوایم static کنیم یعنی میخوایم ازش زیاد استفاده کنیم در heap یه چیزی هست به اسم HFH - heigh frequently heap و متد static تمامی چیز هایی که میخواد رو در خودش داره و قرار نیست با متغییر بیرون تغییر بکنه 

![[Pasted image 20261013114235.png]]


در فضای multi thread این نخ ها 


ودیو تموم شد 

https://www.youtube.com/watch?v=0sWlxJ5hqXU&list=PLN5rV4x2x5Xef7lcvrhdDBnJKVfVEw6ui&index=4


![[Pasted image 20261013114928.png]]


خوب اینجا ما وقتی که داریم از out استفاده میکنیم داریم تعیین میکنیم که حتما باید این متغییر در داخل اون متد باید بهش asssign انجام شود حالا اگر return هم نکردیم ، نکردیم ولی حتما باید روش write انجام شود 

![[Pasted image 20261013120124.png]]


خوب وقتی که از in استفاده میکنیم حتما read only هستش و imutable هستش و قابل تغییر نیست 

ما داریم اینجا refrance اون متغییر رو میدیم ولی بدون تغییر 

چه زمانی cast و convert رو از هم جدا میکنیم ، 

![[Pasted image 20261013121528.png]]

اینجا implicit convert چون دو طرف از نوع numeric هستش 

![[Pasted image 20261013122046.png]]

اینجا explicit اتفاق میوفته و ما داریم به compiler میگیم که اوکیه این کار رو انجام بدیم 
یا explisit convert یا 
این جا بهش cast هم میگن 


![[Pasted image 20261013122401.png]]

خوب upcasting رو زمانیه که کلاس فرزند رو بخوایم cast کنیم بخه کلاس پدر 
و down casitng برعکسه 

 ![[Pasted image 20261013123134.png]]

خوب توی این تبدیل میخوایم - یه value type داریم و یه refrence type 
خوب اول عدد 5 وارد stack میشه 

![[Pasted image 20261013123316.png]]

خوب بعدش obj یه آدرس توی stack میگیره که اون توی heap قرار میگیره 

حالا ما میخوایم 5 رو بریزیم توی heap نه خودش رو بلکه یه کپی ازش رو میبریم میریزیم توی یه object که Ref type هستش - یعنی یه value type رو داریم میبریم به یه ref type اینجا میگن boxing اتفاق میوفته 

![[Pasted image 20261013124814.png]]

خوب برعکسش میشه unboxing 
خوب حالا اگر بخوایم برعکسش کنیم یعنی یه چیزی رو از heap بیاریم توی stack میشه unboxing 

![[Pasted image 20261013125423.png]]


![[Pasted image 20261013125547.png]]


![[Pasted image 20261013125555.png]]



![[Pasted image 20261013125834.png]]


خوب string ها thread safe هستن به خاطر این که immutable هستش 

![[Pasted image 20261013130040.png]]

ما میتونیم اول به یه نغییر string یه اسم بدیم مثلا mohammad بعدش هم میتونیم یه اسم دیگه بدیم مثل hasan ولی اتفاقی که میوفته اینه که وقتی که یه مقدار جدید بهش میدیم اون مقدار قبلی توی heap میمونه و فقط آدرسی که توی stack بوده تغییر میکنه به جایی که hassan هستش - اون مقدار قدیمی انقدر میمونه تا زمانی که gabage collector بیاد پاکش کنه 

خوب برای همین هست که میگن password رو به صورت plain string نگیریم چون توی ram میمونه و میشه ازشون سو استفاده کرد 

![[Pasted image 20261013130603.png]]

اگر اینجوری میخوایم انجام بدیم - انجام ندیم چون کلی string که به درد نمیخورن توی رم باقی میمونه 

![[Pasted image 20261013131115.png]]




برای همین با string builder بسازیم بهتره 

https://code-maze.com/stringbuilder-csharp/

![[Pasted image 20261013130923.png]]


![[Pasted image 20261013130939.png]]


![[Pasted image 20261013131100.png]]



خوب حالا داستان اینجاست که اینجا هم نمیاد همون string رو to upper کنه میاد یه جای دیگه این کار رو میکنه 

![[Pasted image 20261013131226.png]]

خوب ذات string یه array هستش و دونه به دونه اش char هستش 

![[Pasted image 20261013131328.png]]

اینجا هم char به char مقایسه رو انجام میده 24:34

 خوب قابلیت string اینه که theared safe هستش 
خوب یه قابلیت دیگه اش inrerning
![[Pasted image 20261013141148.png]]


![[Pasted image 20261013141204.png]]

خوب این اتفاق در عکس بالا اتفاق نمی اوفته 
چون string ها imutable هستن و در heap هستش این شکلی میشه :
![[Pasted image 20261013141323.png]]


![[Pasted image 20261013141353.png]]

با این دستور بالا میتونیم ref رو چک کنیم 


![[Pasted image 20261013141506.png]]


![[Pasted image 20261013141552.png]]

خوب چطوری میفهمه که این دیتا با هم یکسان هستند ؟

![[Pasted image 20261013142513.png]]



![[Pasted image 20261013142634.png]]


خوب آبجکت هایی که حجمشون زیاد هست میرن توی hoh هستیم ، و اون هایی که کوچک هستن soh هستش 

حالا ممکنه که بین این دو تا هم جا به جا بشن 

![[Pasted image 20261013142943.png]]

خوب وقتی که name_2 رو میخوایم mohamad رو بهش بدیم میره توی hoh چون string هستش و توی اون جا سکشن سکشن هستش و hoh میره اول چک میکنه ببینه mohamad هستش یا نه

خوب interning توی همون گوشه سمت راست هستش که ساختار Array داره 

شاید اسمش اینه 

![[Pasted image 20261013143347.png]]

---
https://www.youtube.com/watch?v=pGGLtkyAP7k&list=PLN5rV4x2x5Xef7lcvrhdDBnJKVfVEw6ui&index=5

ویدیو قبلی تموم شد این شروع شد :

![[Pasted image 20261013144345.png]]


![[Pasted image 20261013144503.png]]

خوب ct میشه compile time و پایینش میشه runtime 
خوب در دل clr ما یه کامپایلر داریم که اسمش jit هستش 
خوب وقتی که میخوایم یه فانکشن رو اجرا کنیم در همون لحظه در زمان rt  کد IL رو اجرا میکنه 
خوب چرا C# مستقیم به کد assembly تیدیل نمیشه ؟

خوب CLR بعد از یه مدتی اومد توی .net نشست 

خوب mirosoft اومد چندین تا rt داده - برای لینوکس و ویندوز  و ...

![[Pasted image 20261013145007.png]]


خوب حالا این jit برای ترجمه زبان میانی به rt ویندوز هستش 
خوب حالا یه jit هستش که مخصوص mac هستش 

![[Pasted image 20261013145228.png]]


![[Pasted image 20261013145308.png]]

اون بخش بالایی فارغ از چند سکویی بودنه 

خوب حالا میرسیم به این قسمت که ما میخوایم از list , dictionary استفاده کنیم که این ها در ویندوز به یه شکلی توی mac به یه شکل دیگه برای همین با CLR اومد یه BCL داد 

7:57

