اصل تک مسئولیته بودن

خوب حالا اگر بخوایم متوجه بشیم که داستانش چیه باید از خودمون این سوال ها رو بپرسیم:

- What is Single Responsibility Principle in C#?
- Why is Single Responsibility Principle important?
- Why use Single Responsibility Principle?
- How to implement Single Responsibility Principle in c#?

اصلا SRP چیه؟ چرا مهمه ؟ چرا باید ازش استفاده کنیم ؟ چجوری باید پیاده سازیش کنیم؟

برای توضیح دادنش باید این جمله رو بفهمیم:

**“Each software module or class should have only one reason to change”**

**هر ماژول یا کلاس فقط و فقط به یک دلیل باید عوض بشه**

**این اصل توضیح دادنش خیلی آسونه ولی توی عمل استفاده کردنش خیلی سخته**

![[{5A24F3EA-F978-420B-9282-475F82EDA7E8}.png]]

**“Enforce that a class only does one thing”**

**حالا چرا باید از SRP استفاده کنیم، چون کدمون تمیز میشه ، پیچیدگی هاش کمتر میشه و تبدیل میشه به یه کد خوانا و راحت برای فهمیدن و کار کردن.**

if you have a class in C# that does **X** thing and also does **Y** thing, I would suspect that you are not complying with the Single Responsibility Principle. It’s like a developer, it doesn’t matter if it’s you or me, if we are developers and our responsibility is to develop but at the same time we do Marketing, yes, we are gods but **we are not complying with the Single Responsibility Principle!**

**اگر شما یه کلاس دارید که کار الف و ب رو انجام میده آدم مشکوک میشه به این که شما احتمالا SRP رو رعایت نمی کنید.**

#### Why you should follow the Single Responsibility Principle

By implementing SRP in the code you can achieve several benefits at the code level and also save time. The biggest advantage of follow the C# SRP is to **have a clean c# code, reducing its complexity** and turning it into a simple and easy to read code.

خوب وقتی که SRP رو پیاده سازی میکنیم یه سری فواید داره برامون که بعدا توی زمان مون هم صرفه جویی و بهینه سازی میشه. یکی از مهمترین فوایدش کد تمیزه ، که باعث میشه پیچیدگی کمتر بشه و کد قابل خوندن بشه.

Another great advantage of implementing SRP in C# code is to gain the ability to **reuse or recycle code excerpts**. If the Single Responsibility principle is followed, it is possible to **reuse the logic of that code** in other parts of the application or directly reuse it in another project. You can save a lot of development time!

فایده بعدیش اینه که بهمون قابلیت دوباره استفاده کردن از این کلاس ها و کامپوننت هایی که درست کردیم رو میده.

Another advantage of using Single Responsibility Principle is coherence, that is, although each method does different things, when they are united they do one thing together and do it well.

مزیت بعدی coherence بودن که به این معنیه که درسته که هر کدوم از متد ها یه کاری انجام میدن ولی وقتی که چند تا متد رو یه جا جمع کنیم برای انجام دادن یک کار خاص عالی میشه.

### Main Benefits of C# Single Responsibility Principle

**Improves code simplicity:** If the Single Responsibility Principle in C# is respected and not violated, classes should only contain a single property or method. This makes it easier to understand what does what and the complexity of the code would be reduced.

خوب ، باعث ساده شدن کد میشه ، اگر میخواید این اصل رو درست پیاده سازی کنید معمولا اینطوری میشه که یه کلاس شما یکی دو تا پراپرتی داره با یکی دو تا متد، و اینطوری کلی از پیچیدگی های کد کمتر میشه.

**Maintains a manageable project:** Related to the previous advantage. When a class has only one responsibility, your developer brain will only have to think about that one responsibility and no more. This allows you to have a “” brain of information and allows you to think and manage the project or application better.

باعث میشه پروژه قابلیت مدیریت بشه، وقتی که یه کلاس وظیفه اش یک چیز باشه برنامه نویس موقعی که میخواد روش کار کنه فقط روی همون مورد کار میکنه نه بیشتر. این باعث میشه که راحت تر بتونید به اجزا پروژه فکر کنید و مدیریتش کنید.

- **maintenance and scalability:** If we think for a second about a class that violates the SRP, we will think about a class that does many things. If for any reason that class has to be modified, it will most likely return errors that did not happen before. If the class does only one thing, you will only have to see to it that you modify that one thing and check that it works well. You don’t have to worry that changing one thing will break another.

