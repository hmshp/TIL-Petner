## 플러터 기본 코드
### void main() => runApp(myApp());
- main 함수: 컴파일러에게 시작점 알려 줌
- main 함수가 runApp 함수를 호출

### 플러터 최상위 함수: runApp()
- 위젯을 argument로 받는다. 여기에 argument로 전달하는 위젯은 최상위 위젯(이 위젯이 앱의 레이아웃 최초로 빌드함)

## 위젯
- 위젯 만드는 단축키: stl(커스텀 위젯 만들 때 stateful vs stateless 어떤 위젯으로 만들지 선택.)
- 모든 커스텀 위젯은 또 다른 위젯을 리턴하는 build 메소드를 갖고 있다.
- 모든 위젯은 argument를 가진다(ex) MaterialApp 위젯의 title, home)
- build 메소드에서 MaterialApp 위젯을 리턴하면 플러터에서 제공하는 기본 위젯(임포트한 머티리얼 앱) 모두 사용 가능
- MaterialApp 안의 home 속성에 오는 위젯: 앱이 실행되면 맨 처음 보여지는 경로
- 함수 호출할 때처럼 위젯도 위젯명 뒤에 ()를 붙여서 호출

#### Column, Row 위젯
- children 속성 사용(자식 위젯들을 세로 정렬하려고 쓰는 건데 자식 위젯이 하나면 의미가 없으므로)
- 위젯을 가로축 정중앙에 위치시키려면 Center 위젯으로 감싸기
- Column 위젯 가로 정렬 설정하려면 crossAxisAlignment 속성 사용(Row 위젯의 경우 반대)

#### 스타일 작업
- 패딩 지정하려면 Padding 위젯 사용 -> Padding 위젯 안의 padding 속성 사용해서 padding: EdgeInsets …. 이런 식으로 패딩 지정 
- 전구 아이콘(commend + .) 클릭하면 손쉽게 Column, Center 등의 위젯 추가 가능
- 텍스트 스타일링(색상, 자간 등)하려면 style 속성에서 TextStyle 위젯 호출

