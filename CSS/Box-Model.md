# CSS의 박스 모델

- 웹 페이지는 박스 모델로 이루어진 요소의 집합으로 레이아웃을 구성한다.
- 박스 모델과 관련된 내용을 정리한다.

## 블록 레벨 vs. 인라인 레벨 vs. 인라인 블록 레벨

- 웹 페이지를 구성하는 요소 중 대부분은 블록 레벨 요소이거나 인라인 레벨 요소이다.
- 블록 레벨의 속성과 인라인 레벨의 속성을 같이 가지고 있는 인라인 블록 레벨 요소도 있다.
  - 인라인 블록 레벨 요소는 display속성으로 설정해야 사용 가능

레벨 | 가로 폭 | 박스 모델 
----|---------|----------
블록 레벨 | 100% | O
인라인 레벨 | 내용의 길이 | X
인라인 블록 레벨 | 내용의 길이 | O

레벨 | 해당 태그
----|-----------
블록 레벨 태그 | `<p>`, `<h1>~<h6>`, `<ul>`, `<ol>`, `<div>`, `<blockquote>`, `<form>`, `<hr>`, `<table>`, `<fieldset>`, `<address>`
인라인 레벨 태그 | `<img>`, `<object>`, `<br>`, `<sub>`, `<sup>`, `<span>`, `<input>`, `<textarea>`, `<label>`, `<button>`

## 박스 모델

- 박스 형태를 가지고 있는 요소를 박스 모델이라고 한다.
- 박스 모델은 콘텐츠 영역, 패딩(padding), 테두리(border), 마진(margin)으로 이루어져 있다.

부분 | 설명
----|------
콘텐츠 영역 | 요소 안에 내용을 나타내는 영역
패딩 | 콘텐츠 영역과 테두리 사이의 영역
테두리 | 요소의 테두리 영역
마진 | 테두리와 다른 요소 사이의 영역

![박스 모델 그림](https://mdn.mozillademos.org/files/8685/boxmodel-(3).png)

> 박스모델 개략도 (출처: [CSS 기본 박스 모델 입문](https://developer.mozilla.org/ko/docs/Web/CSS/CSS_Box_Model/Introduction_to_the_CSS_box_model)
)

### `width`, `height`속성

- 박스 모델은 높이와 폭의 조정이 가능하다.

속성 | 설명
----|------
`width` | 콘텐츠 영역의 폭을 지정
`height` | 콘텐츠 영역의 높이를 지정

- width의 기본형은 `width: <크기> | <백분율> | auto;`이다.
- height의 기본형은 `height: <크기> | <백분율> | auto;`이다.

속성값 | 설명
------|------
크기 | 길이를 단위가 있는 값으로 지정
백분율 | 부모 요소를 기준으로 하는 비율로 지정
auto | 콘텐츠가 점유하고 있는 부분에 맞게 자동 조절. 기본값

- 실제 박스 모델의 길이
  - 콘텐츠 영역의 길이 + padding + border + margin

### `display`속성

- 요소가 화면에 어떻게 보여질지를 지정 할 때 사용한다.
- 기본적으로 가지고 있는 display속성과 다른 속성으로 변경하려 할 때 사용된다.
- 기본형은 `display: none | contents | block | inline | inline-block | table | table-cell 등;`이다.

자주 사용되는<br>속성값 | 설명
----------------------|------
block | 블록 레벨 요소로 지정
inline | 인라인 레벨 요소로 지정
inline-block | 인라인 블록 레벨 요소로 지정
none | 표시하지 않음(공간 점유를 하지 않음)

## 참고

- [Do it! HTML5+CSS3 웹 표준의 정석 <개정판>, 2017, 고경희](http://www.easyspub.co.kr/20_Menu/BookView/119/PUB)