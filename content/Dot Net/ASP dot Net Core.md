![[Pasted image 20241211170700.png]]


حواسمون باید به ورژن .net و ورژن entity framework باشه چون ممکنه با هم سازگاری نداشته باشن و اینجا بهمون ارورش رو میده 

![[Pasted image 20241211170719.png]]

باید حواسمون به این هم باشه که از چه کلاسی داریم ارث بری میکنیم :

![[Pasted image 20241211170724.png]]


خوب تا اینجای کار اینطوری شد که اول اومدیم یه پروژه xunit ساختیم و بعد توی اون پروژه اومدیم پروژه ASP مون رو تعریف کردیم :

![[Pasted image 20241211170732.png]]

تا اونجایی که به خاطرم هست اینطوری میومدیم و با دیتابیس ارتباط برقرار میکردیم ولی بازم باید بخونم و بعد بنویسیم دقیقش رو 

```csharp
    public DataBaseContext(DbContextOptions options) : base(options)
    {
    }

    public DbSet<Product> Products { get; set; }
```


بعد میایم یه اینترفیس درست میکنیم


```csharp
    public interface IProductService
    {
        IEnumerable<Product> GetAll(); 
        Product Add(Product product);
        Product GetById(long id);
        void Remove(long id); 
    }
```




بعدش میایم برای کلاس productService اینترفیس رو پیاده سازی میکنیم 
در قسمتی که اومدیم یه پارامتر private برای دسترسی به دیتا بیس تعریف کردیم اول این که private برای این که فقط در اینجا بتونیم ازش استفاده کنیم و بعد این که readonly هستش چون فقط باید از این اطلاعات استفاده کنیم و نباید تغییرشون بدیم برای همین هم برای اطمینان از Readonly  استفاده شده.

```csharp
 public class ProductService : IProductService
 {

     private readonly DataBaseContext _context;

     public ProductService(DataBaseContext context) 
     {   
         _context = context; 
     }

     public Product Add(Product product)
     {
         throw new NotImplementedException();
     }

     public IEnumerable<Product> GetAll()
     {
         throw new NotImplementedException();
     }

     public Product GetById(long id)
     {
         throw new NotImplementedException();
     }

     public void Remove(long id)
     {
         throw new NotImplementedException();
     }
 }
```

بعد اینطوری تغییرش میدیم 

```csharp
        private readonly DataBaseContext _context;

        public ProductService(DataBaseContext context) 
        {   
            _context = context; 
        }

        public Product Add(Product product)
        {
           _context.Products.Add(product);
           _context.SaveChanges();
            return product;
        }

        public IEnumerable<Product> GetAll()
        {
            return _context.Products.ToList();     
              }

        public Product GetById(long id)
        {
            return _context.Products.Find(id);
                }

        public void Remove(long id)
        {
            var product = _context.Products.Find(id);
            _context.Products.Remove(product);
        }
    }
```

![[Pasted image 20241211170825.png]]

توی ویدیو  میاد و ProductService رو به startup اضافه میکنه ولی این قضیه توی .net ورژن های 4.8.1 به بعد مثل این که حذف شده.

![[Pasted image 20241211170847.png]]

![[Pasted image 20241211170849.png]]

![[Pasted image 20241211170851.png]]

![[Pasted image 20241211170858.png]]


خوب طبق چیزی که اینجا نوشته و من تقریبا خوندمش اینه که دیگه نیازی به این کلاس startup نداریم و میتونیم از program استفاده کنیم.

builder.Services.AddScoped<IProductService, ProductService>();

In ASP.NET Core, the line `builder.Services.AddScoped<IProductService, ProductService>();` is used to register the `ProductService` class as the implementation of the `IProductService` interface with a scoped lifetime. Here’s a breakdown of what this means and how it works:

### Dependency Injection in ASP.NET Core

ASP.NET Core has built-in support for dependency injection (DI), a technique used to achieve Inversion of Control (IoC) between classes and their dependencies. This helps in building loosely coupled, testable, and maintainable applications.

