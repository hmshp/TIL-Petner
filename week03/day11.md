## CSS nth-child
nth-child 쓸 때 종류가 다른 요소라도 형제 개수 카운팅에 포함된다.

```html
<div class="health-check-header"></div>
<div class="health-check-content"></div>
<div class="health-check-content"></div>
```

- .health-check-content 클래스 선택자를 이용해서 위에서 두 번째 div를 선택하고 싶다면, .health-check-content:nth-child(3) 선택자를 써야 한다.
- 형제 요소 중 세 번째 요소이기 때문이다.

## VSCode
- vscode 탐색기에서 회색 표시된 폴더는 gitignore에 들어 있는 폴더다.

## 레일즈
```
rails assets:precompile 
```

위 명령어를 입력하면 assets에 있는 내용이 다른 파일에 적용된다.
