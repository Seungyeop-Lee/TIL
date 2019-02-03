# HTML 개요

- HTML은 Hypertext Markup Language의 줄임말이다.
- 즉, HTML이란 하이퍼텍스트를 포함하고 있는 마크업 언어를 가리킨다.
- 하이퍼텍스트(Hypertext)란 하이퍼링크(참조)를 통해 현재의 문서에서 다른 문서로 즉시 접근가능 한 텍스트를 나타낸다.
- 마크업 언어(Markup Language)란 태그(tag) 등을 이용해 문서나 데이터 구조를 명기하는 언어의 한 종류이다.

## 태그(Tag)

- 모든 태그는 꺽쇠(`<`)로 시작하여 꺽쇠(`>`)로 끝난다.
- `<` 후 태그의 종류가 기입된다.
- 열리는 태그(`<종류>`)가 있으면 닫히는 태그(`</종류>`)가 있어야한다. (몇몇 태그는 닫히는 태그가 필요 없다.)
- 태그는 속성을 가질 수 있으며, 속성은 이름과 값을 가진다. (`속성="값"`)
- 종류와 속성, 속성과 속성은 스페이스로 구분된다.
- 종류와 속성의 이름은 소문자로 쓰는것이 권장된다.

```html
<!-- 
  <종류 속성="값" 속성="값"></종류> 
-->
  <div id="Id" class="Cl"></div>
```

## HTML 문서의 기본 구조

- HTML은 정해진 형식에 맞춰 내용을 입력해야 한다.
- HTML의 필수 태그는 `<!doctype>`, `<html>`, `<head>`, `<body>`이다.

```HTML
<!DOCTYPE html> <!--HTML5로 작성된 웹 문서라는 것을 나타냄-->
<html>  <!--html문서의 시작과 끝을 나타냄-->
  <head>  <!--html문서 정보를 포함한 부분, 웹 브라우저에 표시되지 않음-->
    <meta charset="utf-8" />
    <title>HTML Title</title>
  </head>
  <body>  <!--웹 브라우저에 표시 될 내용-->
    HTML Body
  </body>
</html>
```

### `<!doctype>`

- 문서 유형(document type)을 명기하는 태그이며, 웹 브라우저가 어떤 문서인지를 인지한다.
- HTML5는 `<!doctype html>`을 명기하면 된다.
- 문서 유형을 강조하기 위해 `<!DOCTYPE html>`처럼 사용하기도 한다.

### `<html>`

- html 문서의 시작과 끝을 알리는 태그이다.
- lang속성을 이용하면 문서에서 사용 할 언어의 지정이 가능하다. (ex: `lang="ko"`)
- `<html>`태그는 `<head>`와 `<body>`태그를 가지고 있다.

### `<head>`

- `<head>`태그 안에는 html문서의 정보를 나타낸다. 

#### `<head>`에서 사용하는 주요 태그

태그 | 설명
----|------
`<title>` | 문서 제목, 제목 표시줄에 표시되는 문자열
`<meta>` | 문자 인코딩 및 문서 키워드, 요약 정보 등을 나타낸다.
`<link>` | 외부 CSS 파일 로딩
`<style>` | CSS 정의
`<script>` | 외부 JavaScript 파일 로딩 또는 JavaScript 정의

### `<body>`

- `<body>`태그 안에는 실제 브라우저에 표기될 내용을 나타낸다.

## 참조

- [위키피디아 : HTML](https://ko.wikipedia.org/wiki/HTML)
- [위키피디아 : 하이퍼텍스트](https://ko.wikipedia.org/wiki/%ED%95%98%EC%9D%B4%ED%8D%BC%ED%85%8D%EC%8A%A4%ED%8A%B8)
- [위키피디아 : 마크업 언어](https://ko.wikipedia.org/wiki/%EB%A7%88%ED%81%AC%EC%97%85_%EC%96%B8%EC%96%B4)
- [Do it! HTML5+CSS3 웹 표준의 정석 <개정판>, 2017, 고경희](http://www.easyspub.co.kr/20_Menu/BookView/119/PUB)