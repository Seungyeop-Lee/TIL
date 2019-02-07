# 목록 생성 태그

- 목록을 만드는 태그를 정리한다.

## `<ul>`,`<li>`

- 순서가 없는 목록을 만들 때 사용한다.
- `<ul>`태그는 순서가 없는 목록 자체를 나타낸다.
- `<li>`태그는 목록에 속해있는 리스트 아이템을 나타내며, `<ul>`태그 내부에서 사용된다.
- `<ul>`태그 안의 `<li>`태그가 웹 페이지에 표현 될 때 불릿(ex: 원, 사각형 등)이 자동으로 붙는다.
- `<ul>`태그 안에 `<ul>`태그를 위치시킴으로서 계층적 리스트의 표현이 가능하다.

```html
<div>
  <ul>
    <li>A</li>
    <ul>
      <li>A-1</li>
      <li>A-2</li>
      <li>A-3</li>
    </ul>
    <li>B</li>
    <ul>
      <li>B-1</li>
    </ul>
    <li>C</li>
    <ul>
      <li>C-1</li>
      <li>C-2</li>
    </ul>
  </ul>
</div>
```

[예제코드 실행 결과(codepen)](https://codepen.io/seungyeop-lee/pen/wNrZJY)

## `<ol>`,`<li>`

- 순서가 있는 목록을 만들 때 사용한다.
- `<ol>`태그는 순서가 있는 목록 자체를 나타낸다.
- `<li>`태그는 목록에 속해있는 리스트 아이템을 나타내며, `<ul>`태그 내부에서 사용된다.
- `<ul>`태그 안의 `<li>`태그가 웹 페이지에 표현 될 때 순번이 자동으로 붙는다.

### `<ol>`태그의 속성

속성 | 설명
----|------
`type` | 값에 따라 순번을 나타내는 기호의 변경이 가능하다.<br>1: 숫자(기본값), a: 영문 소문자, A: 영문 대문자, i: 로마숫자 소문자, I: 로마숫자 대문자
`start` | 값으로 설정된 숫자부터 순번이 시작된다. 기본값은 1
`reversed` | 항목을 역순으로 표시한다. 속성의 값은 없다.

```html
<div>
  <ol>
    <li>A</li>
    <ol type="A">
      <li>A-1</li>
      <li>A-2</li>
      <li>A-3</li>
    </ol>
    <li>B</li>
    <ol start="3">
      <li>B-1</li>
    </ol>
    <li>C</li>
    <ol reversed>
      <li>C-1</li>
      <li>C-2</li>
    </ol>
  </ol>
</div>
```

[예제코드 실행 결과(codepen)](https://codepen.io/seungyeop-lee/pen/GzMLmd)

## `<dl>`,`<dt>`,`<dd>`

- 사전 형식(제목과 내용이 있는 형식)의 목록을 만들 때 사용한다.
- `<dl>`태그는 사전 형식의 목록 자체를 나타낸다.
- `<dt>`태그는 제목을 나타낸다.
- `<dd>`태그는 내용을 나타낸다.

```html
<div>
  <dl>
    <dt>첫번째 제목</dt>
    <dd>첫째</dd>
    <dd>둘째</dd>
    <dd>셋째</dd>
    <dt>두번째 제목</dt>
    <dd>넷째</dd>
  </dl>
</div>
```

[예제코드 실행 결과(codepen)](https://codepen.io/seungyeop-lee/pen/exGoRN)

## 참고

- [Do it! HTML5+CSS3 웹 표준의 정석 <개정판>, 2017, 고경희](http://www.easyspub.co.kr/20_Menu/BookView/119/PUB)