# Built-in Declarations and Inheritance
기본적으로 CSS의 역할은 앱 콘텐츠의 모양과 레이아웃을 제어하는 것임.
HTML에는 기본적인 스타일이 적용되어 있다. 

```css
a {
  color: -webkit-link;
  cursor: pointer;
  text-decoration: underline;
}
```
이것을 `user-agent-style`이라고 함. 대부분의 경우 브라우저마다 다 다른 기본 제공 스타일이 있음. 그래서 브라우저마다 다르게 보이는 것임.

### 상속
모든 CSS가 상속되는 것은 아님. 예컨대 폰트의 색상은 상속되지만 테두리에 대한 속성은 상속되지 않음. 상속이 되지 않기 때문에 부모-자식 관계에 있는 두 엘리먼트에 같은 스타일 속성을 적용하려면 부모 엘리먼트에 선언한 것처럼 자식 엘리먼트에도 명시적으로 같은 내용을 추가해야 함.

보통 상속 가능한 속성은 색상이나, 폰트 크기, 텍스트 그림자 등과 같은 타이포그래피 속성이다. 

> 상속 가능한 요소는 다음과 같다.
> - border-collapse
> - border-spacing
> - caption-side
> - color
> - cursor
> - direction
> - empty-cells
> - font-family
> - font-size
> - font-style
> - font-variant
> - font-weight
> - font-size-adjust
> - font-stretch
> - font
> - letter-spacing
> - line-height
> - list-style-image
> - list-style-position
> - list-style-type
> - list-style
> - orphans
> - quotes
> - tab-size
> - text-align
> - text-align-last
> - text-decoration-color
> - text-indent
> - text-justify
> - text-shadow
> - text-transform
> - visibility
> - white-space
> - widows
> - word-break
> - word-spacing
> - word-wrap

### 프로토타입(???)
Javascript의 프로토타입과 CSS의 상속이 좀 비슷해보인다는 이야기.
```html
<main style="color: black;">
    <p style="color: red;">
        Hello <span>World</span>
    </p>
</main>
```
여기서 World의 색상은 무엇일까? red임. 그런데 왜냐면 바로 직속 부모의 스타일을 상속받기 때문임. 그런데 아래와 같이 코드를 변경하자.
```html
<main style="color: black;">
    <p style="background-color: red;">
        Hello <span>World</span>
    </p>
</main>
```
그러면 그랜드 패런트... 인  main의 폰트 컬러를 상속 받을 것임. 그런데 이런 것이 자바스크립트의 작동 방식과 비슷하다는 것.

```Javascript
class Main {
    color = 'black'
}

class Paragraph extends Main {
    color = 'red'
}

class Span extends Paragraph {

}

const s = new Span();

console.log(s.color);
```

자바스크립트의 프로토타입 특성상 color에 대한 코드가 발견될 때까지 부모 클래스를 뒤진다는 점임ㅋㅋㅋㅋㅋㅋㅋㅋ
물론 완전히 똑같은 건 아니다. 왜냐하면  CSS에는 !important라는 마스터키가 있기 때문임.


### Forcing inheritance
상속되지 않는 속성을 상속받고 싶은 경우가 있을 수 있다. 예를 들면 link 태그의 경우인데, 이 태그는 기본적으로 활성화되는 경우(방문 전) 파란 색이다.

문제는 색상이 상속 가능한 속성임에도 불구하고 기본 속성이 적용되고 있다는 점이다. 우리는 이를 수정할 수 있음. 

```css
a {
  color: -webkit-link;
  cursor: pointer;
  text-decoration: underline;
}
```
기본적으로 위와 같이 되어 있음.
이것을 명시적으로

```css
a {
    color: inherit;
}
```
이렇게 표기하면 그 부모 태그의 스타일을 상속 받을 수 있다. 그 부모 태그가 p 태그라면 p 태그의 색상을 상속 받을 것임.

</br>
</br>
</br>
</br>

# The Cascade
두 명의 전사가 들어오지만 한 명만 살아남습니다...
누가 살아남는가? 그것은... ID > CLASS > TAG 
클래스는 태그보다 Specificity 하고, ID는 클래스보다 더 구체적임.

JS의 오퍼레이터를 생각해보자. 그러면 이해가 끝난다. (대박)
```javascript
const tagStyles = {
  fontWeight: 'bold',
  color: 'hsl(0deg 0% 10%)',
};
const classStyles = {
  color: 'violet',
}
const appliedStyles = {
  ...tagStyles,
  ...classStyles,
}
```
이해 완...

</br>
</br>
</br>
</br>

# Directions
block direction => vertical
inline direction => horizontal
블록 방향은 레고와 같고, 인라인 방향은 줄 서있는 사람들과 같다.

### Logical property
```css
p {
  display: block;
  margin-block-start: 1em;
  margin-block-end: 1em;
  margin-inline-start: 0px;
  margin-inline-end: 0px;
}
```

margin-block은 수평축을 말한다. 그러니까 margin-block-start는 블록 엘리먼트가 top to bottom으로 쌓여있을 때 시작을 의미함. 그러므로 margin-linine-start는 단어들이 왼쪽에서 오른쪽으로 놓여있을 때 시작을 의미한다. 

이것이 중요한 이유는 모든 언어가 왼쪽에서 오른쪽으로 전개되는 것이 아니기 때문임. 이건 내가 지난 주에 했던 고민과 정확히... 일치하네...


</br>
</br>
</br>
</br>

# The Box Model
박스 모델은  CSS 렌더링의 중요한 부분이기 때문에 정확하게 알아야 함. 

박스 모델을 구성하는 4가지 측면은 다음과 같음.

1. Content
2. Padding
3. Border
4. Margin

