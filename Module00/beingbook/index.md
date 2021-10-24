# CSS for JS developer, Module 1

전체 코스는 어느정도 CSS와 JS를 사용해서 웹 개발을 해본 사람을 위해 초점이 맞춰져 있다.
이 모듈의 목표는 수강자들간의 격차를 해소하고 모두가 같은 탄탄한 기반지식을 갖추는 것이다.

## 스타일 규칙

```css
.error-text {
  color: red;
}
```

위 코드에 대해 다음과 같이 독립적으로 부를 수 있다:

- 선택자: `.error-text`
- 첫 룰: 첫번째 줄 부터 마지막 줄 전체
- 프로퍼티: `color`
- 첫 선언: `color: red;`

## 미디어 쿼리

미디어 쿼리는 웹이 사용되는 광범위한 디바이스를 위한 if문으로 생각할 수 있다.

컨디션에 사용되는 `max-width`, `min-width` 같은건 CSS의 프로퍼티가 아니라 미디어 쿼리의 기능이다.
모듈 5에서 더 자세하게 다룰 예정이라고 한다.

## 선택자

- 의사클래스 선택자: 엘리먼트의 상태에 따라 부분적인 CSS를 사용할 수 있도록 해준다. `:focus`, `:checked` 등이 있다. 접근성 관련 이슈가 있는 것 같다.
- 의사요소 선택자: 엘리먼트의 또 다른 하위 엘리먼트를 HTML 마크업 없이 만들 수 있다. `::before`, `::after`, `input:placeholder` 등이 있다. placeholder는 사용자가 폼을 다루는 동안 쉽게 날아가는 정보다. 접근성을 고려해서 잘 쓰자.
- Combinators: 자손 선택, 직자손 수준으로 분리해서 선택할 수 있다.

## 색

색은 CSS의 중요한 부분이라 나중에 다시 다룰 예정이라고 한다.

RGB로 표현하는 법과 HSL(Hue, Saturation, Lightness)를 사용하는 방법이 있다.

## 단위

대부분의 단위들은 픽셀과 연관되어 있다. 픽셀은 고밀도 디스플레이에서도 화면 크기와 유사해서 편리하다.

- em: 현재 엘리먼트의 폰트 사이즈를 기준으로 동작한다.
- rem: 루트 엘리먼트의 폰트 사이즈를 기준으로 동작한다.
- percentage