# 애니메이션

- CSS에서 애니메이션 효과를 주는 방법에 관련한 내용을 정리한다.

## CSS에서의 애니메이션 정의 방법

1. `@keyframes`속성에 애니메이션 내용을 정의한다.
   - 애니메이션의 처음, 중간, 끝의 스타일 정의
2. 애니메이션을 적용할 요소에 `animation-name`속성값과 `@keyframes`의 이름을 일치시킨다.
3. 대상 요소에 애니메이션의 시간, 방향, 반복, 실행 속도를 정의하는 각각의 속성을 정의한다.
   - 애니메이션의 시간: `animation-duration`
   - 애니메이션의 방향: `animation-direction`
   - 애니메이션의 반복: `animation-iteration-count`
   - 애니메이션의 실행 속도: `animation-timing-function`

## `@keyframes`속성

- 애니메이션의 처음, 중간, 끝의 각각이 타이밍에 어떠한 스타일을 적용 할 지 정의 할 때 사용한다.
- 기본형은 `@keyframes <이름> { <선택자> { <스타일> }};`이다.

구성 요소 | 설명
---------|------
이름 | `@keyframes`의 이름을 지정. `animation-name`에서 속성값으로 사용하면 해당 애니메이션이 적용됨
선택자 | 스타일이 변하는 지점을 나타냄. 애니메이션의 처음을 0%, 끝을 100%로 원하는 타이밍을 설정 가능. 처음과 끝만 있을 경우, 각각 from과 to로 지정가능
스타일 | 선택자에 해당하는 타이밍에 나타낼 스타일을 정의

## `animation-name`속성

- 요소에 적용 할 애니메이션을 연결 시킬 때 사용한다.
- 기본형은 `animation-name: <@keyframes 이름> | none;`이다.

속성값 | 설명
------|------
@keyframes 이름 | 연결 할 `@keyframes`속성의 이름을 지정
none | 애니메이션을 연결 시키지 않음. 기본값

## `animation-duration`속성

- 애니메이션의 실행 시간을 지정하고 싶을 때 사용한다.
- 기본형은 `animation-duration: <시간>;`이다.
- 시간으로 설정 할 수 있는 속성값은 초(s), 밀리초(ms)이다.
- 기본값은 0이다.

## `animation-direction`속성

- 애니메이션 실행 종료 후 움직임을 지정하고 싶을 때 사용한다.
- 기본형은 `animation-direction: normal | alternate;`이다.

속성값 | 설명
------|------
normal | 애니메이션 실행 종료 후 바로 처음 상태로 돌아간다. 기본값
alternate | 애니메이션 실행 종료 후 역순으로 애니메이션을 실행하여 처음 상태로 돌아간다.

## `animation-iteration-count`속성

- 애니메이션 실행 반복 횟수를 지정하고 싶을 때 사용한다.
- 기본형은 `animation-iteration-count: <숫자> | infinite;`이다.

속성값 | 설명
------|------
숫자 | 숫자 만큼 반복하여 실행. 기본값은 1
infinite | 무한히 반복하여 실행

## `animation-timing-function`속성

- 애니메이션의 속도 곡선을 지정 할 때 사용한다.
- 기본형은 `animation-timing-function: linear | ease | ease-in | ease-out | ease-in-out | cubic-bezier(x1,y1,x2,y2);`이다.

속성값 | 설명
------|------
linear | 시작부터 끝까지 동일 속도
ease | 처음에는 느리게, 중간은 빠르게, 마지막은 느리게. 기본값
ease-in | 시작은 느리게
ease-out | 마지막을 느리게
ease-in-out | 시작부터 마지막까지 느리게(표현하기 애매...)
cubic-bezier(x1,y1,x2,y2) | Cubic Bezier curve를 이용한 속도 곡선지정. x1과 x2는 0과 1사이의 실수를 가져야 함

## `animation`속성

- 애니메이션 속성을 한꺼번에 설정하고 싶을 때 사용한다.
- 기본형은 `animation: [<animation-name 값>] [<animation-duration 값>] [<animation-timing-function 값>] [<transition-delay 값>] [<animation-iteration-count 값>] [animation-direction 값]];`이다.
- 각 값은 띄어쓰기로 구분하며, 생략 할 경우 각 각 속성의 기본값이 적용된다.
- `animation-duration`속성의 기본값은 0이기 때문에 생략 할 경우, 애니메이션 효과를 볼 수 없다.

## 참고

- [Do it! HTML5+CSS3 웹 표준의 정석 <개정판>, 2017, 고경희](http://www.easyspub.co.kr/20_Menu/BookView/119/PUB)