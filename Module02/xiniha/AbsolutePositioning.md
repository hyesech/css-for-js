# Absolute Positioning

- 일반적으로 요소는 Flow 레이아웃에 의해, 흐름에 따라 배치된다.
- 이걸 깨고 아무 데나 갖다 붙이는 데에 Absolute Positioning이 사용된다.

## 프레임을 사용하여 배치

- Absolute Positioning을 사용하면 자신이 속한 컨테이너의 벽면으로부터의 간격을 통해 요소를 배치시킬 수 있다.
- 이를 위해서 `top`/`bottom`/`left`/`right` 속성이 사용된다.
- 이들 속성은 Relative Positioning에서와는 완전히 다르게 동작하는데, 컨테이너의 해당 방향 벽면으로부터의 간격을 지정하는 방식으로 동작한다.
  - 값을 퍼센트 단위로 지정할 경우 사용 가능한 전체 공간에서의 비율에 따라 배치가 이루어진다.
- 만약 이들 속성을 지정하지 않으면, Flow 레이아웃 기준으로 기존에 요소가 배치되었을 위치에 요소가 그대로 배치된다.
  - 단, 여전히 레이아웃에는 영향을 주지 않는다.

## 레이아웃에 미치는 영향

- Absolute Positioning을 사용하면, 요소는 Flow 레이아웃의 흐름에서 제거된다.
- 따라서, 브라우저는 요소를 배치할 때에 Absolute Positioning을 사용하는 요소들을 마치 존재하지 않는 것처럼 간주하고 레이아웃을 구성하게 된다.

## 중앙 정렬 트릭

- 요소에...
  - Absolute Positioning을 적용하고
  - 각 변과의 거리를 일정하게 지정하고 (예: `0px`)
  - 고정된 가로세로 크기를 부여하고
  - `margin: auto`를 설정하면
- 가로세로 모두 중앙 정렬된다.
- 모달 등에 사용하기 유용한 방식의 중앙 정렬 트릭이다.
