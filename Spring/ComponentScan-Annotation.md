# @ComponentScan

- @Configuration과 같이 쓰이며, 대상 범위를 스캔하여 조건에 따른 Bean등록 대상을 판별한다.
- 생략 할 경우, 프로젝트 전체에 대해 스캔한다.

## 기본 동작

- Bean등록 관련 어노테이션이 붙은 클래스를 Bean으로 등록한다.
  - @Controller, @Service, @Bean, @Configration, @Repository, @Component

## @ComponentScan의 속성

### basePackages

- 스캔 대상 패키지를 지정한다.
- 대상 패키지와 하위 패키지를 스캔 범위로 한다.

### Filter 공통

- includeFilters와 excludeFilters로 필터링이 가능하다.
- 각 필터의는 `@ComponentScan.Filter(type = <type>, (pattern = <pattern>|classes = <classes>))`를 통해 조건 설정을 한다.
  - type: ANNOTATION, ASSIGNABLE, REGEX, ASPECTJ
  - pattern은 REGEX, ASPECTJ일 때 사용
  - classes는 ANNOTATION, ASSIGNABLE일 때 사용

### includeFilters

- Bean등록 관련 어노테이션이 없어도 필터 범위에 있는 클래스는 Bean등록 대상이 된다.

### excludeFilters

- Bean등록 관련 어노테이션이 있어도 필터 범위에 있는 클래스는 Bean등록 대상에서 제외된다.

## 예제 코드

```java
@Configuration  //설정 객체임을 나타냄
@ComponentScan(
    basePackages = {"com.xbeast7.springtest"},  //com.xbeast7.springtest패키지와 하위 패키지를 스캔 범위로 지정
    includeFilters = {  //어노테이션이 없어도 해당 클래스를 Bean으로 등록
        @ComponentScan.Filter(
                type = FilterType.REGEX,  //정규표현식을 사용
                pattern = {
                    "com.xbeast7.springtest.dao.*DaoImpl"  //com.xbeast7.springtest.dao에 DaoImpl로 끝나는 클래스
                }
        )
    },
    excludeFilters =  { //어노테이션이 있어도 해당 클래스는 Bean으로 등록하지 않음
        @ComponentScan.Filter(
                type = FilterType.ANNOTATION, //특정 어노테이션
                classes = {
                    org.springframework.stereotype.Controller.class //@Controller 어노테이션
                }
        )
    }
)
public class ComponentScanConfiguration {
}
```

## 참고

- [스프링5 레시피](http://www.hanbit.co.kr/store/books/look.php?p_code=B3859466837)
- [Annotation Type ComponentScan](https://docs.spring.io/spring/docs/current/javadoc-api/org/springframework/context/annotation/ComponentScan.html)
