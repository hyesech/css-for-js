# Relative Positioning

- Relative Positioning은 Positioned 레이아웃에서 가장 미묘한 Positioning 방식임
- 일반적으로 `position: relative`를 적용하더라도 아무 차이도 보이지 않음
- 실제로는 2가지 동작을 함:
  - 자식 요소들에 제약을 검
  - 추가적인 CSS 속성들을 사용할 수 있게 해 줌

- 추가적인 속성들 중 `top`/`bottom`/`left`/`right`를 사용하면 요소를 움직일 수 있음
- `margin` 등의 속성을 사용하는 것과의 차이점은, 이 속성들은 Flow 레이아웃의 요소 배치에 영향을 주지 않는다는 것임
- 또한, 인라인 요소에도 적용할 수 있음
