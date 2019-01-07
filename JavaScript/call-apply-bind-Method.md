# `call`, `apply`, `bind` method
- 함수에서 사용되는 `this`를 임의로 적용시켜 실행하고 싶을 경우 사용한다.

## `call`와 `apply` 메소드
- `call`과 `apply`메소드를 실행 시 인수로 넣은 객체를 함수에서 사용 될 `this`로 설정하고, 대상 함수를 실행한다.
- 두 메소드는 실행 함수의 매개변수로 넣을 인수 값 설정 방식에서 차이가 있다.

### `call`메소드

구문 | `function.call([thisArg[, arg1[, arg2[, ...]]]])`
----|---------------------------------------------------
`thisArg` | `function`에서 `this`로 사용 할 객체, 비어있을 경우 함수 내 디폴트의 `this`가 사용된다.
`arg1`,`arg2`,`...` | `function`의 인수로 설정 할 값
반환값 | `thisArg`를 `this`로, `arg`를 인수로 설정하여 `function`을 실행 한 결과

### `apply`메소드

구문 | `function.apply([thisArg[, argsArray]])`
----|------------------------------------------
`thisArg` | `function`에서 `this`로 사용 할 객체, 비어있을 경우 함수 내 디폴트의 `this`가 사용된다.
`argsArray` | `function`의 인수로 설정 할 값이 저장되어있는 배열
반환값 | `thisArg`를 `this`로, `argsArray`에 저장된 값을 인수로 설정하여 `function`을 실행한 결과

```javascript
function testFunc(c) {
  return this.a + this.b + c;
}

thisArg = {
  a : 10,
  b : 20
}

var callResult = testFunc.call(thisArg, 30);
console.log(callResult);  //60

var applyResult = testFunc.apply(thisArg, [40]);
console.log(applyResult); //70
```

## `bind`메소드
- 실행 시 인수로 넣은 객체를 함수에서 사용 될 `this`로 설정한 새로운 함수를 반환한다.

구문 | `function.bind(thisArg[, arg1[, arg2[, ...]]])`
----|----------------------------------------------
`thisArg` | `function`에서 this로 사용 할 객체
`arg1`, `arg2`, `...` | 바인드된 함수를 실행 할 때, 설정되는 인수의 앞에 붙는 데이터
반환값 | `thisArg`를 `this`로 바인딩한 함수

```javascript
function testFunc(c) {
  return this.a + this.b + c;
}

thisArg = {
  a : 10,
  b : 20
}

var bindFunc = testFunc.bind(thisArg, 50);
var bindResult = bindFunc();
console.log(bindResult);  //80
```

## `bind`메소드 vs. `call`&`apply`메소드
- `bind`메소드가 적용된 함수를 `call`이나 `apply`메소드를 통해 실행하였을 경우 `bind`메소드를 이용해 설정한 `this`가 적용된다. (`call`과 `apply`메소드에서 설정한 `this`는 무시된다.)

```javascript
function testFunc(c) {
  return this.a + this.b + c;
}

thisForBind = {
  a : 1,
  b : 2
}

thisForCallOrApply = {
  a : 10,
  b : 20
}

var bindFunc = testFunc.bind(thisForBind);
var callResult = bindFunc.call(thisForCallOrApply, 30);
console.log(callResult); //33

var applyResult = bindFunc.apply(thisForCallOrApply, [30]);
console.log(applyResult); //33
```

## 참고
- [MDN web docs : 開発者向けのウェブ技術 > JavaScript > JavaScript リファレンス > 標準ビルトインオブジェクト > Function > Function.prototype.call()](https://developer.mozilla.org/ja/docs/Web/JavaScript/Reference/Global_Objects/Function/call)
- [MDN web docs : 開発者向けのウェブ技術 > JavaScript > JavaScript リファレンス > 標準ビルトインオブジェクト > Function > Function.prototype.apply()](https://developer.mozilla.org/ja/docs/Web/JavaScript/Reference/Global_Objects/Function/apply)
- [MDN web docs : 開発者向けのウェブ技術 > JavaScript > JavaScript リファレンス > 標準ビルトインオブジェクト > Function > Function.prototype.bind()](https://developer.mozilla.org/ja/docs/Web/JavaScript/Reference/Global_Objects/Function/bind)
- [Hatena Blog > かもメモ > JS call apply vs bind アロー関数](https://chaika.hatenablog.com/entry/2017/04/21/083000)