# Module2. **Rendering Logic II**

- Position layout에 대해 알아보는 모듈
- `position`에 값을 정하지 않으면 기본 값은 `position: static`

<br />

---

<br />

## 1. **Relative Positioning**

- `position: relative`를 써도 레이아웃에는 전혀 다른 차이점이 없다는 것을 알 수 있다. 사실 이 속성을 쓰는 이유를 두 가지로 나눌 수 있는데
  - 자식요소를 제어하기 위해서
  - CSS의 다른 속성을 이용하기 위해서

> `position: relative`를 보통 자식요소의 위치를 잡는 요소로 많이 사용하곤 했는데, 이걸 적용하면 이걸 적용한 요소 자체에도 *top, right, bottom, left*의 값을 주어 위치를 바꿀 수 있다는 걸 알게 되었다. (신기)

<br />

- element 자체에 `position: relative`를 사용하고 위치 값을 넣어주면 `margin`을 쓰는 것과 달리 주변 레이아웃에 전혀 영향을 주지 않고 본인의 위치만 변함.

- 그리고 이 포지셔닝은 `block` 뿐만 아니라, `inline`에서도 쓸 수 있다!

> 예시로 `p` 태그 안에 있는 `strong` 태그에 포지션을 *relative*로 주고 `top: -4px;`을 줬더니 이 부분만 살짝 위로 올라갔다. 이렇게도 쓸 수 있구나...

<br />
<br />
<br />

## 2. **Absolute Positioning**

- 마크업한 순서대로 레이아웃이 배열되는데 이를 무시하고 원하는 위치에 놓기 위해 사용하는 것이 바로 `position: absolute`
- DOM의 순서를 무시하고 혼자서 붕 뜬 상태이기 때문에 다른 요소들은 이 요소가 있다는 걸 인지하지 못하고 각자의 남은 위치를 차지하려고 한다.
- 프레임을 기본으로 하기 때문에 위치를 **픽셀**뿐만 아니라 **퍼센트**로도 줄 수 있다.

  > _만약에 위치 값을 주지 않고 적용한다면?_ 이렇게로는 사용해본 적이 없는데 예시를 보니까 문장 사이에서 잘 융합되는 것 같으면서도 프레임 크기를 줄이면 다른 글자 사이에서 떠 있는 게 보인다!

<br />

HTML

```HTML
<p>This is a paragraph.</p>
<p>Another paragraph, with different words.</p>
<p>Finally, to complete the set, a third.</p>
```

CSS

```CSS
p {
  position: absolute;
}
```

- 이런 식으로 주면 각각의 문장이 서로가 있는지 모르고 비어있다고 생각하기 때문에 그 위에 차곡차곡 쌓이는 효과를 보여준다.

<br />

- 자식요소가 `position: absolute;`를 가지게 되면 이를 감싸고 있던 부모요소는 자식요소가 없는 걸로 판단해서 차지하고 있던 공간이 비어진다.

<br />

### 2.1. **Absolute sizes**

> _(예시 동영상을 보고나서)_ absolute 속성에 컨텐츠를 가지고 있을 때 정해진 위치에서 뷰포트를 넘지 않을 만큼만 커지고, 컨텐츠를 한 줄로 연결하지 않고 뷰포트에 닿으면 밑으로 내려보낸다. 즉, 컨텐츠에 맞게 사이즈가 커짐.

> 그런데 컨텐츠가 스페이스 없이 한 줄로 쭉 연결되어 있으면 이 컨텐츠를 전부 감싸지 못하고, 본인의 위치에서 브라우저의 뷰포트까지만 커지고, 컨텐츠를 그야말로 넘쳐서 가로 스크롤이 생긴다!

<br />
<br />
<br />

## 3. **Centering Trick**

> 엘레먼트를 가로축으로 가운데에 놓고 싶을 때, `margin: 0 auto;`를 쓰는 편이고, 세로로 가운데 정렬을 할 때는 보통 flexbox를 쓰는 편이었느데 여기서 트릭을 하나 알려준다!

<br />

CSS

```CSS
.box {
  position: absolute;
  top: 0px;
  left: 0px;
  right: 0px;
  bottom: 0px;
  width: 100px;
  height: 100px;
  margin: auto;
  background: deeppink;
}
```

HTML

```HTML
<div class="box"></div>
```

flexbox나 grid 속성을 사용하지 않고도 브라우저의 한 가운데에 엘레먼트를 위치시킬 수 있다. 허나 이 트릭을 사용하기 위해선

