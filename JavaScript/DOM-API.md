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
`element.tagName` | 요소 노드의 태그이름 | 문자열
`node.textContent` | 요소 노드가 가지고 있는 텍스트 | 문자열
`node.nodeType` | 노드의 타입 | 1~12 중 하나의 숫자 <br>(요소 노드: 1, 속성 노드: 2, 텍스트 노드: 3, 코멘트 노드: 8, 문서 노드: 9)
`element.childNodes` | 자식 노드의 콜렉션 | `NodeList`
`element.children` | 자식 요소 노드의 콜렉션 | `HTMLCollection`
`node.firstChild` | 첫번째 자식 노드 | `Node` 상속객체
`element.firstElementChild` | 첫번째 자식 요소 노드 | `HTMLElement` 상속객체
`node.lastChild` | 마지막 자식 노드 | `Node` 상속객체
`element.lastElementChild` | 마지막 자식 요소 노드 | `HTMLElement` 상속객체
`node.parentNode` | 부모 노드 | `Node` 상속객체
`node.parentElement` | 부모 요소 노드 | `HTMLElement` 상속객체
`node.previousSibling` | 자신 전의 형제 노드 | `Node` 상속객체
`node.previousElementSibling` | 자신 전의 형제 요소 노드 | `HTMLElement` 상속객체
`node.nextSibling` | 다음 형제 노드 | `Node` 상속객체
`node.nextElementSibling` | 다음 형제 요소 노드 | `HTMLElement` 상속객체

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
`node.hasChildNodes()` | 자식 노드의 소유 유무를 반환 | `boolean`

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
`document.createElement(tagName)` | 인수 값에 해당하는 태그의 요소 노드 객체를 생성한다. | `HTMLElement` 상속객체
`document.createAttribute(attributeName)` | 인수 값에 해당하는 값의 속성 노드 객체를 생성한다. | `Attr` 객체
`document.createTextNode(data)` | 인수 값에 해당하는 값을 가지는 텍스트 노드 객체를 생성한다. | `Text` 객체
`document.createComment(data)` | 인수 값에 해당하는 값을 가지는 코멘트 노드 객체를 생성한다. | `Comment` 객체
`node.cloneNode(deep)` | `node`를 복제한다. `deep`은 자손복사 유무 설정(`boolean`) | `Node` 상속객체

- DOM 노드 객체 삽입-삭제-치환 메소드

메소드명 | 설명
--------|------
`node.appendChild(newNode)` | `node`의 자식 요소로 `newNode`를 추가한다. 기존 자식 요소가 있을 경우 그 뒤에 추가된다.
`node.insertBefore(newNode, existingNode)` | `node`의 자식 요소 중에 `existingNode` 바로 앞 위치에 `newNode`를 추가한다. `existingNode`가 `null`일 경우 가장 뒤에 추가된다.
`node.insertAdjacentElement(position, element)` | `node`의 `position`('beforebegin', 'afterbegin', 'beforeend', 'afterend')에 해당하는 위치에 `element`를 추가한다.
`element.remove()` | `element`를 트리에서 삭제한다. (실험적 메소드)
`node.removeChild(existingNode)` | `node`의 자식 요소 중 `existingNode`에 해당하는 요소를 삭제한다.
`node.replaceChild(newNode, oldNode)` | `node`의 자식 요소 중 `oldNode`에 해당하는 요소를 `newNode`로 치환한다.

- 속성 노드나 텍스트 노드 객체의 값을 확인하거나 수정 할 때는 `nodeValue` 속성을 이용한다.

