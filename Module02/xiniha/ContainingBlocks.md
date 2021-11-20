# Containing Blocks

- CSS에서 모든 HTML 요소는 Containing Block을 가진다.
- Containing Block은 요소의 컨테이너의 경계를 구성하는 사각형을 의미한다.

- Flow 레이아웃에서 요소들은 부모 요소에 포함된다.
- Flow 레이아웃은 이 부모 요소의 Containing Block에 따라 요소들을 배치한다.

- Absolute Positioning에서, Containing Block은 조금 다르게 동작한다.
- Absolute Positioning을 사용하는 요소에 `top`/`bottom`/`left`/`right` 속성을 사용하면, 바로 이 Containing Block과의 간격을 기준으로 요소가 배치된다.
- Absolute Positioning을 사용하는 요소는 일반적인 Flow 레이아웃의 요소들과는 달리, 조상 요소들 중 Positioned 레이아웃을 사용하는 다른 요소에만 포함될 수 있다.
  - 따라서, 부모 요소에 `position: relative` 등을 부여함으로써 Containing Block을 지정해줄 수 있다.
  - 만약, 조상 요소 중 Positioned 레이아웃을 사용하는 다른 요소가 없을 경우, 뷰포트를 Containing Block으로 사용한다.
- 또한, Absolute Positioning의 Containing Block은 Flow 레이아웃에서와는 달리 패딩을 무시한다.
