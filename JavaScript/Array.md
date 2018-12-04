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
array[1] = 20;  //[10, 20]
array.push(30); //[10, 20, 30]
array.unshift(0); //[0, 10, 20, 30]
//데이터 추출
var data1 = array.pop(); //[0, 10, 20]
console.log(data1); //30
var data2 = array.shift();  //[10, 20]
console.log(data2); //0
//데이터 복사
var data3 = array[0]; //[10, 20]
console.log(data3); //10
var data4 = array['1']; //[10, 20]
console.log(data4); //20
```
----------------------------------------
## 내장 속성
#### `Array.prototype.length`
- 배열의 길이를 저장하고 있다.
- 배열의 길이는 가변적, 값을 저장하지 않으면 초기값(undefined)이 저장된다.
```JavaScript
var a = [];
a.length; //0
a[500] = undefined;
a.length; //501
a[250]; //undefined
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
- CompareFunction을 매개변수로 넣어줬을 경우 CompareFunction을 토대로 정렬한다. (CompareFunction은 java의 Comparator와 동일)
```JavaScript
//오름차순 정렬
var array = [2, 4, 5, 5, 1, 9];
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
#### `Array.prototype.splice()`

#### `Array.prototype.fill()`
----------------------------------------
### Accessor methods
- 배열의 값을 접근하여 새로운 배열을 반환한다.
- 메서드가 실행되는 배열은 변경하지 않는다.
#### `Array.prototype.concat()`
#### `Array.prototype.includes()`
#### `Array.prototype.join()`
#### `Array.prototype.indexOf()`
#### `Array.prototype.lastIndexOf()`
#### `Array.prototype.slice()`
----------------------------------------
### Iteration methods
- 배열의 length만큼 반복하여 실행 된다.
- 매개변수로 받은 함수를 콜백한다.
#### `Array.prototype.foreach()`
#### `Array.prototype.filter()`
#### `Array.prototype.map()`
#### `Array.prototype.reduce()`
#### `Array.prototype.some()`
#### `Array.prototype.every()`
----------------------------------------
## 참고
- [[부스트코스] 웹 프로그래밍 : 웹 애플리케이션 개발 1/4 > 자바스크립트 배열](https://www.edwith.org/boostcourse-web)
- [MDN web docs : JavaScript reference > Standard built-in objects > Array](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array)