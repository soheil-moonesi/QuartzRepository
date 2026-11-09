https://www.youtube.com/watch?v=CLQzLZUTMqU&list=PLN5rV4x2x5XcRubBzzDQ_WApzFBPAgnoh&index=6

![[Pasted image 20261108152549.png]]

![[Pasted image 20261108152634.png]]
حل مشکل وابستگی به دیتا 
![[Pasted image 20261108152708.png]]

بهش میگن port and adapter
یا hexaconal 

![[Pasted image 20261108152744.png]]

هر ضلع از اون آبیه میتونه برای ارتباط با اجزای دیگه ارتباط برقرار کنه

![[Pasted image 20261108152825.png]]

![[Pasted image 20261108153232.png]]

![[Pasted image 20261108153252.png]]

خوب دو تا قسمت اصلی داریم - primary که درخواست میاد بعد وارد app core میشه و بعد میره دیتا رو میاره از secondery 

![[Pasted image 20261108154935.png]]

خوب onion هم شبیه همونه - ولی داخل app core رو هم لایه بندی کرده و تمرکر بر روی جریان وابستگی هاست 

![[Pasted image 20261108155156.png]]


خوب اینطوری میشه که از app service به domain service و بعد domain میره 

هدف اینه که هر جا دققه وابستگی داشتیم توی هر لایه - ببریمش اون رو یه لایه بالاتر 

![[Pasted image 20261108155434.png]]

اینجا domian و domain service در یک لایه هستش 

خوب اینجا repo هر entity رو هم کنارش میزاریم و حتی unit of work 

![[Pasted image 20261108160128.png]]

حالا اگر بخوایم از infra استفاده کنیم میایم اینترفیسش رو توی app درست میکنیم و پیاده سازیش رو توی infra میکنیم 

![[Pasted image 20261108160255.png]]

حالا همون فضای infra رو میتوینم به دو بخش تقسیم کنیم یکی persistance و یکی external 

اگر بخوایم به یه webservice وصل بشیم دقیقا اینترفیس رو توی app پیاده میکنیم و خوده پیاده سازی اصلی رو توی infr قسمت external 

اگر با orm خواستیم کار کنیم اینترفیس app و پیاده سازی prsitance infra 

جریان مبتنی بر di هستش 

دغدغه تکنولوژی رو  هم سپرد به di 

![[Pasted image 20261108162107.png]]

خوب وظیقه این لایه اینه که تمام infra رو بیاد inject کنه به app 

تمامی registration ها و di ها توی web ui انجام میشه 

نه app و نه infra نمیدونن که کی قراره کجا از امکاناتشون استفاده بشه 

![[Pasted image 20261108163143.png]]

![[Pasted image 20261108163154.png]]

![[Pasted image 20261108170145.png]]

![[Pasted image 20261108170240.png]]

![[Pasted image 20261108170432.png]]

![[Pasted image 20261108170601.png]]

اینجا onion به وجود اومد چون اومد app رو لایه بندی کرد 
حالا در Clean اومده domain model رو با domain service یکی کرده و اسمش رو گذاشته domain layer و لایه بالاترش میشه app layer  

و این که به primery وظیفه مدیریت injection ها داده شده - یعنی تمامی اظلاع رو 

خوب command query handler که در لایه App هستش و توی عکس هم هست 

اون هایی که داخل اظلاغ هستن میشن port که میرن به اون چیزا وصل میشن که adapter هستش 

https://www.youtube.com/watch?v=npTJDNsEK4Q&list=PLN5rV4x2x5XcRubBzzDQ_WApzFBPAgnoh&index=7

![[Pasted image 20261109111416.png]]


خوب لایه سمت راست میشه info سمت چپ میشه persentation و core هم میشه همون app وسط

![[Pasted image 20261109111606.png]]


![[Pasted image 20261109111649.png]]


![[Pasted image 20261109111708.png]]

خوب اینجا موضوع مهم ارتباطات هستش 

