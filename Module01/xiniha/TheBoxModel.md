# The Box Model

## Winter Layers

- 박스 모델은 4개의 요소로 구성된다.
  - 내용 (Content)
  - 내부 여백 (Padding)
  - 테두리 (Border)
  - 외부 여백 (Margin)
- 이는 코트를 입은 사람으로 비유될 수 있다.
  - 내용은 코트 안에 있는 사람과 같다.
  - 내부 여백은 코트 내의 단열재와 같다. 단열재가 많이 채워질수록 코트의 부피와 사람의 부피가 커진다.
  - 테두리는 코트의 재질과 같다. 두께와 색깔을 가지며, 겉보기에 영향을 준다.
  - 외부 여백은 사람 주변에 확보된 공간과 같다.

## Box Sizing

- 요소가 `100%`의 `width`를 가지게 한다고 할 때, 이게 정확히 뭘 의미할까?

```html
<style>
  section {
    width: 500px;
  }
  .box {
    width: 100%;
    padding: 20px;
    border: 4px solid;
  }
</style>
<section>
  <div class="box"></div>
</section>
```

- 이 경우에, `div.box`의 크기는 `548px` x `48px`이다.
  - 부모 요소인 `section`의 크기는 `500px` x `0px`이다.
  - `div.box`의 내용의 가로는 `section`의 `width`의 `100%`, 즉 `500px`이다.
  - `div.box`의 내용의 세로는 `0px`이다.
  - `div.box`에는 상하좌우 각각 `20px`의 내부 여백과 `4px`의 테두리가 더해지게 된다.
  - 따라서 `div.box`의 크기는
    - 가로 `4px` + `20px` + `500px` + `20px` + `4px`
    - 세로 `4px` + `20px` + `0px` + `20px` + `4px`
  - 로 `548px` x `48px`가 된다.
- 이건 뭔가 매우 이상하고, 따라서 `box-sizing: border-box`가 나왔다.
- `box-sizing`을 `border-box`로 설정하면, 내부 여백과 테두리의 크기를 요소 크기에 포함하여 계산하게 된다.
- 일반적으로, 와일드카드 선택자를 사용해 `box-sizing: border-box`를 모든 요소에 적용한다.
