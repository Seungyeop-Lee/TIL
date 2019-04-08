# 이클립스에서 자바 자동완성이 작동하지 않을 때

- 이클립스나 STS 버전업 후, 마이크레이션 한 프로젝트에서 자바 자동완성이 작동하지 않을 때 시도해볼만한 방법이다.

## 방법

1. 이클립스나 STS에서 Window -> Preferences -> Java -> Editor -> Content Assist -> Advanced로 이동한다.
2. 위와 아래 섹션에 이하의 항목만 체크를 하고, 나머지 체크는 전부 체크를 해제한다.
   - Java Non-Type Proposals 
   - Java Proposals 
   - Java Type Proposals
3. Apply and Close를 클릭 후, 문제가 되는 프로젝트를 Close Project로 닫고, 다시 연다.
4. 잘 되는지 확인한다.

## 출처

- [[SOLVED] Eclipse Java autocomplete not working](https://www.chrisnewland.com/solved-eclipse-java-autocomplete-not-working-259)