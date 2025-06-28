![[Pasted image 20250430214338.png]]
![[Pasted image 20250430214422.png]]

![[Pasted image 20250430214302.png]]
خوب توی این پروژه اومدیم از mapperly به جای Auto mapper استفاده کردیم :

![[Pasted image 20250504180121.png]]



![[Pasted image 20250504164818.png]]
خوب برای استفاده ازش میایم یه کلاس میسازیم به اسم User Mapper 
نکته اینه که باید از partial استفاده کنیم 
دلیل استفاده از partial اینه که میاد کلاس های اصلی رو extend میکنه و یعنی قسمتی از کلاس های اصلی هستتش 
بعد attribute رو مینویسیم mapper


![[Pasted image 20250504170446.png]]

![[Pasted image 20250504181151.png]]

خوب حالا میخوایم بگیم که بیا و userAddDto رو تبدیل که به user که در تصویر بالا هستش
از name of هم به جای magic string ها استفاده کردیم که اگر تغییرش دادیم ارور بده و متوجه بشیم 
خوب توی User Add dto to user هم ورودی رو با توجه به Dto میگیریم که اینجا تعیین کردیم فقط email باشه و بعد mapperly میاد map اش میکنه به user و اینطوری میتونیم بریزیمش توی database

![[Pasted image 20250512213719.png]]


![[Pasted image 20250512213707.png]]

اون هایی که مرتبطه با bootstrap رو پاک مکینیم و اون هایی که برای mud blazor هستش رو اضافه میکنیم :
![[Pasted image 20250512214222.png]]

https://www.youtube.com/watch?v=IhA_dE4XF9o&t=288s&ab_channel=NaveenBommidiTechSeeker


نکته ای که داره اینه که اگر بخوایم api و front رو به هم وصل کنیم این دو تا موقع compile شدن میرن توی همدیگه و با هم build میشن و این درست نیست برای همین میایم و یک class library رو بینشون میزاریم و بهش refrence میدیم 

error
``` c#
Unable to create a 'DbContext' of type ''. The exception 'The entity type 'IdentityUserLogin<string>' requires a primary key to be defined. If you intended to use a keyless entity type, call 'HasNoKey' in 'OnModelCreating'. For more information on keyless entity types, see https://go.microsoft.com/fwlink/?linkid=2141943.' was thrown while attempting to create an instance. For the different patterns supported at design time, see https://go.microsoft.com/fwlink/?linkid=851728
```

![[Pasted image 20250529135428.png]]

![[Pasted image 20250529135341.png]]
وقتی که بعد از تنظیم کردن jwt میخوایم migration بزنیم این ارور میومد ، بعدش که درستش کردیم migration انجام شد 

دقت کنیم که بعد از این عملیات هستش که یه سری جدول رو میاد توی دیتابیس برای identity درست میکنه 

![[Pasted image 20250529135613.png]]

![[Pasted image 20250529135631.png]]


![[Pasted image 20250529135644.png]]



![[Pasted image 20250529135716.png]]

![[Pasted image 20250529135732.png]]

![[Pasted image 20250529135748.png]]


![[Pasted image 20250529135801.png]]


خوب حالا برای این که بخوایم از سمت blazor به api درخواست بزنیم باید این کار ها رو انجام بدیم :

![[Pasted image 20250606174739.png]]

![[Pasted image 20250606174726.png]]


![[Pasted image 20250606174757.png]]

![[Pasted image 20250606174822.png]]

![[Pasted image 20250606174849.png]]

```c#
// Services/ApiService.cs
using System.Net.Http.Json;

public class ApiService
{
    private readonly HttpClient _httpClient;
    
    public ApiService(HttpClient httpClient)
    {
        _httpClient = httpClient;
    }
    
    public async Task<string> PostExampleData(ExampleModel model)
    {
        var response = await _httpClient.PostAsJsonAsync("api/example", model);
        response.EnsureSuccessStatusCode();
        
        var result = await response.Content.ReadFromJsonAsync<ApiResponse>();
        return result.Message;
    }
}

public class ExampleModel
{
    public string Name { get; set; }
    public int Value { get; set; }
}

public class ApiResponse
{
    public string Message { get; set; }
}
```

