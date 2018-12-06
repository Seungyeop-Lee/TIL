# Array
- 자바스크립트에서 가장 많이 사용되는 자료구조

## 선언과 이용
- 선언
  - 모든 자료형(기본 가료형, 함수, 배열)을 저장 가능하다.
  - `new Array(number)`일 경우 number의 수 만큼의 크기를 갖는 배열이 생성된다. number가 0 ~ 2<sup>32</sup>-1 사이의 정수이여야 하며, 그렇지 않을 경우 `RangeError`가 발생한다.
```JavaScript
var array1 = [1, "String", true, null, undefined, function(){}, ["array1_2"]];  //가장 많이 사용하는 형식
var array2 = new Array(1, 2, 3, 4, 5);
var array3 = new Array(5);  //매개변수의 길이를 갖는 빈 배열 생성
```
- 이용

   데이터 추가 | 데이터 추출 | 데이터 복사 
  ----------|----------|----------
  `array[index] = value`|`variable = array.pop()`|`variable = array[index]`
  `array.push(value)`|`variable = array.shift()`|`variable = array['index']`
  `array.unshift(value)`| - | - 
```Javascript
var array = [10];

//데이터 추가
array[1] = 20;
console.log(array); //[10, 20]

array.push(30);
console.log(array); //[10, 20, 30]

array.unshift(0);
console.log(array); //[0, 10, 20, 30]


//데이터 추출
var data1 = array.pop();
console.log(array); //[0, 10, 20]
console.log(data1); //30

var data2 = array.shift();
console.log(array); //[10, 20]
console.log(data2); //0


//데이터 복사
var data3 = array[0];
console.log(array); //[10, 20]
console.log(data3); //10

var data4 = array['1'];
console.log(array); //[10, 20]
console.log(data4); //20
```
----------------------------------------
## 내장 속성

#### `Array.prototype.length`
- 배열의 길이를 저장하고 있다.
- 배열의 길이는 가변적, 값을 저장하지 않으면 초기값(undefined)이 저장된다.
```JavaScript
var a = [];
console.log(a.length); //0
a[500] = undefined;
console.log(a.length); //501
console.log(a[250]); //undefined
```
----------------------------------------
## 내장 메서드

### Mutator methods
- 메서드가 실행되는 배열 자체를 변경한다.

#### `Array.prototype.reverse()`
- 배열에 저장되어 있는 데이터를 역순으로 변경한다.
```JavaScript
var array = [0, 1, 2, 3, 4];
array.reverse();
console.log(array); //[4, 3, 2, 1, 0]
```

#### `Array.prototype.sort([CompareFunction])`
- 데이터를 오름차순으로 정렬한다.
- `CompareFunction`을 인수로 넣어줬을 경우 `CompareFunction`을 토대로 정렬한다. (`CompareFunction`은 java의 `Comparator`와 동일)
```JavaScript
var array = [2, 4, 5, 5, 1, 9];

//오름차순 정렬
array.sort();
console.log(array); //[1, 2, 4, 5, 5, 9]

//내림차순 정렬
array.sort((a, b) => {
  if(a < b) {
    return 1;
  } else if(a > b) {
    return -1;
  }
  return 0;
});
console.log(array); //[9, 5, 5, 4, 2, 1]
```

#### `Array.prototype.splice(start[, deleteCount[, item1[, item2[, ...]]]])`
- `start`에 해당하는 index부터 `deleteCount`갯수만큼 잘라내고, `item`을 잘라낸 위치에 추가한다.
- `deleteCount`의 초기값은 `array.length - start`
```JavaScript
var array = [0, 10, 20, 30, 40, 50, 60];

//Array.prototype.splice(start)
var splicedArray1 = array.splice(5);
console.log(array); //[0, 10, 20, 30, 40];
console.log(splicedArray1);  //[50, 60];

//Array.prototype.splice(start, deleteCount)
var splicedArray2 = array.splice(0, 2);
console.log(array); //[20, 30, 40];
console.log(splicedArray2); //[0, 10];

//Array.prototype.splice(start, deleteCount, item)
var splicedArray3 = array.splice(1, 1, 99);
console.log(array); //[20, 99, 40];
console.log(splicedArray3); //[30];
```