이 측면에 대한 비유가 엄청나다...

> box-sizing
> 
> 이 속성이 사이즈를 계산하는 룰을 변경한다. 기본값은 content-box인데, 이건 내부의 content만 고려한다. 반대로 border-box는 훨씬 더 직관적으로 동작한다.

그래서 이것이... 사실상 표준이다...
```css
*::before,
*::after {
  box-sizing: border-box;
}
```

</br>
</br>

## Padding
패딩은 내부 공간이다. 따라서 패딩이 있는 박스에 색을 채우면 패딩 색도 바뀐다. 

다른 건 익숙한데, 이게 인상적임
```css
/* The same thing, but using ✨ logical properties ✨ */
.asymmetric-logical-padding {
  padding-block-start: 20px;
  padding-block-end: 40px;
  padding-inline-start: 60px;
  padding-inline-end: 80px;
  ```
  ### Units
  개발자들은 패딩의 단위로 픽셀 쓰는 것을 좀 꺼리는데, 접근성이 떨어진다고 생각해서. 하지만 오히려 적합하다.
  
  타이포그래피의 vertical line 같은 것을 맞출 때를 생각해보면 된다. 굉장히 명시적인 단위라서, 지난 번에 브라우저에서 폰트 사이즈를 변경하는 두 가지 방법에 영향받지 않음. 그냥 언제나 32px이거나, 그 비율을 유지한다. 

  패딩에 백분율을 사용하는 것은 일반적으로 별로인데, 예외의 경우가 있다. 패딩 사이즈를 백분율로 지정해서 특정 비율을 유지하는 것임. 이건 모듈 6에서...!


</br>
</br>

## Border
세 가지 속성이 있음(width, style, color). 필수 값은 스타일이다. 이게 없으면 아예 모양이 그려지지 않음. 스타일만 집어넣었을 때의 기본값은 a black, 3px-thick borde이다. 

테두리 색상을 지정하지 않으면 기본적으로 글꼴 색상이 지정된다. 이걸 명시적으로 지정하는 방법은 currentColor 키워드를 쓰는 것임! 

### border-radius
이건... 백분율의 경우, 50%를 주면 원으로 만들 수 있다. 왜냐하면, 각 모서리의 반지름이 각 border 길이의 50%이기 때문이다. 

### outline vs border
아웃라인은 레이아웃에 영향을 주지 않는다. 이건 그냥 장식임. 쉐도우와 비슷.

### outline: none;
이렇게 설정하면 포커스 기능을 없애버릴 수도 있음. 그래서 일종의 대안을... 줘야 함. 

```css
button {
  outline: none;
}
button:focus {
  background: navy;
  color: white;
}
```

</br>
</br>

## Margin
마진은 가장 확실한 형태가 없는 요소라... 미스테리임. 부모 엘리먼트 바깥으로 엘리먼트를 잡아당기거나, 컨테이너 안에 중간에 위치하도록 하는 등...?(애매하군...)의 일을 가능하게 함. 

패딩과 보더는 양수만 가능하다. 하지만 마진은 음수도 가능함. 이걸 negative margin이라고 함.

```css
main {
  width: 200px;
  height: 200px;
  border: 3px solid;
  color: brown;
}

.pink-box {
  width: 50%;
  height: 50%;
  border: 3px solid deeppink;
  background: white;
  margin-bottom: -32px;
}

.neighbor {
  width: 50%;
  height: 50%;
  background: silver;
  margin-left: 16px;
}
```
이게 뭔 소리인가 싶었는데, 그러니까 원래대로라면 위 css에 해당하는 html이 아래와 같을 때,
```html
<main>
  <div class="pink-box"></div>
  <div class="neighbor"></div>
</main>
```
얘네는 네거티브 마진이 아니었다면 저렇게 겹쳐질 수가 없음. 그런데 명시적으로 핑크 박스의 마진을 네거티브로 만들어버렸고, 덕분에 겹쳐질 수 있음. 또 마진을 변경한다는 것은 선택한 요소의 위치를 바꾸는 것으로 생각하기 쉬운데, 그보다 접근법을 바꿔서 요소 간의 간격을 바꾸는 것임.

그리고 당연히 이 모든 엘리먼트들은 서로 위치 의존 상태이기 때문에 하나의 엘리먼트 위치값이 변경되면 나머지 엘리먼트는 변경된 관계를 가질 수밖에 없음...! 이렇게는 생각 안 해봤는데... 좋군.

</br>
</br>

### auto
마진 오토 속성은 기본적으로 사용 가능한 최댓값을 채우려고 한다. 따라서 좌우 마진을 모두 오토로 설정하면 각자 최댓값을 가지려고 하기 때문에 똑같은 값을 가지게 된다. 비기는 것임. 즉 우리는 좋은 부산물을ㅋㅋㅋㅋㅋㅋㅋㅋㅋ 거저 얻는 것임. 

주의사항이 있다면 이것은 폭 요소에 한해서 동작한다. 또, 너비가 명시적인 경우 오토 사용 가능. 

</br>
</br>
</br>

# Flow Layout
## Width Algorithms
## Height Algorithms
> Our section sits inside the <body> tag, and so when we set a percentage-based height or min-height, the percentage is based on that parent height. <body> doesn't have a specific height set, which means it uses the default behaviour: stay as short as possible, while still containing all the children.
> In other words, we have an impossible condition: we're telling the <section> to be a percentage of the <body>, and the <body> wants to base its size off of the <section>. They're both looking to each other for guidance.
> This is a really common source of confusion. It isn't fixed by Flexbox or Grid, either; those tools help us control the contents of a container, but that container still needs to get its height from somewhere!

여기에 답이 있음.
