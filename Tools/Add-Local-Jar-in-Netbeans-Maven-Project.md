# NetBeans의 Maven Project에서 로컬 Jar파일 추가 방법

- 이 방법은 NetBeans 8.2버전, Maven Web Application 프로젝트에서 동작 확인하였다.

1. 프로젝트 내부에 Dependencies에 마우스 오른쪽 클릭
2. Add Dependency...를 클릭
3. Add Dependency창에 Group ID, Artifact ID, Version을 적절히 기입
4. Add버튼을 클릭
5. Dependencies에 추가한 jar파일이 있는 지 확인
6. Dependencies에 추가한 jar파일에 마우스 오른쪽 클릭
7. Manually install artifact를 클릭
8. Install locally창에서 Browse...버튼을 클릭
9. 추가 할 Jar 파일을 선택하고 Select버튼을 클릭
10. Install locally버튼을 클릭

## 참고

- [stackoverflow > Adding external JAR to Maven project in NetBeans](https://stackoverflow.com/questions/17693040/adding-external-jar-to-maven-project-in-netbeans)