#### `Array.prototype.fill(value[, start[, end]])`
- `value`값으로 `start`에 해당하는 index부터 `end-1`에 해당하는 index까지 채워 넣는다.
- `start`의 초기값은 0, `end`의 초기값은 `array.length`
```JavaScript
var array = [1, 2, 3, 4, 5];

//Array.prototype.fill(value)
array.fill(9);
console.log(array); //[9, 9, 9, 9, 9]

//Array.prototype.fill(value, start)
array.fill('a', 3);
console.log(array); //[9, 9, 9, "a", "a"]

//Array.prototype.fill(value, start, end)
array.fill('b', 0, 2);
console.log(array); //["b", "b", 9, "a", "a"]
```
----------------------------------------
### Accessor methods
- 배열의 값을 접근하여 새로운 배열을 반환한다.
- 메서드가 실행되는 배열은 변경하지 않는다.

#### `Array.prototype.concat(array)`
- 인수로 넣은 배열을 기존 배열의 뒤에 연결한 새로운 배열을 반환한다.
```JavaScript
var frontArray = [10, 20, 30];
var backArray = [40, 50, 60];
var fullArray = frontArray.concat(backArray);
console.log(fullArray); //[10, 20, 30, 40, 50, 60]
```

#### `Array.prototype.includes(searchElement[, fromIndex])`
- `searchElement`에 해당하는 데이터가 있는지 없는지 확인 후 boolean값을 반환한다.
- 검색범위는 `fromIndex`에 해당하는 index부터 `array.length-1`에 해당하는 index까지
- `fromIndex`의 초기값은 0
```JavaScript
var array = [10, 20, 30, 40, 50];

//Array.prototype.includes(searchElement)
var result1 = array.includes(20);
console.log(result1); //true

//Array.prototype.includes(searchElement, fromIndex)
var result2 = array.includes(20, 1);
console.log(result2); //true
var result3 = array.includes(20, 2);
console.log(result3); //false
```

#### `Array.prototype.join([separator])`
- 배열의 데이터를 `separator`로 연결하여 하나의 문자열로 만들어 반환한다.
- `separator`의 초기값은 `','`
```JavaScript
var array = [10, 20, 30, 40, 50];

//Array.prototype.join()
var joinedArray1 = array.join();
console.log(joinedArray1);  //10,20,30,40,50

//Array.prototype.join(separator)
var joinedArray2 = array.join('-');
console.log(joinedArray2);  //10-20-30-40-50
```

#### `Array.prototype.indexOf(searchElement[, fromIndex])`
- `searchElement`에 해당하는 데이터가 존재하는 index를 반환한다.
- 데이터가 존재하지 않으면 -1을 반환한다.
- 검색범위 및 순서는 `fromIndex`에 해당하는 index부터 `array.length-1`에 해당하는 index까지 순차적으로
- `fromIndex`의 초기값은 0
```JavaScript
var array = [10, 20, 30, 20, 50];

//Array.prototype.indexOf(searchElement)
var index1 = array.indexOf(20);
console.log(index1);  //1

//Array.prototype.indexOf(searchElement, fromIndex)
var index2 = array.indexOf(20, 2);
console.log(index2);  //3
```

#### `Array.prototype.lastIndexOf(searchElement)`
#### `Array.prototype.lastIndexOf(searchElement, fromIndex)`
- `searchElement`에 해당하는 데이터가 존재하는 index를 반환한다.
- 데이터가 존재하지 않으면 -1을 반환한다.
- 검색범위 및 순서
  - `fromIndex`가 없는 경우 : `array.length-1`에 해당하는 index부터 index 0까지 순차적으로
  - `fromIndex`가 있는 경우 : `fromIndex`에 해당하는 index부터 index 0까지 순차적으로
```JavaScript
var array = [10, 20, 30, 20, 50];

//Array.prototype.lastIndexOf(searchElement)
var index1 = array.lastIndexOf(20);
console.log(index1);  //3

//Array.prototype.lastIndexOf(searchElement, fromIndex)
var index2 = array.lastIndexOf(20, 2);
console.log(index2);  //1
```

#### `Array.prototype.slice([begin[, end]])`
- `begin`에 해당하는 index부터 `end-1`에 해당하는 index까지의 배열을 반환한다.
- `begin`의 초기값은 0, `end`의 초기값은 `array.length`
```JavaScript
var array = [10, 20, 30, 40, 50];

//Array.prototype.slice()
var slicedArray1 = array.slice();
console.log(slicedArray1);  //[10, 20, 30, 40, 50]

//Array.prototype.slice(begin)
var slicedArray2 = array.slice(1);
console.log(slicedArray2);  //[20, 30, 40, 50]

//Array.prototype.slice(begin, end)
var slicedArray3 = array.slice(1,3);
console.log(slicedArray3);  //[20, 30]
```
----------------------------------------
### Iteration methods
- 배열의 데이터를 매개변수로 하는 콜백함수가 length만큼 반복하여 실행 된다.
- `foreach()`, `filter()`, `map()`, `some()`, `every()`의 경우 `callback` 함수 내 매개변수 및 `thisArg`의 의미

