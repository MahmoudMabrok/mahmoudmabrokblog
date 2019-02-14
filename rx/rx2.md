<div dir="rtl">

# الجزء التاني 
اتكلمنا عن مقدمة لل Rx  وخدنا مثال HelloWorld  
لتقليل الكود المكتوب لانشاء كل من ال Observable 
 فممكن نستخدم مع Observable 
 ``` java
 Observable<String> myObservable =
    Observable.just("Hello, world!");
 ```
`
    Observable.just("Hello, world!");
`  just --> operator  
بياخد مجموعة من العناصر ويرجع **ObseravableSource** 
 بيرسل كل عنصر من العناصر وبعدين يبعت **Compelete**


**subscribe** accepts a subscriber that has implementation to onNext , onError ,onComplete  as next:: 

<div>

 ``` java 
 myObservable.subscribe(onNextAction, onErrorAction, onCompleteAction);
 ```
*so we can specify all of them or just onNext, as below*

 ``` java
 Observable.just("Hello, world!")
    .subscribe(new Action1<String>() {
        @Override
        public void call(String s) {
      	    System.out.println(s);
    	}
    });
 ```
 **Action1** here reprsent what is shoud be done when new item is emitted  (بيمثل onNext)
 
output:: `Hello, world!`


ونقدر نختصر الكود الى اقل حاجة واكثرها وظيفية 
``` java 
Observable.just("Hello, world!").subscribe(s -> System.out.println(s));
```

<div dir="rtl">
# التعديل والتشكيل 
 هنا احنا بيحصل إصدار للداتا ونقلها الى المشركين و يمكننا اضافة بعض التعديلات ع الداتا ويكون معانا امكانية لتبسيط معالجة الداتا عند المشتركين 
مثلا 

<div>

``` java 
Observable.just("Hello, world!")
    .subscribe(s -> System.out.println(s + " -User"));
```
<div dir="rtl">

هنا احنا ضفنا مع كل داتا جديدة كلمة User  
لكن ده بيتم عند المشترك واللى فى الغالب بيكون في **main thread ** طب لو التعديل هيكون كبير وهياخد وقت وعايزه يصل للمشترك جاهز للاستخدام 
فهني تظهر أهمية ال **operator**

# Operator  المعاملات 
 ودي تقدر تقول عليها أدوات سحرية للتحويل والتعامل مع الداتا لتبسيطها وجعلها جاهزة للاستخدام النهائي 

نتعرض لمجموعة منها وهم ***map*** , ****flatMap**** , ***take***  , ***filter*** , ***doOnNext***  

## map  حول وشكل 
ده بيستقبل الداتا وبعدل عليها ويرجعها بشكل تاني 

<div>

``` java
Observable.just("Hello, world!")
    .map(new Func1<String, String>() { // Func1 accept string return string
        @Override
        public String call(String s) {
            return s + " -User";
        }
    })
    .subscribe(s -> System.out.println(s));
```
ويمكن تبسيطها عن طريق
``` java 
Observable.just("Hello, world!")
    .map(s -> s + " -User")
    .subscribe(s -> System.out.println(s));
```
<div>

ويمكن أيضا تحويل ال string  الى اي نوع تانى حسب الحاجة 
وكذلك يمكنك دمج أكثر من map  مع بعض 

<div>

``` java 
Observable.just("Hello, world!")
    .map(s -> s + " -User") // هنا ضاف على النص الناتج كلمة 
    .map(s -> s.hashCode()) // هنا هيحول الناتج الى رقم 
    .map(i -> Integer.toString(i)) // هنا يرجع تانى الرقم الى نص 
    .subscribe(s -> System.out.println(s)); // يعرضه ع الشاشة 
```

<div>

من المثال السابق نلاحظ 
-  map  مش لازم نوع  الداتا يكون نفس النوع اللى هي هتحول الداتا ليه 
- ممكن نضيف اكتر من map
- مفيش اي ارتباط بين Observable , subscriber  اللى بيحصل ف النص غير مرئ ليهم كل واحد شغال حسب اللى اللى جايله وبأدي وظيفته وبس 


ويا رب تكون الرؤية اتضحت شويه 
ونكمل إن شاءالله  ف المقالات القادمة 

<div>