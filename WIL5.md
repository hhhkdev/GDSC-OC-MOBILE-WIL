# 5주차

## 3.0 Header

목표: 위젯 사용에 익숙해지기 (암기하는 것이 목적이 아님.)

콤마를 붙이는 이유: 포매팅을 위해서.

`Row`와 `Column`을 사용할 때 → `children` 이용

`MainAxisAlignment`, `CrossAxisAlignment`: 각각 중심방향을 기준으로 메인 축과 수직 축을 중심으로 정렬함.

화면에 공간을 주기 위해서 사용하는 것: `Padding`

→ body에 사용하여 전체 화면에 padding을 이용함.

## 3.1 Developer Tools

개발자 도구를 통해 간단한 수정이 가능함.

개발자 도구를 통해 iOS 에뮬레이터에서도 정보 확인 가능함. (위젯의 포함 관계, 특성 등)

가이드라인을 활성화하여 보조선과 함께 개발할 수 있음.

## 3.2 Button Section

`Container` : html의 `div`와 비슷한 개념. 모서리가 둥근 박스를 만들 때 사용할 수 있음.

→ `BoxDecorations`

## 3.3 VSCode Settings

파란 줄이 뜨는 이유: 경고(const의 사용을 추천함.)

const는 컴파일의 최적화를 위해 필요한 존재. 동작하기 더 편해짐.

```json
"editor.codeActionsOnSave": {
        "source.fixAll": true
},
```

```json
"dart.previewFlutterUiGuides": true,
```

## 3.4 Code Actions

코드를 간단한 방법으로 리팩토링함. 왼쪽 전구를 통해 한번에 Wrapping이 가능함. `Wrap with widget…`

`command(ctrl) + .`

## 3.5 Reusable Widgets

```json
 "[dart]": {
	"editor.formatOnSave": true,
	"editor.formatOnType": true,
	"editor.rulers": [80],
	"editor.selectionHighlight": false,
  "editor.suggest.snippetsPreventQuickSuggestions": false,
	"editor.suggestSelection": "first",
	"editor.tabCompletion": "onlySnippets",
	"editor.wordBasedSuggestions": false,
},
```

재사용할 수 있는 위젯은 추출하여 따로 만들어냄.

`code action - extracts widget`을 통해 새로운 클래스로 만들어 냄.

`lib/widgets` 폴더를 만들고 그 아래에 위젯이 담긴 새로운 dart 파일을 생성하여 파일을 분리함.

클래스에 변수를 선언해주고 생성자(`super.key`)를 통해 매개변수를 받음 → 일부 특성만 다른 위젯을 만들어낼 수 있음.

위젯을 분리한 경우 상위 위젯이 const인지 아닌지에 유의.

## 3.7 Icons and Transforms

`Transform.scale`(크기 조절), `Transform.translate`(위치 조절)

`clipBehavior: Clip.hardEdge`를 통해 컨테이너를 넘치지 않도록 함. clipBehavior는 컨테이너를 넘치는 상황을 제어함.

## 3.8 Reusable Cards

`SingleChildScrollView`: 스크롤이 되는 화면으로 만들어 줌.