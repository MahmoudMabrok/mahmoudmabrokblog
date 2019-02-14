<div dir= "rtl">

## تعلم  RxJavaوRxAndroid
 إن تعلمها من أهم موضوعات التى يجب الالمام بها لاضافة تفاعلية للتطبيق الخاص بك 
 وهى امتداد لل reactive programming  ولكن معمول تعديل ليها لتعمل على الجافا ومنها ايضا RxAndroid  للعمل على الاندرويد 

##  الفكرة 
هي قائمةعلى ديزاين باترن الا هو **Observer design pattern** 
 واللى قائم على *Observable* , *Subscriber*  
 زي جريدة معينة والمشتركين فيها 
 الجريدة بتنشر نسخ ليها وطبعات ويتم إعلام المشتركين فيها فور اطلاق عدد جديد 
 فهنا الجريدة هى الناشر اي *observable*  وهنا المستخدمين او المشتركين هما *Subscriber* 
 وفي التصميم ده هنا المشترك مش محتاج كل شويه يسأل هل فيه داتا او عدد جديد نزل لانه بمجر ما يصدر عدد بيتم اعلامه فورا 

لكن يختلف انه هنا مش هيتم اصدار التحديثات إلا اذا كان هناك مشتركين 

 وأيضا بيتم تحول الاحداث إلى تتابع من الداتا
 convert actions into series of data 
 زي مثلا الضغطات على زرار معين او **api calls**
   بيتم دمجهم مع بعض وغيرها من العمليات 


## Hello World 
 نبدأ بمثال بسيط نوضح اللى بيحصل 
 التعامل بين Observable , Subscriber  بيكون من خلال ثلاث دوال 
 - *onNext*  ودي بتنقل الداتا الجديد للمشركين 
 - *onComplete*  ودي اشعار انا الداتا كلها تم ارسالها 
 - *onError*  وهنا بيتم معالجة اى اخطاء حصلت خلال عملية الارسال 

  نبدأ ب Observable


</div>


``` java
  Observable<String> myObservable = Observable.create(
    new Observable.OnSubscribe<String>() {
        @Override
        public void call(Subscriber<? super String> sub) {
            sub.onNext("Hello, world!");
            sub.onCompleted();
        }
    }
);
```

``Observable<String>`` *String*  تعبر عن نوع الداتا اللى هيتم ارسالها 

``call`` داله داخل OnSubscribe هيتم استدعاءها عند عمل اشتراك او ربط بين ال Observable , Subscriber 

``sub`` بيمثل المشترك 

``sub.onNext("Hello, world!");``
هنا هيتعمل استدعاء ارسال الداتا للمشترك عن طريق داله ``onNext``
`` sub.onCompleted();``  اعلامه أنه تم اكتمال ارسال الداتا الجديدة 

كده خلصنا المصدر اتبقي المشتركين 

``` java
Subscriber<String> mySubscriber = new Subscriber<String>() {
    @Override
    public void onNext(String s) { System.out.println(s); }

    @Override
    public void onCompleted() { }

    @Override
    public void onError(Throwable e) { }
};
```
<div dir="rtl">

Subscriber  بيكون عنده دوال اللى هيا مشتركة للتواصل ما بينهم 
وعامل برمجة ليها للاستجابة للداتا المرسلة من قبل Observable 
 فمثلا 
``public void onNext(String s) { System.out.println(s); }
``
  هو هنا حدد انه لما تيجي داتا جديدة قم بعرضها ع الشاشة 


كده خلصنا لا ! اتبقي ايه ؟ 
اتبقي اهم حاجة وهي ربطهم ببعض وده عن طريق 
``myObservable.subscribe(mySubscriber);``

هيتم عرض رسالة الترحيب اللى أرسلها 
Observable  الى  Subscriber 

 وكده عرفنا بداية ومقدمة بسيطة عن Rx  
 ولنا تكملة إن شاء الله

<div>