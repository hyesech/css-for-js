# Flow Layout

- Flow 레이아웃은 기본 레이아웃 모드로, 별도 CSS가 없으면 HTML은 기본적으로 Flow 레이아웃을 통해 렌더됨
- Flow 레이아웃에서 요소들은 `inline`, `block`, 또는 `inline-block`의 `display` 값을 가짐
- 기본값은 요소에 따라 다름
  - ex) `<div>`는 `block`, `<span>`은 `inline`, ...
- 인라인 요소는 일반적으로 텍스트의 일부를 특별하게 표시하기 위해 사용됨
  - ex) 강조를 위한 `<strong>`, 링크를 위한 `<a>`, ...
- 대부분의 요소는 블록 요소이다.
- Flow 레이아웃에서 블록 요소는 블록 방향으로, 인라인 요소는 인라인 방향으로 쌓여서 배치된다.

## 각 요소 종류별 규칙

### Inline elements don't want to make a fuss

- 인라인 요소에는 많은 CSS 속성이 작동하지 않음
- `margin-left`나 `margin-right` 등의 속성을 사용하여 인라인 요소들을 인라인 방향으로 움직일 수는 있지만, 넓이/높이를 조정하는 것은 불가능하다.
- 이 규칙에는 예외가 존재하는데, `<img>`나 `<video>`, `<canvas>` 등 "교체되는 요소"들은 블록 레이아웃에 영향을 줄 수 있다.
  - 이 경우 인라인 요소가 블록 요소를 감싸고 있는 것처럼 작동한다고 이해하면 편하다.
  - `<button>`은 교체되는 요소가 아님에도 불구하고 동일하게 예외 처리된다.

### Block elements don't share

- 블록 요소는 기본적으로 주어진 가로 공간의 최대치를 사용한다.
- `width: fit-content`를 사용하면 알맞은 양의 공간만 사용하도록 설정할 수 있다.
  - 파이어폭스 대상으로는 `width: -moz-fit-content`가 필요하다.

### Inline elements have "magic space"

- 인라인 요소는 주로 텍스트 표기에 사용됨
- 따라서 `line-height` 속성에 따라 행간 여백이 적용됨
- 이를 원하지 않을 경우, `display: block`이나 `line-height: 0`을 사용할 수 있음
- 이외에도 인라인 요소 마크업 간에 공백이 있을 경우 약간의 공간이 삽입됨

### Inline elements can line-wrap

- 인라인 요소는 단순 박스 모양 외에 다른 모양으로도 그려질 수 있음
- 예를 들어, 여러 줄에 걸쳐서 그려질 수 있음
- 이 경우, 두 개의 별도의 박스가 그려지는 대신, 하나의 박스를 그리고 줄이 바뀌는 지점을 잘라서 새 줄에 배치시키는 방식으로 작동함
  - 테두리를 그려 보면 분명히 알 수 있음
- `box-decoration-break: clone`을 통해 줄바꿈마다 별도의 박스가 구성되도록 수정할 수 있음
  - WebKit 및 Blink 브라우저들에는 `-webkit-box-decoration-break` 사용이 필요함

### The deal with inline-block

- `inline-block`은 내부적으론 블록 요소처럼, 외부적으론 인라인 요소처럼 작동함
  - 부모 컨테이너는 요소를 블록 요소처럼 다룸
  - 내부적으로는 블록 요소처럼 스타일링할 수 있음
- 인라인 요소는 중간에 줄바꿈이 들어갈 수 없다는 단점이 있음