1. `position: absolute;`
2. 각각의 꼭지점에서부터 같은 거리를 유지할 것. `0px`을 사용하는 것이 이상적으로 한다.
3. `width`와 `height` 값을 정의할 것
4. `margin: auto` (*Hungry margins*라고 표현 ☻)

<br />
<br />
<br />

## 4. **Containing Blocks**

> **Containing Block**을 element를 담고 있는 사각형 박스 정도로 이해하면 될 듯

<br/>

```HTML
<section class="container">
  <p>Hello World!</p>
</section>
```

이 코드에서 'Hello World!'를 담고 있는 `<p>` 태그를 containing block이라고 표현한다.

<br />

> `position: absolute` 일 때는 예외로 볼 수 있는데, `top` / `right` / `bottom` / `left`로 위치 값을 정하면 element는 그 containing block에서 정한 값에 위치한다.

- 보통의 element는 부모 요소에 의해 위치가 정해지는 편인데 `position: absolute`로 하면 이 부모 요소를 무시하고 위치하게 된다. (여기선 반항적인 10대에 비유함)
- 자식 요소는 윗 세대에서 `position` 값을 찾을 때까지 무시하고 본인의 위치 값을 정해준 곳에 자리 잡는다. 부모 요소에서 포지션이 꼭 `relative`일 필요는 없고, `fixed, sticky, absolute`여도 관계없다.
- 윗 세대 요소의 **padding** 값은 고려대상이 아니다.

> 처음 CSS를 접할 때 자식요소를 부모요소와 관계없이 위치를 놓고 싶을 때 자식요소에는 `position: absolute`로 하고, 부모요소에 `position: relative`를 많이 쓰는 건, 이 *relative*는 다른 요소의 위치를 방해하지 않기 때문이라고 배웠던 기억이 있다.

<br />
<br />
<br />

## 5. **Stacking Contexts**

여러 개의 컨텍스트가 쌓일 때 쌓이는 기준은 무엇일까? 그 기준은 **layout mode**에 따라 다르다.

- Flow Layout에서 형제 elements끼리의 레이어를 결정하는 건, DOM의 순서에 따라 결정되고 background-color나 border의 경우 레이어로 쌓이지만 elements 안에 있는 텍스트는 오버랩되지 않고 앞에 떠오른다.
- 한 형제 element가 `position` 속성을 가지고 있으면 DOM의 순서와는 무관하게 무조건 `position`을 가지고 있는 요소가 레이어 가장 앞에 놓인다.
- 두 elements가 다 `position` 속성을 가지고 있으면 이 때에는 DOM의 순서에 따라 레이어가 결정되고, 첫 번째 경우와는 달리 텍스트는 떠오르지 않는다.

<br />
 
### 5.1. **z-index**
Layer의 순서를 정하고 싶을 때, CSS에서 `z-index` 속성을 사용한다. **z-index**는 *position을 가지고 있는 속성에서만* 작용한다. 여기서 말하는 **z**는 **z축**을 이야기하는데, 레이어의 앞 / 뒤쪽을 생각하면 된다.

- `z-index`의 기본 값은 **auto**, 즉 **0**이다.

<br />

> 부모의 element에 z-index가 정해져 있으면, DOM에서 봤을 때 같은 선상에 놓여있지 않더라도 `z-index`의 값에 따라 그 레이어의 위치가 달라진다.

<br />

- 레이어를 쌓을 때 고려할 수 있는 것들
  - `opacity`의 값이 1보다 작을 때
  - `position`을 `fixed` / `sticky`로 했을 때 (z-index의 영향을 받지 않음)
  - `mix-blend-mode` 사용
  - 더 많은 내용은 **MDN**에서 [The stacking context](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Positioning/Understanding_z_index/The_stacking_context)을 검색하면 볼 수 있음

<br />

여러 개의 element의 레이어를 배치하다가 원하는대로 되지 않으면 크롬 익스텐션에서 **CSS Stacking Context Inspector** 툴을 사용해볼 것.

<br />
<br />
<br />

## 6. **Managing z-index**

> 여러 개의 elements의 z축을 신경쓰는 것을 여기에선 **z-index 전쟁**이라는 표현을 썼다-! 각각의 요소에 z-index의 값을 더 높게 주는 것보다 먼저 고려해서 사용할 수 있는 방법들을 알려준다.

<br />

- **DOM의 순서 바꾸기** : 꾸미는 요소를 뒤에 두고, 맨 앞에 카드를 앞에 놓아야할 때 `position`을 쓰고 `z-index`의 값을 정하는 것이 아닌, 카드를 DOM에서 더 뒤에 놓는다면 카드가 제일 앞 레이어로 나온다.

