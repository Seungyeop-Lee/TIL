# 폼 태그

- `<form>`태그에 대해 정리한다.

## `<form>`

- 사용자가 웹 사이트로 정보를 보낼 때 사용하는 태그이다.
- `<form>`태그 내부에 폼 요소를 이용해 입력란이나 전송버튼 등을 위치시킬 수 있다.

### `<form>`태그의 속성

속성 | 설명
----|------
`method` | 데이터를 보낼 때의 전송 방식을 설정한다. `get`과 `post`를 지정 할 수있다. 기본값은 `get`
`name` | `<form>`태그에 이름을 설정한다. 동일 페이지에 여러 `<form>`태그가 존재할 시 구분을 위해 사용한다.
`action` | 데이터를 보낼 URI를 설정한다.
`target` | submit 후 응답 받은 내용을 어떤 창에 표시 할 지를 설정한다.<br>설정 가능한 값에 대한 정보는 [a-Tag](a-Tag.md#`target`속성)를 참조. 기본값은 `_self`
`autocomplete` | 자동완성기능 사용유무 설정. `on`과 `off`를 지정 할 수 있다. 기본값은 `on`

### `<label>`

- 폼 요소에 라벨을 붙여 연결시키는 것이 가능하다.
- 라벨을 붙일 경우, 라벨을 클릭해도 연결되 있는 폼 요소에 포커스가 설정된다.
- `<label>`태그를 사용하는 방법 (두 종류)
  - `<label>`태그로 폼 요소를 감싼다.
  - `<label>`태그의 `for`속성값과 연결시킬 폼 요소의 id를 일치시킨다.

### `<fieldset>`, `<legend>`

- 폼 내부의 구역을 나눌 때 사용된다.
- `<fieldset>`으로 구역을 설정하고, `<fieldset>`내부 최상단에 `<legend>`를 위치시켜 구역의 제목을 설정한다.

## 참고

- [Do it! HTML5+CSS3 웹 표준의 정석 <개정판>, 2017, 고경희](http://www.easyspub.co.kr/20_Menu/BookView/119/PUB)
- [w3schools.com > HTML \<form\> Tag](https://www.w3schools.com/tags/tag_form.asp)