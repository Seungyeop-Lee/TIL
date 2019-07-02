# 스프링에서 HSQL을 적용하는 방법

- 스프링에서 HSQL을 적용하는 두 가지 방법에 대해 정리한다.
- 스프링의 PSA에 의한 내장DB설정 방법이기 때문에 H2나 Derby를 이용 할 경우에도 동일한 방식을 적용 할 수 있다.

## 의존성 추가

- 스프링에서 HSQL을 사용하기 위해서는 세가지 의존성이 필요하다.
    1. HSQL을 사용하기 위한 `hsqldb`
    1. 스프링의 PSA로 HSQL을 이용하기 위한 `spring-jdbc`
    1. Annotation으로 컨텍스트 설정을 하기 위한 `spring-context`

```xml
<dependency>
    <groupId>org.springframework</groupId>
    <artifactId>spring-jdbc</artifactId>
    <version>5.1.8.RELEASE</version>
</dependency>
<dependency>
    <groupId>org.springframework</groupId>
    <artifactId>spring-context</artifactId>
    <version>5.1.8.RELEASE</version>
</dependency>
<dependency>
    <groupId>org.hsqldb</groupId>
    <artifactId>hsqldb</artifactId>
    <version>2.5.0</version>
</dependency>
```

## 적용 및 사용

- 스프링이 제공해주는 내장DB 적용 객체를 사용하여, 내장DB 전용 `DataSource`인 `EmbeddedDatabase`를 얻어서 사용하면 된다.
    - `EmbeddedDatabase`는 `DataSource`를 상속하고 있으며, 내장DB를 종료시키는 `shutdown`메소드를 추가로 제공

### `EmbeddedDatabaseBuilder`를 이용한 HSQL 적용

- `EmbeddedDatabaseBuilder`를 이용하면 매우 간단하게 `HSQL`의 적용이 가능하다.
- DB의 url, username, password는 기본적으로 설정 된 값이 적용된다.

```java
@Bean
public EmbeddedDatabase embeddedDatabase() {
    EmbeddedDatabase db = new EmbeddedDatabaseBuilder()	//내장형 데이터베이스의 데이터소스 생성 빌더
                            .setType(EmbeddedDatabaseType.HSQL)	//내장형 데이터베이스 종류 지정
                            .addScript("classpath:/springbook/learningtest/spring/embeddeddb/schema.sql")	//초기화 스크립트 추가
                            .addScript("classpath:/springbook/learningtest/spring/embeddeddb/data.sql")
                            .build();	//빌드(url: jdbc:hsqldb:mem:testdb, username: sa, password: [빈문자열])
    return db;
}
```

### `EmbeddedDatabaseFactory`를 이용한 HSQL 적용

- `EmbeddedDatabaseFactory`는 `EmbeddedDatabaseBuilder`보다 복잡하지만 세세한 설정이 가능하다.
    - `EmbeddedDatabaseBuilder`도 내부적으로는 `EmbeddedDatabaseFactory`를 사용한다.
- url을 통해 DB의 설정을 변경해야 하는 등, 접속 정보를 수정해야 하는 경우 사용하면 된다.

```java
@Bean
public EmbeddedDatabase embeddedDatabase() {
    EmbeddedDatabaseFactory factory = new EmbeddedDatabaseFactory();
    factory.setDatabaseConfigurer(databaseConfigurer());
    factory.setDatabasePopulator(populator());
    return factory.getDatabase();
}

// DB의 설정정보 제공 빈
@Bean
public EmbeddedDatabaseConfigurer databaseConfigurer() {
    return new EmbeddedDatabaseConfigurer() {
        @Override
        public void configureConnectionProperties(ConnectionProperties properties, String databaseName) {
            properties.setUrl("jdbc:hsqldb:mem:testdb;sql.syntax_ora=true");
            properties.setUsername("sa");
            properties.setPassword("");
            properties.setDriverClass(jdbcDriver.class);
        }

        @Override
        public void shutdown(DataSource dataSource, String databaseName) {
            //AbstractEmbeddedDatabaseConfigurer의 shutdown메소드 로직
            try {
                Connection connection = dataSource.getConnection();
                Statement stmt = connection.createStatement();
                stmt.execute("SHUTDOWN");
            } catch (SQLException ex) {
            }
        }
    };
}

// SQL Script를 이용한 DB 초기화정보 제공 빈
@Bean
public DatabasePopulator populator() {
    ResourceDatabasePopulator populator = new ResourceDatabasePopulator();
    populator.addScript(new DefaultResourceLoader().getResource("sql.sql"));
    return populator;
}
```

## 참고

- [토비의 스프링 3](http://acornpub.co.kr/book/toby-spring3)
- EmbeddedDatabaseBuilder, EmbeddedDatabaseFactory 파일 분석