# 6주차

# #4. Stateful Widgets

## 4.0 State

`**Stateful Widget**`은 `**Stateless Widget**`과 달리 상태를 가지고 있는 위젯. 실시간으로 변동되는 상태를 가짐.

Stateless는 단지 UI를 보여주기만 함.

위젯의 State는 데이터를 가지고 있으며 이에 따라 UI가 변하기도 함.

Stateful은 아래와 같은 두 가지 구조를 가짐.

1) `Widget`

```dart
class MyWidget extends StatefulWidget {
  const MyWidget({super.key});

  @override
  State<MyWidget> createState() => _MyWidgetState();
}
```

2) `State`

UI를 구축하는 곳. 새로고침되면서 데이터를 보여줌.

```dart
class _MyWidgetState extends State<MyWidget> {
  @override
  Widget build(BuildContext context) {
    return const Placeholder();
  }
}
```

`IconButton`을 통해 눌렀을 때 특정 함수가 실행되도록 설정할 수 있음.

## 4.1 setState

왜 위 코드가 동작하지 않았는가?

→ `setState()`, State 클래스에게 데이터가 변경되었다고 알리는 함수.

새로운 데이터와 함께 다시 Build 함수를 호출함.

데이터를 변화시키는 코드는 꼭 setState 안에 적어야 함(명확성을 위해). 혹은 데이터를 변화시키고, setState 함수를 다시 호출해서 데이터를 반영함.

```dart
class App extends StatefulWidget {
  const App({super.key});

  @override
  State<App> createState() => _AppState();
} // 위젯 그 자체, 상태를 가지고 있음.

class _AppState extends State<App> {
  int counter = 0;

  void onClicked() {
    setState(() {
      counter = counter + 1;
    }); // State에게 새로운 데이터가 있다고 전달해줌.
  } // 데이터들은 단순히 Dart의 클래스 프로퍼티
...
```

```dart
import 'package:flutter/material.dart';

void main() {
  runApp(const App());
}

class App extends StatefulWidget {
  const App({super.key});

  @override
  State<App> createState() => _AppState();
}

class _AppState extends State<App> {
  List<int> numbers = [];

  void onClicked() {
    setState(() {
      numbers.add(numbers.length);
    });
  }

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      home: Scaffold(
        backgroundColor: const Color(0xFFF4EDDB),
        body: Center(
          child: Column(
            mainAxisAlignment: MainAxisAlignment.center,
            children: [
              const Text(
                "Click Count!",
                style: TextStyle(fontSize: 30),
              ),
              for (var num in numbers) Text('$num'),
              IconButton(
                iconSize: 40,
                onPressed: onClicked,
                icon: const Icon(
                  Icons.add_box_rounded,
                ),
              )
            ],
          ),
        ),
      ),
    );
  }
}
```

## 4.3 BuildContext

플러터는 한 곳에 배경, 색상 등의 특징을 모아놓을 수 있는 기능을 제공함.

부모 요소에 접근을 어떻게 해야할까? (테마를 이용하기 위해)

context는 이전에 있던 모든 상위 요소들에 대한 정보를 담고 있음.(위젯 트리에 대한 정보들)

위젯 트리의 위젯의 위치에 대한 정보를 담고 있음. 이를 통해 상위 트리의 데이터에 접근함.

`color: Theme.of(context).textTheme.titleLarge!.color`

## 4.4 Widget Lifecycle

Stateful Widget은 살아있음. 

initState → Build → dispose 메소드 순으로 실행됨. 

```dart
class Title extends StatefulWidget {
  const Title({
    super.key,
  });

  @override
  State<Title> createState() => _TitleState();
}

class _TitleState extends State<Title> {
  @override
  void initState() {
    // 대부분의 상황에서는 사용할 필요가 없음. 부모 요소에 의존한 데이터를 선언할 때 필요함.
    super.initState();
  } // 항상 build 메소드보다 먼저 실행되어야 함.

  @override
  void dispose() {
    // API 업데이트나 이벤트 리스너로부터 구독을 취소하거나 form의 리스너로부터 벗어나고 싶을 때.
    super.dispose();
  } // 무언가를 취소함.

  @override
  Widget build(BuildContext context) {
    return Text(
      "타이틀",
      style: TextStyle(
          fontSize: 30, color: Theme.of(context).textTheme.titleLarge!.color),
    );
  }
}
```