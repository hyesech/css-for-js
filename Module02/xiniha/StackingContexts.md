# Stacking Contexts

- Positioned 레이아웃을 사용하거나, Flow 레이아웃에서 음수 마진을 사용하는 등 다양한 방법으로 요소를 겹치도록 배치할 수 있음
- 이때 어떤 요소가 더 위에 배치되는지에 대해 다양한 규칙이 있음

- Flow 레이아웃에서, 나중에 있는 DOM 요소가 먼저 있는 요소보다 위에 배치됨
- 그런데, Flow 레이아웃에서는 배경색과 내용이 별개로 그려짐. 따라서 겹치는 효과가 제대로 구현되지 않음
- Flow 레이아웃은 기본적으로 요소들이 겹치는 상황을 고려하고 만들어지지 않았음
- 따라서 요소를 겹치는 상황에서는 Positioned 레이아웃을 사용하는 것이 일반적으로 원하는 방향임

- Positioned 레이아웃을 사용하는 요소는 언제나 다른 레이아웃의 요소보다 위에 그려짐
- 두 요소가 모두 Positioned 레이아웃을 사용할 경우, 나중에 있는 DOM 요소가 위에 그려짐

## z-index

- `z-index` 속성을 사용하면 요소의 순서에 상관없이 어떤 요소가 위에 그려질지를 지정할 수 있음
- `z-index`는 기본적으로 Positioned 레이아웃 요소에만 작동함
- `z-index` 값이 클수록 위에 그려짐
  - 기본값은 0이며, 따라서 위에 그려질 요소에 더 큰 값을 지정하면 해당 요소가 위로 올라오게 됨
  - 음수 값도 지정 가능하나, 보통 별로 유용하지 않음

## Introducing stacking contexts

- Positioned 요소에 `z-index` 값을 지정하는 것은 하나의 Stacking Context를 생성함
- Stacking Context가 생성되면, 해당 Context 내에 있는 요소 전체가 하나의 묶음으로 간주됨
- 이 경우, Stacking Context 내의 요소가 아무리 높은 `z-index`를 가지더라도, Context 전체가 Context 밖의 요소보다 낮은 `z-index`를 가진다면 해당 요소 위에 그려질 수 없음

### Creating new contexts

- Stacking Context는 Positioned 요소에 `z-index`를 지정하는 것 외에도 다양한 방법으로 생성됨
  - `opacity`를 1 미만으로 설정
  - `position`을 `fixed`나 `sticky`로 설정
  - `mix-blend-mode`를 `normal` 이외의 값으로 설정
  - Flex나 Grid의 자식에 `z-index`를 지정
  - `transform`, `filter`, `clip-path`, `perspective`를 사용
  - `isolation: isolate`를 사용하여 명시적으로 Context 생성
  - 등등 ([MDN 문서](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Positioning/Understanding_z_index/The_stacking_context))

## Debugging stacking contexts

- CSS에 얼마나 숙련되었는지에 상관없이, Stacking Context 관련 문제는 종종 겪게 됨
- 따라서 [CSS Stacking Context Inspector](https://github.com/andreadev-it/stacking-contexts-inspector) 등을 활용하여 디버깅을 편리하게 하는 것이 많은 도움이 된다.
