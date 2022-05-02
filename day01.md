## 개발환경 설정
- flutter doctor(플러터 실행에 필요한 항목 설치 여부 체크) 실행해서 설치 되지 않은 항목 설치

## VSCode 사용법
- flutter run으로 앱 실행
- VSCode 터미널에서 flutter run -a simulator 명령어 입력하면 시뮬레이터 앱에서 아이폰 화면으로 확인 가능
- 변경 사항 있으면 r 명령어로 hot reload(변경 사항 즉각적으로 확인)

## 플러터
### 위젯
- Column: 자식 위젯을 세로로 정렬
- Row: 자식 위젯을 가로로 정렬
- 위젯에 따라 자식 위젯은 하나, 여러 개 모두 가능(하나라면 child 속성, 여러 개라면 children 속성과 [] 사용)

### 그 외
- main.dart 파일 안의 main 함수: 플러터를 처음 실행해 준다.
- 위젯이 변하지 않을 경우 StatelessWidget 상속 받는 클래스를, 위젯이 변할 경우 StatefulWidget를 상속 받는 클래스를 사용 

## 맥 조작법
- command + 스페이스바: 검색
- 프로그램 다운 받을 때 Application 폴더로 드래그 앤 드롭해서 다운로드

