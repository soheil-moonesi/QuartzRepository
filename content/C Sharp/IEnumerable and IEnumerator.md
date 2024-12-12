# Introduction

The IEnumerable interface is the base Interface for many collections in C#, and its job is to provide a way of iteration through a collection. That is why we can use for each loops to go through a List or a Dictionary. In simple English when a collection class implements the IEnumerable interface it becomes countable, and we can count each element in it individually

There are 2 versions of the IEnumerable Interface

1.IEnumerable T for generic collections

2.IEnumerable for nongeneric collections

میگه که IEnumerable interface اینترفیس پایه است برای خیلی از collection ها و وظیفه اش هم فراهم کردن یه راهی برای برای پیمایش توی یک collection هستش.

اگر بخوایم با فارسی راحت بیانش کنیم وقتی که یه کلاس بیاد این اینترفیس رو پیاده سازی کنه دیگه تمام اعضاش قابل شمارش میشن.

حالا دو مدل داریم از این اینترفیس ها :

generic & nongeneric

------

But since generic collections were introduced later after the non-generic ones and it is no longer recommended to use the non-generic collections in a new project due to their need to perform boxing and unboxing (converting the types of objects), we will explain how to use the

IEnumerable T interface in this lesson

خوب از اونجایی که اول generic collection ها معرفی شدن و یکم بعدش nongeneric ها پیشنهاد میشه که دیگه از generic ها توی پروژه های جدید استفاده نشه چرا که اگر بخوایم ازشون استفاده بکنیم باید boxing و unboxing که به نوعی میشه تبدیل تایپ های آبجکت ها رو انجام بدیم (که گفته بعدا توضیح میده راجع بهش)

IEnumerable T contains a single method that you must implement when implementing this interface; GetEnumerator(), which returns an IEnumerator T object. The returned IEnumerator T provides the ability to iterate through the collection by exposing a Current property that points at the object we are currently at in the collection.

حالا چجوری بیایم IEnumerable پیاده سازیش کنیم ؟

خوب یه متدی هست که باید برای این اینترفیس پیاده سازی کنیم که اسمش هست GetEnumerator و میاد IEnumerator T object رو برمیگردونه. خوب اینی که برگردوند هم به ما قابلیت این رو میده که توی اون collection پیمایش کنیم با استفاده از اشاره کردن به آبجکت جاری در کالکشن

IEnumerables have a method to get the next item in the collection, so they look at items 'one at a time,' they don’t need the whole collection to be in memory. They don’t know how many items are in it for each loop. It just keeps getting the next item until it runs out. IEnumerables also help ensure immutability (read-only)

باید یه متدی هم باشه که به آیتم بعدی توی اون collection اشاره کنه، تا بتونیم در لحظه فقط یکی از اون آیتم ها رو ببنیم، دلیل این کار اینه که دیگه مجبور نشیم کل اون کالکشن رو وارد مموری کنیم. ما توی foreach نمیدونیم که چند تا آیتم هستش ولی میریم آیتم بعدی رو میاریم و انقدر انجام میدیم تا برسیم آخرش.

و IEnumerables باعث immutability (read-only) میشه ، این یعنی که کالکشن ما به هیچ عنوان اعضای داخلشون تغییر نمیکنه.

when it is recommended to use the IEnumerable interface:

- Your collection represents a massive database table, you don’t want to copy the entire thing into memory and cause performance issues in your application.

When it is not recommended to use the IEnumerable interface:

- You need the results right away and are possibly mutating/editing the objects later on. In this case, it is better to use an Array or a List

کی بهتره که از IEnumerable استفاده کنیم؟ زمانی که کالکشنی که داریم حاوی یه دیتا table خیلی حجیمه و این که ما نمیخوایم این همه دیتا رو بیاریم بریزیم توی مموری چون باعث اختلال در اجرای برنامه میشه.

خوب حالا کی نباید ازش استفاده کنیم: زمانی که میخوایم همون موقع دیتاهامون رو ببینیم و شاید بعدا بخوایم آبجکت های داخلشون رو تغییر بدیم در این حالت بهتره از همون Array یا List استفاده کنیم

### Making your Classes Enumerable

Class 1: a class called dog which has two properties

1. string Name
2. bool IsNaughtyDog

and one method

1. GiveTreat() which will cause the dog to say 'wuf' on the console :)

خوب حالا ما میخوایم یه کلاس Enumerable درست کنیم

اول مایم یه کلاس به اسم dog تعریف میکنیم با دو تا پراپرتی : نام که از نوع string و isNaughtyDog (آیا سگ بدیه ) که از نوع bool هستش تعریف کردیم . با یک متد GiveTreat که سگه میگه واق ، سناریو در حد بوندسلیگا .

```csharp
//a class named Dog which we will use in another class called DogShelter which will contain a //collection of this class 
class Dog {
//the name of the dog
public string Name { get; set; }
//is this a naughty dog
public bool IsNaughtyDog { get; set; }
//simple constructor
public Dog(string name,bool isNaughtyDog) {
this.Name = name;
this.IsNaughtyDog = isNaughtyDog;
}
//this method will print how many treats the dog received
public void GiveTreat(int numberofTreats) {
//print a message containing the number of treats and the name of the dog
Console.WriteLine('Dog: {0} said wuoff {1} times!.', Name, numberofTreats);
}
}
```

حالا بیایم کلاس DogShelter رو بسازیم :

