# String (문자열)
- 기본 타입 중 하나로서 문자의 배열을 나타낸다.
- 작은 따옴표나 큰 따옴표로 문자을 쌓거나 String Constructor를 이용해 정의 하는 것이 가능하다.

```javascript
var strWithSingleQuotation = 'strWithSingleQuotation';
var strWithDoubleQuotation = "strWithDoubleQuotation";
var strWithStringConstructor = String(123);

console.log(strWithSingleQuotation);  //strWithSingleQuotation
console.log(strWithDoubleQuotation);  //strWithDoubleQuotation
console.log(strWithStringConstructor);  //123
```

## 이스케이프 문자
- 특수 한 문자는 이스케이프 문자를 이용하여 표기한다.
- 이스케이프 문자는 백슬러쉬(`\`)와 영문자로 구성되어 있다.

코드 | 출력 결과
----|-----------
`\0` | NULL 문자
`\'` | 작은 따옴표
`\"` | 큰 따옴표
`\\` | 백슬러쉬 (\문자)
`\n` | 개행 문자
`\r` | 캐리지 리턴
`\v` | 수직 탭
`\t` | 수평 탭
`\b` | 백 스페이스
`\uXXXX` | 유니코드 xxxx에 해당하는 문자

## 긴 문자열 정의
- 문자열의 길이가 길어지면 코드의 가독성이 저하된다.
- 실제로는 개행이 되지않지만 코드 안에서는 개행이되는 방법이 있으며, 그 사용법은 아래와 같다.

### `+`연산자 이용 방법
- 문자열과 문자열을 `+`연산자로 연결 할 경우 문자열이 연결된다.

```javascript
var longStr = 'abcde' +
              '12345' + 
              'ABCDE';
console.log(longStr); //abcde12345ABCDE
```

### `\`이용 방법
- 같은 따옴표 안이라도 코드의 개행이 임의로 될 경우 에러가 발생한다. 
- JavaScript 인터프리터가 1줄을 1개의 완결된 명령으로 해석하기 때문이다.
- `\`를 따옴표 안의 줄의 마지막에 사용 할 경우 인터프리터가 완결된 명령이 아니라고 해석하므로 에러가 발생하지 않는다.

```javascript
var longStr = 'abcde\
12345\
ABCDE';
console.log(longStr); //abcde12345ABCDE
```

## 참고
- [MDN web docs : 開発者向けのウェブ技術 > JavaScript > JavaScript リファレンス > 標準ビルトインオブジェクト > String](https://developer.mozilla.org/ja/docs/Web/JavaScript/Reference/Global_Objects/String)