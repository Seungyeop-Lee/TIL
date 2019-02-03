# String Object
- 문자열에 대한 여러가지 메소드를 포함하고 있는 객체이다.
- 문자열은 primitive type이지만 `.`접근자를 이용 할 경우 내부적으로는 String 객체로 변환 후, prototype에 정의된 메소드의 실행이 가능하다.
```javascript
var str = 'abcde';
console.log(typeof str);  //string
console.log(str.length);  //5
```

## String Object Method

### `String.fromCharCode()`
- 인수로 설정한 숫자를 유니코드로 해석하여 그에 맞는 문자열을 반환한다.

구문 | `String.fromCharCode(num1[, ...[, numN]])`
----|-----------------------------------------
`num1, ..., num N` | 유니코드의 값
반환값 | 인수로 넣은 숫자들에 해당하는 유니코드로 이루어진 문자열

```javascript
var strFromUnicode = String.fromCharCode(65,66,67);
console.log(strFromUnicode);  //ABC
```

## String Instance Property

### `String.length`
- 문자열의 코드 단위의 수를 반환한다.
- JavaScript는 UTF-16을 사용하기 때문에 1문자당 2바이트가 사용된다.
- 몇몇 특수한 문자를 표현하기 위해서는 2바이트가 넘게 사용되는 경우가 있고, 이 경우 `length`의 값은 1이 넘게 된다.
- 그러므로 실제의 문자열의 길이와는 일치하지 않는 경우가 생길 수 있다.
- 빈 문자열인 경우 0을 반환한다.

## String Instance Method

### `String.prototype.charAt()`
- 인수로 설정된 인덱스에 해당하는 위치의 문자열을 반환한다.

구문 | `str.charAt(index)`
----|------------------------------
`index` | 0부터 length-1 사이의 정수, 설정하지 않을경우 자동으로 0이 삽입된다.
반환값 | `index`의 위치에 있는 문자열, `index`가 범위를 초과한 경우 빈 문자열

```javascript
var str = 'abcde';
console.log(str.charAt(4)); //e
console.log(str.charAt(5)); //빈 문자열
```

- `[]`접근자를 이용하면 같은 결과를 얻을 수 있다.
- 차이점은 범위를 초과한 경우 `undefined`가 반환된다.

```javascript
var str = 'abcde';
console.log(str[4]);  //e
console.log(str[5]);  //undefined
```

### `String.prototype.charCodeAt()`
- 인수로 설정된 인덱스에 있는 문자의 UTF-16코드를 반환한다.
- 2자 이상의 UTF-16코드로 표현된 문자의 경우, 첫번째 UTF-16코드가 반환된다.

구문 | `str.charCodeAt(index)`
----|------------------------
`index` | 문자열의 인덱스
반환값 | 인덱스에 있는 문자의 UTF-16코드, 인덱스가 범위 밖이면 `NaN`

```javascript
var str = 'abcde';
console.log(str.charCodeAt(4)); //101
console.log(str.charCodeAt(5)); //NaN
```

### `String.prototype.concat()`
- 문자열과 문자열을 연결하여 새로운 문자열을 반환한다.

구문 | `str.concat(string2[, string3, ..., stringN])`
----|----------------------------------------------
`string2[, string3, ..., stringN]` | `str`과 연결 할 문자열
반환값 | `str`과 `string2[, string3, ..., stringN]`을 연결 한 문자열

```javascript
var str = 'a';
var connectedStr = str.concat('b', 'c', 'd', 'e');
console.log(connectedStr);  //abcde
```

### `String.prototype.indexOf()`
- 인수로 넣은 문자열과 동일한 문자열이 존재하는 인덱스를 반환한다.
- 낮은 인덱스부터 검색한다. (`fromIndex` -> `str.length`)

구문 | `str.indexOf(searchValue[, fromIndex])`
----|---------------------------------------
`searchValue` | 검색하려는 문자열, 빈 문자열인 경우 유효한 모든 인덱스에 일치 가능하다.
`fromIndex` | 검색을 시작하는 인덱스, 초기치는 0, 0보다 작을 경우 0부터 `str.length`를 넘어설 경우 `str.length`부터 검색
반환값 | `str`의 `fromIndex`인덱스 부터 `searchValue`이 처음 출현한 인덱스를 반환, 없으면 -1을 반환

```javascript
var str = 'aa';
console.log(str.indexOf('a'));  //0
console.log(str.indexOf('a', 1));  //1
```

### `String.prototype.lastIndexOf()`
- 인수로 넣은 문자열과 동일한 문자열이 존재하는 인덱스를 반환한다.
- 높은 인덱스부터 검색한다. (`fromIndex` -> 0)

구문 | `str.lastIndexOf(searchValue[, fromIndex])`
----|---------------------------------------
`searchValue` | 검색하려는 문자열, 빈 문자열인 경우 유효한 모든 인덱스에 일치 가능하다.
`fromIndex` | 검색을 시작하는 인덱스, 초기치는 `+Infinity`, 0보다 작을 경우 0만 `str.length`를 넘어설 경우 `str.length`부터 검색
반환값 | `str`의 `fromIndex`인덱스 부터 `searchValue`이 처음 출현한 인덱스를 반환, 없으면 -1을 반환

