# assets 파이프라인

## 주요 기능
1. 에셋 병합 > 요청 건수 감소
- 이유는? 브라우저가 동시에 처리할 수 있는 요청 건수는 제한되어 있기 때문에, 요청이 적을수록 앱 로딩 속도가 빨라진다.
- 모든 자바스크립트 파일을 마스터 .js 파일로, 모든 css 파일을 마스터 .cs 파일로 병합

2. 압축
assets 파일 내에서 불필요한 스페이스와 코멘트 제거해 줌 > 로딩 시간 감소

3. 사전 컴파일링
scss 등의 상위 레벨 언어를 css로 사전 컴파일해 줌

## 핑거프린팅
핑거프린팅은? 파일명이 파일 내용에 따라 달라지게 만드는 기술(ex)레일즈에선 보통 파일명 뒤에 해시값이 붙는다)

### 원리
파일 내용 변경 > 자동으로 핑거프린트 변경 > 캐시 무효화 > 원격 클라이언트가 변경된 파일 내용 복제본 요청
(* 캐싱: 오랜 시간 걸리는 작업의 결과를 임시 저장. 동일한 요청할 때 바로 저장한 것을 줄 수 있도록. 서버 지연 줄이기 위해)

## assets 파이프라인 이용법
- 에셋은 app/assets 디렉토리에 넣는다.
- 레일즈에서 여기 있는 파일을 사전 컴파일 > 웹서버에 정적 에셋으로 전달

### 방법 1. (특정 컨트롤러에만 연결된 스타일시트, 자바스크립트)
예시:
```html.erb
<%= javascript_include_tag params[:controller] %>
<%= stylesheet_link_tag params[:controller] %>)
```

### 방법 2. Asset Organization
- 사용할 assets을 manifest 파일에서 참조
- manifest에서 파일을 참조할 때 레일즈에서는 기본적으로 app/assets 폴더 안에서 다음 세 곳을 확인한다.
1. images 폴더
2. javascripts 폴더
3. stylesheets 폴더

assets > javascripts 안에 있는 manifest 파일에 아래와 같이 적으면 javascripts 폴더 안에 있는 파일 중 파일명이 home인 asset을 참조한다.
```javascript
//= require home
```

app/assets/javascripts/sub/something.js에 있는 파일에 아래와 같이 적으면 javascripts 폴더 안에 있는 파일 중 sub 폴더 안에 있는 something이라는 에셋을 참조한다.

```javascript
//= require sub/something
```

css 파일을 참조하려면 assets > stylesheets 폴더 안의 manifest 파일에서 아래와 같이 적기
```javascript
//= require ‘파일명’
```
그러면 stylesheet 폴더 안에 있는 파일 중 그 파일명에 해당하는 파일을 참조하게 됨


# 레이아웃 개수 최소화하기
그래야 나중에 관리하기가 좋다(예를 들어 구글 관련 코드를 레이아웃에 추가해야 되는 상황이 생겼을 때, 레이아웃 하나로 관리하면 작업을 한 번만 해도 되는데 레이아웃을 뷰별로 따로따로 관리하고 있으면 작업을 여러 번 해야 된다)

## 현재 진행 중인 회사 프로젝트의 경우
모바일, 데스크탑 컨트롤러가 각각 있고
각 컨트롤러별로 다른 레이아웃을 썼는데

레이아웃을 하나로 통일하고
레이아웃 안에 들어갈 manifest 파일(스타일시트, 자바스크립트)은 content_for과 yield를 써서 처리해 줬다.

## yield란?
- 이름 없는 yield 작동 방식? body 안에 yield라고 쓰면 index.html이 들어간다(현재 렌더링된 뷰 내용이 들어간다고 한다. 근데 자세한 원리는 아직 모름..)
- 이름이 있는 yield 작동 방식? index.html 파일이 로딩되면 그 파일 안에 있는 content_for 안의 내용을 읽고 그 content_for 이름(내가 설정한 이름)과 이름이 동일한 yield를 찾아서 그 안에 콘텐츠를 넣어 준다. 
- 모바일 뷰 파일과 데스크탑 뷰 파일(index.html)에 있는 content_for 이름을 모두 동일하게 줬다. 그래야 레이아웃 안에서 이름 있는 yield를 한 번만 적어도 되니까.

참고 사이트
- https://guides.rubyonrails.org/asset_pipeline.html
- https://negabaro.github.io/archive/rails-assets-pipeline
