# 다단 편집관련 속성

- 신문의 인쇄 방식과 같은 다단 텍스트를 표현하는 것과 관련한 속성을 정리한다.

## `column-width`속성

- 요소 내 단을 나누고, 단의 폭을 지정 할 때 사용한다.
- 기본형은 `column-width: <크기> | auto;`이다.

속성값 | 설명
------|------
크기 | 단을 나누고, 폭을 직접 지정
auto | 단을 나누고, `column-count`등의 다른 속성에 따라 자동으로 폭이 계산 됨

## `column-count`속성

- 요소 내 단을 나누고, 단의 개수를 지정 할 때 사용한다.
- 기본형은 `column-count: <숫자> | auto;`이다.

속성값 | 설명
------|------
숫자 | 지정한 갯수만큼 단을 나눔
auto | `column-width`등의 다른 속성에 따라 자동으로 단의 갯수를 계산 후 단을 나눔

## `column-gap`속성

- 단과 단 사이의 여백을 지정 할 때 사용한다.
- 기본형은 `column-gap: <크기> | normal;`

속성값 | 설명
------|------
크기 | 여백을 직접 지정
normal | 여백을 자동으로 지정. W3C의 권장여백은 1em

## `column-rule`속성

- 단과 단 사이의 구분선을 지정 할 때 사용한다.
- 기본형은 `column-rule: <너비> | <스타일> | <색상>;`이다.
- 너비, 스타일, 색상은 각각 다른 속성을 이용하여 정의하는 것도 가능하다.
  - `column-rule-width: <크기> | thin | medium | thick;`
  - `column-rule-style: none | hidden | dotted | dashed | solid | double | groove | ridge;` 
  - `column-rule-color: <색상>;`

### `column-rule-width`속성

- 단과 단 사이, 구분선의 두께를 지정 할 때 사용한다.

속성값 | 설명
------|------
크기 | 길이를 단위가 있는 값으로 지정
thin | 얇은 두께
medium | 보통 두께
thick | 두꺼운 두께

### `column-rule-style`속성

- 단과 단 사이, 구분선의 스타일을 지정 할 때 사용한다.

속성값 | 설명
------|------
none | 구분선이 나타나지 않음. 기본값
hidden | 구분선이 나타나지 않음
dotted | 점선으로 구분선 표시
dashed | 짧은 선으로 구분선 표시(실선과 점선의 중간쯤의 간격)
solid | 실선으로 구분선 표시
double | 이중선으로 구분선 표시
groove | 구분선을 홈이 파인듯 표시
ridge | 구분선이 튀어나온듯 표시

### `column-rule-color`속성

- 단과 단 사이, 구분선의 색을 지정 할 때 사용한다.
- 속성값은 웹 페이지에서 사용하는 색을 나타내는 방법 전부 사용 가능 하다.

## `break-after`, `break-before`, `break-inside`속성

- 단의 시작 위치 등을 지정 할 때 사용한다.
- 각 속성은 위치를 나타낸다.
  - `break-after`는 해당 요소 이후를 가리킨다.
  - `break-before`는 해당 요소 이전을 가리킨다.
  - `break-inside`는 해당 요소의 내부를 가리킨다.

속성값 | 설명
------|------
column | 지정된 위치부터 새로운 단으로 시작
avoid-column | 지정된 위치부터 새로운 단이 시작되는 것을 막음

## `column-span`속성

- 다단 표시 부분 중, 흐름상 여러단을 하나의 단으로 묶어야 할 경우 사용한다.
- 기본형은 `column-span: 1 | all;`이다.

속성값 | 설명
------|------
1 | 단을 하나만 합치는 것이므로 합치지 않은것과 같음. 기본값
all | 모든 단을 하나로 합침

## 참고

- [Do it! HTML5+CSS3 웹 표준의 정석 <개정판>, 2017, 고경희](http://www.easyspub.co.kr/20_Menu/BookView/119/PUB)