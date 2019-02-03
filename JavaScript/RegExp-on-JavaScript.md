# Regular Expression (JavaScript)
- 자바스크립트는 자체적으로 정규표현식을 지원하는 객체를 제공한다.
- `RegExp` 생성자 메소드를 사용하거나, 정규표현 리터럴(`//`)을 사용하여 RegExp객체 생성이 가능하다.

## `RegExp`객체 생성

### 정규표현 리터럴

구문 | `/regexp/[flag]`
----|------------------
`regexp` | 정규표현식
`flag` | 매칭시 사용 할 옵션
반환값 | `RegExp`객체

### `RegExp` 생성자 메소드

구문 | `new RegExp(regexp[, flag])`
----|------------------------------
`regexp` | 정규표현식을 나타내는 문자열, `\`를 사용 할 경우 `\\`로 입력해야한다. (ex: `\d` → `'\\d'`)
`flag` | 매칭시 사용 할 옵션
반환값 | `RegExp`객체

```javascript
var regexFromLiteral = /\d/;
console.log(regexFromLiteral.toString());  // /\d/

var regexFromConstructor = new RegExp('\\d');
console.log(regexFromConstructor.toString());  // /\d/
```

### `RegExp` 객체의 `flag`
- `flag`를 사용하면 전체 검색이나, 대소문자 무시 검색 등이 가능하다.
- 자바스크립트에서는 5종류의 `flag`를 지원한다.
- 각 `flag`는 같이 사용이 가능하다.

`flag` | 설명
-----|------
`g` | 전체 검색 (이 옵션을 설정하지 않는 경우, 최초의 조건일치 부분만 매칭된다.)
`i` | 대소문자 무시 검색
`m` | 복수행 검색 (위치지정자인 `^`와 `$`를 유효화 시킴)
`u` | 풀 스펙의 유니코드 검색가능
`s` | 대상 문자열의 마지막에 매칭된 위치(인덱스)부터 검색을 시작

```javascript
//단독 사용
var regexObj1 = /\d/g;
var regexObj2 = /\d/i;
var regexObj3 = /\d/m;
var regexObj4 = /\d/u;
var regexObj5 = /\d/s;

//여러개 사용
var regexObj6 = /\d/gim;
```

## 정규표현 사용 메소드
- `RegExp`객체의 `exec()`와 `test()`
  - 매개변수로 문자열을 사용
- 문자열의 `match()`, `replace()`, `search()`, `split()`
  - 매개변수로 `RegExp`객체를 사용

### `RegExp.prototype.exec()`
- 정해진 인덱스부터 검색(최초 실행 시 인덱스는 0)하여 정규표현과 매칭되는 최초의 부분의 결과를 반환한다.
- 매칭된 부분의 마지막 인덱스를 다음 실행시 검색을 시작 할 인덱스로 설정한다.  
  매칭된 부분이 없으면 0으로 초기화한다.(`RegExp`객체의 `lastIndex`속성)
- 실행 후 결과정보를 담은 배열이 반환되며, 문자열 끝까지 검색시 매칭되는 문자열이 없을 경우 null이 반환된다.

구문 | `regexObj.exec(str)`
----|-----------------------
`str` | 검색 대상 문자열
반환값 | 결과정보를 담은 배열

#### 실행 후 반환되는 배열의 속성

속성 | 설명
----|------
`[0]` | 매칭된 부분의 문자열
`[1]...[n]` | 그룹화 구성체로 저장 할 것을 나타낸 부분, 숫자는 그룹화 구성체의 순번이다.
`index` | 매칭된 부분의 시작 인덱스
`input` | 검색 대상 문자열

```javascript
var regexObj = /\d(\d)/;

var result = regexObj.exec('abc12efg34');
console.log(result[0]); //12
console.log(result[1]); //2
console.log(result.index);  //3
console.log(result.input);  //abc12efg34
```

#### `RegExp`객체의 속성

속성 | 설명
----|------
`lastIndex` | 다음 `exec()`나 `test()` 실행 시 검색을 시작 할 인덱스, `flag`에 `g`가 설정되어 있지 않으면 0으로 고정된다.
`ignoreCase` | 대소문자 구분 유무를 나타낸다. `flag`에 `i`가 설정되어 있으면 `true`
`global` | 전체 검색 유무를 나타낸다. `flag`에 `g`가 설정되어 있으면 `true`
`multiline` | 복수행 검색 유무를 나타낸다. `flag`에 `m`가 설정되어 있으면 `true`
`source` | `RegExp`객체에 설정되어 있는 정규표현식을 문자열로 저장 한 속성

```javascript
var regexObj = /\d(\d)/g;
console.log(regexObj.lastIndex);  //0
console.log(regexObj.ignoreCase); //false
console.log(regexObj.global); //true
console.log(regexObj.multiline);  //false
console.log(regexObj.source); //\d(\d)

var result1 = regexObj.exec('abc12efg34');
console.log(result1[0]); //12
console.log(regexObj.lastIndex); //5

var result2 = regexObj.exec('abc12efg34');
console.log(result2[0]); //34
console.log(regexObj.lastIndex); //10

var result3 = regexObj.exec('abc12efg34');
console.log(result3); //null
console.log(regexObj.lastIndex); //0
```

### `RegExp.Prototype.test()`
- 대상 문자열에 정규표현과 매칭되는 문자열의 유무를 확인해서 결과를 반환한다.
- 매칭된 부분의 마지막 인덱스를 다음 실행 시 검색시작 인덱스로 설정한다.  
  매칭된 부분이 없으면 0으로 초기화한다. (`RegExp`객체의 `lastIndex`속성)
- 결과는 boolean으로 반환한다.

구문 | `regexObj.test(str)` 
----|----------------------
`str` | 대상 문자열
반환값 | 매칭되는 문자열이 있으면 `true`, 없으면 `false`를 반환한다.

```javascript
var regexObj = /\d(\d)/g;

