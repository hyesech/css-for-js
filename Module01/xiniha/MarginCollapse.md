# Margin Collapse

- 앞서 설명했듯이, 마진은 각 요소 간에 확보된 최소한의 공간임
- 따라서 두 개의 마진이 만나면, 두 마진은 서로 겹칠 수 있음

## 마진이 겹쳐지는 규칙

### 오직 세로 마진만 겹쳐짐

- 가로 마진은 겹쳐지지 않고, 오직 세로 마진만 겹쳐짐
  - 정확히는, 블록 방향의 마진만 합쳐짐
- 이는 CSS가 최초로 만들어질 때 레이아웃을 위해 사용될 것을 전제하고 만들어지지 않았기 때문

### 마진은 Flow 레이아웃에서만 겹쳐짐

- Flexbox 등의 레이아웃에서는 마진이 겹쳐지지 않음

### 인접한 요소들의 마진만 겹쳐짐

- 중간에 `<br>`등의 요소를 끼워넣을 경우, 마진은 겹쳐지지 않음

### 더 큰 마진이 우선됨

- 마진이 겹쳐지는 상황에서, 두 마진의 크기가 다른 경우, 더 큰 마진의 크기만큼 공간이 확보됨

### 중첩은 마진이 겹쳐지는 걸 막지 않음

- 두 마진을 가진 요소 중 하나를 다른 요소로 감싼다고 해도 마진은 그대로 겹쳐짐
- 단, 예외가 존재하는데, 이 경우에는 마진이 겹쳐지지 않음
  - 마진과 마진 사이에 패딩/테두리 등의 "벽"이 존재하는 경우
  - 부모 요소와 자식 요소 사이에 공간이 존재할 경우

### 마진은 같은 방향으로도 겹쳐질 수 있음

- 일반적으로 마진이 겹친다고 하면 위 요소의 아래 마진과 아래 요소의 위 마진이 겹치는 걸 생각하지만, 사실 마진의 방향은 아무 상관이 없음
- 부모 요소의 마진과 자식 요소의 마진이 겹쳐질 수 있음
- `0px` 마진 역시 겹쳐질 수 있는 마진임, 따라서 부모 요소에 마진이 없어도 패딩/테두리 등의 벽이 없다면 자식 요소의 마진이 부모에 적용될 수 있음

### 마진이 겹쳐지는 개수에는 제한이 없음

- 윗 부모 - 윗 자식 - 아랫 부모 - 아랫 자식 등....
- 사실 규칙 자체는 특별한 건 아님

### 음수 마진에도 동일한 규칙이 적용됨

- 음수 마진 + 음수 마진 시 더 큰 음수 마진이 적용됨
- 음수 마진 + 양수 마진 시 더하기 연산으로 일부 상쇄됨

### 여러 개의 음수와 양수 마진이 겹쳐질 수 있음

- 이 경우, 다음과 같은 알고리즘이 적용됨
  - 가장 큰 양수 마진을 찾고
  - 가장 작은 음수 마진을 찾아서
  - 둘이 더함

## Using Margin Effectively

- 마진의 괴상한 특성상 마진을 완전히 쓰지 않는 것이 최근의 트렌드임
- 그러나, 완전히 새로운 프로젝트를 같은 공감대를 가진 팀원들과 시작하는 것이 아니면 마진을 완전히 버리는 것은 현실적으로 어려움

### 마진은 마치 풀과 같다

> 마진은 마치 어디에 붙이게 될지 모르는, 혹은 어디에도 붙어서는 안 되는 물건에 미리 풀을 묻혀 놓는 것과 같다.

- 마진을 컴포넌트 경계에 붙이는 것은 좋은 생각이 아님
- 컴포넌트는 최대한 재사용될 수 있도록 만들어져야 하기 때문에, 어디에 이 컴포넌트가 배치될지도 모르는 상황에서 마진을 적용하는 것은 많은 문제를 발생시킴
