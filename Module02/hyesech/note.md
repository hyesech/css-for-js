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

</br>
</br>

### Managing z-index

</br>
</br>

### Portals



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

</br>
</br>

### Horizontal Overflow

</br>
</br>

### Positioned Layout



</br>
</br>
</br>
</br>

## Sticky Positioning

</br>
</br>

### Exercises

</br>
</br>

### Troubleshooting



</br>
</br>
</br>
</br>

## Hidden Content



</br>
</br>
</br>
</br>

## Workshop: Character Creator


