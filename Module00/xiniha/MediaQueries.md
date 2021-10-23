# Media Queries

## 왜 필요한가?

- 웹의 특성(범용성)에 따라, 동일한 HTML/CSS는 매우 다양한 종류의 디바이스에서 동작하게 될 것임
- Media queries는 CSS가 동작하는 상황에 맞추어 다양한 CSS를 적용할 수 있도록 해 주어, 이런 상황에 대한 대응을 가능하게 함

## 예시

### 기본 예제

```css
@media (max-width: 300px /* Condition, Rule의 Declaration과 다름 */) {
  /* Condition 만족 시 내부 스타일 적용 */
  .small-only {
    color: red;
  }
}
```

### 화면 크기에 따라 다른 요소 표시

```css
.large-screens {
  display: none;
}

@media (min-width: 300px) {
  .large-screens {
    display: block;
  }
  .small-screens {
    display: none;
  }
}
```

```html
<div class="large-screens">I only show up on large screens.</div>
<div class="small-screens">Meanwhile, you'll only see me on small ones.</div>
```
