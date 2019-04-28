# 이클립스에서 Tomcat로그를 영어로 바꾸기

- Tomcat 로그의 경우 운영체제의 언어에 맞는 언어로 로그를 출력한다.
- 오류 메세지 검색의 용이 등의 이유로 Tomcat로그를 영어로 바꾸기 위한 순서는 아래와 같다.
  1. Window -> Preferences 클릭
  2. Java -> Installed JREs로 이동
  3. 설치되어있는 JRE를 선택 후 Edit 클릭
  4. Default VM arguments에 아래의 구문 삽입
     - -Duser.language=en -Duser.country=US
  5. Finish버튼 클릭
- 위의 방법을 통해 JRE에게 현재 언어와 국가를 명시적으로 알려줌으로서 로그 출력이 로컬화 되는 것을 막아준다.

## 출처

- [자바 – 이클립스 콘솔 로케일/언어를 설정하는 방법](https://codeday.me/ko/qa/20190326/97672.html)