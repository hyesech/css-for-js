# Unit

## `px`

- 가장 일반적으로 사용되는 단위
- 화면에 표시되는 그대로를 나타내는 단위로써, 손쉽게 사용할 수 있음
- 글자 크기에 사용하기에는 `rem` 등의 상대 단위가 더 적절함

## `em`

```css
p {
  font-size: 18px;

  /* font-size의 두 배만큼 padding-bottom이 설정됨 */
  padding-bottom: 2em;
}
```

- 현재 요소의 `font-size`에 해당하는 값을 나타내는 상대 단위
- 글자 크기를 조정하는 게 예상 못한 부수효과를 낳는 것은 직관적이지 못하기 때문에 잘 사용되지는 않음
  - 특히 컴포넌트 구조에서는 어떤 요소가 어디에 어떻게 배치될지 알 수 없기 때문에 특히 문제가 될 여지가 많음

## `rem`

```css
html {
  /* 예시를 위해 작성됨 */
  font-size: 16px;
}

h1 {
  font-size: 2rem;
  margin: 0;
}

h2 {
  font-size: 1.25rem;
  margin-bottom: 1.5rem;
  color: gray;
}

p {
  font-size: 1rem;
}
```
> 일반적으로 `html` 태그에 `px` 단위 글자 크기를 설정하는 것은 브라우저의 글자 크기 설정을 덮어쓸 수 있다는 점 때문에 권장되지 않음

- `em` 요소와 유사하나, `rem`은 언제나 루트 요소(`<html>`)의 글자 크기에 상대적이라는 점이 특징
- 따라서 요소가 배치된 위치에 상관없이 일관성 있게 작동함

## `%`

```css
.box {
  width: 250px;
  height: 250px;
  background-color: pink;
}

.child {
  width: 50%;
  height: 75%;
  background-color: black;
}
```

- 주로 `width`나 `height` 속성에서 주어진 공간의 일부를 점유하기 위해 사용

## 정리

- 글자 크기에는 `rem`을 사용하는 것이 접근성 측면에서 바람직
- 박스 모델 관련 값들(`padding`, `margin` 등)에는 `px`을 사용하는 것이 간편하며, 특별한 단점도 없음
- `width` / `height`에는 고정 크기일 경우 `px`, 상대 크기일 경우 `%`를 사용
- 색 단위로는 `hsl`이 여러 장점들 덕에 선호됨
