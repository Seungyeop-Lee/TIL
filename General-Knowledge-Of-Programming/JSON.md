# JSON
- **J**ava**S**cript **O**bject **N**otation의 약자로 JavaScript의 객체 형식을 문자열로 표현한 방식이며, 데이터 기술언어 중 하나다.
- 구문은 JavaScript의 객체 표기법을 베이스로 하고 있지만, JavaScript 전용 데이터 형식은 아니다.
- 상이한 소프트웨어, 프로그래밍 언어 사이에서 주고 받는 데이터로 사용 될 수 있도록 설계되었다.
- XML보다 경량이며, YAML보다는 더 다양한 프로그래밍 언어에 구현되어 있다.

## 표기 방법(문법)
기본적인 문법은 자바스크립트 객체 리터럴의 문법과 동일하다.

- 데이터는 이름과 키의 짝으로 구성되어야 한다.
- 데이터는 콤마로 구분 짓는다.
- 대괄호로 객체를 나타낸다.
- 중괄호로 배열을 나타낸다.

## JSON에서 사용가능한 데이터 형식

데이터 형식 | 주의점
-----------|------
number | 숫자는 10진수만 사용가능, 소수의 경우 지수표기법 사용가능 (ex. 10e-10)
string | unicode 문자열, 더블쿼테이션("")으로 감싸여있어야하며 백슬러쉬(\\)를 이스케이프 문자로 사용가능
boolean | `true` or `false`, 대문자는 사용불가
null | 대문자는 사용 불가
array | index에 따라 value를 가진 배열, value는 JSON에서 사용 가능한 데이터 형식 모두 가능
object | key와 value로 이루어진 속성의 집합, key는 문자열이어야 하며, value는 JSON에서 사용 가능 한 데이터 형식 모두 가능

```JSON
// {key : value}
{
  "number" : 1,
  
  "string" : "a",
  
  "boolean" : true,
  
  "null" : null,
  
  "array" : [2, "b", false, null, [], {}],
  
  "object" : {
    "numInObj" : 3,
    "strInObj" : "c",
    "boolInObj" : true,
    "nullInObj" : null,
    "arrInObj" : [],
    "objInObj" : {}
  }
}
```

## 참고
- [ウィキペディア（Wikipedia）: JavaScript Object Notation](https://ja.wikipedia.org/wiki/JavaScript_Object_Notation)
- [w3school : JAVASCRIPT > JS JSON > JSON Data Types](https://www.w3schools.com/js/js_json_datatypes.asp)