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
