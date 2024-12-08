Changing from `IdentityDbContext` to `IdentityDbContext<ApplicationUser>` in an ASP.NET Core application is typically necessary when you've defined a custom user class (`ApplicationUser`) that extends the default `IdentityUser` class. This change impacts how the Entity Framework Core (EF Core) manages and interacts with the database for your application's Identity-related data. Here’s why this change is important:
خوب ما چرا اومدیم identity db context رو به identity db contex Application user تغییر دادیم؟
این برای این هستش که بتونیم قابلیت های کلاس identity user رو به صورت custom یه سری چیزها بهش اضافه کنیم و این تغییرات باعث تغییر عملکرد ef توی قسمتی که داره برای identity توی دیتابیس عمل میکنه رو داره 
### Default `IdentityDbContext`

- **`IdentityDbContext`**: This is a generic DbContext provided by ASP.NET Core Identity, which is responsible for interacting with the Identity-related tables in your database. By default, it uses the `IdentityUser` class as the user entity, and it automatically sets up the necessary tables for managing users, roles, claims, logins, and tokens.
    
- ==**Default Tables**: When using `IdentityDbContext` with `IdentityUser`, EF Core will generate tables like `AspNetUsers`, `AspNetRoles`, `AspNetUserRoles`, etc., where `AspNetUsers` stores basic user information such as username, email, and password hash.==

خوب خیلی جالبه چون میگه که به صورت دیفالت identity db context برای ارتباطات داده ها در دیتابیس از کلاس Identity user استفاده میکنه و میاد جدول برای مدیریت یوزر ها ، رول ها و چیزهای دیگه مرتبط هستند رو ذخیره میکنه 

به صورت دیفالت هم میاد یه سری جدول درست میکنه که هایلایتش کردم 

### Custom `ApplicationUser` Class

- **Why Create `ApplicationUser`?**
    
    - **Custom Properties**: If you need to store additional data about your users (e.g., `FirstName`, `LastName`, `DateOfBirth`), you create a custom class, `ApplicationUser`, that inherits from `IdentityUser`.
    - **Custom Behavior**: You might also want to add methods or override existing behavior in `ApplicationUser` to customize how users are managed within your application.
خوب حالا چرا این کلاس application user رو ساختیم؟
 برای این که بیایم و یه سری دیتا های اضافی راجع به یوزر هامون رو ذخیره کنیم ، دقت کنید که این کلاس از کلاس identity user ارث بری کرده 
خوب توی این شرایط ما میتونیم متد های جدید درست کنیم یا بیایم روی متد هایی که به صورت دیفالت توی identity user هست رو override کنیم 
### Why Change to `IdentityDbContext<ApplicationUser>`?

1. **Mapping the Custom User Class to the Database**:
    
    - **Purpose**: When you use `IdentityDbContext<ApplicationUser>`, you're telling EF Core that the `ApplicationUser` class should be used to represent users in the database instead of the default `IdentityUser`. This allows EF Core to recognize and map any additional properties in `ApplicationUser` to columns in the `AspNetUsers` table.
    - **Result**: The `AspNetUsers` table will include columns for your custom properties, such as `FirstName` and `LastName`.

خوب میرسیم به این که چرا این کار رو کردیم. برای این که به ef بگیم که کلاس application user باید به جای دیفالت دسترسی identity user برای دسترسی به دیتابیس جایگزین بشه ، این کار باعث میشه که ef بفهمه و تمام پراپرتی های application user رو مپ کنه توی ستون های جدول asp net users 

خوب جدول asp net user شامل ستون هایی که با پراپرتی های custom ای که براش تعیین کردیم پر میشه 

1. **Consistency Across the Application**:
    
    - **DbContext Integration**: By using `IdentityDbContext<ApplicationUser>`, all Identity-related queries and operations performed by EF Core will correctly utilize your `ApplicationUser` class. This ensures that custom properties and behaviors are consistently applied whenever user data is accessed or manipulated.
    - 
خوب توی این قضیه دسترسی  به دیتابیس هم با استفاده از `IdentityDbContext ApplicationUser
اوکی میشه و تمامی کوئری هایی که مرتبط با identity هستش که توسط ef انجام میشه با استفاده از کلاس application user انجام میشه و تمامی پراپرتی ها و رفتارهایی که توی کلاس application user تعیین کردیم توی دسترسی به دیتا بیس اعمال میشه  

**Other Identity Classes**: Other Identity classes like `UserManager<ApplicationUser>` and `SignInManager<ApplicationUser>` will also rely on the same `ApplicationUser` entity, ensuring that all components of your authentication and user management system are in sync.

خوب بقیه کلاس های identity هم وقتی که اون تغییر رو انجام میدیم تحت تاثیر قرار میگیرن مثل user manager و sign in manager که باید بهشون application user رو اضافه کنیم 

3. **Enabling Custom Logic in User Management**:
    
    - **Custom Behavior**: If you override methods in `ApplicationUser` or add additional logic that should be considered when interacting with the user database, this logic will only be used if the DbContext knows about `ApplicationUser`. Changing to `IdentityDbContext<ApplicationUser>` ensures that your custom logic is applied.
- ### Summary

Changing from `IdentityDbContext` to `IdentityDbContext<ApplicationUser>` is necessary when you extend `IdentityUser` with a custom user class (`ApplicationUser`). This change ensures that EF Core correctly maps your custom properties to the database, and it ensures that all Identity-related operations in your application consistently use the `ApplicationUser` class. Without this change, the custom properties and behavior in `ApplicationUser` would not be reflected in your database or user management processes.