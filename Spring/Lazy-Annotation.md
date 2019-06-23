# @Lazy

- 어플리케이션 컨택스트(ApplicationContext)의 설정 정보 클래스의 초기화 타이밍을 조절하는 어노테이션이다.

## 일반적인 어플리케이션 컨택스트의 초기화

- @Configration이 붙은 설정 정보 클래스를 기반으로 어플리케이션 컨택스트를 생성하였을 경우, 설정 정보 클래스의 @Bean어노테이션이 붙은 메소드는 생성 시점에 자동으로 실행되어 싱글톤 레지스트리(어플리케이션 컨택스트)에 등록된다.

## @Lazy가 붙어 있을 경우

- 어플리케이션 컨택스트의 빈 등록 타이밍이 어플리케이션 컨택스트의 생성 직후가 아니라, 최초 요청 시점으로 미루어진다.

## @Lazy가 붙는 위치

### @Bean 다음에 붙는 경우 (메소드)

- 해당 Bean등록 메소드에 대해 초기화 타이밍을 지연시킨다.

### @Configration 다음에 붙는 경우 (클래스)

- 해당 설정 정보 클래스에 속한 모든 Bean등록 메소드에 대해 초기화 타이밍을 지연시킨다.

## 예제 코드

```java
@Configuration
public class DaoFactory {
	
	//최초 요청 시 실행되어 싱글톤 레지스트리에 등록된다.
	@Bean
	@Lazy
	public UserDao userDao() {
		return new UserDao();
	}
	
	//어플리케이션 컨텍스트 생성 시 실행되어 싱글톤 레지스트리에 등록된다.
	@Bean
	public ConnectionMaker connectionMaker() {
		return new SimpleConnectionMaker();
	}
	
}
```

## 참고

- [stackoverflow > Spring default behavior for lazy-init](https://stackoverflow.com/questions/15092898/spring-default-behavior-for-lazy-init)