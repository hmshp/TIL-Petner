## 레일즈에서 Owl carousel 플러그인 사용하기

1. https://owlcarousel2.github.io/OwlCarousel2/docs/started-welcome.html 에서 js, min.js, css, min.css 파일 다운로드

2. app > assets > javascripts 폴더에 js, min.js 파일 넣기(그래야 require 명령어 사용할 수 있다)
3. app > assets > stylesheets 폴더에 css, min.css 파일 넣기(그래야 require 명령어 사용할 수 있다)
4. 뷰 파일과 연결된 js 파일에 아래 코드 입력해서 js 파일 불러오기
```html.erb
//= require owl.carousel
//= require owl.carousel.min
```

5. 뷰 파일과 연결된 css 파일에 아래 코드 입력해서 css 파일 사용할 수 있도록 하기
```html.erb
//= require owl.carousel
//= require owl.carousel.min
```

6. 기본 HTML 세팅
```html
<div class="owl-carousel">
  <div> Your Content </div>
  <div> Your Content </div>
  <div> Your Content </div>
  <div> Your Content </div>
</div>
```

7. 플러그인 초기화
```javascript
$(document).ready(function(){
  $(".owl-carousel").owlCarousel();
});
```

8. 데모 참고하여 커스터마이징하기(아래 예시처럼 패딩, 마진, 한 번에 보여줄 항목 수를 정할 수 있다)
```javascript
 $('.owl-carousel').owlCarousel({
    stagePadding: 20
    items:1,
    center:true,
    margin:10,
  });
```

## position: absolute로 요소를 붕 띄워서 위치 조정하기

1. 기준으로 삼을 조상 요소에 position: relative 값을 준다(position:absolute를 사용하면 position이 static이 아닌 조상 요소 중 가장 가까운 요소를 기준으로 위치가 정해지므로)
2. 화면 너비 기준으로 x축 정 가운데 요소를 위치시키고 싶다면 아래와 같이 퍼센트나 픽셀로 위치를 지정한다.
```css
.item {
  left: 50%;
}
```
3. 위치는 요소의 왼쪽 위 꼭지점을 기준으로 결정되어서 화면에서 봤을 때 원하는 위치가 아닐 수도 있다. 그때는 아래와 같이 transform: translate()를 사용한다.
```css
.item {
/* x축 반대 방향으로 50%, y축 방향으로 25% 이동 */
  transform: translate(-50%, 25%);
}
```
