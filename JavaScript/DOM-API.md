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
  window.onload = function() {
    var tag1 = document.getElementById('divId');
    var tag2 = document.getElementsByName('divName');
    var tag4 = document.getElementsByTagName('div');
    var tag3 = document.getElementsByClassName('divClass');
    var tag5 = document.querySelector('#divId');
    var tag6 = document.querySelectorAll('.divClass');
  }
  </script>
```
- HTMLCollection vs. NodeList
  - 공통점 : DOM Node의 컬렉션 객체이며 유사배열이다.
  - 차이점

HTMLCollection | NodeList
---------------|----------
요소 노드만을 가지고 있다. | 요소 노드, 텍스트, 노드, 코멘트 노드를 가지고 있다.
(컬렉션 객체에 포함된) 노드의 상태변경을 실시간으로 반영한다. | 노드의 상태변경을 반영하지 않는다.


## 참고
- [jsperf : element node search speed test](https://jsperf.com/element-node-search-speed-test)