نگهداری و گسترش پذیری: اگر کلاس هایی که درست میکنیم قوانین SRP رو رعایت نکنه یه کلاس که چندین تا کار رو داره انجام میده داریم، حالا میخوایم به هر دلیلی بیایم داخلش یه چیزی رو تغییر بدیم احتمالا یه اروری بهمون میده که قبلا اتفاق نیوفتاده. اگر یه کلاس فقط یه کار رو انجام بده ما فقط میدونیم که باید برای همون کار بریم و ویرایشش کنیم و وقتی که ویراشش کردیم میریم چک کنیم ببینیم داره درست کار میکنه یا نه، حالا وقتی که اون کلاس داره چند تا کار رو انجام میده و ما میریم یه قسمتی ازش رو تغییر میدیم این تغییر ممکنه روی چند از برنامه تاثیراتی بزاره و ممکنه باعث های ارور های بیشتری بشه و پیدا کردن اون ارور ها هم مشکل تر میشه ولی وقتی که اون کلاس فقط یک رو داره انجام میده تکلیف ما مشخصه.

**Makes testability better:** As any good C# developer we know that writing and running [unit tests](https://www.bytehide.com/blog/unit-testing-csharp) is always advised and considered good practice. By respecting SRP we will find that writing unit tests in the class is an easy task since the class only does one thing and not several and therefore, reduces bux fixes and reduces testing time.

تست نوشتن رو راحت میکنه . خوب همه ما میدونیم که تست نوشتن خوبه. با پیاده سازی SRP ما میتونیم تست های بهتری برای کلاس هایی که داریم بنویسیم و این کار هم راحت تر میشه چون فقط اون کلاسه قراره یک کار رو انجام بده.

- **Reduces coupling:** If methods only do one thing, one of the things we C# developers will avoid is coupling. That is, a method will not depend on another method and this makes them more independent of each other.
- کم کردن کوپل شدگی در کد: اگر یه متد فقط یه کار رو انجام بده یعنی کوپل نشده چون این متد به یه متد دیگه برای اجرا شدنش وابسته نیست و این باعث میشه که هر دو این ها بتونن مستقل از هم کار کنن.
- **Facilitates code extension:** If the Sigle Responsibility Principle is met in C#, we have the possibility to combine these classes and build a more user-friendly and modular code. This can be achieved thanks to the dependency injection getting a more testable and extensible code.

خوب اگر ما این اصول رو رعایت کنیم میتونیم وقتی که برنامه جلوتر رفت بیایم کلاس ها رو با هم ترکیب کنیم و یه کد ماژولار و خوب درست کنیم. خوب میگه که ما میتونیم با استفاده از dependecy injection بیایم کد رو گسترش بدیم و تستش کنیم.

How To Implement Single Responsibility Principle in C#

Follow the Single Responsibility Principle in C# is easy as long as you know the responsibility of each class. That is the trick to be able to implement SRP in our apps or developments: **know the responsibility of each class**.

خوب حالا چجوری بیایم پیاده سازیش کنیم؟ بدونیم مسئولیت هر کدوم از کلاس ها چیه.

For this first case study example of a software C# code extract, we see how SRP is being violated, specifically the `Add` method.

خوب حالا میخوایم ببینیم این متد add چرا و چجوری داره این اصل رو نقض میکنه.

The `add` method is, on the one hand, adding a user and on the other hand, it is writing to the log. These are **too many things for one method**, it should only know and take care of one thing or responsibility.

متد add رو میخوایم بررسی کنیم، متد add از یه طرف داره یوزر رو اضافه میکنه و از یه طرف دیگه هم داره log میگیره . خوب برای یک متد این خیلی کار زیادیه برای یک متد، یه متد فقط باید یه کار بکنه و مسئولیتش یک مورد باشه.

![[{FDF42738-4638-4D5E-B4B3-74D42C158BE0}.png]]

