## Module 0. Fundamental Recap
+ CSS의 전문용어(Terminology)에 대한 개념도 알고 있을 것.

  + **Property** in CSS are the attributes you can specify values for, CSS의 값을 정의할 수 있는 속성
  + **Selector** 페이지에서 내가 원하는 타겟을 특정할 수 있는 기술어(descriptor)
  + **Rule** 'Style'이라고도 알려져 있으며, property를 정하고 선언하는 콜렉션. 여러 개의 rule이 모여 stylesheet를 만듦
  + **Unit** 측정할 수 있는 값, 예를 들어 px, %, em 등...
  + **Declaration** = property + value

<br/>

---

<br/>

### 1. **Media Query**
which allow us to apply different CSS in different scenarios. 
<br/>

``` CSS
@media (condition)
```   
+ media condition은 보통 screen의 사이즈 값이 들어간다. 이와 달리 font-size는 조건에 해당되지 않는다.
+ screen의 사이즈에 따라 보여지는 contentsdml rule을 달리 할 수 있다.

<br/>
<br/>
<br/>

### 2. **Selector**
selector target a specific tag or class

<br/>
<br/>
<br/>

### 3. **Pseudo-classes**
<br/>

``` CSS
:hover
```   
+ 자바스크립트의 `onMouseEnter` 또는 `onMouseLeave` events와 비슷하다.   
<br/>

``` CSS
:focus
```
+ interactive elements like buttons, links and form inputs.
HTML에서 상호작용하는 버튼, 링크, form의 inputs을 누르거나 tap 했을 때 생긴다.

> focus styles은 중요하다. pointer-style input device를 사용하지 않는 경우 매우 유용하다. focus style은 어느 페이지에 있는 지, 어떤 element를 선택했는 지 보여주기 때문에 `outline: none;` 과 같은 rule을 지양하는 것이 좋다.   

<br/>

``` CSS
:checked
```
+ input type의 checkboxes나 radio buttons을 채웠을 때 사용할 수 있는 속성

<br/>
<br/>
<br/>

### 4. **Pseudo-elements**
pseudo-class와 달리 **::** colon을 두 개 쓴다.
<br/>

```CSS
::place-holder
```
+ `<input>`에 있는 속성. HTML의 tag로 생성되는 게 아니기 때문에 *pseudo-elements*라고 부른다.
> *place-holder*는 label 대신으로 쓰이는 것이 아닌, `input`에 들어 갈 예제를 보여주는 용도로 쓰여야 한다.

<br/>

``` CSS
::before, ::after
```
+ element's content의 앞이나 뒤에 위치해서 숨겨진 `span`이라고 볼 수 있다.

<br/>
<br/>
<br/>

### 5. **Combinators**
여러 개의 *selectors*의 조합
<br/>

``` CSS
nav a 
```
+ nav와 a 사이에 한 칸의 space가 존재하며, 이를 후손선택자 : *descendent selector*라고 부른다. 아무리 깊게 존재해도 선택할 수 있다.

<br/>

```CSS
.main-list > li
```
+ `.main-list` 바로 밑에 있는 direct children, 자식만 선택한다.

<br/>
<br/>
<br/>

### 6. **Color**
대부분의 개발자들이 색을 선택할 때 쓰는 것이 `hex code, #FEDD47`과 같이 생긴 코드를 많이 사용하는데 이는 rgb를 코드로 나타낸 것이다. 이는 어떤 색상인지 대략적으로 유추하기가 힘든데, 그래서 추천하는 코드가 `hsl code`

<br/>

```CSS
.first-box {
  background-color: hsl(120deg 100% 50% / 0.75);
}
```
+ **h**는 '*Hue*'의 약자로 둥근 색상환 띠를 생각하면 된다. *0deg* 빨강색으로 시작해서 *360deg* 빨강색으로 이어진다. 각도에 따라 대략적인 색상을 유추해볼 수 있다.
+ **s**는 '*Saturation*'으로 채도. %(퍼센트)로 값을 정하고 그 값이 100%에 가까울수록 채도가 높아 원색에 가깝다.
+ **l**은 '*Lightness*', 명도. 채도와 마찬가지로 %(퍼센트)로 값을 정하고 그 값이 100%의 가까울수록 명도가 높아 흰색에 가깝다.
+ `hsl code`에서 투명도를 설정할 때는 '/' 뒤에 값을 적으며 0부터 1 사이의 숫자를 쓴다.

<br/>
<br/>
<br/>

