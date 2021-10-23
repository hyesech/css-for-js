# Typography

## 폰트 종류

```css
p {
  font-family: "Roboto", sans-serif;
}
```

- 한 폰트가 여러 글자 묶음을 가지고 있기 때문에 (굵기별, 일반/이탤릭 등) 종류라고 한다.
- 다양한 스타일의 폰트가 있으며, 주로 세리프/산세리프/고정폭 폰트로 분류한다.
  - `font-family` 속성에 `serif` / `sans-serif` / `monospace` 등의 속성을 직접 사용하여, 브라우저가 적절한 글꼴을 선택하도록 할 수도 있다.
- 웹 폰트를 사용하면 인터넷에서 폰트를 다운로드하여 적용하도록 구성할 수 있다.
- 여러 폰트 종류를 전달하여 브라우저가 설치 여부 등에 따라 대체 폰트를 선택하도록 할 수 있다.

## 일반적 텍스트 서식들

### 굵은 (Bold)

```css
p {
  font-weight: bold;

  /* 숫자 사용 */
  font-weight: 300; /* Light */
  font-weight: 400; /* Normal, 기본값 */
  font-weight: 700; /* Bold */
}
```

### 기울어진 (Italic)

```css
p {
  font-style: italic;
}
```

### 밑줄 (Underline)

- 웹에서 밑줄은 주로 링크에 사용되며, 따라서 시각적 효과를 위해 밑줄을 사용하는 것은 별로 좋은 생각이 아니다.
- 종종 링크에서 밑줄을 제거하고 싶은 경우도 있을 수 있으며, 이때는 `text-decoration` 속성을 통해 밑줄 표시 여부를 변경할 수 있다.

## 정렬

```css
p.left {
  text-align: left;
}
p.right {
  text-align: right;
}
p.center {
  text-align: center;
}
```

- `text-align`은 이미지 등을 정렬하는 데도 사용할 수 있다.
  - 하지만 일반적으로 `text-align`은 텍스트 정렬 용도로만 사용하고, 다른 것들은 별도의 방법을 사용하는 것이 바람직하다.
- RTL 지원 시 특별한 주의가 필요하다.

## 텍스트 변환

```css
p {
  /* RENDER WITH ALL CAPS */
  text-transform: uppercase;
  /* Capitalize The First Letter Of Every Word */
  text-transform: capitalize;
}
```

- HTMl 컨텐츠의 내용은 유지하고, 시각적으로 보여지는 부분만 변경할 수 있다는 점에서 유용하다.

## 여백 조절

```css
h3 {
  letter-spacing: 3px; /* 자간 */
  line-height: 2; /* 행간 */
}
```

- `line-height`는 글자 크기에 비율로 해석됨
  - `px` 등 단위를 쓸 순 있지만 권장되지 않음
