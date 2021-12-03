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
