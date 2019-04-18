# 표준 API의 함수적 인터페이스

- Java 8부터 빈번하게 사용되는 함수적 인터페이스를 java.util.function 표준 API 패키지로 제공한다.
- 제공되는 함수적 인터페이스는 크게 5가지로 구분된다. 구분 기준은 추상 메소드의 파라미터의 개수 및 리턴값의 유무이다.

| 종류        | 매개값 | 리턴값 | 리턴타입      |
| ----------- | ------ | ------ | ------------- |
| `Consumer`  | O      | X      | -             |
| `Supplier`  | X      | O      | 모든타입      |
| `Function`  | O      | O      | 매개값과 상이 |
| `Operator`  | O      | O      | 매개값과 동일 |
| `Predicate` | O      | O      | boolean       |

## `Consumer`

- 리턴값이 없는 `accept()`메소드를 가지고 있다.
  - `void accept(매개 변수)`

| 인터페이스명      | 매개변수   | 설명                  |
| ----------------- | ---------- | --------------------- |
| `Consumer<T>`     | (T t)      | 객체 T를 받아 소비    |
| `BiConsumer<T,U>` | (T t, U u) | 객체 T, U를 받아 소비 |

- 특정 형태의 값을 받아 소비하는 `Consumer`인터페이스도 존재한다.
  - double, int, long값을 받아 소비하는 `Consumer`인터페이스
  - 임의의 객체와 double, int, long값을 받아 소비하는 `Concumer`인터페이스

## `Supplier`

- 매개변수가 없는 `getXXX()`메소드를 가지고 있다. (XXX는 인터페이스 마다 상이)
  - `리턴 타입 getXXX()`

| 인터페이스명  | 추상 메소드 | 설명                 |
| ------------- | ----------- | -------------------- |
| `Supplier<T>` | T get()     | T 타입의 객체를 반환 |

- 특정 형태의 타입을 반환하는 `Supplier`인터페이스도 존재한다.
  - boolean, double, int, long을 반환하는 `Supplier`인터페이스

## `Function`

- 매개변수와 리턴값이 존재하는 `applyXXX()`메소드를 가지고 있다. (XXX는 인터페이스 마다 상이)
  - `리턴 타입 applyXXX(매개 변수)`
- 매개변수 타입과 리턴 타입은 상이하다.
  - 매개값을 리턴값으로 매핑

| 인터페이스명        | 추상 메소드       | 설명                                           |
| ------------------- | ----------------- | ---------------------------------------------- |
| `Function<T,R>`     | R apply(T t)      | T 타입의 객체를 R 타입으로 매핑                |
| `BiFunction<T,U,R>` | R apply(T t, U u) | T 타입의 객체와 U타입의 객체를 R 타입으로 매핑 |

- 특정 형태의 값을 매개값, 리턴값으로 사용하는 `Function`인터페이스도 존재한다.
  - 공식 API 문서 참조

## `Operator`

- 매개변수와 리턴값이 존재하는 `applyXXX()`메소드를 가지고 있다. (XXX는 인터페이스 마다 상이)
  - `리턴 타입 applyXXX(매개 변수)`
- 매개변수 타입과 리턴 타입이 동일하다.
  - 매개값을 이용해 연산하여 결과를 반환

| 인터페이스명        | 추상 메소드         | 설명                        |
| ------------------- | ------------------- | --------------------------- |
| `BinaryOperator<T>` | T apply(T t1, T t2) | 매개값을 연산하여 결과 반환 |
| `UnaryOperator<T>`  | T apply(T t)        | 매개값을 연산하여 결과 반환 |

- `BinaryOperator<T>`와 `UnaryOperator<T>`는 각각 `BiFunction<T,U,R>`와 `Function<T,R>`의 하위 인터페이스이다.
- 특정 형태의 값을 매개값, 리턴값으로 사용하는 `Operator`인터페이스도 존재한다.
  - 공식 API 문서 참조

## `Predicate`

- 매개변수와 boolean 리턴값이 존재하는 `testXXX()`메소드를 가지고 있다. (XXX는 인터페이스 마다 상이)
  - `boolean testXXX(매개 변수)`

| 인터페이스명       | 추상 메소드            | 설명                                         |
| ------------------ | ---------------------- | -------------------------------------------- |
| `Predicate<T>`     | boolean test(T t)      | T 타입의 객체 조사 결과 반환                 |
| `BiPredicate<T,U>` | boolean test(T t, U u) | T 타입의 객체와 U 타입의 객체 조사 결과 반환 |

- 특정 형태의 매개값을 사용하는 `Predicate`인터페이스도 존재한다.
  - double, int, long값을 매개변수로 하는 `Predicate`인터페이스

## 참고

- [이것이 자바다](http://www.hanbit.co.kr/store/books/look.php?p_code=B1460673937)