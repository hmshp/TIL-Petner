## 루비
- 전역변수명 앞에 $ 붙임.
- 지역변수: 자신이 선언된 스코프에서만 참조 가능

## 레일즈 서버 MVC 패턴 작동 방식
1. 처음에 routes.rb 파일을 읽는다.
3. routes.rb: 브라우저에 입력한 URL이 어느 컨트롤러와 연결되어 있는지 찾고, 해당 컨트롤러로 작업을 넘긴다. 
4. controller: 클라이언트가 요청한 작업에 필요한  정보를 Model에 요청
5. model: 해당 정보를 컨트롤러에 넘겨 준다
6. controller: 그 정보를 View에 넘기면서 데이터를 HTML과 합쳐 달라고 요청
7. view: 합친 다음에 브라우저에 전송

## 커밋과 PR
- 커밋은 주석 개념. 내가 어떤 작업 과거에 했는지 남기는 것. 최소한, 한 섹션 했을 때마다 한 번씩은 커밋하기.
- PR은 작업 한 단위(지금의 경우 랜딩페이지 퍼블리싱) 완료했을 때마다 하기

## CSS background-image
- 화면 너비 조정해도 배경 이미지 고정되게 하려면? background-position 속성 사용. center 값 주면 가운데 정렬된 상태로 고정된다.
