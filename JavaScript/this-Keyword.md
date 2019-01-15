# this keyword
- 자바스크립트의 변수들은 정적 스코프(렉시컬스코프)를 따른다.
- 그러나 `this`키워드는 동적 스코프와 비슷하게 함수를 호출한 곳에 따라 다른 값을 가지며, 크게 5가지 상황으로 나눌 수 있다.
- ECMAScript5부터는 `bind`메소드를 이용하여 `this`값을 임의로 설정하는 것이 가능해졌다.

```javascript
function printThis() {
  console.log(this);
}

var tempThis = {
  message: "this is this"
}

var newPrintThis = printThis.bind(tempThis);
newPrintThis(); //{message: "this is this"}
```

## 전역 문맥(global context)에서의 `this`
- 글로벌 객체(웹브라우저에서는 `window`, node.js에서는 `global`)를 가리킨다.

```javascript
//console of chrome browser
console.log(this === window); //true

//node
console.log(this === global); //true
```

## 함수 내의 `this`
- 글로벌 객체를 가리킨다.
- 내부 함수(메소드나 함수 내부에 선언된 함수)의 경우에도 글로벌 객체를 가리킨다.

```javascript
var globalObj = this;

function printThis() {
  console.log(this === globalObj);
}

printThis();  //true

function printThis2() {
  function printInsideThis() {
    console.log(this === globalObj);
  }
  printInsideThis();
}

printThis2(); //true
```

## 객체 내의 `this`
- `this`를 포함하고 있는 객체 자체를 가리킨다.

```javascript
var obj = {
  returnThis: function(){
    return this;
  }
}

console.log(obj === obj.returnThis()); //true
```

## 생성자 함수 내의 `this`
- `new` 연산자를 이용해 생성 될 객체를 가리킨다.

```javascript
function ConstructorFunc() {
  this.returnThis = function() {
    return this;
  }
}

var obj = new ConstructorFunc();
console.log(obj === obj.returnThis());  //true
```

- 생성자 함수에 `new` 연산자를 이용하지 않고, 실행 할 경우에 `this`는 글로벌 객체를 가리킨다.
- 함수 내에서 `arguments.callee`를 사용하면 생성자 함수의 오용을 막을 수 있다.

```javascript
var globalObj = this;

function ObjConstructor() {
  this.varA = 10;
}

var obj1 = ObjConstructor();
console.log(obj1);  //undefined
console.log(varA);  //10

var obj2 = new ObjConstructor();
console.log(obj2);  //ObjConstructor {varA: 10}


//arguments.callee를 이용한 생성자 함수 오용 방지
function ObjConstructor2() {
  if(!(this instanceof arguments.callee)) {
    return;
  }
  this.varB = 20;
}

var obj3 = ObjConstructor2();
console.log(obj3);  //undefined
// console.log(varB);  //ReferenceError 발생

var obj4 = new ObjConstructor2();
console.log(obj4);  //ObjConstructor2 {varB: 20}
```

## 이벤트 내의 `this`
- 이벤트를 발생시킨 요소의 객체를 가리킨다.

```html
<!DOCTYPE html>
<html>
<head>
  <meta charset="utf-8" />
  <title>this keyword in event callback</title>
</head>
<body>
  <button>Click here!!</button>  
</body>
<script>
  var buttonObj = document.getElementsByTagName('button')[0];
  buttonObj.onclick = function() {
    console.log(this.toString());
  }
  buttonObj.click();  //[object HTMLButtonElement]
</script>
</html>
```

## 참고
- [PoiemaWeb > JavaScript > 함수 호출 방식에 의해 결정되는 this](https://poiemaweb.com/js-this)
- [w3schools.com > The JavaScript this Keyword](https://www.w3schools.com/js/js_this.asp)
- [MDN web docs : 開発者向けのウェブ技術 > JavaScript > JavaScript リファレンス > 式と演算子 > this](https://developer.mozilla.org/ja/docs/Web/JavaScript/Reference/Operators/this)