اینجا domain نباید از لایه های دیگه هیچی بدونه و ارتباط داشته باشه 

![[Pasted image 20261109111805.png]]
توی dependecy هاش هیجی نیست 

![[Pasted image 20261109111908.png]]

خوب application به domain وابستگی داره 


![[Pasted image 20261109112006.png]]

![[Pasted image 20261109112028.png]]

![[Pasted image 20261109112244.png]]

و infra به app وابسته است 

![[Pasted image 20261109112427.png]]

اینجا infra به domain وابسته است - اینطوری که infra به app وابسته است و app به domian و اینطوری infra به domain وابسته است 

![[Pasted image 20261109112519.png]]


![[Pasted image 20261109113008.png]]


![[Pasted image 20261109113031.png]]


![[Pasted image 20261109113105.png]]

خوب 

![[Pasted image 20261109113502.png]]


![[Pasted image 20261109113408.png]]

![[Pasted image 20261109113756.png]]

![[Pasted image 20261109113811.png]]

خوب ما اینجا اگر بخوایم از یک کلاس والدی برای تمام entity هامون ارث بری کنیم میایم توی این قسمت :

![[Pasted image 20261109114921.png]]

خوب حالا ما یه Enum داریم برای این هم جا داریم 

![[Pasted image 20261109115633.png]]


و value object هم داریم 

![[Pasted image 20261109115758.png]]

یه سری Excep داریم 

![[Pasted image 20261109115841.png]]


خوب وقتی که repository patern داریم استفاده میکنیم باید توی همین domian بیاریمش 
چه generic چه غیر generic و فقط اینجا interface هاش وارد میشه 

حالا میخوایم یه قابلیتی برای user بسازیم 

![[Pasted image 20261109121732.png]]

خوب اینجا میایم توی app فولدی user درست میکنیم 

![[Pasted image 20261109121922.png]]

برای cqrs وقتی که command یا Query میاد باید تشخیص بده که command هستش یا query و بعد ارسالش کنه 

دیتابیس میتونه یکی باشه و یا میتونه دو تا باشه که با هم sync هستش 

![[Pasted image 20261109122132.png]]




خوب در لایه app ما یه port یا interface داریم که پیاده سازیش توی infra هستش 

![[Pasted image 20261109122400.png]]

![[Pasted image 20261109122327.png]]

اینجا هم اول ISms رو درست کردیم توی comon گذاشتیم چون که ممکنه توی جاهای دیگه هم ازش استفاده کنیم 

![[Pasted image 20261109122610.png]]


![[Pasted image 20261109132609.png]]

خوب این handler ای که داریم میشه اینجا 

![[Pasted image 20261109132644.png]]

در لایه app داریم command query handler 

![[Pasted image 20261109133242.png]]

خوب حالا ما command داریم که قراره با infra ارتباط داشته باشه - این ارتباط با interface ها انجام میشه 

![[Pasted image 20261109133334.png]]

حالا پیاده سازی IApplication unit of work در infra هستش 

![[Pasted image 20261109133512.png]]


![[Pasted image 20261109133611.png]]

اینجا واضحا port و adapter خخا رو میبنیم ارتباطشون رو 

حالا میریم سراع persis 

![[Pasted image 20261109134256.png]]

خوب config اون entity که بالاتر تعریف کردیم رو توی infra میریزیم


![[Pasted image 20261109135014.png]]


![[Pasted image 20261109141406.png]]

خوب 
![[Pasted image 20261109141655.png]]

اینجا ما یه bus داریم که همه ی query ها و command ها رو میزاره توی bus و یه سری handler هستش 30:23

![[Pasted image 20261109142020.png]]

خوب ما با mediate R این کارا رو انجام میدیم mediate R میاد bus رو میسازه و هندلر هاش رو هم درست میکنه و میاد این درخواست ها و هندلر ها رو بهم وصل میکنه 

![[Pasted image 20261109142542.png]]

