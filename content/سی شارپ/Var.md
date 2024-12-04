یا بهتر بود اسمه این تایپک رو میزاشتم Var چی هه؟

خوب حالا واقعا چی هه؟!

تعریفش میشه این عکسه پایین. کلا به جای هر تایپی میتونیم var بزاریم , و هر تایپی رو هم داشتیم میتونیم بریزیم توی var ، حالا بیایم یه کم بررسیش کنیم.
![[{EBEEE5E0-B62B-4585-8424-6A52961746DC}.png]]

خوب میرسیم به اینجا که Var که خیلی خوبه بیایم برای راحتیه کار همه جا ازش استفاده کنیم و خلاص. ولی نههه، یه سری محدودیت داره:

![[{EAB413E9-CB7D-42EA-9F5D-5C1D54645546}.png]]

این عکس رو از این [مقاله](https://l.vrgl.ir/r?ad=1&l=https%3A%2F%2Fwww.researchgate.net%2Fpublication%2F328999651_To_var_or_not_to_var_how_do_C_developers_use_and_misuse_implicit_and_explicit_typing&si=wgr0u9lbec6d&st=post&k=gkLDvJJjk%2BrI5gmWL0WhAqme%2FwQedIm%2BmJ56fmvjzPQ%3D) گرفتم

حالا کجاها بهتره که ازش استفاده کنیم:

```csharp
II. Object Creation via the _new_ Keyword

List<KeyValuePair<int,string>> niceList = new List<KeyValuePair<int,string>>();

var niceList = new List<KeyValuePair<int,string>>();
```

توی C# 9 هم میشه اینطوری نوشت و اینطوری دیگه حتی نمیخواد از var استفاده کنیم

```csharp
List<KeyValuePair<int,string>> niceList = new();

### III. Explicit Type Conversions

var options = (JsonSerializerOptions)foo;
```

### IV. When a Generic Parameter Controls the Results

Yes, this is wading a bit into non-obvious waters, as it consists of statements not being controlled by built-in keywords, but if the return type of a method is directly controlled via a generic type parameter, then you may feel free to use `var`.

```csharp
var obviousReader = Activator.CreateInstance<StreamReader>();
```

### V. When Enumerating a Local _IEnumerable T 

If we have a local variable of type of `IEnumerable<T>`, we can more or less be assured that the object returned from enumerating it will be of type `T`.

```csharp
IEnumerable<Type> types = FromSomewhere();
foreach (var type in types)
{
// Do stuff...
}
```

Although this too begins to dip its toes into the land of uncertainty, I feel that it’s acceptable to also use `var` if we’re accessing a local collection via an indexer or some other standard method. All within reason of course.

### VI. When Assigning Another Local Variable or Method Parameter

If we need to declare a variable to hold a reference to another local variable or method parameter, there can be no doubt as to what that type is, so no harm in using `var` here as well.

```csharp
IEnumerable<Type> types = FromSomewhere();
foreach (var type in types)
{
// To prevent closures from closing over a non-local variable.
var localType = type;
// Do some lambda stuff.
}
```

این قسمت رو هم از این [سایته](https://l.vrgl.ir/r?ad=1&l=https%3A%2F%2Fbadecho.com%2Findex.php%2F2021%2F01%2F11%2Fwhen-to-use-var%2F&si=wgr0u9lbec6d&st=post&k=8dAg2Cldxu0TNdtb63Pn75a8HVfX6N%2FASyvbSiABIyQ%3D) اوردم

```csharp
Singleton.instance;
```

Copy

```csharp
Singleton.instance;
```

Copy

