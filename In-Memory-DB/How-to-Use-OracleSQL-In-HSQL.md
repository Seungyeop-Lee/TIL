# HSQL에서 Oracle SQL을 사용하는 방법

- HSQL의 호환성 모드를 이용하면 Oracle SQL의 사용이 가능하다.
- HSQL에서 Oracle SQL 호환성 모드를 적용 시키는 방법에 대해 정리한다.
- 아래에 설명한 방법 중 한 가지만 추가해도 적용된다.

## SQL문에 호환성 모드 설정 구문 추가

- HSQL에서 실행 시킬 Oracle SQL이 담겨있는 sql파일의 최상단에 아래와 같은 SQL문을 추가한다.

```sql
SET DATABASE SQL SYNTAX ORA TRUE;
```

## url에 호환성 모드 설정

- HSQL을 적용 할 때의 url에 호환성 모드임을 명시하여 적용한다.
    - `sql.syntax_ora=true`

```java
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

        ...

    };
}
```

## 참고

- [HyperSQL User Guide > Chapter 12. Compatibility With Other DBMS > Oracle Compatibility](http://hsqldb.org/doc/2.0/guide/compatibility-chapt.html#coc_compatibility_oracle)