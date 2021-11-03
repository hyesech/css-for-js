# Module 1. **Rendering Logic I**

+ 기본적으로 CSS의 궁극적인 목적은 app 컨텐츠의 모습과 레이아웃을 다루기 위함이다.

+ CSS를 시작할 시에 비어있는 캔버스에서 시작한다고 할 수 없다. HTML의 태그에는 기본적인 스타일이 적용되어 있다. 이를 *user-agent stylesheet*라고 한다.

+ CSS의 reset은 김버그님의 강의를 듣고 나서 그 강의에서 제시한 걸 쓰곤 했었는데, 본문에서도 나오긴 하지만 본인의 취향대로 만들어서 쓰는 것이 낫지 않을까 싶다. Josh가 쓰고 있는 Global Styles 중에 `html, body { height: 100%; }`와 `body { line-height: 1.5; }` 그리고 `img, picture { max-width: 100%; display: block; }`은 나도 써야겠다.

<br />

---

<br />

## 1. **Inheritance**
+ 타이포그래피와 관련된 CSS 속성들은 대부분 후손들에게 상속된다. 
+ 상속되는 속성들을 볼 수 있는 링크 : [ list of inheritable properties ](https://www.sitepoint.com/css-inheritance-introduction/#list-css-properties-inherit)

<br />
<br />
<br />

## 2. **The Cascade**
 + *selector(선택자)*의 특별함으로부터 선언한 style이 결정된다.
    + `여러 겹으로 중첩된 선택자` > `IDs` > `class` > `tag`


<br />
<br />
<br />

## 3. **Directions**
+ 영어는 왼쪽에서부터 오른쪽으로 읽는 언어이다. 그리고 영어의 문서는 두 가지의 방향으로 이루어졌는데, 문단 개념은 `blocks` 위에서 아래로 *vertically*, 단어 개념은 `inline` 왼쪽에서 오른쪽으로 *horizontally*. CSS는 이러한 개념을 바탕으로 만들어졌다.

<br />

### 3.1. Logical properties
+ `p` tag의 기본적인 스타일
``` CSS
p {
  display: block;
  margin-block-start: 1em;
  margin-block-end: 1em;
  margin-inline-start: 0px;
  margin-inline-end: 0px;
}
```
> CSS의 속성이 어떤 개념으로부터 만들어졌는지를 고려한다면, `margin-block-start,margin-block-end`는 내가 자주 사용했던 `margin-top, margin-bottom`, 그리고 `margin-inline-start, margin-inline-end`는 일반적으로 `margin-left, margin-right` 의미한다. 특정 위치를 가르키는 것보다 전자의 예시를 쓰는 게 더 좋을 거 같은 것이 모든 언어가 왼쪽에서 오른쪽으로 읽지 않기 때문에 더 광범위하게 쓰일 수 있겠다.

<br />
<br />
<br />

## 4. **The Box Model**

> *Box model에 대해서 설명해주세요.   

라는 질문을 들었을 때 어떻게 대답을 해야겠다는 생각이 들지 않는다... 그러므로 앞으로 나오는 설명들에 대해서 자세히 들여다보자-!

<br />

### 4.1. Winter Layers
Josh는 이 box model을 다음과 같이 비유해서 설명을 했는데 정말 이해하기 쉽고 연상하기도 쉬웠다. 추운 겨울날, **두툼한 패딩을 입고 있는 걸어가는 사람**을 연상해보자.

---

#### 1. *Content* : 사람 그 자체, 패딩을 입고 있는 사람.   
#### 2. *Padding* : 사람이 입고 있는 패딩의 폴리에스터 충전재. 충전재가 많을수록, 패딩은 더 크게 보이고 사람 또한 더 많은 공간을 가지게 된다.   
#### 3. *Border* :  패딩의 겉부분. 이것이 두껍거나 색깔을 가지고 있으면 사람의 모습에 영향을 끼친다.   
#### 4.  *Margin* : 사람 간의 거리 정도를 의미. 

<br />

### 4.2. Debugging in the browser
- CSS를 디버깅할 때 가장 많이 쓰이는 건 아무래도 개발자툴을 켜서 화면 왼쪽 상단에 있는, 마우스포인터가 보이는 것을 클릭하고 브라우저에 가져가면 개발자 툴 하단에서 CSS 속성을 볼 수 있다.

<br />

### 4.3. Box Sizing
> 아래와 같은 코드가 있을 때, class가 *box*인 사각형의 크기는 어떻게 될까?
``` HTML
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

> 정답은 548px x 48px
<br />

---

`500px x 0px`을 생각하겠지만 땡 - !   
일반적으로 `box-sizing: content-box`로 되어있다. 그렇기 때문에 `.box`는 `section`에서 `width: 500px`을 가져오고, 그 겉에, 상하좌우로 `padding: 20px; border: 4px`씩을 더 가진다. 

<br />

CSS를 적용할 때 이렇게 예상 외의 box-sizing을 피하려면 
```
*,
*::before,
*::after {
  box-sizing: border-box;
}
```
룰을 꼭 넣어주기 (별표 다섯개⭐️⭐️⭐️⭐️⭐️)

<br />
<br />
<br />

## 5.*Padding*
Padding은 요소 안에 있다는 걸 명심하기

``` CSS
.even-padding {
  padding: 20px;
}
.asymmetric-padding {
  padding-top: 20px;
  padding-bottom: 40px;
  padding-left: 60px;
  padding-right: 80px;
}
/* The same thing, but using ✨ logical properties ✨ */
.asymmetric-logical-padding {
  padding-block-start: 20px;
  padding-block-end: 40px;
  padding-inline-start: 60px;
  padding-inline-end: 80px;
}
```
> padding 역시 `top, bottom, left, right`로 쓸 수 있는 것 뿐만 아니라 `block-start, block-end, inline-start, inline-end`로 속성을 표현할 수 있다.

<br/>

### 5.1 Shorthand properties
``` CSS
.two-way-padding {
  padding: 15px 30px;
}
.asymmetric-padding {
  padding: 10px 20px 30px 40px;
}
```
- padding의 속성을 2개만 쓰면 `top/bottom, left/right`를 지정해서 값을 넣은 것이고, 4개를 연달아서 쓸 경우 `top, right, bottom, left`로 12시를 기준으로 한 시계방향으로 생각하면 속성을 기억하기 쉽다. 이런 *Shorthand properties*는 padding 뿐만 아니라, margin, border-style에도 적용해서 생각하면 된다.

<br />

### 5.2 Units
> 많은 개발자들이 *pixels*은 접근성이 떨이지는 단위라고 생각한다. 나 역시도 `px`보다는 `rem`을 더 많이 쓰기도 했는데, 사용자가 개별적으로 변경할 수 있어야 하는 폰트가 아니라면 `px`을 쓰는 건 접근성이 떨이지는 거라 볼 수 없다고 설명. 그치만 비율 상의 문제로 `percentage`는 쓰지 않기.

<br />

### 5.3. Overwriting values
``` CSS
.box {
  padding: 48px;
  padding-bottom: 0;
}
```
> 이렇게 **덮어씌울** 생각을 많이 안해봤는데, 이게 조금 더 읽기 수월하지 않을까 싶다. 

<br />
<br />
<br />

## 6. **Border**
- 시각적으로 보여지는 컴포넌트, border   
- Border는 세 가지의 스타일을 가진다. 
  - Border width
  - Border style (eg. `solid`, `dotted`), *필수요소*
  - Boder color
- 각각의 속성을 줄여서 쓴다면
```CSS
.box {
  border: 3px solid hotpink;
}
```
- border의 색상을 지정하지 않는다면 기본값으로 폰트의 컬러을 가져다가 쓴다. 혹은 text의 color를 지정하고, 이를 그대로 border에 쓰고 싶다면 `currentColor`라는 키워드로 지정해도 된다.
```CSS
.box {
  color: hotpink;
  border: 1px solid currentColor;
  box-shadow: 2px 2px 2px currentColor;
}
```

<br />

### 6.1. Border radius
> *border-radius*라는 명칭보다 *corner-radius*가 더 알맞은 명칭이 아닐까...

- `border-radius`도 shorthand로 쓸 수도 있고, 아님 각 코너, 모퉁이의 속성을 지정해서 설정할 수도 있다. 

- 다양한 border의 style 속성들: `solid, dotted, dashed, double, groove, ridge, inset, outset, Mixed(dashed solid)`    내가 여기서 써본 건 solid랑 dashed 밖에 없군...

<br />

### 6.2. Border vs. Outline
`border`와 `outline`이 비슷한 양상을 보이나 다른 점은 **outline**의 경우 레이아웃에 영향을 끼치지 않는다. outline은 일종의 box-shadow라고 볼 수 있다.

- *Outline*은 `outline-offset`이라는 속성을 가지고 있다. 이는 border와의 갭이라고 생각하면 된다.

> `outline: none;`이라고 룰을 지정할 경우, 온전힌 키보드만 쓰는 사용자가에게 불편함을 줄 수 있다. 키보드만 쓰는 사용자를 고려한 적이 없는데 앞으로는 눈으로 보여지는 게 전부가 아니라는 사실을 알아야 겠다.

<br />
<br />
<br />

## 7. **Margin**
`margin`은 요소들간의 공간을 의미하는데, 여기선 표현을 숨을 쉴 수 있는 공간이라 표현했다. 

<br />

### 7.1. Syntax
- 사용하는 문법은 앞서 본 *padding*과 매우 유사하다.

<br />

### 7.2. Negative margin
- Padding과 Border의 경우 0을 포함한 양수만 사용할 수 있으나, Margin의 경우 음수 또한 사용할 수 있다.
- 음수의 margin은 부모요소, 형제요소에서 빠져 나오도록 보여진다.
- 이렇게 보면 margin으로 요소의 위치를 지정할 수 있다고 생각할 수 있지만, 그렇다기 보단 앞에서 element간의 숨쉬는 공간으로 표현한 것처럼 각 요소들간의 갭이라고 생각하는 게 더 맞을 듯.
- 음수의 margin은 형제요소들에 모든 영향을 끼친다. (흥미로운 사실)

<br />

### 7.2. Auto margins
- element를 가운데로 정렬하고 싶을 때 많이 쓰는 트릭, `margin: 0 auto;` 
- `auto`로 지정하면 각 왼쪽과 오른쪽이 공간의 여유가 되는만큼 전부 차지하려고 하는 속성 때문에 가운데로 배치되는 것이다. 그러나 **수평적인 margin**에서만 사용할 수 있는 속성. top/bottom margin이 `auto`일 경우엔 `0px`이라고 쓴 것과 동일하다. (처음엔 이것도 모르고 왜 margin을 auto로 지정했는데 한가운데로 가지 않냐며 의아했던 기억이...)
- 이와 같은 트릭은 자식요소가 하나인데, 가운데로 하고 싶을 때 유용하다. 많은 요소들을 정렬하고 싶다면 Flexbox나 Grid를 쓰는 것이 더 낫다.

<br />
<br />
<br />

## 8. *Flow Layout*
- CSS를 전혀 지정하지 않은 순수한 HTML 문서의 경우, 기본 값으로 *Flow layout*을 사용한다. 
- Flow layout에서는 모든 요소는 `display`의 값을 **inline, block, inline-block**으로 가진다. 
- 기본 값은 어떤 태그냐에 따라 달라지는데
  - `div` elements는 기본으로 **block**
  - `span` elements는 **inline**

- 거의 대부분의 요소가 block elements이다. (예외 `<strong> <a>`는 **inline**)

<br />

### 8.1. 평화주의자 **Inline**
그야말로 다른 요소들을 자신의 경계 밖으로 내보내려고 하지 않는다. `margin-right`나 `margin-left`와 같은 속성을 사용할 순 있으나 width와 height를 바꿀 순 없다. 

<br />

- 그러나 `display: inline;` 임에도 불구하고 예외가 있다.
  - `<img />`
  - `<video />`
  - `<canvans />`
  - `<button>` tag : inline 속성임에도 width/height 값을 가진다.

<br />

### 8.2. 개인주의자 **Block**
혼자서 가지는 공간을 무척이나 중요시 여기기 때문에 본인의 바로 옆에 있는 요소들을 밑으로 밀어낸다.

<br />

### 8.3. Inline은 숨겨진 공간을 가지고 있다.
inline이 기본인 이미지의 경우, 이런 경우가 종종 있는데 지정하지 않은 공간이 생기는 이유는, 웹 브라우저가 inline elements를 글자처럼 취급하기 때문이다. 원치 않은 공간을 수정하기 위해서 두 가지 방법으로 해결할 수 있는데,
- image의 속성은 `display: block`으로 바꾸기
- `line-height: 0`
이렇게 수정하면 글자처럼 취급하지 않기 때문에 브라우저가 여유공간이 필요없다는 것을 인식하고 불필요한 공간이 없어진다.   

그리고 HTML Document에서 이미지 코드를 연속으로 나열하며 코드의 줄을 들여쓴 경우, 원치않는 스페이스가 생길 수 있다. 이는 HTML이 스페이스에 민감하기 때문인데, 기본적으로 image 속성이 `display: inline;`이기 때문에 글자로 인식해서 그런 것 같다. 이미지 사이에 갭을 원치 않는 경우, 이미지 코드를 붙여서 쓰면 문제 해결-!

<br />

### 8.4. Inline은 다른 줄에서도 커버 가능합니다.
- 코드의 줄이 바뀌었더라도 inline은 이 속성을 커버한다. 

```HTML
<p>
  This is a paragraph with <strong>some very bolded words in it</strong>.
</p>
```
> This is a paragraph with **some very bolded words**   
**in it**

<br />
그러나 이러한 속성이 이상하게 보일 때가 있는데, paragraph에 배경색을 설정하여 줄을 달리할 때 뚝뚝 끊어진 것처럼 보인다. 비유를 들자면, 한 줄의 김밥을 잘랐을 때 자른 단면 사이에 여분의 공간이 없는 것처럼 뚝- 끊어져 보인다.   

이는 `padding-left`와 `padding-right`가 문장의 처음과 마지막에만 적용돼서 그렇다. 줄이 나누어진 문장에 각각 양쪽에 padding을 주고 싶다면, `box-decoration-break: clone;`으로 이런 문제가 해결된다. 위 속성의 기본 값은 *slice*.

<br />

### 8.4. **inline-block** 다루기
`display: inline-block`으로 설정하면 block 요소들을 inline context처럼 다룰 수 있다. 겉으로는 inline 요소들처럼 다뤄지나, 각각의 요소들의 스타일은 block처럼 취급한다.

- Inline-block은 line으로 감쌀 수 없다. 어찌보면 그런 게, 다른 요소들과 다룰 때만 inline처럼 취급되고, 본인의 스타일 자체는 block이기 때문에 그런 거 같다.

<br />
<br />
<br />