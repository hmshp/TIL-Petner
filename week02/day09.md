## ActionController::InvalidAuthenticityToken 에러

(레일즈 연습하려고 form 태그로 post 요청을 보내는 코드를 작성했을 때 발생한 에러)

### Authenticity Token이란?
- Authenticity 토큰이란 사이트간 요청 위조(CSRF)를 막는 방법이다.
- authenticity_token이 사용자의 세션에 저장되고, get 이외의 요청을 할 때 form의 숨겨진 필드 안에도 authenticity_token이 저장된다.
- 두 토큰이 같지 않으면 요청을 실행하지 않는다.
- 레일즈 6 버전에는 authenticity token을 이용해 CSRF 공격을 막는 부분이 디폴트로 설정되어 있다. 내가 작성한 html form 태그 안에 이 토큰이 없어서 에러가 난 게 아닐까 싶다(아마)

### 해결 방법
1. rails에서 제공하는 폼 헬퍼를 사용하면 자동으로 토큰을 생성해 주는 코드가 만들어진다.
2. 폼 안에 직접 토큰을 넣어 준다.
(이 외에도 여러 방법이 있다)

## 사파리 폰트 적용
- 문제: 데스크탑 버전 사파리에서 Pretendard 폰트 적용 안 됨
- 해결: 보통 @woff이나 woff2 파일을 받고 @font-face를 이용하는 듯하다.
- Pretendard의 경우에는 그렇게 해도 안 돼서 Pretendard 깃헙 리드미를 읽어 보니 cdn을 이용하라고 안내가 되어 있어서 그 방법으로 해결했다.
