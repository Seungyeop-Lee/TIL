# Math Object
- 수학에서 사용되는 상수나 함수를 제공하는 빌트인 객체이다.

## Math Object Property

### `Math.PI`
- 원주율을 저장하고 있는 속성이다.
- 약 3.14159

## Math Object Method

### 올림, 내림, 반올림, 절대값

연산 종류 | 구문
---------|------
올림 | `Math.ceil(x)`
내림 | `Math.floor(x)`
반올림 | `Math.round(x)`
절대값 | `Math.abs(x)`

```javascript
/*---Math.ceil()---*/
console.log(Math.ceil(1.2)); //2
console.log(Math.ceil()); //NaN
console.log(Math.ceil(Object)); //NaN

/*---Math.floor()---*/
console.log(Math.floor(1.8));  //1
console.log(Math.floor());  //NaN
console.log(Math.floor(Object));  //NaN

/*---Math.round()---*/
console.log(Math.round(1.6));  //2
console.log(Math.round());  //NaN
console.log(Math.round(Object));  //NaN

/*---Math.abs()---*/
console.log(Math.abs(-1));  //1
console.log(Math.abs());  //NaN
console.log(Math.abs(Object));  //NaN
```

### 제곱, 제곱근

연산 종류 | 구문
---------|------
제곱 | `Math.pow(x, y)`
제곱근 | `Math.sqrt(x)`

```javascript
/*---Math.pow---*/
console.log(Math.pow(2, 10)); //1024

//인수가 0, 1개만 있거나, number형으로 변환이 불가능 할 경우
console.log(Math.pow(2)); //NaN
console.log(Math.pow()); //NaN
console.log(Math.pow(2, Object)); //NaN


/*---Math.sqrt---*/
console.log(Math.sqrt(9));  //3

//인수가 없거나, number형으로 변환이 불가능 할 경우
console.log(Math.sqrt()); //NaN
console.log(Math.sqrt(Object)); //NaN
```

### 최대, 최소

연산 종류 | 구문
---------|------
최대 | `Math.max([x[, y[, ...]]])`
최소 | `Math.min([x[, y[, ...]]])`

```javascript
var maxNum = Math.max(1, 2, 3, 4, 5);
var minNum = Math.min(1, 2, 3, 4, 5);
console.log(maxNum);  //5
console.log(minNum);  //1

//인수로 아무 값이 없을 경우
console.log(Math.max());  //-Infinity
console.log(Math.min());  //Infinity

//number형으로 변환이 불가능 한 값이 있을 경우
console.log(Math.max(Object));  //NaN
console.log(Math.min(Object));  //NaN
```

### 랜덤값
- `Math.random()`을 사용하여 얻을 수 있다.

```javascript
console.log(Math.random()); //0이상 1미만의 숫자가 랜덤하게 발생
```

## 참고
- [MDN web docs : 開発者向けのウェブ技術 > JavaScript > JavaScript リファレンス > 標準ビルトインオブジェクト > Math](https://developer.mozilla.org/ja/docs/Web/JavaScript/Reference/Global_Objects/Math)