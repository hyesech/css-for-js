# Selectors

- CSS Selector의 종류는 매우 다양하며, 서로 조합하여 사용하는 것도 가능하다.

## Pseudo-classes

- Pseudo-class는 요소의 현재 상태에 따라 유동적으로 CSS Rule을 적용할 수 있도록 해 준다.
- 선언적 상태 형태로 동작함 ex) `:hover`

### 예시

#### `:hover`

```css
button:hover /* Pseudo-class Selector */ {
  color: blue;
}
```

- 요소 위에 커서가 있을 때 활성화

#### `:focus`

```css
button:focus {
  border: 2px solid royalblue;
  background: royalblue;
  color: white;
}
```

- 요소가 (마우스 클릭이나 Tab 키를 사용하여) 포커스되어 있을 때 활성화
- 포커스되었을 때 별도 CSS를 적용하는 게 왜 중요한가?
  - 포인터 기반 입력장치를 사용하지 않는 사람들은 키보드 등을 통해 요소를 포커스한 후에 해당 요소를 조작함 (텍스트 입력, 클릭 등)
  - 적절한 포커스 스타일이 적용되지 않으면 사용자들은 현재 자신이 어떤 요소를 포커스한 것인지 알아차리기 힘듬
  - 브라우저에서 기본적으로 `outline` 등의 스타일을 제공하며, 대체 스타일 없이 이를 덮어씌우는 것은 부적절함

#### `:checked`

```css
input:checked {
  width: 24px;
  height: 24px;
}
```

- 체크박스나 라디오 버튼이 체크되었을 때 활성화됨

## Pseudo-elements

- Pseudo-element는 선택된 요소의 "부 요소 (sub-elements)"를 선택함

### 예시

#### `::placeholder`

```css
input::placeholder /* Pseudo-element Selector */ {
  color: goldenrod;
}
```

- `input` 요소 내부의 `placeholder` 요소를 선택함
- `placeholder` 요소는 직접 작성되는 대신, `input` 요소의 `placeholder` 속성을 설정하면 자동으로 생성됨

#### `::before`와 `::after`

```css
p::before {
  content: "→ ";
  color: deeppink;
}

p::after {
  content: " ←";
  color: deeppink;
}
```

- 요소 안에, 해당 요소 내용의 전후에 `::before`와 `::after` 요소가 생성됨
- 숨겨진 `span`에 불과하며, 단순한 문법적 설탕임
- 일반적으로 컴포넌트 시대에 쓸 물건은 아니나, 단순히 꾸미기 용도로 `content`를 빈 문자열로 설정하여 사용하는 건 문제 없음

## Combinators

- 여러 Selector를 합치는 데에 사용

### 예시

- `a b` (공백): `a` 요소 안에 있는 `b` 요소를 선택
- `a > b`: `a` 요소 바로 안에 있는 (`b` 요소의 부모 요소가 `a`인 경우) `b` 요소를 선택
