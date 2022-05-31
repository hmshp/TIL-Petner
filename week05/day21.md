## 가상 선택자
### :checked
체크박스나 라디오 박스를 선택할 때 쓸 수 있다.
```css
input:checked {
  width: 24px;
  height: 24px;
}
```

## 가상 요소
가상 요소는 요소 안의 요소를 선택할 때 사용한다.
### ::placeholder
```css
input::placeholder {
  color: orange /* 플레이스홀더 색을 주황색으로 */
}
```
이렇게 하면, input 태그 뒤에 ::placeholder를 붙임으로써 가상 요소가 생성된다. (HTML 태그를 이용해 명시적으로 요소를 생성하진 않았음에도)

#### placeholder 관련 참고 사항
- 플레이스홀더는 중요한 정보를 표시하는 용도로 쓰는 것이 아니다. input 태그에 어떤 데이터를 입력해야 될지 예시로 보여줄 때처럼 **필수적이진 않은** 정보를 보여줄 때 사용한다. 라벨처럼 중요한 용도로 사용하면 안 된다.

- 즉, 플레이스홀더 없이도 아무 무리 없이 폼을 채울 수 있어야 한다(그만큼 필수적인 정보는 플레이스 홀더에 담지 말아야 한다는 의미)

### ::before, ::after
이 두 선택자는 사실 span 태그이다.
```html
<p>
  Hello World!
</p>
```

```css
p::before {
	content: '👉';
}
p::before {
	content: '👈';
}
```

위 코드는 아래 코드와 동일하다.

```
<p>
  <span>👉</span>
  Hello World!
  <span>👈</span>
</p>
```

semantic ui 같은 라이브러리에서 제공하는 아이콘 태그에서도 쓰인다(아래 코드처럼)

```html
<i class="angle right icon">
	::before 
</i>
```

- ❗❕장식 목적으로만(예를 들어 색이 들어간 동그라미 만들 때) 사용하는 것이 좋다.
- content 값을 읽어 주지 않는 스크린 리더도 있어서 접근성이 좋지 않기 때문이다.