```html
<!DOCTYPE html>
<html>
<head>
  <meta charset="utf-8" />
  <title>Example of DOM HTML - Object creation and handling</title>
</head>
<body>
</body>
<script>
  //DOM 객체 생성
  //document.createElement(tagName)
  var divTag = document.createElement('div');
  var pTag = document.createElement('p');

  //document.createAttribute(attributeName)
  var classAttr = document.createAttribute('class');
  classAttr.nodeValue = 'div-class';

  //document.createComment(data)
  var commentNode = document.createComment('This is CommentNode');
  
  //node.cloneNode(deep)
  var pTag2 = pTag.cloneNode();
  var pTag3 = pTag.cloneNode();

  //document.createTextNode(data)
  var textNode = document.createTextNode('This is TextNode');
  var pTag2Text = document.createTextNode('This is ClonedNode!');
  var pTag3Text = document.createTextNode('This is replacedNode!');


  //DOM 객체 삽입
  //node.appendChild(node)
  document.body.appendChild(divTag);
  pTag.appendChild(textNode);
  divTag.appendChild(pTag);
  divTag.appendChild(pTag2);
  pTag2.appendChild(pTag2Text);
  pTag3.appendChild(pTag3Text);
  
  //node.insertAdjacentElement(position, element)
  divTag.insertAdjacentElement('afterbegin', pTag);

  //node.insertBefore(newNode, existingNode)
  divTag.insertBefore(commentNode, pTag);

  //DOM 객체 치환
  //node.replaceChild(newNode, oldNode)
  divTag.replaceChild(pTag3, pTag);

  //DOM 객체 삭제
  //node.removeChild(node)
  divTag.removeChild(pTag2);

  //element.remove()
  pTag3.remove();
</script>
</html>
```

- 속성 노드 객체 관련 메소드 및 속성

메소드 또는 속성명 | 설명 | 반환 형태
--------|------|---------
`element.className` | `element`의 class이름을 저장하고 있다. 변경 가능하다. | 문자열
`element.id` | `element`의 id이름을 저장하고 있다. 변경 가능하다. | 문자열
`node.hasAttributes()` | `node`의 속성 소유 유무를 반환한다. | `boolean`
`element.getAttributeNode(attributeName)` | `element`가 가지고 있는 `attributeName`과 동일한 이름의 속성 노드 객체를 반환한다. | `Attr` 객체
`element.setAttributeNode(attributeNode)` | `element`에 `attributeNode`를 속성으로 추가한다. | 없음
`element.removeAttributeNode(attributeNode)` | `element`가 가지고 있는 `attributeNode`와 동일한 이름의 속성 노드 객체를 삭제 후 반환한다. | `Attr` 객체


```html
<!DOCTYPE html>
<html>
<head>
  <meta charset="utf-8" />
  <title>Example of DOM Attribution Object</title>
</head>
<body>
  <p class="pTagClass" id="pTagId"></p>
</body>
<script>
var pTag = document.getElementById('pTagId');

//element.className
console.log(pTag.className);  //pTagClass
pTag.className = 'pTagClass2';
console.log(pTag.className);  //pTagClass2

//element.id
console.log(pTag.id); //pTagId
pTag.id = 'pTagId2';
console.log(pTag.id); //pTagId2

//node.hasAttributes()
console.log(pTag.hasAttributes());  //true

//element.getAttributeNode(attributeName)
var pTagClassAttr = pTag.getAttributeNode('class');

var clonePTagClassAttr = pTagClassAttr.cloneNode();
clonePTagClassAttr.nodeValue = 'clonePTagClass';

//element.setAttributeNode(attributeNode)
pTag.setAttributeNode(clonePTagClassAttr);
console.log(pTag.className);  //clonePTagClass

//element.removeAttributeNode(attributeNode)
var removedAttr = pTag.removeAttributeNode(clonePTagClassAttr);
console.log(removedAttr.nodeValue); //clonePTagClass
console.log(pTag.className);  //(빈 문자열)
</script>
</html>
```
- 속성 직접 접근 메소드 및 속성

