# Portals

- Stacking Context를 활용해서 겹치는 순서를 관리하다 보면, 종종 Modal 등의 사용으로 Stacking Context를 뚫고 나와야 하는 경우가 발생함
  - 특히 최근 프론트엔드의 JS, 컴포넌트 기반 개발 방식에서 자주 발생함
- 이를 위해 많은 프론트엔드 프레임워크에선 Portal/Teleport 등의 개념을 제공함
- 이를 이용하면, 컴포넌트가 각 루트 DOM 요소 바깥에도 UI를 그릴 수 있음
- 단, 앱 내에서 z-index가 어떻게 사용되는지에 따라 문제가 발생할 수 있으므로, 앱 루트 (`.root`, `#app` 등) 에 `isolation: isolate` 등을 활용하여 Stacking Context를 분리시켜 주는 것이 좋음