매개변수 | 의미
--------|------
`curruntValue`|현재의 데이터
`index`|배열 상 `curruntValue`의  index
`array`|현재 반복하고 있는 배열의 참조
`thisArg`|`callback` 함수 내에서 `this`가 가르키는 객체를 설정(`this`를 설정하는 것이 일반적, 설정하지 않으면 디폴트의 `this`)

#### `Array.prototype.foreach(callback(curruntValue[, index[, array]])[, thisArg])`
- `array.length`에 해당하는 값만큼 `callback` 함수가 실행된다.
- return값은 `void`
```JavaScript
var array = [10, 20, 30, 40, 50];

var curruntValues = [];
var indexs = [];

//Array.prototype.foreach(callback(curruntValue[, index[, array]]))
var forEachResult = array.forEach(function(v, i, a) {
  curruntValues.push(v);
  indexs.push(i);
  console.log(a); //[10, 20, 30, 40, 50]
});
console.log(curruntValues); //[10, 20, 30, 40, 50]
console.log(indexs);  //[0, 1, 2, 3, 4]
console.log(forEachResult); //undefined
```
#### `Array.prototype.filter(callback(curruntValue[, index[, array]])[, thisArg])`
- `callback` 함수의 실행 결과 `true`면 `curruntValue`를 남기고, `false`면 제외하여 새로운 배열을 반환한다.
```JavaScript
var array = [1, 2, 3, 4, 5];

//Array.prototype.filter(callback(curruntValue))
var filterResult = array.filter(function(v) {
  return v % 2 === 0;
});
console.log(filterResult); //[2, 4]
```
#### `Array.prototype.map(callback(curruntValue[, index[, array]])[, thisArg])`
- `callback` 함수에서 반환되는 값으로 구성된 새로운 배열을 반환한다.
```JavaScript
var array = [1, 2, 3, 4, 5];

//Array.prototype.map(callback(curruntValue))
var mapResult = array.map(function(v) {
  return v * 10;
});
console.log(mapResult); //[10, 20, 30, 40, 50]
```
#### `Array.prototype.some(callback(curruntValue[, index[, array]])[, thisArg])`
- `callback` 함수 실행결과, 1번이라도 `true`가 반환되면 `some()`메소드의 결과로 `true`가 반환된다.
```JavaScript
var array = [1, 2, 3, 4, 5];

//Array.prototype.some(callback(curruntValue))
var someResult = array.some(function(v) {
  return v === 2;
});
console.log(someResult); //true
```
#### `Array.prototype.every(callback(curruntValue[, index[, array]])[, thisArg])`
- `callback` 함수 실행결과, 1번이라도 `false`가 반환되면 `every()`메소드의 결과로 `false`가 반환된다.
```JavaScript
var array = [1, 2, 3, 4, 5];

//Array.prototype.every(callback(curruntValue))
var everyResult = array.every(function(v) {
  return typeof v === 'number';
});
console.log(everyResult); //true
```
#### `Array.prototype.reduce(callback(accumulator, currentValue[, currentIndexOptional[, array]])[, initialValue])`
- `callback` 함수를 실행시켜 반환된 값을 다음 `callback` 함수의 `accumulator`로 설정하는 것을 반복한다.
- 마지막 `callback` 함수를 실행시켜 반환된 값을 `reduce()`메소드의 결과로 반환한다.
- `callback` 함수 내 매개변수 및 `initialValue`의 의미

매개변수 | 의미
--------|------
`accumulator`|`callback`함수가 반복되면서 누산 된 데이터
`currentValue`|현재의 데이터
`currentIndex`|배열 상 `curruntValue`의 index
`array`|현재 반복하고 있는 배열의 참조
`initialValue`|`callback`함수가 최초로 실행되기 전 `accumulator`의 초기 값 설정, 생략하였을 경우 배열의 첫번째 데이터가 초기값으로 지정 됨
```JavaScript
var array = [1, 2, 3, 4];

//Array.prototype.reduce(callback(accumulator, currentValue))
var reduceResult = array.reduce(function(acc, curr) {
  return acc + curr;
});
console.log(reduceResult); //10
```
----------------------------------------
## 참고
- [[부스트코스] 웹 프로그래밍 : 웹 애플리케이션 개발 1/4 > 자바스크립트 배열](https://www.edwith.org/boostcourse-web)
- [MDN web docs : JavaScript reference > Standard built-in objects > Array](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array)