<br />

- **`isolation: isolate` 사용하기** : 가격표가 붙은 카드들의 레이어 위치를 바꿔야할 때 각각의 카드만 고려하다가 `position: fixed`로 고정해놓은 `<header>`의 z-index를 신경쓰지 못해 버그가 발생할 수도 있다. 이럴 때는 class card로 묶은 것에 z-index를 `<header>`보다 낮게 주고 그 자식요소들끼리 z-index의 값을 달리하는 방법도 있지만 class card에 `isolation: isolate`를 줘서 안에 있는 자식요소들끼리 고려하여 사용할 수도 있다. 그렇지만 이것은 인터넷 익스플로러...에서는 사용할 수 없다 ☹︎

<br />

> 여기서 `isolation: isolate`라는 것을 처음 봤는데, 다음에 한 번 사용해봐야겠다. 그리고 Flow Layout만 적용된 것에서 z-index를 사용할 수 없을 뿐이지, Flexbox, Grid와 같은 것은 z-index 속성을 적용할 수 있다.

<br />
<br />
<br />

## 7. **Portals**

> JS 기반의 프레임워크를 사용할 때 앱의 `#root`에 기반하여 렌더링되는 메인의 레이어와 관계없이 띄워지는 *modal*의 경우, 사용할 수 있는 UI(_Reach UI_)를 추천하며 `style.css` 파일을 만들고 여기에 `#root {isolation: isolate;}` 값을 주어 모달과 메인 레이아웃의 레이어를 신경쓰지 않고 작업할 수 있는 방법을 제시했다.

<br />
<br />
<br />

## 8. **Fixed Positioning**

- `position: absolute`와 비슷한 점이 많다. 다른 점이 있다면 `position: fixed`는 사용자가 보고 있는 viewport에만 담긴다.
- `.modal`을 **absolute**를 이용해서 한 가운데에 배치할 때처럼 **fixed** 역시 그와 같은 속성으로 뷰포트 정 가운데에 배치할 수 있다.

```CSS
.modal {
    /*
      For this party trick, we need:
      - Position absolute or fixed
      - All sides set to '0'
      - explicit dimensions
      - auto margins
    */
    position: fixed;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    width: 85%;
    height: 200px;
    margin: auto;
  }
```

<br />

> `position: fixed`에 위치 값을 지정하지 않는다면? DOM에서 원래 위치해야할 자리에 놓여지며 그 속성 그대로 스크롤이 생겨서 아래로 내려도 고정한 위치에 그대로 고정되어 있다.

<br />

### 8.1. **The transform exception**

그렇지만! `position: fixed`를 가지고 있는 element의 윗 세대에서 `transform` 속성을 가지고 있다면 원하는대로 이 위치가 고정되지 않는다. (띠-용) **transformed된 부모요소는 자식요소를 고정시킬 수 없다.** 바로 위 부모요소뿐만 아니라 DOM 트리를 타고 올라가서 그 윗 세대에 존재한다면. 그리고 또, transform 속성 뿐만 아니라 `will-change: transform` 역시 같은 양상을 보인다.

<br />

element가 `position: fixed`로 고정되지 않는다면, 그것은 윗 세대에 **transform** 속성을 가지고 있다는 얘기가 된다. 그래서 이 범인(?)을 찾기 위해 다음과 같은 코드를 이용할 수 있다.

```JavaScript
// Replace this with a relevant selector.
// If you use a tool that auto-generates classes,
// you can temporarily add an ID and select it
// with '#id'.
const selector = '.the-fixed-child';
function findCulprits(elem) {
  if (!elem) {
    throw new Error(
      'Could not find element with that selector'
    );
  }
  let parent = elem.parentElement;
  while (parent) {
    const {
      transform,
      willChange
    } = getComputedStyle(parent);
    if (transform !== 'none' || willChange === 'transform') {
      console.warn(
        '🚨 Found a culprit! 🚨\n',
        parent,
        { transform, willChange }
      );
    }
    parent = parent.parentElement;
  }
}
findCulprits(document.querySelector(selector));
```

<br />
<br />
<br />

## 9. **Overflow**

> 저번 협업프로젝트할 때 이 `overflow`로 꽤나 곤혹을 치뤘던 기억이 있다... 내 마음대로 만들어지지 않는 스크롤들... (또르르)

텍스트를 담고 있는 컨테이너가 텍스트의 길이보다 작을 때 이 텍스트가 넘치고, 이를 밑에 있는 DOM은 신경쓰지 않고 본인의 자리를 꿋꿋하게 지켜 넘친 텍스트와 밑에 있는 요소가 가지고 있는 텍스트가 겹치는 경우가 있다. 이럴 경우에 사용할 수 있는 속성이 바로 `overflow`.

