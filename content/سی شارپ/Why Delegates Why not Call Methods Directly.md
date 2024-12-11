خوب همونطوری که از عنوان هم معلومه میخوایم راجع به delegate ها بیشتر بدونیم و این که اصلا چرا باید ازشون استفاده کنیم؟

خوب سوالی که همیشه موقع استفاده کردن از delegate پیش میاد اینه که خوب اصلا چرا از همون اول نیایم مستقیم اون متدی رو که میخوایم رو call نکنیم به جای این که بخوایم بیایم و از delegate استفاده کنیم؟

I’m going to use an example from the video [C# Design Patterns with Jon Skeet: Outtakes](https://l.vrgl.ir/r?ad=1&l=https%3A%2F%2Fwww.youtube.com%2Fwatch%3Fv%3DJSjL7vShiFM&si=yl7anacxmrwq&st=post&k=Q6ou%2B4DeB%2FSfChZiSP4oeLJsAsBjPAGawBS1%2BadKOm0%3D) where Mr. Skeet implements the Decorator Pattern using delegates.

خوب فکر کنید شما پیتزا فروشی دارید و میخواید تخفیف بدید روی هر کدوم از سفارش هاتون. خوب برای این کار میایم یه کلاس درست میکنیم که تمام مدل های تخفیف رو داخلش داره.


```csharp
```csharp
class PizzaOrderingSystemMethod {
    private readonly DiscountPoliciesMethods _discountPoliciesMethods;
    public PizzaOrderingSystemMethod() {
        _discountPoliciesMethods = new DiscountPoliciesMethods();
    }
    public decimal ComputePrice(PizzaOrder order) {
        decimal total = order.Pizzas.Sum(p => p.Price);

        decimal[] discounts = new[] {
            _discountPoliciesMethods.BuyOneGetOneFree(order),
            _discountPoliciesMethods.FivePercentOffMoreThanFiftyDollars(order),
            _discountPoliciesMethods.FiveDollarsOffStuffedCrust(order),
        };

        decimal bestDiscount = discounts.Max(discount => discount);
        total = total - bestDiscount;
        return total;
    }
}

public class DiscountPoliciesMethods {
    public decimal BuyOneGetOneFree(PizzaOrder order) {
        var pizzas = order.Pizzas;
        if (pizzas.Count < 2) {
            return 0m;
        }
        return pizzas.Min(p => p.Price);
    }
    public decimal FivePercentOffMoreThanFiftyDollars(PizzaOrder order) {
        decimal nonDiscounted = order.Pizzas.Sum(p => p.Price);
        return nonDiscounted >= 50 ? nonDiscounted * 0.05m : 0M;

    }
    public decimal FiveDollarsOffStuffedCrust(PizzaOrder order) {
        return order.Pizzas.Sum(p => p.Crust == Crust.Stuffed ? 5m : 0m);
    }
}
```


خوب همونطوری که میبینید پیتزا فروشی داره 3 مدل تخفیف میده و ما برای هر کدوم از سفارش هایی که داریم میایم و دونه دونه هر کدوم رو چک میکنیم که ببینیم سفارشی که اومده شامل کدوم تخفیف میشه.

خوب نقطه ی ضعفی که این کد داره اینه که اگر بخوایم هر کدوم از این تخفیف ها رو آپدیت کنیم یا یه تخفیف اضافه کنیم یا کم کنیم باید ComputePrice و اون متد رو در PizzaOrderingSystem تغییر بدیم.

Open Closed Principle with Delegates

What we really want is to be able to extend the PizzaOrderingSystem **without** modifying it. We want to make it **[Open for Extension, Closed for Modification](https://l.vrgl.ir/r?ad=1&l=https%3A%2F%2Fen.wikipedia.org%2Fwiki%2FOpen%2Fclosed_principle&si=yl7anacxmrwq&st=post&k=2Ph2zibU9hAOskRUCA7J%2FNE1b29fKoKStj5XfrInH04%3D)**.

We can do this with delegates.

ما میخوایم که بتونیم pizzaOrderingSystem رو extend کنیم بدون این که بخوایم modify اش کنیم.

با استفاده از Delegate میتونیم این کار رو بکنیم.

چجوری؟ اینجوری که اول میایم delegate تعریف میکنیم:

`public delegate decimal DiscountPolicy(PizzaOrder order)`

با توجه به این داستان، میبینیم که مدل تخفیف ها به مدل delegate مون میخوره.


![[{6700D3A6-32AF-4BF5-B76E-E4C84A8AFF80}.png]]

خوب حالا بت این داستان ها میبینیم که چقدر شبیه به اینترفیس هاست.

```csharp
`public interface IDiscountPolicy {`  
`decimal ApplyDiscount(PizzaOrder order);`  
`}`
```


![[{841EA2C0-7E9E-410B-AC53-0BAF70C7A86D}.png]]

خوب حالا متوجه میشیم که چقدر کاری که delegate میکنن شبیه به همین اینترفیس هاست .

ولی یه فرقی دارن

They allow clients of our delegates to ignore all the details of their implementations - even their names!

```csharp
```csharp
class PizzaOrderingSystem {
    readonly DiscountPolicy _discountPolicy;

    public PizzaOrderingSystem(DiscountPolicy discountPolicy) {
        _discountPolicy = discountPolicy;
    }

    public decimal ComputePrice(PizzaOrder order) {
        decimal nonDiscounted = order.Pizzas.Sum(p => p.Price);
        decimal discountedValue = _discountPolicy(order);
        return nonDiscounted - discountedValue;
    }
}
```

Here’s how the delegates are implemented, including one that returns the best discount for the current order:

```csharp
```csharp
public delegate decimal DiscountPolicy(PizzaOrder order);

public static class DiscountPolicyDelegates {
    public static decimal BuyOneGetOneFree(PizzaOrder order) {
        var pizzas = order.Pizzas;
        if (pizzas.Count < 2) {
            return 0m;
        }
        return pizzas.Min(p => p.Price);
    }
    public static decimal FivePercentOffMoreThanFiftyDollars(PizzaOrder order) {
        decimal nonDiscounted = order.Pizzas.Sum(p => p.Price);
        return nonDiscounted >= 50 ? nonDiscounted*0.05m : 0M;
    }
    public static decimal FiveDollarsOffStuffedCrust(PizzaOrder order) {
        return order.Pizzas.Sum(p => p.Crust == Crust.Stuffed ? 5m : 0m);
    }
    public static DiscountPolicy CreateBest(params DiscountPolicy[] policies) {
        return order => policies.Max(policy => policy.Invoke(order));
    }

    public static DiscountPolicy DiscountAllThePizzas() {
        DiscountPolicy best = CreateBest(
            BuyOneGetOneFree,
            FivePercentOffMoreThanFiftyDollars,
            FiveDollarsOffStuffedCrust);
        return best;
    }
}
```

لینک مقاله :
https://buildplease.com/pages/why-delegates/

خوب کجا ها بهتره که از delegate استفاده کنیم؟

callBack mechanism :

از delegate ها میشه برای درست کردن callback ها استفاده کر، چون میتونیم با متد، متد دیگه رو با استفاده delegate صدا کنیم. این قضیه توی event handeling, async programming خیلی به کار میاد.

decoupling

با استفاده از delegate میتونیم فرستنده درخواست رو از جایی که داره درخواست handle میشه جدا کنیم که به اصطلاح میگن decoupling کردن. این باعث میشه که نگهداری و scale دادن کد راحت تر بشه چرا که اینطوری وقتی که اعضا به هم وابسته نباشن خیلی راحت تر میشه کارها رو انجام داد.

event handling

توضیحش رو توی مطلب جداگانه نوشتم.

functional programming

با استفاده از delegate میتونیم یه سری فانکشن درست کنیم که توی ورودیشون فانکشن میگیرن. این قابلیت توی جاهایی که میخوایم filtering , mapping, reduceing روی کالکشن ها انجام بدیم کارایی داره.

**Dynamic Method Invocation**

**با استفاده از delegate میتونیم جاهایی که میخوایم یه سری متد بر اساس شرایطی که ایجاد میشه به صورت dynamic اجرا بشن رو پیاده سازی کنیم.**

**حالا کجاها نباید استفاده بشه**

**Simple Method Calls**

**جاهایی که نمیخوایم از این قابلیت ها استفاده کنیم بهتره که سمت delegate نریم**

callback mechanisms, event handling, or dynamic method invocation

و بیایم مستقیم اون متد رو صدا کنیم.

**Performance Critical Applications**

**اگر متد که میخوایم توی delegate استفاده کنیم خیلی ازش استفاده میشه ممکنه بار پردازشی غیر ضروری رو ایجاد کنیم پس بهتره که در مواقعی که متدی که میخوایم ازش استفاده کنیم خیلی استفاده میشه بهتره که از Delegate استفاده نکنیم.**

**Overuse in Small-Scale Projects**:

توی برنامه های کوچیک لازم نیست ازش استفاده کنیم، استفاده کردن ازش یه جورایی overkill کردنه

**Static Method Invocation**

**جاهایی که متدی که میخوایم call کنیم از نوع static هستش بهتره که از delegate استفاده نکنیم و بیایم مستقیم متد رو call کنیم.**

**When Lambdas or Anonymous Methods Suffice**

**خوب در زمانی که میتونیم از lamdas یا anonymous method ها استفاده کنیم و کار رو دربیاریم. بهتره که از delegate استفاده نکنیم.**

**When There's a Clear Alternative**:

همیشه فرض رو بر این بزاریم که تا جایی که میتونیم کد رو ساده بنویسیم و در اینجور مواقع استفاده کردن از delegate اگر باعث پیچیدگی میشه بهتره که از یه چیزه دیگه استفاده کنیم.

**Avoid Mixing Delegate Types with Different Signatures**:

  
// Example: Avoid mixing delegate types with different signatures

public delegate void MyDelegate(string message);

// Incorrect usage

MyDelegate delegate1 = (string message) => { /* Do something */ };

MyDelegate delegate2 = (int value) => { /* Do something else */ }; // Compiler error

در اینطور مواقع که متد هایی که داریم مدلشون فرق دارن بهتره که از delegate استفاده نکنیم


