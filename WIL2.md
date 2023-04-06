# WIL2

Flutter 프로젝트 생성

프로젝트 명은 모두 영어 소문자로 하기를 권장

`lib/main.dart`에서 코딩함

# 1. `yaml`파일 설정

`analysis_options.yaml`에서 `rules` 부분에 내용 추가(Lint를 끄는 용도)

```yaml
rules:
	prefer_typing_uninitialized_variables : false
	prefer_const_constructors_in_immutables : false
	prefer_const_constructors : false
	avoid_print : false
```

# 2. 기본 파일 형식

```dart
import 'package:flutter/material.dart';

void main() {
	runApp(const MyApp() /*앱 메인 페이지*/); // 앱 구동
}

// stless 입력 후 Tab키를 누르면 자동으로 생성
class MyApp extends StatelessWidget {
	const MyApp({Key? key}) : super(key: key);
	@override
	Widget build(BuildContext context) {

		return MaterialApp( // 메인 페이지 작성하는 위치
			home:
		);
	}
}
```

### Flutter에서 앱 디자인하는 방법 : 위젯 `Widget`

# 3. Widget 활용

### 1. 글자위젯

`Text()`

### 2. 아이콘위젯

`Icon(Icons.{NAME})`

### 3. 이미지위젯

`Image.asset('{assets/사진}')`

이미지 보관용 `assets` 폴더를 만들고 이미지를 넣어둠

- `pubspec.yaml` 파일(모든 자료를 정리해놓은 파일)

```yaml
flutter:
	assets:
		- assets/
```

### 4. 박스 위젯

`Container()` 혹은 `SizedBox()`

Flutter의 사이즈 단위는 LP(50LP = 1.2cm)

`Center()` : 자식 위젯의 기준점을 중앙으로 설정