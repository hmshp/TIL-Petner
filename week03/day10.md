## 레일즈 
#### 새 컨트롤러 라우팅 설정
```ruby
resources :photos
```

- 이런 식으로 리소스 라우팅을 하면 photos라는 컨트롤러에 7개의 라우트 설정이 생성된다
- 7개의 설정: index, new, create, show, edit, upodate, destroy 7개의 액션에 해당하는 경로

#### 기존 경로 안에 새 경로 추가하기

기존 경로 다음에 새 경로를 추가하고 싶을 땐 routes.rb 파일의  resources 구문 안에다가 collection do end 구문 추가하기. 
```ruby
resources :medical_center_landings do
    collection do
      get :mobile
    end
  end
```

- 이런 식으로 작성하면 /medical_center_landings/mobile 경로를 입력했을 때 mobile.html.erb 파일 볼 수 있다.
- collection은 id 값이 필요 없을 때 쓰고, id값을 넣어야 할 때는(ex)선택한 특정 게시물 수정 페이지) member를 씀.


## 깃헙 데스크탑 버전
- push 하기 전에 깃헙 데스크탑 버전에서 current Branch 누르고
- 맨 아래에 있는 ‘Choose a branch to merge into …’ 여기서 master 브랜치 눌러서
- master 브랜치 내용을 내 브랜치에 먼저 merge하고, 그 다음에 내가 변경한 내용을 push하기
- 다른 분들이 같은 리포지토리에서 수정한 변경 내역을 먼저 머지하기! pull 해도 되는데 가끔 반영이 안 될 때가 있다고 함
- gemfile.lock 빼고 다 깃헙에 올린다(커피파일, helper 등 다 올림)

## 메타 태그

- 메타 태그에 user-scalable=no 쓰면 개발자 도구 모바일 뷰에서 화면이 깨지지 않는다.
- 근데 접근성 지원이 안 된다.

## 스마트폰에서 작업 확인하는 방법
- rails s -b '사무실 와이파이 ip'
- 이 주소를 폰에서 입력하면 폰에서 확인 가능. 사무실 와이파이에 연결되어 있으니까.

## display: flex
- display: flex 설정하면 해당 요소에 너비가 생기는 듯하다.
- flex 속성 준 요소 자식에게 margin: 0 auto 했을 때 가운데 정렬이 되는 걸 보면 그런 것 같다(부모가 width값을 갖고 있어야 마진으로 가운데 정렬이 되니까).
