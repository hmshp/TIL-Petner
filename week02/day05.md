## 크롬 개발자 도구 기기 선택
- 크롬 개발자 도구에서 기기 지정하면 화면 크기가 기기 크기(너비, 높이)로 고정된다.
- 너비가 고정되므로 데스크탑 화면에서 너비만 줄인 화면과는 다르게 보인다.

## 너비 지정 방법
- 콘텐츠 width를 직접 지정하지 말고(%나 px로 지정하지 말기. 그럼 모바일 기기에서 레이아웃 이상하게 보인다)
- 가운데 정렬하거나 margin 같은 걸로 조정하기

## rails
- routes 파일 안에 등록한 resources 명이랑 컨트롤러명이랑 같아야 한다.
- rails는 MVC 구조로 되어 있다(model: DB, controller: 모델과 뷰 연결, view: 화면)
- 레이아웃 지정 안하면 layout/application.html.erb 레이아웃으로 자동 지정된다(디폴트)
- 직접 레이아웃 지정해 줄 수 있음.