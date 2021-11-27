# Rendering Logic II

</br>

## Relative Positioning
Reletive Positioning의  가장 큰 특징은 항목이 중복될 수 있다는 점이다.
> 1. relative, absolute, fixed, or sticky
> 2. position 프로퍼티의 기본값은 static, initial이다. 

일단 relative 포지션은 아무 효과도 없는 것 같지만 다음 두 과지 효과를 기대할 수 있다.

1. 특정 차일드를 구속한다. 영향을 미친다.
2. 추가적인 css 사용이 가능하다. 

여기서 추가적인 css란 top, botton, left, right 를 말하는데, 이 요소들은 자연적인 위치에 대해 상대적이다.  레이아웃에 영향을 미치지 않고 오로지 혼자 이동할 수 있음. 

인라인 방식으로 작성되었을 때도 사용 가능하다.

</br>
</br>
</br>
</br>

## Absolute Positioning
이건 이런 것이다. 여태까지의 요소들은 관계 속에 있었는데, 특정 요소를 그런 관계를 완전히 무시하고 원하는 위치에 가져다 붙이는 것임. 따라서 이것은 relative와 달리 기준점이 스크린이다. 좌우 0px을 주면 얘는 스크린의 좌우에 붙는다. 

</br>
</br>

### Centering Trick

</br>
</br>
</br>
</br>

## Containing BLocks
HTML에서는 거의 대부분 Containing Block이라는 것이 있음. 

```html
<section class="container">
  <p>Hello World!</p>
</section>
```
이런 것임. p태그를 감싸고 있는 section이 있고 거기에 container 클래스가 붙어있는 식이다. container를 이용해서 하위 태그의 위치를 정하는 일종의 전략. absolute 요소는 거의 자기 마음대로 움직이는데... 부모 요소에 position: relative를 붙ㅇ버리면 자식 태그(ㄹㅇ 자기 멋대로)가 부모 요소의 위치값을 기준으로 자리한다. 원래 left:0, bottom:0 으로 설정한 absolute 요소는 그냥 스크린의 왼쪽 아래에 가서 붙는데, 상위 태그에 relative를 적용하는 순간 이 자식 요소는 상위 요소의 위치를 기준으로 상위 요소의 left:0, bottom:0 지점에 위치하게 된다. wowwwwwww

상위에 존재하는 부모 태그가 없는 경우, 상위 -> 상위를 찾다가 relative가 적용되어있는 상위 태그 기준으로...

반드시 relative일 필요는 없고... 어쨌든...
> It doesn't have to be relative, as seen here, but it has to use Positioned layout. absolute, fixed, and sticky will also work.

positioned layout이면 된다. absolute, fixed, sticky 그런 것들.

> The way to think about this: padding is used in Flow layout calculations, and absolute elements are taken out-of-flow. Those rules don't apply.

그리고 이 룰도 중요하다. padding은 플ㄹ우 레이아웃 계산임. 따라서 absolute의 케이스에서는 적용되지 않기 때문에 상위 태그의 Padding을 무시한 것.


</br>
</br>

### Containing Puzzle
```html
<div class="freeway">
  <div class="truck">🚛</div>
  <div class="taxi">🚕</div>
  <div class="helicopter">🚁</div>
</div>
```
```css
.freeway {
  position: absolute;
  height: 200px;
  top: 0px;
  bottom: 0px;
  margin-top: auto;
  margin-bottom: auto;
}
.truck {
  position: absolute;
  top: 0px;
  left: 50px;
}
.taxi {
  position: absolute;
  top: 50px;
  right: 100px;
}
.helicopter {
  position: absolute;
  top: -100px;
  left: 200px;
}
```

여기 음수 마진값에 대해 잘 모름. 
질문 필요

</br>
</br>

### Exercises



</br>
</br>
</br>
</br>

## Stacking Contexts
브라우저는 요소가 겹치는 경우 뭘 기준으로 어떤 요소를 상위에 둘지 결정하는가? 그건 레이아웃 모드에 따라 다름.

</br>
</br>

### z-index
사실 이걸 많이 쓰게 된다.
z인덱스의 숫자가 높을수록 좀 더 화면과 가깝다고 이해하면 된다. 

기본적으로 0이고, 여기에 숫자를 더할수록 계층화된다. 음수를 사용할 수도 있지만 비추임. 

</br>
</br>

### Managing z-index


</br>
</br>

### Portals
포탈은 리액트에서 적용했을 때 아예 body태그 하위로 빠져버려서 컨트롤이 어렵다. 아예 공통 모달을 만들 때는 어려울 게 없는데, 만약 그런 식의 모달을 여러 개 만들어야 하는 경우 굉장히 피곤해지기 시작. 이런 문제를 해결할 수 있는 방법은 없는지?


</br>
</br>
</br>
</br>

## Fixed Positioning



</br>
</br>
</br>
</br>

## Overflow
오버플로우를 처리하는 방법.

</br>
</br>

### Scroll
콘텐츠가 겹칠 것 같으면 스크롤...
x축과 y축 중 하나를 선택할 수 있다.

윈도우와 리눅스는 기본적으로 오버플로우 스크롤 발생 시 스크롤바를 노출시키는데 맥 os는 약간 다름.

</br>
</br>

