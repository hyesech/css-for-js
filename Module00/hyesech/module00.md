# Media Query
```css
/* CSS */
@media (condition) {
  /* Some CSS that'll run if the condition is met. */
}
```
JS의 분기와 비슷함. condition에 어떤 조건이 들어갈 것인지가 관건. 당연히 `font-size`와 같은 요소에는 미디어 쿼리가 적용되지 않는다.

보통 4분기 또는 3분기를 기본 적용하는 것으로 알고 있음.

- 4개의 반응형 분기점 
  - 낮은 해상도의 PC, 태블릿 가로 : ~1024px `(min-width:1024px)`
  - 태블릿 가로 : 768px ~ 1023px `(min-width:768px) and (max-width: 1023px)`
  - 모바일 가로, 태블릿 : 480px ~ 767px `(min-width:480px) and (max-width:767px)`
  - 모바일 : ~480px `(max-width:480px)`
  

- 3개의 반응형 분기점 
  - PC : 1024px ~ `(min-width:1024px)`
  - 태블릿 가로, 세로 : 768px ~ 1023px `(min-width:768px) and (min-width:1023px)`
  - 모바일 가로, 세로 : ~767px `(min-width:767px)`

> 헷갈리는 부분을 짚고 넘어가자면, `min-width`, `max-width`는 모두 **이상**과 **이하**다. **초과**나 **미만**이 아님. 따라서 위의 예시와 같이 실제로 작업을 할 때 픽셀이 겹치지 않도록 지정해야 한다. 


# Selector
여기서 재미있는 부분은 사실 CSS는 선택자 조합이 관건인데, 최근에는 이 선택자 조합을 툴에 의존하기 때문에 중요성이 줄어들고 있음. 어차피 컴파일 되기 때문에 선택자를 이용한 것과 다름없음.

### Pseudo-classes
JS로 이 기능을 구현하기 위해서는 별도로 이벤트 리스너 등을 달아야 한다. CSS로 구현하는 경우 일이 훨씬 쉬워짐.

### Pseudo-elements
:: 이렇게 표기하고 특정 대상이 아니라 대상의 하위 elements를 대상으로 한다. 즉 특정 대상의 상태값 변화에 대응하는 것보다 특정 대상의 하위 요소(더 디테일한 부분)에 접근할 수 있음. 그 중에서도 DOM을 제어하여 명시적으로 만들어주지 않은 elements를 대상으로 함.

### before and after
이게 가장 중요했음. 앞뒤에 뭔가를 추가한다고 보면 된다.
```css
<p>
  This paragraph has little arrows!
</p>
```
```css
<p>
  <span class="pseudo-pseudo">→ </span>
    This paragraph has little arrows!
  <span class="pseudo-pseudo"> ←</span>
</p>
```
첫 번째 html에 befor, after를 더하면 아래 html과 동일한 표현을 할 수 있다. 하지만 의미를 표현할 수는 없기 때문에 표현하고자 하는 대상이 완전히 장식적인 경우. 예를 들어 이미 버튼임이 명확한 상태일 때 어떤 모양을 더하고자 하는 경우에 유용하다.


### Combinators
선택자를 결합하는 경우.
```css
nav a {
}
```
위와 같이 사용하는 경우 실제 `nav`와 `a` 사이에 몇 가지 계층이 더 있더라도 관계없이 작동한다. 
```css
nav > a {
}
```
위와 같이 표현하는 경우 직접적인 child에 적용된다. 

