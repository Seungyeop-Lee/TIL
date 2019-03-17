# 트랜지션

- 단순 변형을 넘어 하나의 스타일에서 다른 스타일로 바꾸는 것을 의미한다.
- 스타일이 바뀌는 시간을 지정하면 애니메이션 효과를 내는 것도 가능하다.
- 요소에 트랜지션을 적용시키는 방법에 대해 정리한다.

## `transition-property`속성

- 트렌지션을 적용 할 속성을 지정 할 때 사용한다.
- 기본형은 `transition-property: all | none | <속성 이름>;`이다.

속성값 | 설명
------|------
all | 요소의 모든 속성을 대상으로 지정. `transition-property`속성을 생략 할 경우에도 이 속성값이 적용 됨
none | 트랜지션 동안 아무런 속성도 바뀌지 않음
속성 이름 | 트랜지션 효과를 적용 할 속성을 지정. 2개 이상의 속성을 지정 할 경우 콤마(,)로 구분

## `transition-duration`속성

- 트렌지션의 진행시간을 지정 할 때 사용한다.
- 기본형은 `transition-duration: <시간>;`이다.
- 속성값의 단위는 초(s), 밀리초(ms)이다.
- 대상 속성이 2개 이상일 경우, `transition-property`속성내 속성값 선언 순서에 맞춰서 시간을 나열한다. (콤마(,)로 구분)
- 대상 속성의 갯수에 비해, 속성값의 갯수가 적을 경우 설정 한 시간을 돌아가면서 적용한다.
  - 대상 속성이 A, B, C, D, E이고, 설정 시간이 2s, 1s일 경우
  - A: 2s, B: 1s, C: 2s, D: 1s, E: 2s가 설정
- 기본값은 0s이다.

## `transition-timing-function`속성

- 트렌지션의 속도 곡선을 지정 할 때 사용한다.
- 기본형은 `transition-timing-function: linear | ease | ease-in | ease-out | ease-in-out | cubic-bezier(x1,y1,x2,y2);`이다.

속성값 | 설명
------|------
linear | 시작부터 끝까지 동일 속도
ease | 처음에는 느리게, 중간은 빠르게, 마지막은 느리게. 기본값
ease-in | 시작은 느리게
ease-out | 마지막을 느리게
ease-in-out | 시작부터 마지막까지 느리게(표현하기 애매...)
cubic-bezier(x1,y1,x2,y2) | Cubic Bezier curve를 이용한 속도 곡선지정. x1과 x2는 0과 1사이의 실수를 가져야 함

## `transition-delay`속성

- 트렌지션의 지연 시간을 설정 하고 싶을 때 사용한다.
- 기본형은 `transition-delay: <시간>;`이다.
- 기본값은 0s이다.

## `trasition`속성

- 트렌지션 속성을 한꺼번에 설정하고 싶을 때 사용한다.
- 기본형은 `transition: [<transition-property 값>] [<transition-duration 값>] [<transition-timing-function 값>] [<transition-delay 값>];`이다.
- 각 값은 띄어쓰기로 구분하며, 생략 할 경우 각 각 속성의 기본값이 적용된다.
- 트랜지션 적용 대상이 전체이며, 트렌지션 실행 시간이 동일하다면 한번에 지정하는 것이 효과적이다.

## 참고

- [Do it! HTML5+CSS3 웹 표준의 정석 <개정판>, 2017, 고경희](http://www.easyspub.co.kr/20_Menu/BookView/119/PUB)
- [w3schools.com > CSS cubic-bezier() Function](https://www.w3schools.com/cssref/func_cubic-bezier.asp)