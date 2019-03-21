# 미디어쿼리를 이용한 선택적 CSS적용

- 실제 미디어 쿼리를 이용하여 선택적으로 CSS를 적용하는 방법에 대해 정리한다.

## 조건에 따른 외부 CSS 파일 연결

### `<link>`태그를 이용한 방법

- `<link>`태그의 `media`속성을 이용하여 미디어 쿼리의 이용이 가능하다.
- 미디어 쿼리의 조건에 따라 외부 CSS파일이 선택된다.
- 기본형은 `<link rel="stylesheet" media="미디어 쿼리 조건" href="CSS 파일 경로">`이다.

```html
<link rel="stylesheet" media="screen" href="./static/css/index.css">
```

### `@import`구문을 이용한 방법

- `@import`구문은 `<style>`태그 내부나 외부 CSS파일 내부에서 사용가능하다.
- 기본형은 `@import url(CSS 파일 경로) 미디어 쿼리 조건;`이다.

```css
@import url("./static/css/header.css") only screen;
```

## 조건에 따른 내부 CSS 정의 적용

### `<style>`태그에 직접 적용

- `<style>`태그의 `media`속성을 이용하여 미디어 쿼리에 따른 `<style>`태그의 선택적 사용이 가능하다.
- 기본형은 `<style media="미디어 쿼리 조건"> 스타일 규칙들 </style>`이다.

```html
<style media="screen">
* {
  /* 미디어 타입이 screen일 경우 이곳에 선언된 CSS가 적용됨 */
}
</style>
```

### `<style>`태그 내부에 적용

- 스타일 규칙에 직접 미디어 쿼리를 적용하여 선택적으로 스타일을 사용하는 것이 가능하다.
- 기본형은 `<style> @media 미디어 쿼리조건 { 스타일 규칙들 } </style>`이다.

```html
<style>
  @media screen {
    * {
      /* 미디어 타입이 screen일 경우 이곳에 선언된 CSS가 적용됨 */
    }
  }
</style>
```

## 참고

- [Do it! HTML5+CSS3 웹 표준의 정석 <개정판>, 2017, 고경희](http://www.easyspub.co.kr/20_Menu/BookView/119/PUB)