# web.xml이 없음을 pom.xml에 명시하는 방법
```xml
<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
  xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/maven-v4_0_0.xsd">
  <properties>
  	<failOnMissingWebXml>false</failOnMissingWebXml>
  </properties>
</project>
```
## 참고
- [[부스트코스] 웹 프로그래밍 : DB연결 웹 애플리케이션 > Web API 실습](https://www.edwith.org/boostcourse-web)