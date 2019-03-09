# 여백 조절 관련 속성

- 박스 모델의 여백(패딩, 마진)과 관련된 속성에 대해 정리한다.

## `margin` 속성

- 마진(margin)의 크기를 설정 할 때 사용한다.
- 마진이란 테두리와 다른 요소 사이의 영역을 뜻한다.
- 기본형은 `margin[-방향]: <크기> | <백분율> | auto;`이다.
- 방향은 top, right, bottom, left가 올 수 있으며, 생략 할 경우 모든 방향에 대해 적용된다.
- 한번에 각 방향에 대한 설정도 가능하다.
  - `margin: top마진 right마진 bottom마진 left마진;`
  - `margin: top/bottom마진 left/right마진;`

속성값 | 설명
------|------
크기 | 길이를 단위가 있는 값으로 지정
백분율 | 부모 요소를 기준으로 하는 비율로 지정
auto | `display`속성값에 지정한 값에 맞는 적절한 값을 자동으로 지정

## `padding` 속성

- 패딩(padding)의 크기를 설정 할 때 사용한다.
- 패딩이란 콘텐츠 영역과 테두리 사이의 영역을 뜻한다.
- 기본형은 `padding[-방향]: <크기> | <백분율> | auto;`이다.
- 방향은 top, right, bottom, left가 올 수 있으며, 생략 할 경우 모든 방향에 대해 적용된다.
- 한번에 각 방향에 대한 설정도 가능하다.
  - `padding: top패딩 right패딩 bottom패딩 left패딩;`
  - `padding: top/bottom패딩 left/right패딩;`

속성값 | 설명
------|------
크기 | 길이를 단위가 있는 값으로 지정
백분율 | 부모 요소를 기준으로 하는 비율로 지정
auto | `display`속성값에 지정한 값에 맞는 적절한 값을 자동으로 지정

## 참고

- [Do it! HTML5+CSS3 웹 표준의 정석 <개정판>, 2017, 고경희](http://www.easyspub.co.kr/20_Menu/BookView/119/PUB)