![[Pasted image 20261109142548.png]]

این جا از سمت primery این ها ارسال میشن و خروجی یه guid برمیگردونه 

خوب این درخواست رو روی bus میزاریم و بعدش باید یه هندلری باشه که این درسخوات رو مدیریت کنه 

![[Pasted image 20261109143227.png]]

خوب اینجا هندلر ورودی که میخواد و خروجی که میخواد رو داره 

![[Pasted image 20261109143440.png]]

![[Pasted image 20261109143450.png]]

![[Pasted image 20261109143519.png]]


![[Pasted image 20261109143628.png]]

برای Validate کردن هم از Validator استفاده میکنیم 

![[Pasted image 20261109143704.png]]

خوب حالا میتونیم یه chain درست کنیم برای اجرا عملیات 

![[Pasted image 20261109143915.png]]


![[Pasted image 20261109143936.png]]

اینجا میاد چک میکنه در pipe line خطایی خورده یا نه ؟

خوب اگر به خطا خورده بود - بیا تمامی rule هایی که ایجاد شده همه رو دربیار در قالب یه Ex که خودمون تعیین کردیم 

![[Pasted image 20261109144217.png]]

اینجا اگر validation اوکی بود میره middleware بعدی رو call میکنه و اگر نه اون اتفاقات بالا 

![[Pasted image 20261109150842.png]]


![[Pasted image 20261109150859.png]]

اینجا اومدیم تمام سرویس ها رو داریم register میکنه به ترتیب - application بعد infra و بعد persistance و بعد peresentation 

https://www.youtube.com/watch?v=ePocOdXTi0U&list=PLN5rV4x2x5XcRubBzzDQ_WApzFBPAgnoh&index=8

![[Pasted image 20261109151814.png]]

خوب این ایده از اینجا درست شده ما نباید هم command و هم query مون در یک متد و یک functianlity قرار بگیره این کانسپت میشه CQS

ایا این ادبیات CQS رو میتونیم در سطح resposniblity انجامش بدیم ؟ مسئولیت هم در سطح متده هم در سطح سرویسه و هم در سطح app service و هم در سطح دیتابیس هستش - یعنی در تمامی سطوح میتونیم این CQS رو پیاده سازی کنیم ؟

![[Pasted image 20261109154000.png]]

خوب مشکل این عکس بالا اینه که اگر یه کوئری سنگین داشتیم که طول میکشید انجام دادنش و اوردن دیتاهاش - command ها میموندن توی صف و نمیتونستن روی دیتابیس اعمال بشن چون lock شده توسط query و این مشکل بود 

مشکل بعدی این بود که وابسته بودیم در لایه app و نمیتونستیم چیزی رو تغییر بدیم مثلا command رو میخوایم با daper انجام بدیم و Query رو با ado , ef ولی اینجا نمیشه 

![[Pasted image 20261109154333.png]]

ولی با cqrs اومدیم جداش کردیم 

![[Pasted image 20261109154508.png]]


خوب حالا میتونیم دیتا بیس هامون رو هم جدا کنیم - میتونیم برای Command بیایم sqlserver اسفتاده کنیم و برای query بیایم Doc db استفاده کنیم 

خوب cqrs پترن خوبیه برای Event soursing 

![[Pasted image 20261109154851.png]]

خوب حالا میتونیم یه کار دیگه هم انجام بدیم اون وسط که syncronization داریم - یعنی وقتی که command داره میاد میخوایم روی دیتابیس read store میخوایم ذخیره کنیم بیایم تر و تمیزش کنیم و بهینه سازیش کنیم برای query ها 

مثلا ما توی دیتا ها رو در write store به صورت relational داریم حالا میتونیم توی read store بیایم اون دیتا ها رو flat اش کنیم 

یا دیتا بیس خواندن رو به صورت non relational استفاده کنیم 

اون شکل راستی داره اتفاقاتی که میتونی توی مسیر synctonization بیوفته رو داره نشون میده 
11:44

