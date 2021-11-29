# Managing z-index

- z-index와 싸우는 것은 CSS를 다룰 때 가장 흔히 좌절을 가져다주는 것 중 하나로 꼽힌다.
- 어떤 요소를 다른 요소 위에 보이게 하기 위해 점점 더 높은 값을 지정하고, 그러면서 z-index 값이 비정상적으로 커지게 되고, 결과적으로 적절한 z-index 값을 찾기 점점 더 힘들어지는 문제가 자주 발생한다.
- 사실 이런 짓을 할 필요는 없으며, Stacking Context 분리나 DOM 순서 조정 등을 통해서 z-index를 설정하는 것 자체를 회피할 수 있다.

## DOM 순서 바꾸기

- 더 앞에 보여질 요소를 HTML에서 더 뒤에 작성함으로써, z-index 설정 없이 쌓이는 순서를 변경할 수 있음
- 단, 이는 Tab 키를 사용하여 사이트를 탐색할 때의 순서를 변경하기 때문에, 상황에 맞추어 사용하여야 한다.

## 격리된 Stacking Context

- 겹치는 순서를 조정하고자 하는 항목들의 컨테이너에 `isolation: isolate`를 삽입하여 Stacking Context를 생성할 수 있다.
- 이렇게 하면 Context 외부 요소와 z-index로 문제가 생기는 것을 방지할 수 있다.
- TailwindCSS에선 `isolate` 유틸리티를 사용하여 적용 가능하다.
