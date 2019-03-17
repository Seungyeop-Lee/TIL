# 요소 변형과 관련된 속성

- 요소 변형과 관련된 속성, 특히 3차원 변형과 관련된 속성에 대해 정리한다.

## `transform-origin`속성

- 변형의 기준점을 각 방향의 축이 아닌 부분으로 지정하고 싶은 경우 사용한다.
- 기본형은 `transform-origin: <x축> <y축> <z축> | initial | inherit;`이다.

속성값 종류 | 사용가능 속성값
-----------|---------------
x축 | 길이값, 백분율, left, center, right
y축 | 길이값, 백분율, top, center, bottom
z축 | 길이값

## `perspective`속성

- 2차원 평면에서 사용자의 방향 또는 반대 방향으로 잡아당기거나 밀어내어 원근감을 갖게하고 싶을 때 사용한다.
- 3차원 변형을 사용 할때 같이 사용하는 속성이다.
- 기본형은 `perspective: <크기> | none;`이다.

속성값 | 설명
------|------
크기 | 픽셀 크기로 지정. 0보다 큰 값을 지니며, 클수록 사용자로 부터 멀어짐
none | perspective를 지정하지 않음. 기본값

## `perspective-origin`속성

- 원근감 설정의 기준점을 각 방향의 축이 아닌 부분을 설정하고 싶을 경우 사용한다.
- `perspective`속성과 같이 사용하여야 한다.
- 기본형은 `perspective-origin: <x축 값> | <y축 값>;`이다.

속성값 종류 | 사용가능 속성값 | 초기값
-----------|---------------|--------
x축 값 | 길이의 값, 백분율, left, right, center | 50%
y축 값 | 길이의 값, 백분율, top, bottom, center | 50%

## `transform-style`속성

- 계층 형태에서 각 층마다 3D 변형을 설정하였을 경우, 하위 요소의 3D 변형 적용 유무를 설정하고 싶을 때 사용한다.
- 기본형은 `transform-style: flat | preserve-3d;`이다.

속성값 | 설명
------|------
flat | 하위 요소의 3D 변형을 허용하지 않음
preserve-3d | 하위 요소의 3D 변형을 허용

## `backface-visibility`속성

- 요소가 90도 이상 회전하여 뒷면이 앞으로 오는 경우, 표시 유무를 설정하고 싶을 때 사용한다.
- 기본형은 `backface-visibility: visible | hidden;`이다.

속성값 | 설명
------|------
visible | 뒷면을 표시. 기본값
hidden | 뒷면을 표시하지 않음

## 참고

- [Do it! HTML5+CSS3 웹 표준의 정석 <개정판>, 2017, 고경희](http://www.easyspub.co.kr/20_Menu/BookView/119/PUB)