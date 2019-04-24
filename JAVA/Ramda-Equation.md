# 람다식(Ramda Equation)

- 익명 함수를 표현하는 식으로, 함수형 프로그래밍에 주로 사용되었다.
- Java 8부터 추가 되었으며, 컬렉션 프레임워크와 같이 사용되는 경우가 많다.
- 객체에 전략을 주입 할 때, 보다 깔끔한 형태로 사용 가능하다는 장점이 있다. (ex. handler)

## 람다식의 형태

- `(매개변수) -> {실행코드}`형태로 나타낸다.
- 내부적으로는 익명 구현 객체로 만들어져 실행되는 형태이다.

## 람다식의 기본 문법

- 기본적인 형태
  - `(타입 매개변수, ...) -> {실행문; ...}`
- 람다식의 매개변수의 경우 타입을 명시 해 줄 필요가 없다.
  - 매개변수의 타입은 컴파일러가 람다식이 저장되거나, 사용되는 부분의 타입을 분석하여 자동으로 타입을 정한다.
  - `(매개변수, ...) -> {실행문; ...}`
- 매개변수가 1개만 있다면 `()`는 생략 가능하다.
  - `매개변수 -> {실행문; ...}`
- 매개변수가 없으면 `()`는 생략 불가능하다.
  - `() -> {실행문; ...}`
- 실행문이 `return`문 1개밖에 없다면 `return`과 `{}`는 생략 가능하다.
  - `() -> 실행문`

## 타겟 타입과 함수적 인터페이스

- 람다식은 내부적으로 익명 구현 객체를 만들기때문에 익명 구현 객체의 타입인 인터페이스가 필요하다.
- 람다식을 저장 할 인터페이스 타입은 1개의 추상 메소드만 가진 인터페이스여야 한다.
  - 인터페이스 내에 상수 및 static 메소드, default 메소드는 상관 없음
- 람다식 전용의 인터페이스를 선언 할 경우 `@FunctionalInterface`어노테이션을 붙여 함수적 인터페이스라는 것을 명시 할 수 있다.
  - 함수적 인터페이스라는 것을 명시 할 경우, 인터페이스 내에 0개 또는 2개 이상의 추상 메소드가 선언 되었을 경우 컴파일 에러를 발생 시킨다.
  - `@FunctionalInterface`어노테이션을 선언하지 않아도, 함수적 인터페이스로 사용이 가능하다.

## 람다식 내부에서 클래스 맴버 접근

- `this`키워드로 클래스의 참조값에 접근이 가능하다.
- 람다식 내부에서 사용되는 `this`는 람다식을 실행한 객체의 참조이다.
  - 내부적으로 생성되는 익명 객체의 참조가 아님!!!
- 람다식을 실행한 객체가 내부 클래스이고, 외부 클래스의 맴버에 접근하려는 경우 `외부 클래스명.this`를 사용하면 된다.

## 람다식 내부에서 로컬 변수 사용

- 메소드 내부에서 람다식 사용시에는 로컬 익명 구현 객체를 생성시키는 것과 동일하다.
- 즉, 람다식 내부에서 로컬 변수 사용은 익명 객체의 로컬 변수 사용과 동일하다.
  - 람다식 내부에서 사용하는 로컬 변수는 `final`특성을 가진다. (수정 불가)

## 참고

- [이것이 자바다](http://www.hanbit.co.kr/store/books/look.php?p_code=B1460673937)