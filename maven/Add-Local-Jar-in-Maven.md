# Maven에서 로컬 jar를 추가하는 방법

1. 프로젝트 내 적당한 위치에 jar파일을 위치시킨다.
1. 이하의 태그를 `pom.xml`에 추가한다.

```xml
<dependencies>
  <!-- ...다른 의존성 설정 태그 -->
  <dependency>
      <groupId>groupId</groupId>
      <artifactId>aritifactId</artifactId>
      <version>1.0</version>
      <scope>system</scope> <!-- 로컬 jar를 추가 할 때 필수 태그 -->
      <systemPath>${project.basedir}/jar파일 위치</systemPath> <!-- ${project.basedir}는 project의 root폴더를 가리킨다. -->
  </dependency>
</dependencies>
```

## 참고

- [stackoverflow > How to add local jar files to a Maven project?](https://stackoverflow.com/questions/4955635/how-to-add-local-jar-files-to-a-maven-project)