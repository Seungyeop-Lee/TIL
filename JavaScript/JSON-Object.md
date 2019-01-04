# JSON Object
- JSON 문자열을 분석하여 객체로 만드는 메소드(`parse`)와 객체를 JSON 문자열로 변환하는 메소드(`stringify`)를 가진 객체이다.

## `JSON.parse()`
- 문자열을 JSON으로서 분석하여 객체를 만들어 반환한다.
- 문자열이 유효한 JSON형식이 아닐경우 `SyntaxError` 예외가 발생한다.

구문 | JSON.parse(text[, reviver])
-----|----------------------------
`text` | JSON으로서 분석 할 문자열
`reviver` | text를 분석하여 객체를 만들기 전 변환방법을 지정 한 함수. null인 경우 분석 결과 그대로 객체로 만든다. 초기치는 null
반환값 | JSON문자열을 분석하여 만든 객체

```javascript
var jsonStr = '{"a" : 1}';

var jsonObj = JSON.parse(jsonStr);
console.log(jsonObj); //Object {a: 1}
```

### `reviver` 설정 함수
- `reviver`에 설정하는 함수의 매개변수로 `key`와 `value`를 사용 할 수 있다.
- return값이 key에 해당하는 value로 재설정되어 객체로 만들어진다.
- `this`가 가리키는 것은 함수 실행 당시의 key와 value로 이루어진 객체다. 마지막 실행시에는 `{"" : 반환 객체}`
- `reviver`에 설정된 함수는 JSON문자열의 키의 갯수 + 1번 반복되어 실행된다. (JSON의 속성 + "" : 반환 객체)
- `{"" : 반환 객체}`페어가 `this`로 설정될 때 (`reviver`설정 함수가 마지막으로 호출될 때) return값으로 설정한 값이 최종적으로 반환되는 값이 된다.
```javascript
var jsonStr = '{"a" : 1}';
var reviverFunc = function(key, value) {
  if(key !== "") {
    console.log(key); //a
    console.log(value); //1
    console.log(this);  //Object {a: 1}
    return value + 10;
  } else {
    console.log(key); //(빈 문자열)
    console.log(value); //Object {a: 11}
    console.log(this);  //Object {"": Object}
    return value; //이 구문이 없을경우 아무 값도 반환되지 않는다.
  }
}

var jsonObj = JSON.parse(jsonStr, reviverFunc);
console.log(jsonObj); //Object {a: 11}
```

### 주의점
- JSON 문자열에서는 배열이나 객체의 값의 마지막에 콤마(,)가 들어가 있을 경우 예외가 발생한다. (자바스크립트의 배열, 객체의 문법에서는 허용)

```javascript
var obj = {"a" : 1, };
console.log(obj); //Object {a: 1}

var jsonStr = '{"a" : 1, }';
var jsonObj = JSON.parse(jsonStr);  //SyntaxError: Unexpected token } in JSON at position 10
```

## `JSON.stringify()`
- 인수로 설정된 객체를 JSON문자열로 변환하여 반환한다.
- 객체분석 시 `undefined`, 함수, 심볼이 포함되어 있는 속성은 변환 대상에서 제외된다.
- `enumerable`이 false인 속성은 변환 대상에서 제외된다.

구문 | `JSON.stringify(value[, replacer[, space]])`
----|----------------------------------------------
`value` | JSON문자열로 만들 객체
`replacer` | JSON문자열로 만들기 전 변환방법을 지정한 함수 또는 변환 대상 키의 목록을 지정 한 배열. `null`인 경우 분석 결과 그대로 JSON 문자열로 변환한다.
`space` | 공백 및 탭을 삽입 할 때 사용. 숫자를 넣으면 숫자만큼의 공백을, 문자를 넣으면 그 문자를 속성 사이에 삽입한다. (JSON문자열의 가독성 향상 목적으로 사용)
반환값 | 객체를 분석하여 변환한 JSON문자열

```javascript
var obj = {"a" : 1};

var jsonStr1 = JSON.stringify(obj);
console.log(jsonStr1);  //{"a":1}

var jsonStr2 = JSON.stringify(obj, null, 1);
console.log(jsonStr2);
/* 
{
 "a": 1
}
*/

var jsonStr3 = JSON.stringify(obj, null, '\t');
console.log(jsonStr3);
/* 
{
	"a": 1
} 
*/
```

