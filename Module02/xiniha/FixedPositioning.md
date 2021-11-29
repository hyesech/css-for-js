# Fixed Positioning

- Fixed 포지셔닝은 Absolute 포지셔닝과 유사하지만, Containing Block으로 반드시 뷰포트만을 사용한다는 차이점이 있다.
  - 단, 상위 요소가 `transform`이나 `will-change: transform`을 사용할 경우, Absolute 포지셔닝처럼 작동함
- 이로 얻어지는 주된 장점은 스크롤과 상관없이 요소를 배치할 수 있다는 것이다.
- Absolute 포지셔닝에서 사용한 많은 트릭들이 Fixed 포지셔닝에도 동일하게 적용될 수 있음
