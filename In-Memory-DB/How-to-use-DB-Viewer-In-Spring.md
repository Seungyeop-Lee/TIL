# Spring에서 적용시킨 내장DB를 DB뷰어로 확인하는 방법

- Spring에서 내장DB를 적용시켜 사용하는 경우, 내장 DB는 JVM상에 존재하기 때문에 외부의 다른 프로그램으로는 접근이 불가능하다.
- 이런 문제를 해결하기 위해, 각 내장DB들은 Swing으로 만들어진 DB Viewer를 제공하며, 스프링이 실행되고 있는 코드에서 실행 가능하다.

## 사용법

- 아래와 같은 코드를 삽입시켜 준 후에, 적당한 위치에서 실행시키면 된다.

```java
public void startDBManager() {
	
	//EmbeddedDatabaseBuilder를 이용하여 내장 DB를 적용시켰을 경우(기본 설정값 이용)

	//hsqldb
	DatabaseManagerSwing.main(new String[] { "--url", "jdbc:hsqldb:mem:testdb", "--user", "sa", "--password", "" });

	//derby
	DatabaseManagerSwing.main(new String[] { "--url", "jdbc:derby:memory:testdb", "--user", "", "--password", "" });

	//h2
	DatabaseManagerSwing.main(new String[] { "--url", "jdbc:h2:mem:testdb", "--user", "sa", "--password", "" });

}
```

## 참고

- [mkyong.com > Spring embedded database examples](https://www.mkyong.com/spring/spring-embedded-database-examples/)