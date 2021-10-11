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