### 7. **Unit** 
크기(size)와 관련된 가장 많이 쓰이는 unit은 *pixel*이다. pixel(px)은 대부분의 경우, 어떤 size의 screen에서도 디자인이 무너질 가능성이 가장 적은 unit이다. 예외의 경우는 **Typography**

<br/>

#### 7.1. **Ems**
+ 해당 rule의 font-size에 따라 상대적으로 값이 정해진다.
  + 예를 들어 `p { font-size: 18px }`이면 `1em`은 `18px`이다.

<br/>

#### 7.2. **Rems**
+ `em`과 비슷해보이지만, 결정적으로 다른 한 가지는 *rem*은 항상 `<html>` tag를 기준으로 해서 그 상대적인 값이 달라진다.
  + 기본적으로 `<html>` tag는 font-size가 `16px`이라서 `1rem`은 `16px`과 같다.
+ 어떤 DOM tree와 관련이 있는 지와 관계없이 `rem`은 고정된다.
> You should not actually set a `px` font-size on `html` tag.   
> `font-size`를 `px`로 고정할 경우, 이는 사용자가 선택한 폰트의 기본 사이즈를 무시한다.

<br/>

#### 7.3. **Percentages**
+ `width/height`에 주로 사용하며, 부모요소에 비례하여 그만큼의 공간을 차지한다.

<br/>
<br/>
<br/>

### 8. **Typography**
<br/>

#### 8.1. **font-family**
+ 여러 글꼴의 집합체. 예를 들어 `Roboto` 글꼴은 12개 집합을 가지는데 6개는 폰트의 굵기(font-weight)에 따라, 그리고 2개의 종류(nomal, italic)를 가진다.
+ 대표적인 글꼴로 `serif, sans-serif, Monospace`가 있다.
  + `serif`는 글자 가장자리에 획이 있으며, 웹상에서보다 프린트물에서 많이 쓰인다.

<br/>

```CSS
body {
  font-family: 'Roboto', sans-serif;
}
```
+ 웹 글꼴 사용시 앞, 뒤를 따옴표로 둘러싸며, 브라우저가 앞에 위치한 글꼴을 사용할 수 없을 때 그 뒤에 있는 글꼴을 사용할 수 있도록 다중 값을 전달한다.(font-stack)

<br/>

#### 8.2. **Typical text formatting**
+ **Bold text** : 폰트의 굵기(font-weight)의 속성이며 1부터 1000까지의 숫자로 표현할 수 있다. 기본 값은 400이며 **bold**를 대체할 수 있는 값은 700이다.

+ **Italic text** : 대화를 할 때 강조하는 동작을 하듯, 웹의 문서에서 강조하고 싶을 때 텍스트에 각도를 준다. *bold text*와 비슷하다.
+ **Underlined text** : 웹에서는 보통 `link`의 의미를 가진다. 그렇기 때문에 시각적인 효과를 주기 위해서 underlined을 쓰는 것은 지양해야 한다.
  + 한편 `navigation`은 사용자가 이것이 누를 수 있다(click)것을 인지하고 있기 때문에 underlined을 쓰지 않아도 되며, 아래와 같이 CSS에서 제거할 수 있다.
  ``` CSS
  a {text-decoration: none}
  ```

<br/>

#### 8.3. **Alignment**
+ 글자들을 수평적으로 줄을 맞출 때 사용한다.
```CSS
p.left {
  text-align: left;
}

p.center {
  text-align: center;
}

p.right {
  text-align: right;
}
```

<br/>

#### 8.4. **Text-transform**
```CSS
/* RENDER WITH ALL CAPS */
text-transform: uppercase;

/* Capitalize The First Letter Of Every Word */
text-transform: capitalize;
```
+ `HTML`에서 text-transform 하는 것보다 `CSS`에서 처리하면, 이를 수정해야 할 때 한 번에 수정할 수 있다.

<br/>

#### 8.5. **Spacing**
+ `letter-spacing` : 각 글자 간의 수평 간격을 조정
+ `line-height` : 각 글자 간의 수직 거리를 조정
  + 대부분의 경우 `unit`을 사용하지 않고 숫자만으로 표현
  > The minimum recommended value is **1.5**

<br/>
<br/>
<br/>

### 9. **Debugging in the Browser**
+ 브라우저에서 오른쪽 마우스를 클릭하고 'Inspect element'를 누르면 사용할 수 있다.
+ 단축키
  + Mac에서는 `Command` + `Option` + `I`
  + Window나 Linux에서는 `Control` + `Shift` +`I`
