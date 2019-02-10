<div dir = "rtl">

# الجزء الاول 
هنتعلم ف الى الجزء ده بداية  flutter 

- إزاى نكتب اول تطبيق  بFlutter 
- ايه هو هيكلة التطبيق 
- ازاى اضيف package  والاقيها فين 
- استخدام hot reload 
- ايه هو  stateful widget 
- ازاى نعمل listview  مع lazy load


### هيكلية التطبيق 
- ملفات الكود بلغة ال dart  واللى تحتوي على logic  مع ال design   وده حل مشاكل كتير من اختلاف لغة التصميم ولغة التنفيذ 

- فيه package manager  وهو **pub**  وده المختص  عن ربط ال packages 
 والملف اللى فيه الاعدادات ومن خليه نقدر نضيف packages  **pubspec.yaml**


### packages 
 دي تجميعة لمحموعة من classes  بتسهل علينا الكود واداء الوظائف المطلوبة منا 
 ده الموقع اللى عليه كل packages  [pub](https://pub.dartlang.org/)
 يمكنك البحث على packages  ومعرفة حالتها 
 من المتابعة والصيانة 

 وينصح بالتعامل مع 70 في 100 فما اكثر للحصول على 
 استقرار 

بيتم إضافتها في ملف  pubspec.yaml 

زي  english words 
</div>

``` yaml 
dependencies:
  flutter:
    sdk: flutter

  # The following adds the Cupertino Icons font to your application.
  # Use with the CupertinoIcons class for iOS style icons.
  cupertino_icons: ^0.1.0
  english_words: ^3.1.3 # added 

```



complete code  **main.dart** 
```  dart
import 'package:english_words/english_words.dart';
import 'package:flutter/material.dart';

void main() => runApp(new MyApp());

class MyApp extends StatelessWidget {
  // This widget is the root of your application.
  @override
  Widget build(BuildContext context) {
    return new MaterialApp(
        home: new Scaffold(
            appBar: AppBar(
              title:  Text('Random Generator'),

            ),
            body: Center(
                  child: new Random(),
                )
        )
    );
  }
}
class Random extends StatefulWidget {
  @override
  _RandomState createState() => _RandomState();
}

class _RandomState extends State<Random> {
  final List<WordPair> _suggestions = <WordPair>[] ;
  @override
  Widget build(BuildContext context) {
    return _generateRandom();
  }

  Widget _generateRandom (){
    return new ListView.builder(
        padding: const EdgeInsets.all(16.0),
        itemBuilder: (BuildContext _context, int i) {
          final int index = i ~/ 2;
          print (i);
          if (index >= _suggestions.length) {
            // generateWordPairs() is a method inside WordPair generate list of wordpairs
            _suggestions.addAll(generateWordPairs().take(10));
          }
          return _buildRow(_suggestions[index]);
        }
    );
  }

  Widget _buildRow(WordPair pair) {
    return new ListTile(
      title: new Text(
        pair.asPascalCase,
      ),
    );
  }

}

```

pubspec.yaml 
``` yaml
name: first_workshop_app
description: A new Flutter application.

dependencies:
  flutter:
    sdk: flutter

  # The following adds the Cupertino Icons font to your application.
  # Use with the CupertinoIcons class for iOS style icons.
  cupertino_icons: ^0.1.0
  english_words: ^3.1.3 # added 

dev_dependencies:
  flutter_test:
    sdk: flutter


# For information on the generic Dart part of this file, see the
# following page: https://www.dartlang.org/tools/pub/pubspec

# The following section is specific to Flutter.
flutter:

  # The following line ensures that the Material Icons font is
  # included with your application, so that you can use the icons in
  # the material Icons class.
  uses-material-design: true

  # To add assets to your application, add an assets section, like this:
  # assets:
  #  - images/a_dot_burr.jpeg
  #  - images/a_dot_ham.jpeg

  # An image asset can refer to one or more resolution-specific "variants", see
  # https://flutter.io/assets-and-images/#resolution-aware.

  # For details regarding adding assets from package dependencies, see
  # https://flutter.io/assets-and-images/#from-packages

  # To add custom fonts to your application, add a fonts section here,
  # in this "flutter" section. Each entry in this list should have a
  # "family" key with the font family name, and a "fonts" key with a
  # list giving the asset and other descriptors for the font. For
  # example:
  # fonts:
  #   - family: Schyler
  #     fonts:
  #       - asset: fonts/Schyler-Regular.ttf
  #       - asset: fonts/Schyler-Italic.ttf
  #         style: italic
  #   - family: Trajan Pro
  #     fonts:
  #       - asset: fonts/TrajanPro.ttf
  #       - asset: fonts/TrajanPro_Bold.ttf
  #         weight: 700
  #
  # For details regarding fonts from package dependencies, 
  # see https://flutter.io/custom-fonts/#from-packages

```




