# 표 태그

- `<table>`태그와 관련된 내용을 정리한다.

## `<table>`태그의 기본 구성

- `<table>`태그 내부에 사용되는 대표적인 태그는 `<tr>`, `<td>`, `<th>`이다.
- `<tr>`로 표의 행을 구분하고, `<td>` 및 `<th>`로 해당 행의 셀을 나타낸다.
- `<td>`는 일반셀, `<th>`는 제목셀을 나타낸다.

```html
<style>
table, th, td {
  border: 1px solid black;
  border-collapse: collapse;
}
</style>
<div>
  <table>
    <tr>
      <th>순번</th>
      <th>태그</th>
      <th>설명</th>
    </tr>
    <tr>
      <td>1</td>
      <td><code>&lt;table&gt;</code></td>
      <td>테이블 태그를 나타냅니다.</td>
    </tr>
  </table>
<div>
```

[예제코드 실행 결과(codepen)](https://codepen.io/seungyeop-lee/pen/BMYPXQ)

### 셀 합치기(`colspan`, `rowspan`속성)

- `<td>`나 `<th>`태그의 속성으로 `colspan`과 `rowspan`이 있다.
- `colspan`은 값에 해당하는 숫자만큼 열을 합치는 것을 나타낸다.
- `rowspan`은 값에 해당하는 숫자만큼 행을 합치는 것을 나타낸다.

```html
<style>
table, th, td {
  border: 1px solid black;
  border-collapse: collapse;
}
</style>
<div>
  <table>
    <tr>
      <td colspan="2">colspan</td>
      <td rowspan="2">rowspan</td>
    </tr>
    <tr>
      <td>-</td>
      <td>-</td>
    </tr>
  </table>
</div>
```

[예제코드 실행 결과(codepen)](https://codepen.io/seungyeop-lee/pen/aXqazX)

## 표에 제목 붙이기

- `<caption>` 또는 `<figcaption>`태그를 사용하여 제목을 붙일 수 있다.

### `<caption>`

- `<table>`태그 내부 최상단에 위치해야 한다.
- `<caption>`태그는 블록 레벨 태그이므로 내부에 텍스트를 꾸밀 다른 태그의 사용이 가능하다.
- `<caption>`태그 내부의 내용은 표 상단에 중앙 정렬된 상태로 나타난다.

```html
<style>
table, th, td {
  border: 1px solid black;
  border-collapse: collapse;
}
</style>
<div>
  <table>
    <caption><p>태그 설명 표</p></caption>
    <tr>
      <th>순번</th>
      <th>태그</th>
      <th>설명</th>
    </tr>
    <tr>
      <td>1</td>
      <td><code>&lt;table&gt;</code></td>
      <td>테이블 태그를 나타냅니다.</td>
    </tr>
  </table>
<div>
```

[예제코드 실행 결과(codepen)](https://codepen.io/seungyeop-lee/pen/LqQJpw)

### `<figure>`, `<figcaption>`

- 그림, 도형의 제목을 붙일 때 사용되는 태그이지만, 표의 제목을 붙일 때도 사용가능하다.
- `<figure>`태그로 `<table>`태그를 감싼 후, `<figcaption>`태그를 `<table>`직전 또는 `</table>`직후에 위치시킨다.
- `<figcaption>`태그도 블록 레벨 태그이므로 내부에 텍스트를 꾸밀 다른 태그의 사용이 가능하다.
- `<figcaption>`태그 내부의 내용은 태그의 위치에 따라 표 상단 또는 표 하단에 나타나며 중앙 정렬되지 않는다.

```html
<style>
table, th, td {
  border: 1px solid black;
  border-collapse: collapse;
}
</style>
<div>
  <figure>
    <figcaption><p>태그 설명 표 시작</p></figcaption>
    <table>
      <tr>
        <th>순번</th>
        <th>태그</th>
        <th>설명</th>
      </tr>
      <tr>
        <td>1</td>
        <td><code>&lt;table&gt;</code></td>
        <td>테이블 태그를 나타냅니다.</td>
      </tr>
    </table>
    <figcaption><p>태그 설명 표 끝</p></figcaption>
  </figure>
<div>
```

[예제코드 실행 결과(codepen)](https://codepen.io/seungyeop-lee/pen/QYQVEa)

## 표의 구조 정의하기

- `<thead>`, `<tbody>`, `<tfoot>`로 표의 제목부분, 본문부분, 요약부분을 나타낼 수 있다.
- 시맨틱 태그로서 부분을 명시 할 뿐, 브라우저에서의 변경은 없다.
- 각 태그는 `<tr>`태그를 감싼 형태로 사용된다.

```html
<style>
table, th, td {
  border: 1px solid black;
  border-collapse: collapse;
}
</style>
<div>
  <table>
    <thead>
      <tr>
        <th>순번</th>
        <th>태그</th>
        <th>설명</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td>1</td>
        <td><code>&lt;table&gt;</code></td>
        <td>테이블 태그를 나타냅니다.</td>
      </tr>
    </tbody>
    <tfoot>
      <tr>
        <td colspan="3">이상 입니다.</td>
      </tr>
    </tfoot>
  </table>
<div>
```

[예제코드 실행 결과(codepen)](https://codepen.io/seungyeop-lee/pen/MLQqJq)

## 여러 열을 묶어 정의하기

- `<col>`태그를 이용하면 열을 가리킬 수 있다.
- `<col>`태그는 `<caption>`태그 뒤, 표 구성요소 태그 앞에 위치하여야 한다.
- `<col>`태그의 순서가 표의 열 순서이며, 관례적으로 표의 열의 갯수와 동일한 수의 `<col>`태그를 사용하여야 한다.
- 인접한 여러열을 묶고 싶을 경우 `<colgroup>`태그로 묶을`<col>`을 감싸면된다.

```html
<style>
table, th, td {
  border: 1px solid black;
  border-collapse: collapse;
}
.col1 {
  background-color: gray;
}
.col2-3 {
  background-color: yellowgreen;
}
</style>
<div>
  <table>
    <col class="col1">
    <colgroup class="col2-3">
      <col>
      <col>
    </colgroup>
    <tr>
      <th>순번</th>
      <th>태그</th>
      <th>설명</th>
    </tr>
    <tr>
      <td>1</td>
      <td><code>&lt;table&gt;</code></td>
      <td>테이블 태그를 나타냅니다.</td>
    </tr>
  </table>
<div>
```

[예제코드 실행 결과(codepen)](https://codepen.io/seungyeop-lee/pen/WPMgEM)

## 참고

- [Do it! HTML5+CSS3 웹 표준의 정석 <개정판>, 2017, 고경희](http://www.easyspub.co.kr/20_Menu/BookView/119/PUB)