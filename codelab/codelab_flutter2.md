import 'package:flutter/material.dart';
import './second_screen.dart';

void main() => runApp(new MyApp());

class MyApp extends StatelessWidget {
  // This widget is the root of your application.
  @override
  Widget build(BuildContext context) {
    return new MaterialApp(
        home: new Scaffold(
            appBar: new  AppBar(
              title:  new Text('Random Generator'),
            ),
            body: Center(
              child: new Text('Hi'),
            )
        )
    );
  }

}
/*

class Random extends StatefulWidget {
  @override
  _RandomState createState() => _RandomState();
}

class _RandomState extends State<Random> {
  final List<WordPair> _suggestions = <WordPair>[];
  final Set<WordPair> _loved = Set<WordPair>();
  final TextStyle customStyle = TextStyle(
      fontSize: 30.0,
      color: Colors.blueGrey
  );

  @override
  Widget build(BuildContext context) {
    return new Scaffold(
      appBar: new AppBar(
        title: new Text("Random "),
        actions: <Widget>[
          new IconButton(
              icon: const Icon(Icons.list), onPressed: _pushNewRout(context))
        ],
      ),
      body: Center(
        child: _generateRandom(),
      ),
    );
  }

  _pushNewRout(BuildContext context) {
    Navigator.push(
        context, MaterialPageRoute(builder: (context) => SecondScreen(_loved)));
  }

  Widget _generateRandom() {
    return new ListView.builder(
        padding: const EdgeInsets.all(16.0),
        itemBuilder: (BuildContext _context, int i) {
          final int index = i ~/ 2;
          if (i.isOdd) {
            return Divider();
          }
          if (index >= _suggestions.length) {
            // generateWordPairs() is a method inside WordPair generate list of wordpairs
            _suggestions.addAll(generateWordPairs().take(10));
          }
          return _buildRow(_suggestions[index]);
        }
    );
  }

  Widget _buildRow(WordPair pair) {
    final isLoved = _loved.contains(pair);
    return new ListTile(
      title: new Text(
        pair.asPascalCase,
      ),
      trailing: new Icon(
        isLoved ? Icons.favorite : Icons.favorite_border,
        color: isLoved ? Colors.red : null,
      )
      ,
      onTap: () {
        // used to update UI by calling build method
        setState(() {
          // check if it loved then remove it otherwise add it to loved Set
          if (isLoved) {
            _loved.remove(pair);
          } else {
            _loved.add(pair);
          }
        });
      },
    );
  }

}
*/




## second 

``` dart 

import 'package:english_words/english_words.dart';
import 'package:flutter/material.dart';

class SecondScreen extends StatelessWidget {
  final Set<WordPair> _selectedWords;

  SecondScreen(this._selectedWords);

  @override
  Widget build(BuildContext context) {
    return Material(child: new Scaffold(body: Center(child: setData())));
  }

  setData() {
    return new ListView.builder(
        padding: const EdgeInsets.all(16.0),
        itemBuilder: (BuildContext _context, int i) {
          return _buildRow(_selectedWords.elementAt(i));
        });
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