<br />

### 9.1. **Accepted values**

- `overflow: visible` 이것이 기본 값이다. 그래서 텍스트의 양에 비해 컨테이너가 작으면 이를 넘쳐서 그 내용을 다 보여주고자 한다.
- `overflow: scroll` 컨테이너보다 텍스트의 양이 넘칠 때 이 속성을 사용하면 컨테이너에 스크롤이 생기고 스크롤을 내리면서 모든 텍스트를 담을 수 있다. `overflow`는 `overflow-x` / `overflow-y`를 축약한 것이다.

  > MAC OS의 경우, `overflow: auto`가 아닌 `scroll`을 사용할 경우, 내용이 넘칠 때만 스크롤이 보여지는 것이 아니라 _항상_ x축, y축의 스크롤이 보인다. (겪어봄...) 맥 OS 설정 자체에서 스크롤이 필요할 때만 보이도록 수정할 수 있으나, 이걸 과연 하고 있는 사용자가 몇이나 될런지. 그래서 항상 유념하고 있어야 하는 부분.

- `overflow: auto` 스크롤이 생길 수 있는 상황에서 가장 추천하는 방법. 뷰포트 자체가 어떤 사이즈인지 다 예측할 수 없고 때로는 스크롤이 생기길 원할 수도 아닐 수도 있다. 이럴 때 쓰면 가장 좋다.

  > 그럼에도 `scroll` 값을 쓰는 때는? 스크롤이 생길 때는 여유 공간이 ~15px 정도가 필요할 수 있어 컨테이너가 조금 줄어들 수 있다. 만일 스크롤이 **반드시** 생긴다는 걸 알 수 있다면 `overflow: scroll`을 사용할 때 조금 더 부드러운 사용감을 보여준다고 한다.

- `overflow: hidden` 이를 사용하는 이유는,

  1. 넘치는 텍스트에 이클립스 (...)를 사용하기 위해서
  2. 데코용으로 사용하는 것을 안보이게 하기 위해서 (미관상)
  3. 원치않는 가로 스크롤을 숨기기 위해서

  > 조쉬는 `overflow: hidden`을 사용할 때 주석을 달아놓는 것이 좋다고 추천한다. 이를 사용할 때는 어떠한 목적이 있을 때 사용했을텐데 미래의 자신이 보거나 다른 개발자들이 작업을 할 때 `overflow: hidden`을 지우고 무너지는 레이아웃을 보지 않도록...

<br />
<br />
<br />

## 10. **Horizontal Overflow**

> **Q.** 컨테이너 안에 사진을 넣을 때 이 컨테이너보다 사진의 양이 많아서 컨테이너 밑으로 사진이 내려갈 때, 이를 방지하고 가로스크롤이 생기게 하려면 어떻게 해야할까?

> **A.** `white-space: nowrap`과 `overflow: auto`를 사용하면 사진이 그 위치에 일렬로 정렬 되면서 가로스크롤이 생기게 만들 수 있다. `white-space`는 **inline**이나 **inline-block**을 줄바꿈을 관리할 수 있는 속성이다.

<br />
<br />
<br />

## 11. **Positioned Layout**

### 11.1. **Overflow and containing blocks**

> **Q.** 부모요소가 `overflow: hidden`을 가지고 있고 자식요소가 `position: absolute`라면 자식요소가 가려질까?

```HTML
<style>
.wrapper {
  overflow: hidden;
  width: 150px;
  height: 150px;
  border: 3px solid;
}
.box {
  position: absolute;
  top: 24px;
  left: 24px;
  background: deeppink;
  width: 150px;
  height: 200px;
}
</style>

<div class="wrapper">
  <div class="box" />
</div>
```

> **A.** `position: absolute`는 윗 세대가 `position`을 가지고 있지 않으면 그 바운더리를 벗어난다. 벗어난 자식요소를 가리려고 `overflow: hidden`을 사용한 것이라면 `position: relative` 속성도 함께 넣어주어야 한다. 대신에 `overflow: auto`를 사용하면 containing block 안에서 있어야 할 위체에 `.box`가 위치하며 x축과 y축에 스크롤이 자동으로 생겨서 이 안에 담겨있는 걸 확인할 수 있다.

<br />

### 11.2. **Fixed positioning**

> 같은 HTML 구조로 `.box`에 `position: fixed`가 적용되면 `.wrapper`는 전혀 상관하지 않는다. `.box`가 고려하는 건 뷰포트다.
