# Scope
- 스코프란 변수가 어떤 위치부터 참조가능한지를 나타내는 것이다. 간단히 말해서 변수의 유효범위를 뜻한다.
- 스코프의 영향유무에 따라 전역 변수(global variable)와 지역 변수(local variable)로 나눌 수 있다.
- 스코프의 형태에 따라서는 전역 스코프(global scope), 지역 스코프(local scope)로 나눌 수 있고, 지역 스코프는 함수 스코프(function scope)와 블록 스코프(block scope)로 나눌 수 있다.
- 실행 시 스코프 결정 방식에 따라서는 동적 스코프(dynamic scope)와 정적 스코프(static scope)로 나눌 수 있다. 정적 스코프는 렉시컬 스코프(lexical scope)로도 불린다.

## 전역 변수와 지역 변수
- 전역변수란 어떤 스코프에서든 사용 가능한 변수를 의미한다.
- 지역변수란 특정 스코프에서만 사용 가능한 변수를 의미한다.

## 전역 스코프와 지역 스코프

### 전역 스코프
- 자바스크립트의 최상위 레벨(중괄호에 속하지 않은 영역)을 의미한다.
- 전역 스코프에서 선언한 변수는 전역번수가 된다. (실제로는 글로벌 객체의 속성으로 저장)

```javascript
var varA = 10;

console.log(varA);  //10

function printVarA(){
  console.log(varA);
};
printVarA();  //10

console.log(varA === window.varA);  //(웹 브라우저 상에서)true
```

### 지역 스코프

#### 함수 스코프
- 함수 내의 영역을 의미한다.
- 함수 스코프에서 선언한 변수는 지역 변수가 된다.
- `var`를 생략하고, 변수명만으로 선언 할 경우 전역 변수가 된다.

```javascript
function printVarB() {
  //var를 붙였을 경우 로컬 변수로 선언
  var varB = 20;
  console.log(varB);
}

printVarB();  //20
// console.log(varB);  //ReferenceError 발생


function printVarC() {
  //var를 생략 할 경우 전역 변수로 선언
  varC = 30;
  console.log(varC);
}

printVarC();  //30
console.log(varC);  //30
```

#### 블록 스코프
- 중괄호({})로 쌓여있는 영역을 말한다. 
- if문, for문, switch문, while문에 사용하는 중괄호도 블록 스코프에 속한다.
- `var`로 선언된 변수는 블록 스코프를 무시하며, 상위 스코프의 영향을 받는다.

```javascript
if(true) {
  //상위 스코프가 전역 스코프이므로 전역 변수로 선언
  var varD = 40;
}
console.log(varD);  //40

function printVarE() {
  var whileFlag = true;
  while(whileFlag) {
    //상위 스코프가 함수 스코프이므로 로컬 변수로 선언
    var varE = 50;
    whileFlag = false;
  }
  console.log(varE);
}

printVarE();  //50
// console.log(varE);  //ReferenceError 발생
```

## 동적 스코프와 정적 스코프

스코프 | 결정방식
------|----------
정적 스코프 | 구문이 선언 된 곳을 기준으로 상위 스코프를 정하는 방식 (실행 전 결정 됨)
동적 스코프 | 구문을 호출 한 곳을 상위 스코프로 정하는 방식 (실행 시 결정 됨)

- 자바스크립트는 정적 스코프를 따른다.

```javascript
var varF = 60;

function callPrintVarF() {
  var varF = 6000;
  printVarF();
}

function printVarF() {
  //정적 스코프를 따를경우 60이 출력
  //동적 스코프를 따를경우 6000이 출력
  console.log(varF);
}

callPrintVarF();  //60
```

## 참고
- [CodeGrid > JavaScriptのスコープ総まとめ > 第1回 スコープの種類とその基本](https://app.codegrid.net/entry/2017-js-scope-1)
- [PoiemaWeb > JavaScript > 스코프](https://poiemaweb.com/js-scope)