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
