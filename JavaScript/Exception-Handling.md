# 예외 처리

## 예외
- 자바스크립트 코드를 파서가 해석하지 못하거나, 실행 중 상정 외의 상황이 발생하는 경우 예외가 발생한다.
- 자바스크립트에서는 예외와 에러를 구분하지 않는 것 같다. (예외가 곧 에러다)
- 예외를 처리하지 않을 경우, 예외가 발생 한 시점에서 실행은 중단된다.

```javascript
notExistFunc(); //ReferenceError: notExistFunc is not defined
//이하의 구문은 실행되지 않는다.
console.log('after occur exception');
```

## 예외 처리 방법
- 기본 예외 처리와 고급 예외 처리로 나눌 수 있다.

### 기본 예외 처리
- 예외가 발생 할 상황을 미리 판단하여, 예외를 발생 시키지 않게하는 방법이다.
- 분기문(if문)을 사용하여 기본 예외 처리를 구현한다.
```javascript
//TODO 예제코드 추가
```

### 고급
- try-catch-finally구문을 이용해 처리하는 것을 뜻한다.
- try-catch-finally구문은 try-catch, try-finally 구문 만으로도 사용 가능하다.

```javascript
try {

  //예외 발생 가능성이 있는 구문
  //예외가 발생 할 경우, 예외 발생 구문 이후의 구문은 실행되지 않고
  //바로 catch 부분의 구문이 실행

} catch(e) {

  //try 부분에서 예외 발생 시 실행 될 구문
  //e는 예외정보를 담고있는 객체

} finally {

  //try-catch 범위의 실행이 끝난 후 실행 될 구문
  //try-catch 범위에 return문이 실행되었을 경우,
  //return문 이후에 finally 구문이 실행되므로 반환결과를 바꾸는 것이 가능하다.

}
```

```javascript
//TODO 예제코드 추가
```

## 강제 예외 발생
- `throw`키워드를 이용하여 코드 상에서 강제적인 예외 발생이 가능하다.

구문 | `throw expression`
----|--------------------
`expression` | 발생한 예외의 정보를 나타내는 데이터. 자바스크립트에서 사용되는 모든 데이터 타입이 사용가능하다. try-catch로 예외처리 시 catch의 매개변수로 설정된다.

```javascript
//TODO 예제코드 추가
```

## 내장 에러 객체
- 강제 예외 발생 시 `expression`으로 모든 데이터 타입이 사용 가능하다.
- 하지만, 자바스크립트에서 제공하는 내장 에러 객체를 사용하는 것을 추천한다.
- 내장 에러 객체를 사용 시, 에러 객체의 생성 위치가 `stack`으로 제공되므로 디버깅 시 유리하기 때문이다.
- 아래는 내장 에러 객체 중 대표적인 것들에 대한 설명이다.

### `Error`
- 모든 내장 에러 객체의 부모 객체이다.
- 속성으로는 `name`과 `message`를 가지고 있으며, 객체 생성시 `stack`속성이 자동 생성된다.

속성 | 설명
----|-------
`name` | 에러의 이름 (생성자 객체의 이름으로 설정된다.)
`message` | 에러의 상세설명 (객체 생성 시 인수로 설정한 값이 저장된다.)
`stack` | 에러 객체가 생성 된 위치의 call stack 정보

```javascript
//TODO 예제코드 추가
```

### `ReferenceError`
- 존재하지 않는 변수나 함수 등이 참조될 때 발생하는 에러 객체이다.

```javascript
//TODO 예제코드 추가
```

### `SyntaxError`
- 자바스크립트 문법에 어긋나는 구문이 있을 경우 발생하는 에러 객체이다.
- 실행 전 파서가 파일을 분석 할 때 발생하기 때문에 예외 처리가 불가능하다.
- `eval()`함수를 사용 할 경우에는 동적으로 구문을 파싱하므로 예외처리가 가능하다.

```javascript
//TODO 예제코드 추가
```

### `TypeError`
- 데이터가 기대하지 않은 형태인 경우 발생하는 에러 객체이다.

```javascript
//TODO 예제코드 추가
```

### `RangeError`
- 수치변수 및 인수가 유효범위 밖을 가리킬 경우 발생하는 에러 객체이다.

```javascript
//TODO 예제코드 추가
```

## 참고
- [MDN web docs : 開発者向けのウェブ技術 > JavaScript > JavaScript ガイド > 制御フローとエラー処理](https://developer.mozilla.org/ja/docs/Web/JavaScript/Guide/Control_flow_and_error_handling)
- [MDN web docs : 開発者向けのウェブ技術 > JavaScript > JavaScript リファレンス > 文と宣言 > try...catch](https://developer.mozilla.org/ja/docs/Web/JavaScript/Reference/Statements/try...catch)
- [MDN web docs : 開発者向けのウェブ技術 > JavaScript > JavaScript リファレンス > 標準ビルトインオブジェクト > Error](https://developer.mozilla.org/ja/docs/Web/JavaScript/Reference/Global_Objects/Error)
- [js-primer : 例外処理](https://jsprimer.net/basic/error-try-catch/)
- [모던 웹을 위한 JavaScript jQuery 입문(3판) : 예외 처리](http://www.hanbit.co.kr/store/books/look.php?p_code=B6367089342)