메소드 또는 속성명 | 설명 | 반환 형태
--------|------|---------
`element.hasAttribute(attributename)` | `element`가 가지고 있는 `attributename`과 동일한 이름의 속성 존재유무를 반환한다. | `boolean`
`element.getAttribute(attributename)` | `element`가 가지고 있는 `attributename`과 동일한 이름의 속성 값을 반환한다. | 문자열
`element.setAttribute(attributename, attributevalue)` | `element`에 `attributename`의 이름과 `attributevalue`의 값을 가진 속성을 추가한다. | 없음
`element.removeAttribute(attributename)` | `element`가 가지고 있는 `attributename`과 동일한 이름의 속성 노드 객체를 삭제한다. | 없음

```html
<!DOCTYPE html>
<html>
<head>
  <meta charset="utf-8" />
  <title>Example of DOM Attribution Object</title>
</head>
<body>
  <p class="pTagClass" id="pTagId"></p>
</body>
<script>
var pTag = document.getElementById('pTagId');

//element.hasAttribute(attributename)
console.log(pTag.hasAttribute('class'));  //true

//element.getAttribute(attributename)
var className = pTag.getAttribute('class');
console.log(className); //pTagClass

//element.setAttribute(attributename, attributevalue)
pTag.setAttribute('class', 'modPTagClass');
console.log(pTag.className);  //modPTagClass

//element.removeAttribute(attributename)
pTag.removeAttribute('class');
console.log(pTag.className);  //(빈 문자열)
</script>
</html>
```

### HTML 구문 직접 삽입-삭제
- HTML 구문 직접 접근 메소드 및 속성

메소드 또는 속성명 | 설명 | 반환 형태
-----------------|------|---------
`element.innerHTML` | `element` 태그 내부의 HTML구문을 반환한다. 변경가능 하다. | 문자열
`element.outerHTML` | `element` 태그를 포함한 HTML구문을 반환한다. 변경가능 하다. | 문자열
`element.insertAdjacentHTML(position, text)` | `element`의 `position`('beforebegin', 'afterbegin', 'beforeend', 'afterend')에 해당하는 위치에 `text`를 HTML구문으로서 추가한다.

```html
<!DOCTYPE html>
<html>
<head>
  <meta charset="utf-8" />
  <title>Example of DOM HTML - Direct handling</title>
</head>
<body>
  <div id="divTag">div tag context</div>
</body>
<script>
var divTag = document.getElementById('divTag');

//element.innerHTML
console.log(divTag.innerHTML);  //div tag context
divTag.innerHTML += ' | Additional context';
console.log(divTag.innerHTML);  //div tag context | Additional context

//element.insertAdjacentHTML(position, text)
divTag.insertAdjacentHTML('afterbegin', 'Additional context | ');
console.log(divTag.innerHTML); //Additional context | div tag context | Additional context

//element.outerHTML
console.log(divTag.outerHTML); //<div id="divTag">Additional context | div tag context | Additional context</div>
</script>
</html>
```

## 스타일 속성 (Style Property)

- 스타일 속성을 이용하면 inline style의 삽입 및 조작이 가능하다.
- `window.getComputedStyle(element).getPropertyValue(prop)`로 `element`가 가지고 있는 스타일 속성 중 `prop`과 동일한 이름을 가진 값을 확인 할 수 있다.
- 스타일 속성에 접근 시 `.`접근자 이용이 가능하다. 단, 속성명의 `-`에 해당하는 부분을 무시하고, 대신 `-`뒤에 영문자하나를 대분자로 변경한 이름으로 접근 가능하다.
- 스타일 속성에 `.cssText`속성을 이용하면 적용된 CSS구문을 확인 가능하며, 변경이 가능하기 때문에 CSS구문을 직접 삽입도 가능하다.

## 참고
- [jsperf : element node search speed test](https://jsperf.com/element-node-search-speed-test)
- [PoiemaWeb : JavaScript > 문서 객체 모델(Document Object Model)](https://poiemaweb.com/js-dom)
- [MDN web docs : Web technology for developers > Web APIs > Element](https://developer.mozilla.org/en-US/docs/Web/API/Element)
- [w3schools.com : The HTML DOM Element Object](https://www.w3schools.com/jsref/dom_obj_all.asp)