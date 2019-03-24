# 플렉스 박스(Flex Box)

- 플렉스 박스와 관련된 내용을 정리한다.

## 플렉스 박스의 구성요소

![](https://developer.mozilla.org/files/3739/flex_terms.png)

> 플렉스 박스 개략도(출처: [MDN Web docs > CSS flexible box の利用](https://developer.mozilla.org/ja/docs/Web/CSS/CSS_Flexible_Box_Layout/Using_CSS_flexible_boxes))

구성요소 | 설명
--------|------
플렉스 컨테이너<br>Flex container | 플렉스 아이템을 담은 그릇
플렉스 아이템<br>Flex item | 플렉스 컨테이너에 포함된 요소
주축<br>Main axis | 플렉스 아이템을 배치하는 기본 방향
교차축<br>Cross axis | 주축과 교차하는 축

## 플렉스 박스의 레이아웃 기본 속성

### `display`속성

- 요소를 플렉스 컨테이너로 지정하기 위해 사용한다.
- 기본형은 `display: flex | inline-flex;`이다.
- 플렉스 컨테이너로 지정된 요소 내부의 자식 요소들은 자동적으로 플렉스 아이템이 된다.

속성값 | 설명
------|------
flex | 블럭 레벨 요소인 플렉스 컨테이너
inline-flex | 인라인 레벨 요소인 플렉스 컨테이너

### `flex-direction`속성

- 플렉스 아이템을 배치하는 기본 방향(주축)을 지정 할 때 사용한다.
- 기본형은 `flex-direction: row | row-inverse | column | column-inverse;`이다.

속성값 | 설명
------|------
row | 가로 순방향 (왼쪽 끝에서 오른쪽 끝으로)
row-inverse | 가로 역방향 (오른쪽 끝에서 왼쪽 끝으로)
column | 세로 순방향 (위에서 아래로)
column-inverse | 세로 역방향 (아래에서 위로)

### `flex-wrap`속성

- 플렉스 아이템이 화면을 넘어가는 경우의 표시방법을 지정 할 때 사용한다.
- 기본형은 `flex-wrap: no-wrap | wrap | wrap-reverse;`이다.

속성값 | 설명
------|------
no-wrap | 한 줄에 표시. 기본값
wrap | 여러 줄에 표시. 교차축 방향으로 배치
wrap-reverse | 여러 줄에 표시. 교차축의 방향과 반대 방향으로 배치

### `flex-flow`속성

- `flex-direction`속성과 `flex-wrap`속성을 한번에 지정 할 때 사용한다.
- 기본형은 `flex-flow: [<flex-direction 속성값>] [<flex-wrap 속성값>];`
- `<flex-direction 속성값>`이나 `<flex-wrap 속성값>`를 생략하는 것도 가능하다.
  - `<flex-direction 속성값>` 생략시 row로 설정
  - `<flex-wrap 속성값>` 생략시 no-wrap으로 설정

### `order`속성

- 플렉스 아이템의 순서를 임의로 지정 하고 싶을 때 사용한다.
- 기본형은 `order: 0 | 숫자;`이다.
- `order`속성은 순서를 지정 할 플렉스 아이템에 정의하여야 한다.

속성값 | 설명
------|------
`0` | 코드 순서대로 배치(코드 상 먼저 선언된 요소 부터 배치). 기본값
숫자 | 배치 순번. 숫자가 낮을 수록 앞에, 높을 수록 뒤에 배치

### `flex`속성

- 플렉스 아이템의 상대적 크기를 조절하고 싶을 때 사용한다.
- 플렉스 컨테이너의 크기에 맞춰 최소 비율과 최대 비율, 기본 비율을 지정하는 것이 가능하다.
- 기본형은 `flex: [<flex-grow> <flex-shrink> <flex-basis>] | <positive-number> | auto | initial | none;`이다.
- `flex`속성은 크기를 조절 할 플렉스 아이템에 정의하여야 한다.

속성값 | 설명
------|------
flex-grow | 너비를 늘릴 비율(최대 비율; 0 이상)을 지정
flex-shrink | 너비를 줄일 비율(최소 배율; 0 이상)을 지정
flex-basis | 기본 크기를 지정
positive-number | `flex: <positive-number> 1 0;`과 동일
auto | `flex: 1 1 auto;`와 동일
initial | `flex: 0 1 auto;`와 동일. 기본값
none | `flex: 0 0 auto;`와 동일

flex-basis 속성값 | 설명
---------------------|------
크기값 | 플렉스 아이템의 기본 폭을 단위가 있는 크기값(ex. px, em, rem)으로 지정
백분율 | 플렉스 컨테이너의 폭을 기준으로 하는 비율(%)을 지정
0 | flex-grow와 flex-basis의 값을 함께 사용
auto | 플렉스 아이템의 너비값을 사용

- flex-grow가 0인 경우
  - 컨테이너의 폭이 늘어나도 아이템의 폭이 늘어나지는 않음
- flex-shrink가 0인 경우
  - 컨테이너으 폭이 줄어들어도 아이템의 폭이 줄어들지 않음

## 플렉스 아이템 배치관련 속성

### `justify-content`속성

- 주축 기준으로의 배치방법을 지정하는 경우 사용한다.
- 기본형은 `justify-content: flex-start | flex-end | center | space-between | space-around;`이다.

속성값 | 설명
------|------
flex-start | 주축의 시작점부터 배치. 기본값
flex-end | 주축의 끝점부터 배치
center | 주축의 중앙을 기준으로 배치
space-between | 첫번째 항목을 주축의 시작점, 마지막 항목을 주축의 끝점에 배치 후, 나머지 항목을 같은 간격으로 사이에 배치
space-around | 모든 아이템을 같은 간격으로 배치(첫번째 항목과 마지막 항목도 시작점과 끝점 사이의 간격이 발생)

### `align-items`속성

- 교차축 기준으로의 배치방법을 지정하는 경우 사용한다.
- 플렉스 컨테이너에 정의하며, 해당 컨테이너에 포함되어있는 아이템에게 동일하게 적용된다.
- 기본형은 `align-items: stretch | flex-start | flex-end | center | baseline;`이다.

속성값 | 설명
------|------
stretch | 플렉스 아이템을 확장하여 교차축을 꽉 채움. 기본값
flex-start | 교차축의 시작점에 배치
flex-end | 교차축의 끝점에 배치
center | 교차축의 중앙을 기준으로 배치
baseline | 가장 높이가 큰 아이템을 시작점에 배치 후, 그 아이템의 기준선(중앙)과 다른 아이템의 기준선(중앙)을 일치시켜 배치

### `align-self`속성

- 교차축 기준으로의 배치방법을 지정하는 경우 사용한다.
- 플렉스 아이템에 정의하여, 해당 아이템에 한정된 배치의 정의가 가능하다.
- 기본형은 `align-self: auto | stretch | flex-start | flex-end | center | baseline;`이다.
- 속성값 중 auto를 제외하고는 전부 `align-items`속성의 속성값과 동일하다.

속성값 | 설명
------|------
auto | `align-items`속성값을 따름. 기본값

### `align-content`속성

- 여러 줄로 배치될 때의 배치방법을 지정하는 경우 사용한다.
- 기본형은 `align-content: flex-start | flex-end | center | space-between | space-around;`이다.

속성값 | 설명
------|------
flex-start | 교차축의 시작점부터 배치. 기본값
flex-end | 교차축의 끝점부터 배치
center | 교차축의 중앙을 기준으로 배치
space-between | 첫번째 항목을 교차축의 시작점, 마지막 항목을 교차축의 끝점에 배치 후, 나머지 항목을 같은 간격으로 사이에 배치
space-around | 모든 아이템을 같은 간격으로 배치(첫번째 항목과 마지막 항목도 시작점과 끝점 사이의 간격이 발생)

## 참고

- [Do it! HTML5+CSS3 웹 표준의 정석 <개정판>, 2017, 고경희](http://www.easyspub.co.kr/20_Menu/BookView/119/PUB)
- [MDN Web docs > flex](https://developer.mozilla.org/ja/docs/Web/CSS/flex)