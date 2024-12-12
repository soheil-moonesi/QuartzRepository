![[{01419EB7-CBF7-4A5C-96B0-FFB5A6F255DA}.png]]

## Importance of ISP

Adhering to the ISP leads to cleaner, more maintainable code by reducing the **coupling** between classes and ensuring that interfaces are tailored to specific client requirements. This enables developers to create modular systems that are easy to extend and modify, promoting a more flexible architecture.

خوب اهمیت ISP چیه؟ برای این که کد قابل نگهداری و تمیزی داشته باشیم اگر این قوانین رو رعایت کنیم کوپل شدگی بین کلاسهامون کم میشه و میتونیم با توجه به نیازهای client بیایم یه سری اینترفیس رو درست کنیم که به اون نیازها جواب بدیم.

## Examples of Violating ISP

### Fat Interfaces

A fat interface is an interface that contains too many methods, some of which may be unrelated or unnecessary for certain clients. Implementing a fat interface can lead to code bloat and increased coupling, violating the ISP.

خوب چیزهایی که این قانون رو نقض میکنن :

اینترفیس های شلوغ و چاق باعث میشن که ما بخوایم کلی متد غیر مرتبط و به درد نخور رو پیاده سازی کنیم. اگر از این مدل اینترفیس ها بخوایم استفاده کنیم کوپل شدگی توی کدمون بیشتر میشه.

### Unrelated Methods

When an interface contains methods that are unrelated to its core purpose, it becomes more difficult for clients to implement the interface correctly. Clients are forced to depend on methods they don’t need, leading to a violation of the ISP.

اگر توی اینترفیسمون بیایم متدی رو قرار بدیم که با اصل و هدف اصلی اون اینترفیس مغایرت داشته باشه ، پیاده سازیش توی کلاس های مورد استفاده سخت تر میشه و مجبور میشیم که این متد هایی که لازم نداریم رو هم پیاده سازی کنیم که همین باعث نقض قانون میشه.

Interface Segregation Principle in C#: Key Concepts

Implementing Interfaces

خوب فرض کنید که اومدیم و یه اینترفیس IWorker رو تعریف کردیم

```csharp
public interface IWorker{
     void Work();  
   void Eat();  
   void Sleep(); }
```

![[{9BBE0666-77D3-4F0A-86DB-5571892677C4}.png]]

خوب همونطور که میبینید این جا یه سری متدی که هیچ ربطی به رباط ها ندارن رو باید پیاده سازی کنیم که این قانون ISP رو نقض میکنه.

راه درست تعریف اینترفیس به این شکله :


![[{D88E6EB8-7F66-41BC-9D8E-E37EF8DD876D}.png]]

حالا اینجا دیگه انسان ها اینترفیس های خودشون رو دارن و رباط ها هم اینترفیس خودشون رو :

![[{90BCA653-80F1-472D-88E8-12EB4E811FED}.png]]


C# ISP: Best Practices

### Keep Interfaces Focused

Design interfaces with a single, focused purpose to prevent clients from being forced to implement unrelated methods.

### Use Multiple Interfaces

Instead of creating a single, monolithic interface, use multiple, smaller interfaces that can be combined as needed to suit different client requirements.

### Leverage Composition

Use composition to combine multiple interfaces and create flexible, modular classes that can be easily extended and modified.

[لینک](https://l.vrgl.ir/r?ad=1&l=https%3A%2F%2Fwww.bytehide.com%2Fblog%2Finterface-segregation-principle-in-csharp-solid-principles&si=qcdttrwckomm&st=post&k=mZfB62himmGIKll5XJ%2B0UB1syElab37D9mUrvj1KpNM%3D)


