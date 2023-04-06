# WIL1

### Flutter 개발환경 세팅

1. Flutter SDK 설치
2. Android Studio 설치
3. 환경변수 등록
4. 기타 작업
5. 프로젝트 생성

# 1. Flutter SDK 설치

flutter install 검색 → OS에 맞춰 다운로드

다운로드 후 적당한 위치에 압축 해제

# 2. Andriod Studio 설치

(참고) Virtual Device는 빼고 설치해도 상관없음

Plugins → Flutter 플러그인 검색 후 설치

Projects → More Actions → SDK Manager

Android SDK → SDK Tools → Andriod SDK Command-line Tools 설치

# 3. 환경변수 등록

시스템 환경 변수 편집 → 환경 변수 → PATH 편집 → 설치한 `Flutter` 폴더의 `bin` 폴더 경로를 입력

# 4. 기타 작업

1) 크롬 브라우저 설치

2) 터미널 → `flutter doctor` 입력 → 경고가 뜰 경우 입력하라는대로 입력 → 모두 동의 선택(`y/N`)

# 5. 프로젝트 생성

Projects → New Flutter Project를 통해 생성

Flutter SDK path에 설치한 Flutter 폴더의 경로를 입력

필요한 정보 입력 후 생성 완료

`lib/main.dart`에 코드 작성