var result1 = regexObj.test('abc12efg');
console.log(result1); //true

var result2 = regexObj.test('abc12efg');
console.log(result2); //false
```

### `String.prototype.match()`
- 대상 문자열에 정규표현과 매칭되는 문자열을 찾아서 결과를 반환한다.
- 결과는 배열로 반환되며, 매칭되는 문자열이 없을경우 `null`을 반환한다.

구문 | `str.match(regexp)`
----|---------------------
`regexp` | 검색 조건으로 설정 할 `RegExp`객체
반환값 | 매칭된 문자열을 담은 배열, `flag`로 `g`가 설정되지 않았을 경우 `RegExp.prototype.exec()`의 반환값과 동일형태의 배열

```javascript
var regexObjWithoutG = /\d(\d)/;
var regexObjWithG = /\d(\d)/g;

//RegExp.prototype.exec()의 반환값과 동일한 배열이 반환 됨
var result1 = 'abc12efg34'.match(regexObjWithoutG);
console.log(result1[0]); //12
console.log(result1[1]); //3

//문자열 전체에서 매칭된 부분을 담은 배열이 반환 됨
var result2 = 'abc12efg34'.match(regexObjWithG);
console.log(result2[0]); //12
console.log(result2[1]); //34
```

### `String.prototype.search()`
- 대상 문자열에 정규표현과 매칭되는 문자열의 유무를 확인해서 결과를 반환한다.
- 결과는 매칭된 부분의 시작 인덱스가 반환되며, 매칭되는 문자열이 없는경우 -1이 반환된다.
- 매칭가능 부분이 2개이상이면 낮은 인덱스의 부분의 인덱스가 반환된다.

구문 | `str.search(regexp)`
----|----------------------
`regexp` | 검색 조건으로 설정 할 `RegExp`객체
반환값 | 매칭 부분의 시작 인덱스, 없을 경우 -1

```javascript
var regexObj = /\d(\d)/g;

var result1 = 'abc12efg34'.search(regexObj);
console.log(result1); //3

var result2 = 'abcefg'.search(regexObj);
console.log(result2); //-1
```

### `String.prototype.replace()`
- 대상 문자열에 정규표현과 매칭되는 문자열을 찾은 후, 다른 문자열로 치환 한 새로운 문자열을 반환한다.

구문 | `str.replace(regexp, newSubstr)`
----|---------------------------------
`regexp` | 검색 조건으로 설정 할 `RegExp`객체
`newSubstr` | 치환 할 문자열
반환값 | 정규표현에 매칭된 부분이 `newSubstr`로 치환된 새로운 문자열

#### `newSubstr`에 사용가능 한 패턴

패턴 | 설명
----|------
`$$` | $를 나타낸다.
`$1` | 그룹화 구성체를 통해 저장 한 부분을 나타낸다. $뒤 숫자는 포착 순번을 나타낸다.
<code>$`</code> | 매칭된 부분의 앞쪽 내용을 나타낸다.
`$'` | 매칭된 부분의 뒤쪽 내용을 나타낸다.
`$&` | 매칭된 부분을 나타낸다.

```javascript
var regexObj = /\d(\d)/g;
var str = 'abc[12]efg';

var resultStr1 = str.replace(regexObj, '$$');
console.log(resultStr1); //abc[$]efg

var resultStr2 = str.replace(regexObj, '$1');
console.log(resultStr2); //abc[2]efg

var resultStr3 = str.replace(regexObj, '$`');
console.log(resultStr3); //abc[abc[]efg

var resultStr4 = str.replace(regexObj, "$'");
console.log(resultStr4); //abc[]efg]efg

var resultStr5 = str.replace(regexObj, "$&");
console.log(resultStr5); //abc[12]efg
```

### `String.prototype.split()`
- 정규표현을 이용하여 대상 문자열을 분할한 후, 분할된 문자열을 배열에 담아 반환한다.
- 정규표현에 그룹화 구성체가 속해있을 경우, 그룹화 구성체로 저장된 부분 문자열은 결과 배열에 담긴다.

구문 | `str.split([regex[, limit]])`
----|------------------------------
`regex` | 문자열을 나누는 구분자로서 설정 할 `RegExp`객체
`limit` | 반환되는 배열의 아이템 갯수제한, 생략하면 문자열의 끝까지 전부 배열에 담긴다.
반환값 | `regex`의 매칭부분으로 구분된 부분 문자열을 `limit`만큼 담은 배열. 매칭되는 부분이 없는 경우 문자열은 잘리지 않고 1개의 아이템으로서 배열에 담긴다.

```javascript
var regexObj = /\d\d/;
var str = 'abc12efg';

var result1 = str.split(regexObj);
console.log(result1); //["abc", "efg"]

var result2 = str.split(regexObj, 1);
console.log(result2); //Array(1) ["abc"]

regexObj = /(\d)\d/;
var result3 = str.split(regexObj);
console.log(result3); //["abc", "1", "efg"]

regexObj = /\d(\d)/;
var result4 = str.split(regexObj);
console.log(result4); //["abc", "2", "efg"]
```

## 참고
- [MDN web docs : 開発者向けのウェブ技術 > JavaScript > JavaScript ガイド > 正規表現](https://developer.mozilla.org/ja/docs/Web/JavaScript/Guide/Regular_Expressions)