```javascript
var str = 'aa';
console.log(str.lastIndexOf('a'));  //1
console.log(str.lastIndexOf('a', 0));  //0
```

### `String.prototype.localeCompare()`
- 실행이 되는 문자열과 인수로 설정된 문자열을 문자열 순서를 기준으로 비교한 결과를 반환한다.

구문 | `str.localeCompare(compareString)`
----|------------------------------------
`compareString` | 비교 대상이 되는 문자열
반환값 | `str`이 `compareString`보다 순서가 앞이면 -1, 순서가 뒤면 1, 같으면 0

```javascript
console.log('a'.localeCompare('b'));  //-1
console.log('b'.localeCompare('a'));  //1
console.log('a'.localeCompare('a'));  //0
```

### `String.prototype.replace()`
- 문자열의 일부 또는 전체 내용을 치환한 새로운 문자열을 반환한다.
- 0부터 length-1순으로 치환대상 문자열 검색을 검색한다.
- 첫번째로 동일하다고 확인 한 부분만 치환됨을 주의한다.

구문 | `str.replace(substr, newSubstr)`
----|----------------------------------
`substr` | 치환 될 문자열
`newSubstr` | 치환 할 문자열
반환값 | `str`에 `substr`과 동일한 부분을 `newSubstr`로 치환한 문자열

```javascript
var str = 'aba';

var replacedStr1 = str.replace('a','c');
console.log(replacedStr1);  //cba

var replacedStr2 = replacedStr1.replace('a', 'c');
console.log(replacedStr2);  //cbc
```

### `String.prototype.slice()`
- 지정한 범위의 문자열을 추출하여 새로운 문자열을 반환한다.

구문 | `str.slice(beginIndex[, endIndex])`
----|-------------------------------------
`beginIndex` | 추출 시작 인덱스
`endIndex` | 추출 종료 인덱스
반환값 | `beginIndex`부터 `endIndex-1`까지의 문자열을 추출한 새로운 문자열

```javascript
var str = 'abcde';

console.log(str.slice(1, 4)); //bcd
```

### `String.prototype.substring()`
- 지정한 범위의 문자열을 추출하여 새로운 문자열을 반환한다.

구문 | `str.substring(indexStart[, indexEnd])`
----|------------------------------------------
`beginIndex` | 추출 시작 인덱스
`endIndex` | 추출 종료 인덱스
반환값 | `beginIndex`부터 `endIndex-1`까지의 문자열을 추출한 새로운 문자열

```javascript
var str = 'abcde';

console.log(str.substring(1, 4)); //bcd
```

### `String.prototype.substr()`
- 지정한 인덱스부터 지정한 길이만큼의 문자열을 추출하여 새로운 문자열을 반환한다.

구문 | `str.substr(start[, length])`
----|-------------------------------
`start` | 추출 시작 인덱스
`length` | 추출 할 문자열의 길이, 없으면 문자열의 끝까지 추출
반환값 | `start`부터 `length`만큼의 문자열을 추출한 새로운 문자열

```javascript
var str = 'abcde';

console.log(str.substr(1, 3)); //bcd
```

### `String.prototype.split()`
- 구분자를 기준으로 문자열을 잘라 배열에 담아 반환한다.

구문 | `str.split([separator[, limit]])`
----|-----------------------------------
`separator` | 문자열을 나눌 구분자, 없으면 문자열은 잘리지 않고 1개의 아이템으로서 배열에 담긴다.
`limit` | 반환 되는 배열의 아이템 갯수제한, 없으면 문자열의 끝까지 전부 배열에 담긴다.
반환값 | `separator`로 구분된 문자열을 `limit`만큼 담은 배열

```javascript
var str = 'a;b;c;d;e';
console.log(str.split(';',3));  //['a','b','c']
console.log(str.split()); //['a;b;c;d;e']
console.log(str.split("")); //['a',';','b',';','c',';','d',';','e']
```

### `String.prototype.toLowerCase()`
- 문자열을 전부 **소문자**로 바꾼 새로운 문자열을 반환한다.

```javascript
var str = 'abCDe';
console.log(str.toLowerCase()); //abcde
```

### `String.prototype.toUpperCase()`
- 문자열을 전부 **대문자**로 바꾼 새로운 문자열을 반환한다.

```javascript
var str = 'abCDe';
console.log(str.toUpperCase()); //ABCDE
```

### `String.prototype.trim()`
- 문자열의 앞과 뒤에 있는 공백(스페이스, 탭)을 삭제한 새로운 문자열을 반환한다.

```javascript
var str = '   abc       ';
console.log(str.trim()); //abc
```

## 참고
- [MDN web docs : 開発者向けのウェブ技術 > JavaScript > JavaScript リファレンス > 標準ビルトインオブジェクト > String](https://developer.mozilla.org/ja/docs/Web/JavaScript/Reference/Global_Objects/String)