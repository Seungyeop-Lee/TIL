# JSON Object
- JSON 문자열을 분석하여 객체로 만드는 메소드(`parse`)와 객체를 JSON 문자열로 변환하는 메소드(`stringify`)를 가진 객체이다.

## `JSON.parse` 메소드
- 문자열을 JSON으로서 분석하여 객체를 만들어 반환한다.
- 문자열이 유효한 JSON형식이 아닐경우 `SyntaxError` 예외가 발생한다.

구문 | JSON.parse(text[, reviver])
-----|----------------------------
text | JSON으로서 분석 할 문자열
reviver | text를 분석하여 객체를 만들기 전 변환방법을 지정 한 함수. null인 경우 분석 결과 그대로 객체로 만든다. 초기치는 null
반환값 | JSON문자열을 분석하여 만든 객체

```javascript
//TODO 예제코드 작성
```

### `reviver` 설정 함수
- `reviver`에 설정하는 함수의 매개변수로 `key`와 `value`를 사용 할 수 있다.
- 설정된 함수에서 반환한 값이 key에 해당하는 value로 재설정되어 객체로 만들어진다.
- `this`가 가리키는 것은 함수 실행 당시의 key와 value로 이루어진 객체다.
- `reviver`에 설정된 함수는 JSON문자열의 키의 갯수 + 1번 반복되어 실행된다. (JSON의 속성 + "" : {})

```javascript
//TODO 예제코드 작성
```

### 주의점
- JSON 문자열에서는 배열이나 객체의 값의 마지막에 콤마(,)가 들어가 있을 경우 예외가 발생한다. (자바스크립트의 배열, 객체의 문법에서는 허용)

```javascript
//TODO 예제코드 작성
```