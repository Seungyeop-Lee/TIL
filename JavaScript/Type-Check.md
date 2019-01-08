# Type Check
- `typeof`키워드, `Object.prototype.toString.call()`, `instanceof`키워드, `function.prototype.constructor`값 비교를 이용하여 type check가 가능하다.

*각 type check 방법의 특징과 단점*

type check 방법 | 특징 | 단점
---------------|------|-------
`typeof`키워드 | primitive 타입과 객체의 구별이 가능하다. | 객체에 대해서는 자세한 구별이 불가
`Object.prototype.toString.call()` | 객체의 [[Class]] 내부 속성에 따라 구별이 가능하다. | 사용자가 선언한 생성자 함수를 이용해 만든 객체는 구별이 불가
`instanceof`키워드, `function.prototype.constructor`값 비교 | 사용자가 선언한 생성자 함수를 이용해 만든 객체의 구별이 가능하다. | prototype 속성 및 prototype.constructor의 값을 임의로 변경하였을 경우 원하는 겨로가가 나오지 않을 수 있다.

## `typeof`키워드

구문 | `typeof operand`
----|------------------
`operand` | 객체나 primitive 타입의 데이터
반환값 | 타입에 따른 문자열

*`operand`에 따른 반환값 일람*

type | 반환값
-----|-------
undefined | "undefined"
null | "object"
boolean | "boolean"
number | "number"
string | "string"
function | "function"
object | "object"

```javascript
//TODO 예제코드 작성
```

## `Object.prototype.toString.call()`
- 객체의 [[Class]] 내부 속성의 값을 포함한 문자열을 반환하는 메소드이다.
- 모든 객체는 Object.prototype을 상속받고 있으므로 `toString`메소드를 직접 사용가능하다.
- 하지만 객체에 따라서는 `toString`을 override한 경우도 있기 때문에 `Object.prototype.toString.call()`을 이용한다.

구문 | `Object.prototype.toString.call(object)`
----|-----------------------------------------
`object` | 확인 할 객체, primitive 타입의 데이터의 경우 자동으로 wrapping된다.
반환값 | 객체의 [[Class]] 내부 속성의 값을 포함한 문자열

```javascript
//TODO 예제코드 작성
```

## `instanceof`키워드

구문 | `object instanceof construtor`
----|--------------------------------
`object` | 확인 할 객체
`construtor` | 생성자 함수
반환값 | `object`의 속성 중 `constructor.prototype`가 존재하면 `true`, 그렇지 않으면 `false`를 반환한다. `object`의 prototype(`__proto__`)내부에 prototype이 존재하는 경우(상속한 경우), 그 prototype도 확인 대상이 된다. (재귀적)

```javascript
//TODO 예제코드 작성
```

## `function.prototype.constructor`값 비교
- 객체가 가지고 있는 prototype의 constructor 속성은 그 객체의 생성자 함수를 가리킨다.
- 이것을 이용하면 type check가 가능하다.

```javascript
//TODO 예제코드 작성
```

## 참고
- [Qiita : JavaScriptの「型」の判定について](https://qiita.com/south37/items/c8d20a069fcbfe4fce85)
- [MDN web docs : JavaScript リファレンス > 式と演算子 > typeof](https://developer.mozilla.org/ja/docs/Web/JavaScript/Reference/Operators/typeof)
- [MDN web docs : JavaScript リファレンス > 式と演算子 > instanceof](https://developer.mozilla.org/ja/docs/Web/JavaScript/Reference/Operators/instanceof)
- [MDN web docs :  JavaScript リファレンス > 標準ビルトインオブジェクト > Object > Object.prototype.toString()](https://developer.mozilla.org/ja/docs/Web/JavaScript/Reference/Global_Objects/Object/toString)