### Auto
다른 예시로는 오토 옵션이 있음. 오버플로우 케이스의 대부분의 경우 권장된다. 자동임.

그러면 왜 스크롤을 사용하는 걸까?
최적화 전략과 관련이 있음. 굳이 필요하지 않은데 오버플로우를 설정할 필요는 없다. 

</br>
</br>

### Hidden
그리고 숨기기. 컨테이너의 경계 바깥으로 오버플로우되는 부분을 잘라낸다. 보통 텍스트를 자르거나, 장식적 요소를 위해 이렇게 한다. 

> 오버플로우가 특정 문제를 해결하기 위해 전략적으로 배치되는 경우.
> 이 페이지에서 메뉴를 열 때 수업 내용 부분을 잘라서 오버플로우 시킨다. 

오버플로우를 사용할 때는 왜 오버플로우를 사용했는지 적어두면 좋다. 분명히 까먹기 때문임. 이렇게!

```css
.wrapper {
  /*
    On mobile, we shift the lesson-content 300px to the right,
    off-screen. I want it to be truncated, so that we only see
    a sliver of the content when the menu is open.
  */
  overflow: hidden;
}
```


</br>
</br>

### Horizontal Overflow
white space는 단어나 컨텐츠, 블록의 줄바꿈 옵션을 지정한다. nowrap 속성을 지정하면 줄바꿈되지 않는다. 

</br>
</br>

### Positioned Layout
지금까지는 플로우 레이아웃 상에서의 오버플로우 속성을 이야기했다. 그렇다면 '흐름' 레이아웃이 아닌 positioned 레이아웃에서의 오버플로우는 어떻게 작동하는가? 

</br>
</br>

### Overflow and containing blocks
positioned 레이아웃의 특징이 영향을 미친다. 특정 블록 안에서(이 블록이 positioned layout인 경우) 오버플로우를 설정하더라도 의미가 없음. 

```html
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
위와 같은 경우, wrapper에 hidden을 설정했지만 box는 absolute이고, 따라서 wrapper가 선언된 태그에 속하지 않음. 따라서 무시한다. 이것을 해결하는 방법은 부모 요소에 relative 속성을 추가해서 명시적으로 지정해주는 것임. 

</br>
</br>

### Fixed positioning
위의 분홍색 박스를 absolute에서 fixed로 변경하면 어떻게 되나? 

상위 스크롤 막대가 사라지고 오버플로우가 디폴트 값으로 설정된 것처럼 상위 뷰 위치로 튀어나오게 된다. relative는 자식 속성을 귀속시킬 수 있지만 fixed와 같은 고정적인 속성의 경우는 DOM 구조 외부에 존재하는 initial containing block에 의해서만 제어된다. 따라서 일반 HTML 요소에는 fixed 된 자식 태그가 존재할 수 없음. 

</br>
</br>
</br>
</br>

## Sticky Positioning
가장 큰 차이점은 크기가 상대적인 요소에서 고정적인 요소로 변화한다는 것임. 

</br>
</br>

### Stays in their box
sticky 요소는 상위 태그를 벗어나지 않는다. wrapper가 있다면 이 속성은 wrapper 안쪽에서만 기능한다. 

</br>
</br>

### Offset
top:0 로 설정하는 경우 0으로 빈틈없이 붙고, 25 또는 -25px을 설정하는 경우 붙는 위치(정지점)가 변한다. 

</br>
</br>

### Not incorporeal
실재하지 않음. 보통 위치를 변경하면, 그 아래에 있는 블록이 칸을 채우기 위해 위로 붙는데, sticky를 적용하는 경우 마치 그 자리에 있는 것처럼 공간을 빼앗기지 않는다. 

</br>
</br>

### Exercises

</br>
</br>

### Troubleshooting
몇가지 sticky가 작동하지 않는 케이스
overflow가 있는 경우, 스크롤 가능한 요소에 작동한다.  
이상하게 sticky가 작동하지 않는다면 그건, 상위 요소가 overflow를 핸들링하고 있기 때문일 확률이 높다. 


</br>
</br>
</br>
</br>

## Hidden Content
React 개발자 입장에서 display:hidden은 리액트를 이용해 DOM을 제어하는 것보다 나은 선택일 수도 있다. 성능상 그렇고,  디스플레이로 숨김처리된 요소는 렌더링되지 않은 엘리먼트이므로 메모리를 소비하지 않는다. 

요소를 표시한 이후 바로 애니메이션을 적용해야 하는 경우에는 엘리먼트가 DOM에 존재하지만 보이지 않는 편이 낫다. 

</br>
</br>

### Visibility
visibility와 display의 가장 큰 차이점은 DOM에 존재하고, 공간을 차지하면서 보이지 않는 것임. 보통은 UI에 구멍나는 것을 좋아하지 않아서 잘 쓰이지는 않음. 


</br>
</br>

### Opacity
투명도 설정은 접근성 측면에서 좋지 않을 수도 있다. 다만 애니메이션과 관련되어 있으면 고려해볼만함. 이걸 이용해서 요소를 감추는 것은 좋은 선택이 아니다. 
> Buttons can still be clicked

> Text is still selectable

> Form elements can still be focused

> If we're not careful, we can introduce accessibility issues

</br>
</br>

### 요소를 숨기되 접근성을 가져가는 방식


</br>
</br>
</br>
</br>

## Workshop: Character Creator