```csharp
//a class named DogShelter this class contains a generic collection of type Dog
//objects of this class can't be used inside a for each loop because it lacks an implementation //of the IEnumerable interface
class DogShelter {
//list of type List<Dog> dogs
public List<Dog> dogs
//this constructor will initialize the dogs list with some values
public DogShelter() {
//initialize the dogs list using the collection-initializer
dogs = new List<Dog>() {
new Dog('Casper',false),
new Dog('Sif',true),
new Dog('Oreo',false),
new Dog('Pixel',false),
};
}
}
```

خوب حالا بیایم و foreach کار رو در بیاریم :

```csharp
using System;
using System.Collections.Generic;
namespace IEnumerableandIEnumerator {
class Program {
static void Main(string[] args) {
//create a new object of type DogShelter
DogShelter shelter = new DogShelter();
//for each dog in the DogShelter object
foreach(Dog dog in shelter) {  //error because the DogShelter class does't implement the
//IEnumerable interface yet
//if the dog is not naughty (good boy)
if (!dog.IsNaughtyDog) {
//give this dog 2 treats
dog.GiveTreat(2);
} else {
//also give treats :) but only 1
dog.GiveTreat(1);
}
}
}
}
}
```

ولی اینجا اتفاقی که میوفته اینه که به این ارور بر میخوریم:

_//error because the DogShelter class does't implement the IEnumerable interface yet_

_چون هنوز IEnumerable رو اوکی نکردیم :_

```csharp
class DogShelter : IEnumerable<Dog>{
//list of type List<Dogs>
public List<Dog> dogs;
//this constructor will initialize the dogs list with some values
public DogShelter() {
//initialize the dogs list using the collection-initializer
dogs = new List<Dog> dogs() {
new Dog('Casper',false),
new Dog('Sif',true),
new Dog('Oreo',false),
new Dog('Pixel',false),
};
}
//this method will get generated for us
//we will use this method to provide implementation to the GetEnumerator() method of the //IEnumerator interface
public IEnumerator<Dog> GetEnumerator() {
//since our list of dogs is a generic collection that already implements its own IEnumerable //interface we will return it
return dogs.GetEnumerator();
}
//this method will get generated for us
//since in this example we won't be passing our class to a non-generic method we don't need //to provide an implementation for it at this point
IEnumerator IEnumerable.GetEnumerator() {
throw new NotImplementedException();
}}
```

کد نهایی:

```csharp
using System;
using System.Collections;
using System.Collections.Generic;
namespace IEnumerableandIEnumerator
{

    class Program
    {

        static void Main(string[] args)
        {

            //create a new object of type DogShelter
            DogShelter shelter = new DogShelter();
            //for each dog in the DogShelter object
            foreach (Dog dog in shelter)
            {//error because the DogShelter class does't implement the IEnumerable interface yet
             //if the dog is not naughty (good boy)
                if (!dog.IsNaughtyDog)
                {
                    //give this dog 2 treats
                    dog.GiveTreat(2);
                }
                else
                {
                    //also give treats :) but only 1
                    dog.GiveTreat(1);
                }
            }
        }
    }

    //a class named Dog which we will use in another class called DogShelter which will contain a collection of this class
    class Dog
    {
        //the name of the dog
        public string Name { get; set; }
        //is this a naughty dog
        public bool IsNaughtyDog { get; set; }
        //simple constructor 
        public Dog(string name, bool isNaughtyDog)
        {
            this.Name = name;
            this.IsNaughtyDog = isNaughtyDog;
        }
        //this method will print how many treats the dog received 
        public void GiveTreat(int numberofTreats)
        {
            //print a message containing the number of treats and the name of the dog
            Console.WriteLine('Dog: {0} said wuoff {1} times!.', Name, numberofTreats);
        }
    }

    class DogShelter : IEnumerable<Dog> {
 
       //list of type List<Dog>
        public List<Dog> dogs;
	//this constructor will initialize the dogs list with some values
        public DogShelter()
    {
        //initialize the dogs list using the collection-initializer
        dogs = new List<Dog>() {
        new Dog('Casper', false),
        new Dog('Sif', true),
        new Dog('Oreo', false),
        new Dog('Pixel', false),
            };
    }

    //this method will get generated for us 
    //we will use this method to provide implementation to the GetEnumerator() method of the
   //IEnumerator interface
    public IEnumerator<Dog> GetEnumerator()
    {
        //since our list of dogs is a generic collection that already implements its own
        //IEnumerable interface
        //we will return it
        return dogs.GetEnumerator();
    }

    //this method will get generated for us
    //since in this example we won't be passing our class to a non-generic method we don't 
   //need to provide an implementation for it at this point
    IEnumerator IEnumerable.GetEnumerator()
    {
        throw new NotImplementedException();
    }
}
}
```

البته شاید این کد ها توی این محیط ویرگول ناخوانا باشند برای همین به [لینک مقاله اصلی](https://l.vrgl.ir/r?ad=1&l=https%3A%2F%2Ftutorials.eu%2Fienumerable-and-ienumerator%2F&si=b2uo8zrfsgdt&st=post&k=rXZTZ6lAwhUrHsGP5Zbu88wCFqan9IyoZEa5wBHfBeI%3D) مراجعه کنید و همچنین برای درک بیشتر مطالب به این لینک [یوتیوب](https://l.vrgl.ir/r?ad=1&l=https%3A%2F%2Fwww.youtube.com%2Fwatch%3Fv%3DVcAubtFBOdY%26ab_channel%3DtutorialsEU&si=b2uo8zrfsgdt&st=post&k=ZqKI0l%2BPHUdmLkjMiMAoP93J7S7cMvn6D2DA0kIwlxE%3D) مراجعه کنید