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
요소 노드만을 가지고 있다. | 요소 노드, 텍스트 노드, 코멘트 노드를 가지고 있다.
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
<!DOCTYPE html>
<html>
<head>
  <meta charset="utf-8" />
  <title>Example of DOM exploration</title>
</head>
<body>
  <div class="parent">
    <div class="nowDiv">
      begin
      <p class="firstChild">p1</p>
      <p class="secondChild">p2</p>
      <p class="thirdChild">p3</p>
      end
    </div>
  </div>
</body>
<script>
  var nowDivTag = document.getElementsByClassName('nowDiv')[0];
  console.log(nowDivTag.tagName); //DIV
  console.log(nowDivTag.textContent); //\n      begin\n      p1\n      p2\n      p3\n      end\n    
  console.log(nowDivTag.nodeType);  //1

  var childNodes = nowDivTag.childNodes;
  console.log(childNodes.toString()); //[object NodeList]
  console.log(childNodes.length); //7
  
  var children = nowDivTag.children;
  console.log(children.toString()); //[object HTMLCollection]
  console.log(children.length); //3


  var firstChild = nowDivTag.firstChild;
  console.log(firstChild.textContent);  //\n      begin\n      
  
  var firstElementChild = nowDivTag.firstElementChild;
  console.log(firstElementChild.textContent); //p1
  
  var lastChild = nowDivTag.lastChild;
  console.log(lastChild.textContent); //\n      end\n    
  
  var lastElementChild = nowDivTag.lastElementChild;
  console.log(lastElementChild.textContent);  //p3


  var parentNode = nowDivTag.parentNode;
  console.log(parentNode.className);  //parent

  var parentElement = nowDivTag.parentElement;
  console.log(parentElement.className); //parent


  var secondChildElement = document.getElementsByClassName('secondChild')[0];
  
  var previousSibling = secondChildElement.previousSibling;
  console.log(previousSibling.textContent); //\n      
  
  var previousElementSibling = secondChildElement.previousElementSibling;
  console.log(previousElementSibling.textContent);  //p1
  
  var nextSibling = secondChildElement.nextSibling;
  console.log(nextSibling.textContent); //\n      

  var nextElementSibling = secondChildElement.nextElementSibling;
  console.log(nextElementSibling.textContent);  //p3
</script>
</html>
```

### 내장 메소드

메소드명 | 설명 | 반환 형태
------|------|----------
`hasChildNodes()` | 자식 노드를 소유유무를 반환 | `boolean`

```html
<!DOCTYPE html>
<html>
<head>
  <meta charset="utf-8" />
  <title>Example of DOM exploration</title>
</head>
<body>
  <p>pTagText</p>
</body>
<script>
  var pTag = document.getElementsByTagName('p')[0];
  console.log(pTag.hasChildNodes());  //true

  var pTagTextNode = pTag.firstChild;
  console.log(pTagTextNode.hasChildNodes());  //false
</script>
</html>
```


## 생성 및 삽입-삭제
- DOM 노드 객체 삽입-삭제 방법은 DOM 객체 생성 후 삽입-삭제, HTML 구문 직접 삽입-삭제로 나눌 수 있다.

### DOM 객체 생성 후 삽입-삭제
- DOM 노드 객체 생성 메소드

메소드명 | 설명 | 반환 형태
--------|------|----------
`document.createElement(tagName)` | 인수값에 해당하는 태그의 요소 노드 객체를 생성한다. | `HTMLElement` 상속객체
`document.createAttribute(attributeName)` | 인수값에 해당하는 값의 속성 노드 객체를 생성한다. | `Attr` 객체
`document.createTextNode(data)` | 인수값에 해당하는 값을 가지는 텍스트 노드 객체를 생성한다. | `Text` 객체
`document.createComment(data)` | 인수값에 해당하는 값을 가지는 코멘트 노드 객체를 생성한다. | `Comment` 객체
`node.cloneNode(deep)` | node에 해당하는 노드를 복제한다. deep은 자손복사 유무 설정 | `Node` 상속객체

- DOM 노드 객체 삽입-삭제-수정 메소드

메소드명 | 설명
--------|------
`appendChild(node)` | 메소드가 실행되는 객체의 자식 요소로 `node`를 추가한다. 기존 자식 요소가 있을 경우 그 뒤에 추가된다.
`insertBefore(newNode, existingNode)` | 메소드가 실행되는 객체의 자식 요소 중에 `existingNode` 바로 앞 위치에 `newNode`를 추가한다. `existingNode`가 `null`일 경우 가장 뒤에 추가된다.
`insertAdjacentElement(position, element)` | 메소드가 실행되는 객체의 `position`에 해당하는 위치에 `element`를 추가한다.
`removeChild(node)` | 메소드가 실행되는 객체의 자식 요소 중 `node`에 해당하는 요소를 삭제한다.
`replaceChild(newNode, oldNode)` | 메소드가 실행되는 객체의 자식 요소 중 `oldNode`에 해당하는 요소를 `newNode`로 치환한다.

```html

```

## 참고
- [jsperf : element node search speed test](https://jsperf.com/element-node-search-speed-test)
- [PoiemaWeb : JavaScript > 문서 객체 모델(Document Object Model)](https://poiemaweb.com/js-dom)
- [MDN web docs : Web technology for developers > Web APIs > Element](https://developer.mozilla.org/en-US/docs/Web/API/Element)