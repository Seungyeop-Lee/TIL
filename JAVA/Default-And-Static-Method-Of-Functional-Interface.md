# 함수적 인터페이스의 default메소드와 static메소드

- Java 8에서 추가된 default메소드와 static메소드가 함수적 인터페이스에도 존재한다.
- 함수적 인터페이스의 default메소드와 static메소드에 대해 정리한다.

## `andThen()`, `compose()` default메소드

- 두 개 이상의 함수적 인터페이스를 연결하는 메소드이다.
- `Consumer`, `Function`, `Operator`인터페이스에서 사용가능하다.
  - 다른 인터페이스끼리 혼용 사용불가
  - `BinaryOperator`와 `UnaryOperator`는 `Function`인터페이스와 혼용 사용가능
    - `Function`인터페이스의 하위 인터페이스

### 실행 순서에 따른 차이

- `andThen()`은 두개의 함수적 인터페이스를 **순차적**으로 연결하여 실행시키는 새로운 인터페이스를 반환한다.
  - `인터페이스C = 인터페이스A.andThen(인터페이스B);`
  - `최종결과 = 인터페이스C.method();`
  - 라면 인터페이스A가 먼저 실행되고, 인터페이스B가 그 다음 실행된다.
- `compose()`는 두개의 함수족 인터페이스를 **역순**으로 연결하여 실행시키는 새로운 인터페이스를 반환한다.
  - `인터페이스C = 인터페이스A.compose(인터페이스B);`
  - `최종결과 = 인터페이스C.method();`
  - 라면 인터페이스B가 먼저 실행되고, 인터페이스A가 그 다음 실행된다.

### `Consumer`와 `Function`에서의 동작 차이

- `Consumer`인 경우 연결된 두개의 인터페이스에는 동일한 매개값이 들어가서 각각 실행된다.
  - 매개값만 있고, 반환값은 없으므로
- `Function`인 경우 매개값은 첫번째 인터페이스에 들어가고, 그 결과값이 두번째 인터페이스의 매개값에 들어가서 실행된다.

## `and()`, `or()`, `negate()` default메소드

- 두 개 이상의 `Predicate`인터페이스를 연결하는 메소드이다. (`negate()`는 제외)
- `and()`, `or()`, `negate()`는 각각 논리 연산자의 `&&`, `||`, `!`과 대응된다.

## `isEqual()` static메소드

- `Predicate`인터페이스의 static메소드로서 매개값으로 설정한 값과 동일한지 판단해주는 `Predicate`인터페이스 객체를 생성한다.
- 내부 동작으로는 `Objects.equals(sourceObject, targetObject)`와 동일하며, 각 값에 따른 판단 규칙은 아래와 같다.

| sourceObject | targetObject | 리턴값                                     |
| ------------ | ------------ | ------------------------------------------ |
| null         | null         | true                                       |
| not null     | null         | false                                      |
| null         | not null     | false                                      |
| not null     | not null     | sourceObject.equals(targetObject의 리턴값) |

## `minBy()`, `maxBy()` static메소드

- `BinaryOperator<T>`인터페이스의 static메소드로서 매개값으로 설정한 Comparator를 이용해서 최대 T 또는 최소 T를 반환해주는 `BinaryOperator<T>`인터페이스 객체를 생성한다.

## 참고

- [이것이 자바다](http://www.hanbit.co.kr/store/books/look.php?p_code=B1460673937)