### Service Lifetimes

There are three main service lifetimes in ASP.NET Core:

1. **Transient**: Services are created each time they are requested.
2. **Scoped**: Services are created once per request.
3. **Singleton**: Services are created the first time they are requested and every subsequent request uses the same instance.

### Scoped Lifetime

`Scoped` services are created once per client request (connection). This is particularly useful in web applications where each HTTP request can have its own instance of a service.

### Registering Services

The `AddScoped` method registers the `ProductService` to be created and injected wherever `IProductService` is required. Here's a detailed explanation of the code:

builder.Services.AddScoped<IProductService, ProductService>();

- `builder.Services`: Accesses the `IServiceCollection` where services are registered.
- `AddScoped<IProductService, ProductService>()`: Registers `ProductService` as a scoped service for the `IProductService` interface.

خوب entity framework یه ورژن داره که میاد و توی مموری تست میکنه دیتا بیس رو و fake object و دیگه نیاز به sql server نداریم


![[Pasted image 20241211170914.png]]


builder.Services.AddDbContext< DataBaseContext >(ops => ops.UseInMemoryDatabase("TestDataBase"));

میام از لامدا استفاده میکنیم و بعد از متد Use in memory database استفاده میکنیم و بعد هم اسم اون دیتابیس فرضی رو  که میخوایم ازش استفاده کنیم رو مینویسیم.

خوب اینجا یه کار دیگه ای که میکنه اینه میاد میگه ما یه چیزی داریم به اسم Scaffolding 

![[Pasted image 20241211170927.png]]


یه سری کد برامون generate میکنه :

![[Pasted image 20241211170933.png]]![[Pasted image 20241211170936.png]]

![[Pasted image 20241211170940.png]]این نکته رو باید دقت کنیم که آخر اسم کلاسمون باید controller باشه تا عضو controler ها محسوب بشه و اجرا بشه



خوب برای ایجاد view ها میزنیم روی index کلیک راست میکنیم و بعد میزنیم روی razor view

![[Pasted image 20241211170951.png]]

![[Pasted image 20241211170955.png]]

بعد برای تست میام این کار رو میکنیم:

![[Pasted image 20241211171001.png]]

بعد میام این پروژه تستی که ساختیم رو وصل میکنیم به پروژه MVC

![[Pasted image 20241211171007.png]]


خوب حالا میخوایم برای index تست بنویسیم و ببینیم که براش یه لیست از product میفرسته یا نه ؟

![[Pasted image 20241211171014.png]]

خوب همونطوری که میبینید اینجا productController نیاز داره به یه پارامتر ورودی IproductService که ما میایم اون رو با moq درستش میکنیم.
با استفاده از سرویس ماک میتونیم سرویسمون رو به کنترلرمون وارد کنیم و ازش استفاده کنیم
توی محیط تست نمیشه IproductService رو اجرا کنیم و بعد اطلاعاتش رو بگیریم و در اختیار کنترلر بزاریم

![[Pasted image 20241211171022.png]]
اینجا توی استارت آپ تعریف شده و وقتی که برنامه شروع میشه از IproductService نمونه ساخته میشه و ازش در برنامه استفاده میشه.


![[Pasted image 20241211171030.png]]

این رو باید روی پروژه تست ناگتش رو نصب کنیم
 
ما سه تا کار رو باید انجام بدیم arrange , act , assert
خوب arrange کردن یعنی آماده سازی دیتا هایی که میخوایم ازشون استفاده کنیم
خوب Act یعنی اون عملیاتی که میخوایم بیایم روشون انجام بدیم

            var moq = new Mock<IProductService>();
    
اینجا اومدیم و میخوایم IprodutService رو که میخوایم رو ازش یه ماک درست کردیم و ریختیم توی پارامتر moq

![[Pasted image 20241211171045.png]]

