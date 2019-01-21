# Date Object
- 날짜나 시간을 다루는데 사용되는 객체이다.
- 1970년 1월 1일 (UTC)부터 밀리초 단위를 사용하는 것이 표준으로 되어 있다.
- 밀리초 단위는 사용 상 불편하기 때문에 Date 객체가 단위 변환 메소드 및 계산 메소드를 제공한다. 

## Date Object 생성

구문 | 인수 | 반환 시각
----|------|-----------
`new Date()` | - | 현재 시간
`new Date(value)` | 밀리초 단위의 수치 | `value`에 해당하는 시간
`new Date(dateString)` | 시간을 나타내는 문자열 | `dateString`에 해당하는 시간

구문 | `new Date((year, monthIndex [, day [, hours [, minutes [, seconds [, milliseconds]]]]]));`
----|---------------------------------------------------
`year` | 년도. 0~99를 넣을경우(생략년도) 1900~1999년에 해당하지만, 2000년 이후 호환성을 위해 생략년도는 사용하지 않는 것이 좋다.
`monthIndex` | **0~11이 1~12월 달에 해당한다.** ([가리키려는 달 - 1]의 숫자를 설정)
`day` | 1~31이 1~31일에 해당한다.
`hours` | 0~23이 0~23시에 해당한다.
`minutes` | 0~59이 0~59분에 해당한다.
`seconds` | 0~59이 0~59초에 해당한다.
`milliseconds` | 0~999이 0~999밀리초에 해당한다.

```javascript
var nowDate = new Date();
console.log(nowDate); //Sun Jan 20 2019 20:51:41 GMT+0900 (한국 표준시)

var dateFromValue = new Date(86400000);
console.log(dateFromValue); //Fri Jan 02 1970 09:00:00 GMT+0900 (한국 표준시)

var dateFromStr = new Date('2000-01-02');
console.log(dateFromStr); //Sun Jan 02 2000 09:00:00 GMT+0900 (한국 표준시)

var dateFromYearMonth = new Date(2019, 0);
console.log(dateFromYearMonth); //Tue Jan 01 2019 00:00:00 GMT+0900 (한국 표준시)
```
- TimeZone은 시스템의 Local TimeZone을 따른다.

## Date Object Method

### `Date.now()`
- 현재의 시간에 대응하는 수치를 반환한다.
- 즉 1970년 1월 1일(UTC) 00:00:00부터 지금까지 경과한 밀리초를 나타내는 수치를 반환한다.

```javascript
var nowTime = Date.now();
var afterOneSec;
setTimeout(function() {
  afterOneSec = Date.now();
  var intervalSec = Math.floor((afterOneSec - nowTime)/1000);
  console.log('Executed after ' + intervalSec + 'sec');  //Executed after 1sec
}, 1000);
```

### `Date.parse(dateString)`
- `dateString`을 분석하여 그에 맞는 시간에 대응하는 수치를 반환한다.
- 문자열 분석 방법은 브라우저에 따라 다르므로, ISO-8601 format으로 문자열을 넣는 것이 바람직하다. (IE9 이후에서는 모든 브라우저에서 사용가능)
- 분석이 가능하지 않으면 `NaN`을 반환한다.

```javascript
//날짜
var dateValue1 = Date.parse('2010-01-02');
console.log(dateValue1);  //1262390400000
//날짜 + 시간
var dateValue2 = Date.parse('2010-01-02T11:22:33+09:00');
console.log(dateValue2);  //1262398953000
```

### `Date.UTC((year, monthIndex [, day [, hours [, minutes [, seconds [, milliseconds]]]]]))`
- `new Date((year, monthIndex [, day [, hours [, minutes [, seconds [, milliseconds]]]]]));`와 유사하나 UTC 기준의 시간에 해당하는 수치를 반환한다.

```javascript
var localDate = new Date(2019, 0);
console.log(localDate.toUTCString()); //Mon, 31 Dec 2018 15:00:00 GMT

var UTCDate = new Date(Date.UTC(2019, 0));
console.log(UTCDate.toUTCString()); //Tue, 01 Jan 2019 00:00:00 GMT
```

## Date Instance Method

### 단위별 값 획득 및 값 수정

단위 | 값 획득 메소드 | 값 수정 메소드
----|---------------|---------------
년 | `getFullYear()` | `setFullYear()`
월 | `getMonth()` | `setMonth()`
일 | `getDate()` | `setDate()`
요일 | `getDay()` | -
시간 | `getHours()` | `setHours()`
분 | `getMinutes()` | `setMinutes()`
초 | `getSeconds()` | `setSeconds()`
밀리초 | `getMilliseconds()` | `setMilliseconds()`

※ 메소드에는 `Date.prototype.`을 생략하여 표기 함
- `getDate()` 반환값 0~6까지가 일요일~토요일을 나타낸다.

```javascript
var date = new Date();

date.setFullYear(2010);
date.setMonth(0);
date.setDate(2);
date.setHours(11);
date.setMinutes(22);
date.setSeconds(33);
date.setMilliseconds(444);

console.log(date.toString()); //Sat Jan 02 2010 11:22:33 GMT+0900 (한국 표준시)
console.log(date.getFullYear());  //2010
console.log(date.getMonth()); //0
console.log(date.getDate());  //2
console.log(date.getDay()); //6
console.log(date.getHours()); //11
console.log(date.getMinutes()); //22
console.log(date.getSeconds()); //33
console.log(date.getMilliseconds());  //444
```

### 문자열로 반환

반환 종류 | 구문
---------|------
날짜 | `Date.prototype.toDateString()`
시간 | `Date.prototype.toTimeString()`
날짜 + 시간  | `Date.prototype.toString()`

```javascript
var date = new Date('2010-01-02T11:22:33+09:00');
console.log(date.toDateString()); //Sat Jan 02 2010
console.log(date.toTimeString()); //11:22:33 GMT+0900 (한국 표준시)
console.log(date.toString()); //Sat Jan 02 2010 11:22:33 GMT+0900 (한국 표준시)
```

### 그 외

구문 | 설명
----|------
`Date.prototype.getTime()` | 시간에 해당하는 수치를 반환한다.
`Date.prototype.setTime()` | 수치에 해당하는 시간을 설정한다.
`Date.prototype.getTimezoneOffset()` | UTC와 Local TimeZone차이를 분 단위로 반환한다.

```javascript
var date = new Date('2010-01-02T11:22:33+09:00');

var dateToValue = date.getTime();
date.setTime(dateToValue + 1000);

console.log(dateToValue); //1262398953000
console.log(date);  //Sat Jan 02 2010 11:22:34 GMT+0900 (한국 표준시)

//UTC = KST - 9h
var timeZoneOffset = date.getTimezoneOffset() / 60;
console.log(timeZoneOffset);  //-9
```

## 참고
- [MDN web docs : Web technology for developers > JavaScript > JavaScript reference > Standard built-in objects > Date](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Date)
- [PoiemaWeb : JavaScript > 날짜와 시간을 위한 Date 객체](https://poiemaweb.com/js-date)