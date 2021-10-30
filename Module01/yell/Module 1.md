## Module 1. **Rendering Logic I**

+ 기본적으로 CSS의 궁극적인 목적은 app 컨텐츠의 모습과 레이아웃을 다루기 위함이다.

+ CSS를 시작할 시에 비어있는 캔버스에서 시작한다고 할 수 없다. HTML의 태그에는 기본적인 스타일이 적용되어 있다. 이를 *user-agent stylesheet*라고 한다.

+ CSS의 reset은 김버그님의 강의를 듣고 나서 그 강의에서 제시한 걸 쓰곤 했었는데, 본문에서도 나오긴 하지만 본인의 취향대로 만들어서 쓰는 것이 낫지 않을까 싶다. Josh가 쓰고 있는 Global Styles 중에 `html, body { height: 100%; }`와 `body { line-height: 1.5; }` 그리고 `img, picture { max-width: 100%; display: block; }`은 나도 써야겠다.

<br />

---

<br />

### 1. **Inheritance**
+ 타이포그래피와 관련된 CSS 속성들은 대부분 후손들에게 상속된다. 
+ 상속되는 속성들을 볼 수 있는 링크 : [ list of inheritable properties ](https://www.sitepoint.com/css-inheritance-introduction/#list-css-properties-inherit)

<br />
<br />
<br />

### 2. **The Cascade**
 + *selector(선택자)*의 특별함으로부터 선언한 style이 결정된다.
    + `여러 겹으로 중첩된 선택자` > `IDs` > `class` > `tag`


<br />
<br />
<br />

### 3. **Directions**
+ 영어는 왼쪽에서부터 오른쪽으로 읽는 언어이다. 그리고 영어의 문서는 두 가지의 방향으로 이루어졌는데, 문단 개념은 `blocks` 위에서 아래로 *vertically*, 단어 개념은 `inline` 왼쪽에서 오른쪽으로 *horizontally*. CSS는 이러한 개념을 바탕으로 만들어졌다.

<br />

#### 3.1. Logical properties
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