بعد اومدیم با استفاده از setup که برای کتابخانه moq هستش میخوایم GetAll رو تست کنیم و حالا توی قسمت بعدش میگیم که اگر این صدا زده شد باید چی برگردونه 

خوب حالا اینجا میایم و یه لیست درست کنیم 

![[Pasted image 20241211171054.png]]


همونطوری که میبینید توی عکس دو تا بالایی اومدیم و از products استفاده کردیم
خوب حالا دیگه اصل کار که این همه کاره دیگه براش کردیم میشه این 

![[Pasted image 20241211171106.png]]

اینجا میایم و moq.object رو میدیم بهش
حالا میرسیم به قسمت Act که میخوایم عمل کنیم 

![[Pasted image 20241211171112.png]]

ما اون قسمت های بالا رو برای آماده سازی دیتاهایی که قراره به از این کنترلر وارد و خارج بشه انجام دادیم
حالا در مرحله آخر هم میایم assert اش رو انجام میدیم 
1.خوب توی productController همیشه باید index چیزی که میخواد برگردونه view باشه برای همین ما میخوایم برای این قضیه یه تست بنویسیم 

![[Pasted image 20241211171119.png]]


.تست بعدی که میخوایم بنویسیم اینه که میخوایم چیزی که برمیگردونه از لیستی از product ها باشه

![[Pasted image 20241211171128.png]]


خوب توی خط اول که با استفاده از تایپ داخلی تعیین شده ViewResult میایم چک کنیم که retrun result مون از نوع View هست یا نه 
بعدش میایم result رو خودمون دستی به نوع ViewResult تبدیل میکنیم ، چرا؟ چون میخوایم مدل و نوع دیتاش رو با نوع و مدل list product هامون توی تست چک کنیم برای همین این کار رو میکنیم 

خوب حالا برای این که خیلی توی تستمون رو شلوغ نکینم میتونیم یه کلاس جداگانه تعریف کنیم و دیتایی که میخوایم رو اون تو بنویسیم

![[Pasted image 20241211171134.png]]

حالا میایم اول ازش یه new میگیریم و بعد هم ازش استفاده میکنیم

![[Pasted image 20241211171145.png]]
خوب حالا میخوایم یه جای دیگه رو هم با این دیتا ها تست کنیم 

![[Pasted image 20241211171154.png]]


حالا اینجا داستانش چیه؟ ما اینجا میخوایم getById رو تست کنیم برای همین اول اومدیم از theory استفاده کردیم ، چرا؟ چون ورودی داریم و بعد با inlinedata ورودی میدیم به تست و بعد مثل روال قبلی اومدیم iproductservice رو ازش ماک درست کردیم و بعد بهش داریم میگیم که برو توی کلاس moqdata.getAll و بعد برو اولین چیزی رو که برات شرطش رو تعیین کردیم بیا یا اگر نتونستی دیفالتت رو بیار  و بعد براش تعریف کردیم که کدوم id رو میخوایم و کدوم valid هستش

![[Pasted image 20241211171201.png]]

حالا میرسیم به قسمت act و براش اینطوری تست رو مینویسیم فقط دقت کنید اینجا فقط برای یدونه از این product ها رو زدیم و میخوایم detail رو ببینیم و فقط لازمه که مدل دیتا از نوع کلاس product باشه 

خوب حالا برای این که تست خطاش رو هم انجام بدیم 
![[Pasted image 20241211171214.png]]


برای تستش هم اینجوری مینویسیم

![[Pasted image 20241211171224.png]]

خوب حالا تست بعدی رو میتونیم برای create بنویسیم اینطوری:
![[Pasted image 20241211171239.png]]

اول میایم چکش میکنیم ببینم مدلش درسته اگر درست بود badRequest میفرستیم

![[Pasted image 20241211171252.png]]

![[Pasted image 20241211171257.png]]
اینجا رفتیم قبلش توی کلاس product و پارامتر name رو attribute براش گذاشتیم Requied