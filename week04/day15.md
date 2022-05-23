## rails에서 css, js 파일 참조하기

### 상황
owl 캐러셀을 사용하려고 API 설명대로 아래와 같은 코드를 작성했다.

```html
<link rel="stylesheet" href="owlcarousel/owl.carousel.min.css">
<link rel="stylesheet" href="owlcarousel/owl.carousel.css">
```

### 문제
css 파일을 app > assets > stylesheets 폴더에 다운로드 받고 위 링크 태그에 상대 경로를 입력했는데도 css, min.css 파일이 인식이 안 됐다.

### 해결
레일즈 안에서 작업을 하고 있기 때문에 레일즈 방식으로 css 파일을 참조해야 하는 게 아닐까 싶어서 

```html.erb
<%= stylesheet_link_tag 'owl.carousel', media: 'all' %>
<%= stylesheet_link_tag 'owl.carousel.min', media: 'all' %>
```

위와 같이 코드를 수정했더니 파일 인식이 잘 됐다.

```html.erb
<%= javascript_include_tag 'owl.carousel' %>
<%= javascript_include_tag 'owl.carousel.min' %>
```

js 파일도 다운 받은 다음 위와 같이 코드를 작성하면 잘 인식된다.(나는 js 파일은 cdn을 사용했다)

### 그 외 사소한 시행착오
```html.erb
  <body>
    <%= javascript_include_tag 'owl.carousel' %>
    <%= javascript_include_tag 'owl.carousel.min' %>
    <%= yield %>
  </body>
```

- 이렇게 owl 캐러셀 js 파일을 참조하는 코드를 위쪽에 적어 주어야 yield 안에서 해당 js 파일을 사용할 수가 있는데
- 처음에는 아래와 같이 yield 아래에 owl js를 참조하는 코드를 적어서 에러가 났다.

```html.erb
  <body>
    <%= yield %>
    <%= javascript_include_tag 'owl.carousel' %>
    <%= javascript_include_tag 'owl.carousel.min' %>
  </body>
```

## content_for과 yield

### yield
레이아웃 안에서 콘텐츠를 <em>어느 위치</em>에 둘 건지 결정할 때 사용

```html.erb
<div>
  <h1> This is the wrapper!</h1>
  <%= yield :my_content %>
</div>
```

### content_for
<em>어느 콘텐츠</em>가 렌더링되도록 할지 결정할 때 사용

```html.erb
<% content_for :my_content do %>
  This is the content.
<% end %>
```

content_for, yield를 사용해서 위와 같은 코드를 적으면 다음과 같은 결과가 나온다.

```html.erb
<div>
  <h1> This is the wrapper!</h1>
  This is the content.
</div>
```
참고한 자료: https://stackoverflow.com/questions/13150983/rails-what-is-the-difference-between-content-for-and-yield
(베스트 프렉티스도 제시되어 있다)


