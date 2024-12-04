

- **The basics**: A HashSet is a collection that holds unique elements in no particular order (`O(1)` complexity for adding, searching or removing). The `HashSet<T>` is a generic class in the `System.Collections.Generic` namespace, ideal for managing large data sets and performing set operations.
- **Core aspects**: The C# HashSet is a hash-based collection that allows only distinct elements. It supports various operations such as Union, Intersection, Difference, and more.

خوب hashset یه کاکشنه که دیتا های منحصر به فرد رو توی خودش بدون هیچ ترتیبی نگهداری میکنه.

پیچیدگیه اضافه کردن و سرچ کردن یا پاک کردن توی hasshet ها O1 هستش.

و Hashse T یه کلاس generic هستش که که برای مدیریت کردن data set ها و برای Set Operation ها هم خیلی خوبه.

و hashset ها کالکشن هایی بر مبنای hash هستند که فقط اجازه ذخیره کردن دیتایی متمایز از هم رو میدن و operation های union intersection , difference و ... رو هم میتونن انجام بدن

C# HashSet vs Dictionary, List, and Set

Hashset vs Set

Use `HashSet` when the order doesn’t matter and you need quicker set operation results, with no required duplicate elements.

Use `SortedSet` when you need a sorted [list](https://l.vrgl.ir/r?ad=1&l=https%3A%2F%2Fwww.bytehide.com%2Fblog%2Flist-csharp&si=tur3swmcxoxv&st=post&k=wn83y9NFVkfF3IMfJaJbESoQHBS%2BEVHDlyYpacCE43o%3D) of unique items but with slower operations due to the tree structure.

از hashset ها زمانی که که ترتیب مهم نباشه و فقط مهم این باشه که سریع بتونیم set رو انجام بدیم بدون این که المان های duplicate داشته باشیم.

زمانی هم که sort بودن و متمایز (منحصر به فرد بودن) مهم باشه میتونیم از sortedSet استفاده کنیم. ولی یکم سرعتش یکم کمتره


```csharp
// Creating a HashSet
HashSet<int> myHashSet = new HashSet<int> {1, 2, 3, 4, 5}; 
 // Creating a SortedSet
SortedSet<int> mySortedSet = new SortedSet<int> {1, 2, 3, 4, 5};  
// Adding elements
myHashSet.Add(6); 
mySortedSet.Add(6); 
 // Retrieving elements 
foreach (int item in myHashSet) { 
    Console.WriteLine(item); // Output won't have any specific order}  foreach (int item in mySortedSet) { 
    Console.WriteLine(item);  // Output will be in ascending order}
```

C# HashSet vs Dictionary

the HashSet stores only unique elements, Dictionary stores key-value pairs, with unique keys. Use Dictionary when you require a 'lookup table' type of structure, and HashSet when you only need a unique collection without any associated values. Let’s understand this with an example:

خوب وقتی که میخوایم فقط و فقط المان های منحصر به فرد رو ذخیره کنیم میایم از Hashset ها استفاده میکنیم. dictionary ها میان بر اساس یک کلید دیتاها رو دخیره میکنن. وقتی که یه lookup table بخوایم میتونیم از Dictionary ها استفاده کنیم.


```csharp
// Creating a HashSet
HashSet<string> uniqueNamesHashSet = new HashSet<string> {'Alice', 'Bob', 'Carol'};  
// Creating a Dictionary
Dictionary<string, int> ageDictionary = new Dictionary<string, int> {     {'Alice', 25},     {'Bob', 30},     {'Carol', 28}, }; 
 // Adding values to HashSet
uniqueNamesHashSet.Add('David');  
// Adding values to Dictionary
ageDictionary.Add('David', 34);  
// Retrieving values from HashSet
 foreach (string name in uniqueNamesHashSet) { 
    Console.WriteLine(name); } 
 // Retrieving values from Dictionary 
foreach (KeyValuePair<string, int> element in ageDictionary) {     Console.WriteLine($'{element.Key}: {element.Value}'); }
```

C# HashSet vs List

List stores elements in sequential order, allowing duplicate elements and supports indexed access. HashSet, on the other hand, emphasizes uniqueness and faster performance. Choose List when the order of elements plays a critical role, and HashSet when you need to optimize for set operations and speed. To illustrate the differences, let’s compare `HashSet` and `List` in code:

خوب list ها المان ها رو به صورت متوالی و به ترتیب ذخیره میکنه و اجازه این که از یک مقدار چند تا داشته باشیم رو هم میده ، همچنین به ما دسترسی از طریق indexed رو هم میده.

زمانی که توی برنامه ترتیب خیلی مهم باشه از List استفاده کنیم بهتره.
```csharp
// Creating a List
List<int> myList = new List<int> {1, 2, 3, 4, 5};  
// Creating a HashSet
HashSet<int> myHashSet = new HashSet<int> {1, 2, 3, 4, 5}; 
 // Adding elements to List
myList.Add(2); 
// List allows duplicates 
// Adding elements to HashSet
 bool result = myHashSet.Add(2); // HashSet doesn't allow duplicates, result will be False 
// Indexed access in List
 int firstElement = myList[0]; // firstElement will hold the value 1 // Indexed access is not allowed in HashSet 
// int firstElement = myHashSet[0]; // This line will cause a compilation error
```

#### Mastering the Art of HashSet Manipulation and Methods With great power comes great responsibility—or, in the case of HashSet, great Methods!

میگه که قدرت زیاد مسئولیت زیاد میاره که این مورد برای hashset ها میشه متد های توووپ.


```csharp
// Create a new hash set to hold unique integers
HashSet<int> intHashSet = new HashSet<int>();  
// Add elements using the Add method
intHashSet.Add(42);
 intHashSet.Add(7); 
bool added = intHashSet.Add(42); // Returns false, because 42 is already //present 
Console.WriteLine('Hash set contains 42: ' + intHashSet.Contains(42)); 
// Outputs: &quotHash set contains 42: True&quot
```

### Union, Intersect, and Except: Performing Set Operations with Ease

```csharp
HashSet<int> firstSet = new HashSet<int> { 1, 2, 3 }; 
HashSet<int> secondSet = new HashSet<int> { 2, 3, 4 }; 
 // Perform a union
firstSet.UnionWith(secondSet); 
// firstSet now contains {1, 2, 3, 4} 
// Perform an intersection
firstSet.IntersectWith(secondSet);
 // firstSet now contains {2, 3} 
// Perform a difference(except)
firstSet.ExceptWith(secondSet); 
// firstSet now contains {1}
```

### Clear, Remove and Count: Housekeeping Methods for Your HashSet.

```csharp
HashSet<string> myHashSet = new HashSet<string> {'apple', 'orange', 'banana'};  
// Remove an element
myHashSet.Remove('apple'); 
// myHashSet now contains {'orange', 'banana'} 
// Clear all elements
myHashSet.Clear(); 
// myHashSet is empty 
// Count the number of elements 
int count = myHashSet.Count; 
// count will be 2 before Clear() and 0 after Clear()
```