### `replacer` 상세 설명
- `replacer`는 함수나 배열을 설정 할 수 있다.

#### 함수 설정
- `replacer`에 설정하는 함수의 매개변수로 `key`와 `value`를 사용 할 수 있다.
- return값이 속성의 key에 해당하는 value로 설정되어 JSON문자열로 변환되지만, return한 값의 종류에 따라 변환 대상에서 제외되기도 한다.
- `this`가 가리키는 것은 변환 대상 객체이다. 처음 실행시에는 `{"" : 변환 대상 객체}`
- `replacer`는 객체의 속성 갯수 + 1번 반복되어 실행된다. ("" : 변환 대상 객체 + 객체의 속성)
- `{"" : 변환 대상 객체}`페어가 `this`로 설정될 때 (`replacer`설정 함수가 처음으로 호출될 때) return값으로 설정한 값이 변환 대상 객체로 설정된다.

```javascript
var obj = {"a" : 1};
var replacerFunc = function(key, value) {
  if(key === "") {
    console.log(key); //(빈 문자열)
    console.log(value); //Object {a: 1}
    console.log(this);  //Object {"": Object}
    return value; //이 구문이 없을경우 변환 객체가 없는것으로 간주된다.
  } else {
    console.log(key); //a
    console.log(value); //1
    console.log(this);  //Object {a: 1}
    return value + 10;
  }
}

var jsonStr = JSON.stringify(obj, replacerFunc);
console.log(jsonStr); //{"a":11}
```

- *return된 값의 종류에 따른 JSON문자열 변환 거동차이*

자료형 | JSON문자열 변환 거동
------|---------------------
number, string, boolean, null | return된 값 그대로 적용되어 JSON 문자열 변환 대상이 된다.
object | return된 객체에 대해 재귀적으로 JSON문자열 변환을 시도한다. 객체가 함수일 경우 해당 속성은 변환 대상에서 제외된다.
undefined | 해당하는 속성은 변환 대상에서 제외된다.

#### 배열 설정
- 배열의 값에 해당하는 키를 가지고 있는 속성만이 JSON문자열 변환 대상이 된다.

```javascript
var obj = {"a" : 1, "b" : 2, "c" : 3};
var replacerArr = ["b"];

var jsonStr = JSON.stringify(obj, replacerArr);
console.log(jsonStr); //{"b":2}
```

### toJSON 속성
- 객체의 속성 중 `toJSON`이라는 키에 값이 함수라면(메소드), `toJSON`이 `stringify`메소드 로직 실행 전에 실행된다. (`toJSON`에서 return된 값이 `stringify`의 `value`인수에 설정된다.)
- 그러므로 `toJSON`을 이용하여 JSON문자열 변환방법을 커스터마이징 할 수 있다.
- `toJSON`의 매개변수로 한 개의 값이 설정되며, 상황에 따라 다른 값이 설정된다.

- *상황에 따른 `toJSON`의 매개변수로 설정되는 값*

상황 | 매개변수
----|---------
`toJSON`이 존재하는 객체가 속성의 값일 경우 | 속성의 키
`toJSON`이 존재하는 객체가 배열의 값일 경우 | 배열의 index
`toJSON`이 존재하는 `stringify`메소드의 `value`로 직접 설정 한 경우 | 빈 문자열

```javascript
var obj = {
  param : undefined,
  toJSON : function(param) {
    this.param = param;
    return this;
  }
};
var inObj = {"a" : obj};
var inArr = [obj];

console.log(JSON.stringify(inObj));  //{"a":{"param":"a"}}
console.log(JSON.stringify(inArr));  //[{"param":"0"}]
console.log(JSON.stringify(obj)); //{"param":""}
```

## 참고
- [MDN web docs : 開発者向けのウェブ技術 > JavaScript > JavaScript リファレンス > 標準ビルトインオブジェクト > JSON](https://developer.mozilla.org/ja/docs/Web/JavaScript/Reference/Global_Objects/JSON)