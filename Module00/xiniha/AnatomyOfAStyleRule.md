# Anatomy of a Style Rule

## CSS Rule의 구성요소

- CSS Rule은 Declaration 묶음과 1개 이상의 Selector로 이루어진다.

```css
/* Rule */
h2.apple /* Selector */ {
  font-size: 16px; /* Property: Value(Unit) */
  color: red;
}
```

### Selector
- 페이지 내의 요소들을 특정할 수 있도록 해줌
- 다양한 종류의 선택자 구성요소가 존재
  - 태그 선택자: 선택자와 종류가 일치하는 태그를 선택 ex) `h2`
  - 클래스 선택자: 선택자가 나타내는 클래스를 포함하는 태그를 선택 ex) `.apple`

### Declaration
- 한 Property에 대해 Value를 지정함
  - Property: 값을 지정할 수 있는 속성 ex) `color`, `font-size`
  - Value: 속성에 들어가는 값
    - Unit: 값에 지정할 수 있는 단위 ex) `px`, `%`, `rem`
