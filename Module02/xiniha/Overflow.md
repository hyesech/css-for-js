# Overflow

- 디자이너들이 목업을 작업할 때, 보통 데이터에 대한 이런저런 가정을 한다
  - 예를 들어, 이름이 20글자를 넘지 않을 것이라던가
- 개발자인 우리는 이런 가정들이 실제 데이터에서 절대 살아남지 못한다는 사실을 알고 있다.
- 따라서 UI에 넘치는 데이터들을 적절한 형태로 보여주도록 처리하여야 한다.
- 이를 위해 `overflow` (`overflow-x` & `overflow-y`) 속성이 사용된다.

## 사용 가능한 값들

- `scroll`: 항상 스크롤바를 보여줌
- `auto`: 내용이 넘칠 때만 스크롤바를 보여줌
- `hidden`: 넘치는 내용을 표시하지 않음
  - 주로 `overflow: hidden` 설정은 특수한 목적을 가지는 경우가 많기 때문에, 해당 부분에 주석을 달아 놓으면 리팩토링 시에 많은 도움이 된다.

## 스크롤 컨테이너

- `overflow` 속성을 설정하면, 해당 요소가 스크롤 컨테이너로 변함
- 이 경우, 요소의 자식은 요소 바깥으로 벗어날 수 없음
- 따라서, 가로로는 `hidden`이면서 세로로는 `visible`인 컨테이너 같은 건 불가능함
- `hidden` 속성은 단지 스크롤 컨테이너에서 스크롤바를 숨기는 방식으로 동작함


## Horizontal Overflow

- 텍스트나 이미지 등의 인라인 요소를 `overflow-x: auto` 등으로 스크롤시키는 건 제대로 동작하지 않음
- 이는 컨테이너 크기에 따른 줄바꿈이 일어나기 때문임
- `white-space: nowrap`을 활용하여 줄바꿈을 비활성화하는 등의 방식으로 해결 가능

## Positioned Layout

- Overflow는 주로 흐름 내의 요소들(비-Positioned)에 대한 것임
- Positioned 요소들은 Containing Block 요소에 적용된 `overflow` 속성만 적용맏음
  - 단, Fixed Positioning을 사용하는 요소들은 뷰포트를 Containing Block으로 사용하기 때문에 일반적인 `overflow` 속성들을 적용받지 않음
