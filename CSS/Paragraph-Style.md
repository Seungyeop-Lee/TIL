# 문단 스타일

- 문단과 관련된 스타일에 대해 정리한다.

## `direction` 속성

- 텍스트의 쓰기 방향을 지정하는 속성이다.
- 기본형은 `direction: ltr | rtl;`이다.

```css
direction: rtl;
```

속성값 | 설명
------|------
ltr | left-to-right. 기본값
rtl | right-to-left

## `text-align` 속성

- 텍스트의 정렬 방식을 지정하는 속성이다.
- 기본형은 `text-align: start | end | left | right | center | justify | match-parent;`이다.

```css
text-align: center;
```

속성값 | 설명
------|------
start | 텍스트의 시작 위치에 맞추어 정렬. `direction`속성 값에 따라 방향이 가변적
end | 텍스트의 끝 위치에 맞추어 정렬. `direction`속성 값에 따라 방향이 가변적
left | 왼쪽 정렬
right | 오른쪽 정렬
center | 중앙 정렬
justify | 영역의 양쪽 끝에 맞추어 정렬
match-parent | 부모 요소의 정렬 방식과 동일 정렬 방식 사용

## `text-justify` 속성

- 양쪽 끝에 맞추어 정렬 시, 공백의 정도를 지정하는 속성이다.
- `text-align`의 속성값이 justify인 경우 사용한다.
- 기본형은 `text-justify: auto | none | inter-word | distribute;`

```css
text-justify: auto;
```

속성값 | 설명
------|------
auto | 브라우저에서 자동 지정
none | 정렬하지 않음을 지정
inter-word | 단어 사이의 공백을 조절하여 정렬
distribute | 인접한 글자 사이의 공백을 똑같이 맞추어 정렬

## `text-indent` 속성

- 문단의 들어쓰기를 지정하는 속성이다.
- 기본형은 `text-indent: <크기> | <백분율>;`이다.

```css
text-indent: 3%;
```

속성값 | 설명
------|------
크기 | 단위와 함께 들여쓸 크기를 지정. 음수 지정시 내여쓰기
백분율 | 부모 요소의 너비를 기준으로하는 비율 지정.

## `line-height` 속성

- 줄 간격을 지정하는 속성이다.
- 기본형은 `line-height: normal | <숫자> | <크기> | <백분율> | inherit;`이다.

```css
line-height: 2;
```

속성값 | 설명
------|------
normal | 브라우저의 기본값을 사용
숫자 | 글자크기의 몇 배수에 해당하는 크기의 간격을 설정 할지 지정
크기 | 단위와 함께 크기를 지정
백분율 | 글자크기를 기준으로하는 비율 지정
inherit | 부모 요소의 설정값을 상속

## `text-overflow` 속성

- 영역을 넘치는 텍스트에 대한 표시방법을 지정하는 속성이다.
- 아래의 조건이 만족하면 해당 속성을 사용한다.
  - `white-space`속성값이 nowrap 경우
  - `overflow`속성값이 hidden, scroll, auto일 경우
- 기본형은 `text-overflow: clip | ellipsis;`

```css
text-overflow: ellipsis;
```

속성값 | 설명
------|------
clip | 넘치는 텍스트를 잘라서 비표시. 기본값
ellipsis | 말 줄임표(...)로 잘린 텍스트의 존재를 표시

## 참고

- [Do it! HTML5+CSS3 웹 표준의 정석 <개정판>, 2017, 고경희](http://www.easyspub.co.kr/20_Menu/BookView/119/PUB)