![[Pasted image 20250606174936.png]]

![[Pasted image 20250606175002.png]]

```C#
@page "/example"
@inject ApiService ApiService

<h3>Post Example</h3>

<EditForm Model="@model" OnValidSubmit="@HandleSubmit">
    <DataAnnotationsValidator />
    <ValidationSummary />
    
    <div class="form-group">
        <label>Name:</label>
        <InputText @bind-Value="model.Name" class="form-control" />
    </div>
    
    <div class="form-group">
        <label>Value:</label>
        <InputNumber @bind-Value="model.Value" class="form-control" />
    </div>
    
    <button type="submit" class="btn btn-primary">Submit</button>
</EditForm>

@if (!string.IsNullOrEmpty(resultMessage))
{
    <div class="alert alert-success mt-3">@resultMessage</div>
}

@code {
    private ExampleModel model = new ExampleModel();
    private string resultMessage;
    
    private async Task HandleSubmit()
    {
        resultMessage = await ApiService.PostExampleData(model);
    }
}
```

خوب حالا میخوایم jwt همراه req بیاد توی سرور :

![[Pasted image 20250609123414.png]]


![[Pasted image 20250609120024.png]]

خوب اول میایم  IHttpClientFactory service رو register میکنیم با استفاده از DI

بعدش httpClent Configuration با یه اسمی درست میکنه که بعدا میتونیم ازش استفاده کنیم 

![[Pasted image 20250609120351.png]]

خوب اون اسمی که بالا گفتیم رو گذاشتیم به طور مثال Api Calls که برای HttpClient Configuration استفاده میشه 

خوب http clinet factory پترن میاد http clinet رو life time اش رو مدیریت میکنه ، از Socket exhustion و مشکلاتی که داره جلوگیری میکنه 

تغییرات dns رو هندل میکنه 

![[Pasted image 20250609120620.png]]

خوب حالا از بالا ما اومدیم یه http clinet رو درست کردیم حالا میخوایم configure اش کنیم قبل از این که بخوایم ازش استفاده کنیم 

در نهایت client میشه htto clint که configure اش تموم شده و تنظیماتش انجام شده 

هر باری که یه http clinet درست میشه - یعنی هر باری که یه درخواستی از سمت کاربر به سمت سرور میاد http clinet ساخته میشه 

این امکان رو به ما میده که dynamic بیایم configuration رو انجام بدیم 


![[Pasted image 20250609121057.png]]


خوب base address میشه url ریشه ای که تمامی req ها بهش زده میشه 
اجزای url میشه https , host , port  و traling slash که برای درست کردن ترکیب url ها استفاده میشه 

![[Pasted image 20250609121258.png]]

![[Pasted image 20250609121325.png]]

خوب حالا میخوایم header رو تنظمیات براش درست کنیم 

میخوایم تعیین کنیم و به سرور بگیم که از سمت clinet درخواست هایی که داره میاد باید از چه نوع media type ای باشه 

با media type with quality header value میایم میگیم که media type چه خصوصیاتی باید داشته باشه ، اینجا داریم تعیین میکنیم که از نوع Application / json باشه 

![[Pasted image 20250609122401.png]]

میتونیم بهش authorization header اضافه کنیم ، custom api kkey اضافه کنیم , cache control رو باهاش تنظیم کنیم 

![[Pasted image 20250609122544.png]]

خوب اینطوری شروع میشه که اول این configuration تو سروریس ها ثبت میشه 

بعد IHttp clinet factory رو به صورت singlethon میایم و register اش میکنیم 

بعد وقتی که clinet اومد درخواست زد factory میاد و http message handler رو با تنظیماتی که درست کردیم درست میکنه 

بعد hanlder ها و policy ها میتونن بهش اضافه بشن 

و handler ها میرن داخل httpclinet 


خوب یه نکته ی مهم اینه که ما اینجا اومدیم و نوع media رو اومدیم json تعیین کردیم و در جلوتر میایم میگیم که وقتی که داره یه درخواست میاد باید یه سری تنظیمات دیگه رو هم داخلش داشته باشه 



```c#
            client.DefaultRequestHeaders.Authorization = new AuthenticationHeaderValue("Bearer", tokenParts[1]);
```