For example, we should separate on one side the [action](https://www.bytehide.com/blog/action-in-csharp-tutorial) of adding a user and on the other side writing in the log.

خوب برای مثال باید یه طرف رو میزاشتیم برای اضافه کردن یوزر و یه طرف رو میذاشتیم برای log گرفتن.

Let’s take a look at the following example. In this example we have refactored the code following the SRP principle, separating the responsibilities into several classes.

خوب بیایم این مثال رو ببینیم. اینجا اومدیم کد رو ریفکتور کردیم با استفاده از SRP و مسئولیت ها رو جدا کردیم.

![[{114D9FCE-A2CD-4D4C-9AE4-8B95221C82D2}.png]]

In this simple way we respect the SRP principle and we could **reuse the code elsewhere** in a much simpler way. However, even if SRP is implemented and is not violated, **it can be done in a better way.**

**خوب ما میتونیم با اجرا کردن SRP کدی بنویسیم که بتونیم جاهای دیگه هم استفاده کنیم. خوب حالا میتونیم حتی بهتر از این مورد بالا رو هم پیاده سازی کنیم:**
![[{7951FD6E-ED90-492E-9473-846C6BE367FD}.png]]

In this example we can see that the `Add` method has been wrapped in an error handler. This way `User` only knows how to add the user and that is his only responsibility.

It is not really necessary to get to this point, this is a very punctual way and may not apply to all cases. As long as each of your classes handles only one responsibility, you will be complying with the SRP principle.

#### Single Responisbility Principle Example in Practice

When we are developing a project, we must take SRP into account and respect it, especially to give some reusability to our code. Let’s look at some Single Responsibility Principle example in C# and see how we can reduce coupling and increase cohesion.

خوب حالا میخوایم یه موردی رو بررسی کنیم که کوپل شدگی رو کمتر کنیم و cohesion رو بیشتر کنیم.

Violating the Single Responsibility Principle in C# (real world example)

Let’s imagine that we have a user logging. In this first example of SRP in C# we see that the `UserSettings` class has **several responsibilities** such as getting the user and verifying its credentials. Obviously this works but we are violating SRP.

خوب فرض کنید که userLogging داریم. حالا میبینیم که چند تا مسئولیت داره یکی این که یوزر رو بگیره و بعدیش چک کردن مشخصاتش هستش ، خوب این کد قطعا داره درست کار میکنه ولی SRP رو نقض کرده:

![[{BDFC62B8-C76B-4468-AEC6-2131EB6090FB}.png]]

To solve the Single Responsibility Princile violation in C# we should separate the methods of this class in several different classes.

خوب برای حل کردنش باید بیایم این متد ها رو جدا کنیم و توی کلاس های جداگانه قرار بدیم.

#### Refactoring Towards SRP in C#

As I said before, the best solution is to **split the functionality into 2 classes** so that there is only one task in the class. In this example the class `UserAuth` is born (_to identify and verify the user_), keeping the class `UserSettings` which is in charge of the rest of the user settings.

خوب حالا برای ریفکتور کردنش ، قرار شد که فانکشنالیتیمون رو به تا کلاس تبدیل کنیم که هر کلاس یه وظیفه داشته باشه. خوب در این حالت UserAuth وظیفه شناسایی و تایید یوزر میشه و کلاس UserSetting مسئول بقیه موارد.

![[{928552A5-4039-4D3D-9B6D-D893143C36FA}.png]]

![[{89CD8FF1-7EAC-42DF-8BD5-DA9F56D72CEE}.png]]

Now yes, now **each class only handles one responsibility**. If, for example, at some point we need to make a change in the responsibility, it will be as easy as modifying that single class.

خوب هر کلاس در این شرایط فقط یه مسئولیت دارن. حالا اگر بخوایم تغییری رو هم ایجاد کنیم دیگه کارمون راحته.

Detecting if the Single Responsibility Principle is being violated

از کجا بفهمیم که SRP نقض شده

**Number of imports:** Always keep an eye on the number of imports because if this number is high, it is very likely that the number of classes we are importing is very high and maybe there are extra things we are doing.

تعداد import ها : خوب یادمون باشه که تعداد بیشتری کلاس import داریم میکنیم به احتمال زیاد داریم چند تا کار رو انجام میدیم پس حواسمون باید بهش باشه.

**Number of public methods:** A simple way to detect SRP violation in C# is to check how many public methods a class has. If you wonder why, if a class has a large number of different public methods, most likely that class is doing several things at once and leads to not comply with Single Responsibility Principle.

تعداد public متد ها : خوب یه راهی که داریم اینه که چک کنیم ببینیم چند تا متد public داریم توی کلاسمون، اگر براتون سوال پیش میاد که چرا انقدر تعداشون زیاده احتمالا به خاطره اینه که اون کلاس داره چند تا کار انجام میده و SRP توش رعایت نشده.

**Difficult testing:** A good practice is to manage to write unit tests on the class. If writing these unit tests costs a little, most likely the class is doing several things at the same time.

خوب یه راه هم اینه که بیایم و برای کلاسمون تست بنویسیم اگر خیلی پیچیده شد و خیلی ازمون وقت گرفت احتمالا اون کلاس هم داره چند تا کار رو با هم انجام میده. چون اگر یک کارو انجام میداد راحت تست رو مینوشتیم و تمام.

**Number of lines:** Although it may seem absurd, this is often the way to identify that the Single Responsibility Principle is being violated. You only have to look at the size of the class and its number of lines. If you suspect that it has too much code for what it does, probably not only one task and has more than one responsibility.

با این به نظر غیر منطقی میاد ولی یه موقع هایی میشه از تعداد خط کد هایی که توی یه کلاس هستش حدس بزنیم که داره SRP رعایت میکنه یا خیر. اگر خیلی تعداد خط کد ها زیاد بود احتمالا اون کلاس داره چندین کار رو با هم انجام میده.

لینک مطلب : [لینک](https://www.bytehide.com/blog/single-responsibility-principle-in-csharp-solid-principles)
