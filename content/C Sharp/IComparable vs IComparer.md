خوب اینجا یه مطلب در حد بوندسلیگا نوشته که میخوایم با هم بخونیم : [لینک](https://l.vrgl.ir/r?ad=1&l=https%3A%2F%2Fdev.to%2Fdigionix%2Ficomparable-vs-icomparer-274f&si=znfnlpphloq8&st=post&k=PjbEOg5Ry0ra4MZPOKA3VNsKTs4NEzoMsBgg3yvFTJ4%3D)

## **Introduction**

When doing sorting in C#, you will come across with the interface IComparable and IComparer.  
Both of the interfaces are frequently used together, and people often got confused because of its similar name, even though they serve different purposes.  
On this article, I will explain the difference between both of the IComparable and IComparer.

خوب وقتی که میخوایم sort کنیم همیشه به این دو تا برمیخوریم IComparable و IComparer حالا با هم بررسیشون میکنیم.

First, let us dive into the concept of sorting.  
Assume that we have a list of integer that we want to sort in an ascending order.  
Since we are using the data type **Int** and the built in **List**, we can use the provided **Sort** method by Microsoft.

حالا بیایم برای این قضیه اول کانسپتشو رو ببینیم چیه. بیاید فرض کنیم که یه آرایه ای از integer داریم و میخوایم به صورت صعودی sort کنیم. خوب طبیعتا چون از list استقاده کردیم برای تایپ پس میتونیم از متد sort هم توش استفاده کنیم.

![[{4010B455-F429-4324-9168-1D3A14AA063C}.png]]

بعد نتیجه کد بالا میشه این:

![[{CA8F485F-13C5-4032-9015-F81C5AFEB948}.png]]


This works because the Sort method knows what it has to sort, which in this case is an Integer number.

این اینجا کار میکنه. چرا؟ چون متد sort میدونه دقیقا چطوری باید اعداد رو sort کنه.

But, what if I want to sort a list that contains user-defined class?  
Let's create a new class called Student, which will contain a name and age of a student.

Note: The age will be a random integer number between 17 to 50.

حالا فرض کنید که بخوایم یه list ای که شامل یه کلاس هستش رو sort کنیم و یه نکته ای هم که هست اینه که توی این کلاس ها سن یه عدد تصادفی از 17 تا 50 هستش، حالا چه کنیم؟

![[{4901F648-E8B4-4DDD-A773-5CE4B3CF888D}.png]]

اینجا میایم و 6 تا نمونه از این کلاس درست میکنیم و میریزیمش توی یک list

![[{395CAA96-A5B8-4DF4-989A-BAC0BDA36C97}.png]]

Then let's print out the list and sort it by their Age using the built in Sort function.

خوب حالا بیایم با همین متد sort کار رو انجام بدیم و نتایج مرتب شده رو هم نشون بدیم:

![[{A13120AF-C8FB-4F7D-8502-7A5A34179BE3}.png]]

اینجوری میشه:

![[{ED263343-77BE-49FD-A763-3B05F3A8487C}.png]]
میتونیم توی کنسول نمایش بدیمشون ولی نمیتونیم sort اش کنیم و به همچین اروری میخوریم:

![[{CED22C0D-D879-40DB-B27E-F18097287167}.png]]


This happens because the sorting algorithm doesn't know how to sort the elements. Which in this case is the Name of the student's class.

خوب این اتفاق برای این داره میوفته که الگوریتم sort نمیدونه چجوری باید این المان ها رو sort کنه.

## **IComparable**

To be able to sort it, we will have to implement the IComparable interface into our Student class.  
So let's start by implementing it to our class.

خوب حالا برای این که داستان رو رفعش کنیم باید بیایم اینترفیس IComparable رو پیاده سازی کنیم

![[{87054A9E-BF7B-47BD-80A7-0F851B9117FF}.png]]Now because we implemented the interface, we will have to implement its method as well.

Here we will be overriding the CompareTo method.  
The CompareTo method is used to compare one object with another object of the same type. It will then return an integer that indicates the position of the object in the sort order (precedes, follows, occurs)

خوب حالا وقتی که از اینترفیس استفاده کردیم باید متد مرتبط باهاش رو هم پیاده سازی کنیم. برای پیاده سازی هم باید متد CompareTo رو override کنیم.

این متد برای مقایسه یک آبجکت با یک آبجکت دیگه از همون تایپ استفاده میشه. مقدار خروجیش هم یه int هستش که نمایانگر موقعیت اون آبجکت در مرتب سازی داره.

If the current value is bigger than the next value it will return 1, else it will return -1. And if both of the value are the same it will return 0. It works like this:

- 1: Swap
- 0: Keep
- -1: Don't swap

اگر مقدار جاری از مقدار بعدی بزرگتر باشه 1 رو برمیگردونه اگر نبود -1 رو ، و اگر با هم برابر بودند 0 رو برمیگردونه.

For example, let's say that we have a List of [6,2,10,7,3].

Then we call the CompareTo method on the list, and it will compare the current item **6** with the next item **2**.

Since 6 is bigger than 2, it will return the value 1. So both of the element will swap.

The list is now [2,6,10,7,3] and it will repeat the process again until it becomes [2,3,6,7,10].

خوب برای مثال فرض کنید که یه لیست داریم با مقادیری که در خط بالا نوشته شده.

خوب حالا وقتی که متد CompareTo میخواد کارش رو انجام بده این کار رو میکنه

اول میاد 6 رو در نظر میگیره و بعد میاد با عدد بعدی که 2 هستش مقایسه میکنه و بعد چون عدد 2 از 6 کوچتر هستش مقدار -1 رو برمیگردونه پس در نتیجه جای این دو تا توی آرایه تغییر میکنه و همین پروسه برای المان های بعدی هم تکرار میشن.

حالا بیایم همین کار رو برای همون سوالی که ابتدای این متن اورده شده بود بکنیم:

![[{B3667E31-7565-4F2C-9B24-B382565436CE}.png]]

خوب اینم از نتیجه اش:![[{2D0F5886-C622-4F86-A999-17A83A3A43C2}.png]]

حالا بیایم همین قضیه رو برای اسامی تکرار کنیم یعنی بیایم بر است اسم sort کنیم:

![[{440994AE-7B51-4DB8-8208-0618F0F6B396}.png]]

این میشه نتیجه اش:

![[{2DF10378-63C8-4349-977F-E3F6C6C10697}.png]]

## **IComparer**

## حالا میرسیم به IComparer

Now after understanding how IComparable works, we can go into how IComparer works.

IComparable allows you to sort on a user-defined class that you have full control in. But, what if you want to apply the sorting in a class you don't have control? Which means you can't change the implementation of the class.

حالا که IComparable رو فهمیدیم میریم سراغ IComparer . خوب Icomparable بهتون آپشن هایی زیادی برای sort کردن یه کلاسی که کاملا تحت کنترلتون هست رو میده. حالا بیاید این رو در نظر بگیریم که کلاسی که میخوایم sort رو انجام بدیم کنترل کاملی روش نداریم و این به معنی این هستش که نمیتونیم داخل اون کلاس چیزی رو پیاده سازی کنیم.

![[{88E74264-12FB-4151-837D-144C2F1B274D}.png]]

Right now, if we call the sort method, it will sort the student by their names.

Let's say that we want to sort it by their ages. But since we can't modify the Student class, we won't be able to modify the CompareTo method.

This is where IComparer comes in. We will have to create a new class that implements the IComparer interface.

بیاید همین کد بالا رو نظر بگیریم، اینجا sort بر اساس name فقط داره انجام میشه و ما نمیتونیم کلاس student رو تغییر بدیم و میخوایم sort بر اساس Age هم انجام بشه ، اینجا دیگه نمیتونیم از متد CompareTo استفاده کنیم و اینجاست که میرسیم به IComparer که کار رو در میاره.

خوب اینجا همون اول میایم یه کلاس جدید میسازیم :

![[{3D6A9412-9925-4518-92A6-8FAF7919BD66}.png]]

خوب حالا وقتی که از این اینترفیس استفاده کردیم باید متد مرتبط باهاش رو هم پیاده سازی کنیم.

The Compare method is used to perform a comparison between two objects with the same type. It will then return a value which will indicate if one object is less than, equal to, or greater than the other object.  
This is what it means by the returned value:

- Less than zero: x is less than y
- Zero: x equals y
- Greater than zero: x is greater than y

خوب این متد compare برای مقایسه دو تا آبجکت از یک تایپ استفاده میشه و در جواب این مقایسه یه نتیجه ای رو برمیگردونه ، اگر x از y کوچک تر باشه less than zero اگر برابر باشه 0 و اگر بزرگتر باشه greater than zero

For example, let's say that we are comparing between two object 9 and 3.

When we are comparing it based on x - y, we will compare if 9 is bigger than 3, and since 9 is bigger than 3 it will return 1.

خوب فرض کنید دو تا آبجکت 9 و 3 رو میخوایم مقایسه کنیم ، اگر بخوایم مقایسه رو بر اساس x-y انجام بدیم چون 9 از 3 بزرگتره مقداری که برمیگردونه 1 هستش.

اینطوری هم پیاده سازی میشه:

![[{A813834E-6ACB-4CF7-BB97-120F057164C4}.png]]

What this is saying is that we will compare the first student's age by the second student's age.

Then we will have to implement our new StudentComparer class into our sorting method by passing it as parameter:

خوب حالا بعد از این که یه کلاس جدید ساختیم و متد compare رو توش پیاده سازی کردیم و بعد هم الگوریتیم sort اش رو تعریف کردیم ، حالا نوبت به این میرسه که این کلاس رو به عنوان پارامتر بندازیم توی متد sort برای این کار نهایی بشه.

![[{54CFC544-F010-4858-9192-7FB9CCFB380F}.png]]

این هم نتیجه اش:

![[{386E4A55-11CD-40B5-9685-D7FD4F39EA4A}.png]]

نکته : اگر بخوایم به ترتیب نزولی این کار رو بکنیم کافیه که جای x و y رو عوض کنیم و تمام.