## 레일즈
- js 파일에 있는 //= require로 시작하는 문장은 //= require 뒤에 적은 파일을 포함한다는 의미. 이 js 파일은 메타 데이터를 담은 manifest 파일이다.
- csrf meta tag: authentication(토큰 보내고 내가 의도한 요청이 맞는지 확인하는 것인 듯..)
- js 파일명과 레이아웃 파일명이 같아야 에러 안 나는 것 같다.
- <% %> 안에선 루비 코드를 쓸 수 있다. 루비코드를 실행(출력은 X)
- 출력까지 하려면 <%=  %> 이렇게.
```erb
<%= "hello world" %>
<%= @message %>
```
- erb는 embedded ruby라는 의미
- 마이그레이션 파일: 데이터를 넣을 형식 결정하는 파일
- 레일즈에서 버튼 누르면 링크 이동하게 하고 싶을 때: link_to 쓰기
```erb
<%= link_to "https://google.com", class: "ui button" do %>
  이동하기
<% end %>
```
- 원래 한 줄로 짧게 쓸 수 있는데 이 안에 여러 태그 넣고 싶을 때 이렇게 do end 구문 쓴다.
### 레일즈로 페이지 만드는 과정
1. 레일즈 프로젝트 만들고 컨트롤러 만든다(rails g (또는 generate) controller ‘컨트롤러 이름’)
2. 그러면 app > controllers 폴더 안에 컨트롤러가 생성된다.
3. 컨트롤러 안에서 index라는 액션(메소드)를 만든다. 컨트롤러 안의 메소드를 레일즈에선 액션이라고 함
4. index라는 액션에 상응하는 view 파일 생성. 그러면 액션이랑 뷰 파일이 연결(?)이 된다.
5. 라우팅 - routes.rb 파일 안에
```ruby
get '/' => 'home#index'
```
라고 적으면 home 컨트롤러 안의 index와 root('/')가 연결됨. 이런 식으로 해 두면 routes.rb가 url을 보고 url에 대응하는 액션을 찾아 준다.

### 메소드, 변수 만들기
- 컨트롤러에서 정의한 메소드 안에서 변수를 만들 수 있다.
```ruby
class HomeController < ApplicationController
    def index 
    end

    def hi
        @message = "안녕"
        @show_message = true
    end
    
end
```
