# enum

## enum이란

- Java 1.5버전에서 추가된 타입이다.
- 관련이 있는 상수를 모아놓은 집합이다.
- 클래스와 동일하며, 컴파일 시 각 enum에 해당하는 객체를 생성한다.
- 기존 상수 사용방법의 단점을 보완하였다.

## enum사용법

### enum선언과 사용

```java
public enum Direction {
  //열거 상수 선언, enum클래스의 최상단에 위치하여야 한다.
  STRAIGHT(false), LEFT(true), RIGHT(true);
  
  //열거 상수 내부에서 사용 할 필드 선언 가능
  boolean turn;
  
  //열거 상수 초기화 시, 생성자가 자동 실행
  //생성자에 사용가능한 접근제어자는 private뿐, 생략가능
  Direction(boolean turn) {
    this.turn = turn;
  }
  
  //열거 상수에서 사용가능한 메소드 선언 가능
  public boolean isTurn() {
    return turn;
  }
}
```

- 일반적인 클래스 선언 방법과 동일하며, 구성요소도 동일하다.
- 차이점이라면 최상단에 열거 상수를 선언하여야 하며, 클래스 상속이 불가하다.　(인터페이스 구현은 가능)

```java
Direction direction = Direction.STRAIGHT;
boolean turn = direction.isTurn();
```

- `열거 타입.열거 상수`로 사용가능하다. (스테틱 변수를 사용하는 느낌으로 사용)
- 열거 상수는 객체로 존재하며, enum 클래스에 정의한 메소드의 실행도 가능하다.
- 열거 상수는 싱글톤으로 존재하며, JVM이 직접 생성해 주는 싱글톤이므로 매우 안전하다.

### enum관련 메소드

- `열거 상수.name()`
  - 열거 상수 이름을 문자열로 반환한다.

```java
String name = Direction.STRAIGHT.name();
System.out.println(name); //STRAIGHT
```

- `열거 타입.valueOf(String name)`
  - 열거 타입이 가지고 있는 열거 상수 중 `name`과 동일한 이름을 가진 열거 상수를 반환한다.

```java
Direction direction = Direction.valueOf("LEFT");
System.out.println(direction.name()); //LEFT
```

- `열거 타입.values()`
  - 열거 타입이 가지고 있는 열거 상수들을 배열로 반환한다.

```java
Direction[] directions = Direction.values();
for(Direction direction : directions) {
  System.out.println(direction.name()); //STRAIGHT
                                        //LEFT
                                        //RIGHT
}
```

## 기존 방법 vs. enum사용

### 클래스에 static final로 변수 선언

```java
public class Control {
  private static final int STRAIGHT = 0;
  private static final int LEFT = 1;
  private static final int RIGHT = 2;

  public int turnTo(String direction) {
    switch(direction) {
      case "left":
        return LEFT;
      case "right":
        return RIGHT;
      default:
        return STRAIGHT;
    }
  }
}
```

- 필요한 상수를 `static final` 필드로 선언하여 사용한다.
- 상수로 사용하는 변수 안에는 실제로 다른 값(ex. 0, 1, 2)이 들어가 있다.
- 가장 원시적인 상수 선언방법이다.

### 인터페이스에 상수 선언

```java
public class Control {
  
  interface Direction {
    int STRAIGHT = 0;
    int LEFT = 1;
    int RIGHT = 2;
  }

  public int turnTo(String direction) {
    switch(direction) {
      case "left":
        return Direction.LEFT;
      case "right":
        return Direction.RIGHT;
      default:
        return Direction.STRAIGHT;
    }
  }
}
```

- 관련이 있는 상수를 인터페이스에 모아서 선언한 후 사용한다.
- 인터페이스에 상수를 모아놨기 때문에 관리가 용이하다.
- 인터페이스의 이름을 통해 상수의 정의가 명확해진다.

### 기존 상수 사용방법의 단점

- 상수끼리 비교(동등 비교, 우열 비교)가 가능하다.
- 상수 대신 상수에 담겨있는 실제값을 사용해도 동일하게 작동한다.

### enum사용

```java
public class Control {
  
  enum Direction {
    STRAIGHT, LEFT, RIGHT;
  }

  public Direction turnTo(String direction) {
    switch(direction) {
      case "left":
        return Direction.LEFT;
      case "right":
        return Direction.RIGHT;
      default:
        return Direction.STRAIGHT;
    }
  }
}
```

- 관련있는 상수를 enum에 모아서 선언한 후 사용한다.
- 다른 enum에 속한 상수끼리의 비교가 불가능하다.
  - 컴파일 에러가 발생, 실행 전에 버그 유발 가능성이 높은 코드작성을 방지
  - 같은 enum에 속한 상수끼리는 가능
- enum값을 제외한 다른 값은 사용이 불가능하다.
  - enum값을 강제하여, 정해진 틀 안에서 코드를 작성하도록 유도 가능

## 참고
- [enum (이전 방식, 개념, 동작방식, 사용예제, 관련메소드)](https://sjh836.tistory.com/134)
- [Java Enum 활용기](http://woowabros.github.io/tools/2017/07/10/java-enum-uses.html)
- [이것이 자바다](http://www.hanbit.co.kr/store/books/look.php?p_code=B1460673937)