![[Pasted image 20250609131136.png]]

و اینجا داریم تعیین میکنیم که اولش باید bearer باشه و بعدش قسمت اول توکن که این میتونه چندین تا قسمت داشته باشه که جلوتر چکش میکنیم 

```c#
public class AuthService
{
    private readonly IHttpClientFactory _httpClientFactory;
    private readonly IJSRuntime _jsRuntime;

    public AuthService(IHttpClientFactory httpClientFactory, IJSRuntime jsRuntime)
    {
        _httpClientFactory = httpClientFactory;
        _jsRuntime = jsRuntime;
    }

    public async Task<bool> CheckAuth()
    {
        try
        {
            var client = _httpClientFactory.CreateClient("ApiCalls");
            
            // Get the token from localStorage
            var token = await _jsRuntime.InvokeAsync<string>("localStorage.getItem", "user");
            if (string.IsNullOrEmpty(token))
            {
                return false;
            }

            // Split the token to get the JWT part
            var tokenParts = token.Split(';');
            if (tokenParts.Length < 2)
            {
                return false;
            }

            // Set the Authorization header
            client.DefaultRequestHeaders.Authorization = new AuthenticationHeaderValue("Bearer", tokenParts[1]);

            // Make the request
            var response = await client.GetAsync("api/Auth/authCheck");
            return response.IsSuccessStatusCode;
        }
        catch
        {
            return false;
        }
    }
}

```


خوب در آخر هم میایم چک میکنیم ببینیم این توکن درست هستش یا خیر 

البته این تنظیمات در حال حاضر هستش ولی در جلوتر ممکنه تغییر کنه 

https://medium.com/@shahriyarali08/authentication-and-role-based-authorization-in-blazor-wasm-using-jwt-and-7bcc12317ea
از روی لینک بالا پیاده سازیشو انجام دادم 

https://blazorschool.com/tutorial/blazor-wasm/dotnet7/basic-jwt-authentication-683869


برای ریفکتور کردن بهتره که توی قسمت Share فقط dto ها باشند 
اون هایی که مرتبط با دیتابیس هستند وارد share نکنند یعنی اون هایی که مرتبط با ef هستند 
اون هایی که مرتبط با auth هستند توی share نباشند 
فقط dto هایی که هم در سمت api و هم در سمت clinet مورد نیاز هستند رو در share قرار بدیم نه همه ی dto ها رو 
قسمت frontend پروژه اصلا نباید داخلش dto باشه اصلا لازم نیست front از نوع و مدل دیتایی که قراره از api به سمتش بیاد رو بدونه 

اگر قراره سمت front بیایم و dto داشته باشیم این dto ها نباید به هیچ عنوان در api مورد استفاده قراره گرفته باشند یا شبیه به این ها باشند چون باعث عدم یکپارچگی در پروژه میشن 

وقتی میخوایم از سرویسی استفاده کنیم ، باید اون رو در program اضافه کنیم .

![[Pasted image 20250625163544.png]]

![[Pasted image 20250625163602.png]]


![[Pasted image 20250625163613.png]]

![[Pasted image 20250625163626.png]]



![[Pasted image 20250625163937.png]]

```C#
 exiting constructor. Consider adding the 'required' modifier or declaring the property as nullable.
    C:\Web\Soheil\LinkMeetShareProject\ShareLib\AuthResponseDto.cs(9,23): warning CS8618: Non-nullable property 'RefreshToken' must contain a non-null value when exiting constructor. Consider adding the 'required' modifier or declaring the property as nullable.
  LinkMeetShareProject failed with 3 error(s) (0.7s)
    C:\Web\Soheil\LinkMeetShareProject\LinkMeetShareProject\Program.cs(138,11): error CS1513: } expected
    C:\Web\Soheil\LinkMeetShareProject\LinkMeetShareProject\Program.cs(138,11): error CS1026: ) expected
    C:\Web\Soheil\LinkMeetShareProject\LinkMeetShareProject\Program.cs(138,11): error CS1002: ; expected

Build failed with 3 error(s) and 7 warning(s) in 2.5s
```


![[Pasted image 20250625165916.png]]

