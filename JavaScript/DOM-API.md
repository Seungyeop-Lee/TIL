# DOM API (Document Object Model Application Programming Interface)
- DOM을 프로그래밍 언어(JavaScript)에서 이용할 수 있게 제공되는 인터페이스를 가리킨다.

## 검색
- `document`의 내장 메소드를 통하여 검색 가능하다.


접근 메소드 | 매개변수 | 속도 | 반환 형태
-----------|---------|------|----------
`document.getElementById()` | id 속성값 | 1등 | `HTMLElement` 상속객체
`document.getElementsByName()` | name 속성값 | 2등 | `NodeList`
`document.getElementsByTagName()` | tag 이름 | 3등 | `HTMLCollection`
`document.getElementsByClassName()` | class 속성값 | 4등 | `HTMLCollection`
`document.querySelector()` | CSS 선택자 | 5등 | `HTMLElement` 상속객체
`document.querySelectorAll()` | CSS 선택자 | 6등 | `NodeList`

```HTML
  <body>
    <div id="divId" class="divClass" name="divName"></div>
  </body>
  <script>
    var tag1 = document.getElementById('divId');
    var tag2 = document.getElementsByName('divName');
    var tag4 = document.getElementsByTagName('div');
    var tag3 = document.getElementsByClassName('divClass');
    var tag5 = document.querySelector('#divId');
    var tag6 = document.querySelectorAll('.divClass');
  </script>
```
- `HTMLCollection` vs. `NodeList`
  - 공통점 : DOM Node의 컬렉션 객체이며 유사배열이다.
  - 차이점

`HTMLCollection` | `NodeList`
---------------|----------
요소 노드만을 가지고 있다. | 요소 노드, 텍스트, 노드, 코멘트 노드를 가지고 있다.
(컬렉션 객체에 포함된) 노드의 상태변경을 실시간으로 반영한다. | 노드의 상태변경을 반영하지 않는다.

## 탐색
- 요소 노드 객체의 내장 속성 및 메소드를 이용한다.
### 내장 속성
속성명 | 설명 | 반환 형태
------|------|----------
`tagName` | 요소 노드의 태그이름 | 문자열
`textContent` | 요소 노드가 가지고 있는 텍스트 | 문자열
`nodeType` | 노드의 타입 | 1~12 중 하나의 숫자 <br>(요소 노드: 1, 속성 노드: 2, 텍스트 노드: 3, 코멘트 노드: 8, 문서 노드: 9)
`childNodes` | 자식 노드의 콜렉션 | `NodeList`
`children` | 자식 요소 노드의 콜렉션 | `HTMLCollection`
`firstChild` | 첫번째 자식 노드 | `Node` 상속객체
`firstElementChild` | 첫번째 자식 요소 노드 | `HTMLElement` 상속객체
`lastChild` | 마지막 자식 노드 | `Node` 상속객체
`lastElementChild` | 마지막 자식 요소 노드 | `HTMLElement` 상속객체
`parentNode` | 부모 노드 | `Node` 상속객체
`parentElement` | 부모 요소 노드 | `HTMLElement` 상속객체
`previousSibling` | 자신 전의 형제 노드 | `Node` 상속객체
`previoutElementSibling` | 자신 전의 형제 요소 노드 | `HTMLElement` 상속객체
`nextSibling` | 다음 형제 노드 | `Node` 상속객체
`nextElementSibling` | 다음 형제 요소 노드 | `HTMLElement` 상속객체
- 값이 존재하지 않는경우
  - 반환 형태가 콜렉션 : 빈 콜렉션 객체 반환
  - 반환 형태가 객체 : `null`
```HTML
<!-- TODO 예제코드 작성 -->
```

## 참고
- [jsperf : element node search speed test](https://jsperf.com/element-node-search-speed-test)
- [PoiemaWeb : JavaScript > 문서 객체 모델(Document Object Model)](https://poiemaweb.com/js-dom)
- [MDN web docs : Web technology for developers > Web APIs > Element](https://developer.mozilla.org/en-US/docs/Web/API/Element)