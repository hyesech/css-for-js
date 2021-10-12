# Module 0. Fundamental Recap
+ CSS의 전문용어(Terminology)에 대한 개념도 알고 있을 것.

  + **Property** in CSS are the attributes you can specify values for, CSS의 값을 정의할 수 있는 속성
  + **Selector** 페이지에서 내가 원하는 타겟을 특정할 수 있는 기술어(descriptor)
  + **Rule** 'Style'이라고도 알려져 있으며, property를 정하고 선언하는 콜렉션. 여러 개의 rule이 모여 stylesheet를 만듦
  + **Unit** 측정할 수 있는 값, 예를 들어 px, %, em 등...
  + **Declaration** = property + value

<br/>

---

<br/>

### 1. **Media Query**, which allow us to apply different CSS in different scenarios. 
<br/>

``` CSS
@media (condition)
```   
+ media condition에 들어가는 조건은 보통 screen의 사이즈 값이 들어간다. font-size는 condition 조건에 해당되지 않는다.
+ screen의 사이즈에 따라 보여지는 contentsdml rule을 달리 할 수 있다.

<br/>
<br/>

### 2. **Selector**, selector target a specific tag or class

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

+ focus styles은 중요하다. pointer-style input device를 사용하지 않는 경우 매우 유용하다. focus style은 어느 페이지에 있는 지, 어떤 element를 선택했는 지 보여주기 때문에 
`outline: none;` 과 같은 rule을 지양하는 것이 좋다.   

<br/>

``` CSS
:checked
```
+ input type의 checkboxes나 radio buttons을 채웠을 때 사용할 수 있는 속성

<br/>
<br/>

### 4. **Pseudo-elements**, pseudo-class와 달리 **::** colon을 두 개 쓴다.
<br/>

```CSS
::place-holder
```
+ `<input>`에 있는 속성. HTML의 tag로 생성되는 게 아니기 때문에 *pseudo-elements*라고 부른다.
+ *place-holder*는 label 대신으로 쓰이는 것이 아닌, `input`에 들어 갈 예제를 보여주는 용도로 쓰여야 한다.

<br/>

``` CSS
::before, ::after
```
+ element's content의 앞이나 뒤에 위치해서 숨겨진 `span`이라고 볼 수 있다.

<br/>
<br/>

### 5. **Combinators**, 여러 개의 *selectors*의 조합
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

### 6. **Color**
+ 대부분의 개발자들이 색을 선택할 때 쓰는 것이 `hex code, #FEDD47`과 같이 생긴 코드를 많이 사용하는데 이는 rgb를 코드로 나타낸 것이다. 이는 어떤 색상인지 대략적으로 유추하기가 힘든데, 그래서 추천하는 코드가 `hsl code`

<br/>

```CSS
.first-box {
  background-color: hsl(120deg 100% 50% / 0.75);
}
```
+ **h**는 '*Hue*'의 약자로 둥근 색상환 띠를 생각하면 된다. *0deg* 빨강색으로 시작해서 *360deg* 빨강색으로 이어진다. 각도에 따라 대략적인 색상을 유추해볼 수 있다.
+ **s**는 '*Saturation*으로 채도. %(퍼센트)로 값을 정하고 그 값이 100%에 가까울수록 채도가 높아 원색에 가깝다.
+ **l**은 '*Lightness*, 명도. 채도와 마찬가지로 %(퍼센트)로 값을 정하고 그 값이 100%의 가까울수록 명도가 높아 흰색에 가깝다.
+ `hsl code`에서 투명도를 설정할 때는 '/' 뒤에 값을 적으며 0부터 1 사이의 숫자를 쓴다.



