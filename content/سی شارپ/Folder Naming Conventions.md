
### General Guidelines for Folder Naming Conventions in C#

Here are some general guidelines to follow when naming folders in a C# project:

- Use `PascalCasing`: This means each new word begins with a capital letter.
- Be Descriptive: The name should indicate what kind of files are inside the folder.
- Avoid Special Characters: Stick to alphabets and numbers to ensure that the name is easily readable and accessible.

خوب بیایم یکی یکی بررسی کنیم موارد رو، مورد اول توضیح pascal case هست که میگه شروع هر کلمه باید به حرف بزرگ باشه مثل PascalCase

مورد دوم میگه که باید خوده اسمی که داریم تعیین میکنه نشون دهنده این باشه که اون فایل متعلق به چه فولدری هستش

از special character ها استفاده نکنیم و اسم انتخاب کنیم که مطمئن باشیم راحت بشه خوندش

![[{621DA1D2-65E9-4255-907B-3CCD51099D39}.png]]

### MVC Project Structure

- **Controllers**: Houses all controller classes.
- **Models**: Contains all model classes.
- **Views**: For storing all view files.

### API Project Structure

- **ApiControllers**: For controllers handling API routes.
- **Services**: Where business logic services are stored.
- **DTOs**: To store Data Transfer Objects.

### Library Project Structure

- **Core**: Holds the main logic.
- **Utils or Helpers**: Where utility and helper classes are stored.
- **Interfaces**: To hold all interface files.


## Common Pitfalls

- **Inconsistency**: Mixing different naming styles can make the codebase confusing.
- **Vagueness**: Using non-descriptive names like ‘temp’, ‘stuff’, etc.
- **Over Abbreviation**: Names like ‘Utl’, ‘Ctr’, etc., are not self-explanatory and should be avoided.

اشتباهاتی که ممکنه انجام بدیم :

ناهماهنگی : زمانی اتفاق میوفته که بیام استایل های اسم گذاری که داریم رو با هم میکس کنیم ، این باعث میشه که کدمون ناخوانا بشه و ساختارش بهم بریزه.

نامفهوم بودن: بیایم از کلمه های ناقص برای اسم گذاری استفاده کنیم

خلاصه نویسی بیش از اندازه: زمانی که بیایم از کلمات خیلی خلاصه شده و مخفف استفاده کنیم.

لینک اصل متن نوشته شده : [لینک](https://l.vrgl.ir/r?ad=1&l=https%3A%2F%2Faspdotnethelp.com%2Fcsharp-folder-naming-conventions%2F&si=uhiili35hewq&st=post&k=uJBEpM9pbs8MAr%2BYOiRFhERJZcHbIg6tWvAiHSbUdPc%3D)
