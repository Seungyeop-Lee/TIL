# Event
- 이벤트란 어떤 사건 자체를 의미한다.
- 웹 브라우저에서는 웹 페이지 로드, 사용자에 의한 조작, 통신상태변경 등을 의미한다.
- 웹 브라우저에서 발생하는 이벤트의 종류 및 설명은 [MDN web docs : Event](https://developer.mozilla.org/ja/docs/Web/Events)을 참고한다.

## 이벤트 핸들러 등록 및 제거
- 웹 브라우저에서 이벤트가 발생하였을 경우 이벤트 리스너가 이벤트를 인지 후 등록된 이벤트 핸들러를 실행시킨다.
- 이벤트 핸들러의 등록 및 제거 방법은 고전 이벤트 모델, 인라인 이벤트 모델, 표준 이벤트 모델로 나눌 수 있다.

### 고전 이벤트 모델(이벤트 핸들러 속성)
- 객체의 속성으로 존재하는 이벤트 핸들러 속성에 대입 연산자(`=`)를 이용하여 이벤트 핸들러를 설정한다.
- 이벤트 핸들러 속성의 이름은 `on + 이벤트 종류`로 정해져 있다.
- 이벤트 핸들러 속성에 `null`을 대입 할 경우 등록된 이벤트 핸들러가 제거된다.
- 실행되는 이벤트 핸들러 내부의 `this`는 해당 태그의 DOM객체를 가리킨다.

```html
<!DOCTYPE html>
<html>
<head>
  <meta charset="utf-8" />
  <title>Example of event handler property</title>
</head>
<body>
  <input id="btn" type="button" value="button"/>
</body>
<script>
  var handlerThis;
  var btn = document.getElementById('btn');
  btn.onclick = function() {
    console.log('click!!!');
    handlerThis = this;
  }
  btn.click();  //click!!!
  console.log(handlerThis.toString());  //[object HTMLInputElement]

  btn.onclick = null;
  btn.click();  //(반응없음)
</script>
</html>
```

### 인라인 이벤트 모델
- HTML 태그에 `on + 이벤트 종류`로 된 속성을 추가하고, 값으로 실행 될 자바스크립트 코드를 넣는다.
- DOM객체에 있는 `on + 이벤트 종류`로 된 속성을 삭제하면 이벤트 핸들러가 제거된다.
- 실행되는 이벤트 핸들러 내부의 `this`는 해당 태그의 DOM객체를 가리킨다.

```html
<!DOCTYPE html>
<html>
<head>
  <meta charset="utf-8" />
  <title>Example of inline event attribution</title>
</head>
<body>
  <input id="btn" type="button" value="button" onclick="console.log('click!!!'); handlerThis = this;"/>
</body>
<script>
  var handlerThis;
  btn.click();  //click!!!
  console.log(handlerThis.toString());  //[object HTMLInputElement]

  document.getElementById('btn').removeAttribute('onclick');
  btn.click();  //(반응없음)
</script>
</html>
```

### 표준 이벤트 모델
- `EventTarget.addEventListener()`메소드를 사용하여 이벤트 핸들러를 설정한다.
- 다른 이벤트 모델과 다르게 하나의 이벤트에 두 개 이상의 핸들러 등록이 가능하다.
- `EventTagrget.removeEventListener()`메소드를 사용하면 이벤트 핸들러를 제거 할 수있다.
- 실행되는 이벤트 핸들러 내부의 `this`는 이벤트 핸들러가 등록된 객체(`target`)를 가리킨다.

구문 | `target.addEventListener(type, listener[, useCapture])`
----|---------------------------------------------------------
`type` | 이벤트 핸들러를 등록하려는 이벤트의 종류를 나타내는 문자열
`listener` | 등록 할 이벤트 핸들러
`useCapture` | 이벤트 전달 방식 지정(`true`면 캡쳐링만), 초기치는 `false`

구문 | `target.removeEventListener(type, listener[, useCapture])`
----|----------------------------------------------------------
`type` | 삭제하려는 이벤트 핸들러가 등록되어 있는 이벤트의 종류를 나타내는 문자열
`listener` | 제거 할 이벤트 핸들러
`useCapture` | 핸들러가 설정되었을 때의 `useCapture` 값, `type`과 `listener`에 해당하는 삭제 대상 핸들러가 있어도 `useCapture`의 값이 다를경우 제거되지 않는다.

```html
<!DOCTYPE html>
<html>
<head>
  <meta charset="utf-8" />
  <title>Example of standard event model</title>
</head>
<body>
  <input id="btn" type="button" value="button"/>
</body>
<script>
  var handlerThis;
  var btn = document.getElementById('btn');
  var handlerFunc = function() {
    console.log('click!!!');
    handlerThis = this;
  };
  
  btn.addEventListener('click', handlerFunc);
  btn.click();  //click!!!
  console.log(handlerThis.toString()); //[object HTMLInputElement]

  btn.removeEventListener('click', handlerFunc);
  btn.click();  //(반응없음)
</script>
</html>
```

## 이벤트 전달
- 웹 페이지 상에서 어떤 DOM노드에 이벤트가 발생하였을 경우 최상위 노드부터 이벤트가 전달된다.
- 전달되는 방향에 따라 이벤트 버블링과 이벤트 캡처링으로 나누어지며, 이벤트 핸들러 등록 시 하나의 방법을 정할 수 있다.

### 이벤트 발생 시 이벤트 전달 경로
1. 이벤트 발생 노드의 최상위 노드에서 동일 이벤트 발생
1. 하위 노드로 이벤트 전달 (이벤트 캡처링)
1. 이벤트 발생 노드에 도달
1. 상위 노드로 이벤트 전달 (이벤트 버블링)
1. 이벤트 발생 노드의 최상위 노드까지 이벤트 전달 후 이벤트 발생 종료

![Graphical representation of an event dispatched in a DOM tree using the DOM event flow](https://www.w3.org/TR/DOM-Level-3-Events/images/eventflow.svg)
Graphical representation of an event dispatched in a DOM tree using the DOM event flow (출처: https://www.w3.org/TR/DOM-Level-3-Events/#dom-event-architecture)

### 이벤트 버블링
- 이벤트 발생 노드의 상위노드로 이벤트가 전달되는 것을 뜻한다.
- 이벤트 전달 방식을 지정하지 않는 경우 자동으로 이벤트 버블링 방식으로 설정된다.
- 고전 이벤트 모델, 인라인 이벤트 모델은 이벤트 버블링 방식이다.

### 이벤트 캡처링
- 이벤트 발생 노드의 하위노드로 이벤트가 전달되는 것을 뜻한다.
- 표준 이벤트 모델에서는 `useCapture`인수를 통해 이벤트 캡처링 방식으로 설정 가능하다.

```html
<!DOCTYPE html>
<html>
<head>
  <meta charset="utf-8" />
  <title>Example of event bubbling and capturing</title>
</head>
<body id="body">
  body
  <div id="outsideDiv">
    outside div
    <div id="insideDiv">
      inside div
    </div>
  </div>
</body>
<script>
var body = document.getElementById('body');
var outsideDiv = document.getElementById('outsideDiv');
var insideDiv = document.getElementById('insideDiv');
var handlerFunc = function(e) {
  var eventPhase;
  switch(e.eventPhase) {
    case Event.CAPTURING_PHASE:
      eventPhase = 'Capturing';
      break;
    case Event.AT_TARGET:
      eventPhase = 'Target';
      break;
    case Event.BUBBLING_PHASE:
      eventPhase = 'Bubbling';
      break;
  }
  console.log(this.id + ' ---> ' + eventPhase);
};

body.addEventListener('click', handlerFunc, false);
body.addEventListener('click', handlerFunc, true);
outsideDiv.addEventListener('click', handlerFunc, false);
outsideDiv.addEventListener('click', handlerFunc, true);
insideDiv.addEventListener('click', handlerFunc);

insideDiv.click();
/*
body ---> Capturing
outsideDiv ---> Capturing
insideDiv ---> Target
outsideDiv ---> Bubbling
body ---> Bubbling
*/
</script>
</html>
```

## 이벤트 강제 발생
- 고전 이벤트 모델로 이벤트 핸들러를 등록했을 경우에 한해, 이벤트 핸들러 속성을 실행시키는 것으로 이벤트 강제 발생이 가능하다.
- 이벤트 강제 발생 대상이 `HTMLElement` 객체일 경우, `HTMLElement.click()`, `HTMLElement.blur()`, `HTMLElement.focus()`를 사용가능하다.

```html
<!DOCTYPE html>
<html>
<head>
  <meta charset="utf-8" />
  <title>Example of event occurring</title>
</head>
<body>
  <input id="textbox" type="text"/>
</body>
<script>
  var textbox = document.getElementById('textbox');
  textbox.onclick = function() {
    console.log('click!!!');
  }
  textbox.onfocus = function() {
    console.log('focus!!!');
  }
  textbox.onblur = function() {
    console.log('blur!!!');
  }

  textbox.onclick();  //click!!!
  textbox.onfocus();  //focus!!!
  textbox.onblur();   //blur!!!

  textbox.click();  //click!!!
  textbox.focus();  //focus!!!
  textbox.blur();   //blur!!!
</script>
</html>
```

## 참조
- [PoiemaWeb : JavaScript > 이벤트](https://poiemaweb.com/js-event)
- [MDN web docs : 開発者向けのウェブ技術 > Web API > EventTarget > EventTarget.addEventListener()](https://developer.mozilla.org/ja/docs/Web/API/EventTarget/addEventListener)
- [MDN web docs : 開発者向けのウェブ技術 > Web API > EventTarget > EventTarget.removeEventListener](https://developer.mozilla.org/ja/docs/Web/API/EventTarget/removeEventListener)
- [MDN web docs : 開発者向けのウェブ技術 > Web API > HTMLElement](https://developer.mozilla.org/en-US/docs/Web/API/HTMLElement)
- [모던 웹을 위한 JavaScript jQuery 입문(3판) : 이벤트](http://www.hanbit.co.kr/store/books/look.php?p_code=B6367089342)