# EL과 JSTL

## EL(Expression Language)

- 값을 표현하는 새로운 언어로서 JSP의 기본문법을 보완하는 역할을 한다.
- 내장객체 접근, 연산 기능, 집합객체에 대한 접근 등이 가능하다.

### EL의 내장객체

- EL에는 11개의 내장객체가 존재한다.

| 내장 객체        | 설명                                           |
| ---------------- | ---------------------------------------------- |
| pageScope        | Page 영역에 존재하는 객체에 저장된 속성        |
| requestScope     | Request 영역에 존재하는 객체에 저장된 속성     |
| sessionScope     | Session 영역에 존재하는 객체에 저장된 속성     |
| applicationScope | Application 영역에 존재하는 객체에 저장된 속성 |
| param            | 파라미터 값(단일값)                            |
| paramValues      | 파라미터 값(배열)                              |
| header           | Header 정보(단일값)                            |
| headerValues     | Header 정보(배열)                              |
| cookie           | 쿠키 객체                                      |
| initParam        | 컨텍스트의 초기화 파라미터                     |
| pageContext      | PageContext(JSP의 Page기본 객체) 객체          |

- pageContext를 제외한 내장 객체는 값을 매핑한 Map 객체이다.
- Scope의 범위는 Application > Session > Request > Page 순으로 넓다.
  - ApplicationScope : 웹 어플리케이션이 기동을 시작해서 기동을 끝낼 때 까지
  - SessionScope : 클라이언트가 시작하여 서버에 접속 후, 종료하여 서버와의 연결이 끊어질 때 까지
  - RequestScope : 클라이언트가 서버에 한번의 요청을 한 후, 그 요청에 대한 처리가 완료될 때 까지
  - PageScope : 1개의 JSP에 한정

### EL의 연산자

#### 기본 연산자

| 기본 연산자 | 설명                                                                           |
| ----------- | ------------------------------------------------------------------------------ |
| `.`         | Bean, Map객체의 속성에 접근하기 위한 접근 연산자                               |
| `[]`        | 배열, 리스트의 요소에 접근하기 위한 접근 연산자(Bean, Map객체 접근시 이용가능) |
| `()`        | 연산의 우선 순위 설정                                                          |
| `x ? a : b` | 삼항 연산자                                                                    |

#### 산술 연산자

| 산술 연산자    | 설명   |
| -------------- | ------ |
| `+`            | 더하기 |
| `-`            | 빼기   |
| `*`            | 곱하기 |
| `/` 또는 `div` | 나누기 |
| `%` 또는 `mod` | 나머지 |

#### 논리 연산자

| 논리 연산자     | 설명   |
| --------------- | ------ |
| `&&` 또는 `and` | 논리곱 |
| `||` 또는 `or`  | 논리합 |
| `!` 또는 `not`  | 부정   |

#### 비교 연산자

| 비교 연산자    | 설명                 |
| -------------- | -------------------- |
| `==` 또는 `eq` | 일반적인 `==`와 동일 |
| `!=` 또는 `ne` | 일반적인 `!=`와 동일 |
| `<` 또는 `lt`  | 일반적인 `<`와 동일  |
| `>` 또는 `gt`  | 일반적인 `>`와 동일  |
| `<=` 또는 `le` | 일반적인 `<=`와 동일 |
| `>=` 또는 `ge` | 일반적인 `>=`와 동일 |

### EL의 객체 접근 및 탐색

- `${표현1.표현2}`의 형태로 사용하여 객체가 가지고 있는 값에 접근한다.
  1. 표현1이 null이면 null을 리턴
  2. 표현1이 null이 아니면 표현1의 내부에서 표현2를 검색
  3. 표현2가 null이면 null을 리턴
  4. 표현2가 키가 프로퍼티로 존재하는 데이터의 값을 리턴
- 내장 객체를 표기하지 않을경우, 4개의 스코프(application, session, request, page)에 해당하는 내장 객체 전체를 대상으로 해당 표현에 맞는 데이터를 검색한다.
  - 검색 순서는 page -> request -> session -> application이며, 처음 찾은 데이터를 리턴
- 특정 스코프의 내장 객체에 저장되어 있는 속성에 접근하려는 경우에는 `${내장객체.표현}`의 형태를 사용한다.
- EL에서 접근한 객체의 메소드를 실행하는 것도 가능하다. (ex. `${loginUser.regDate.toString()}`)

## JSTL(JSP Standard Tag Library)

- 자주 사용되는 필요한 기능들을 모아놓은 커스텀 태그 라이브러리이며 EL과 같이 사용되는 경우가 많다.
  - [Apache Taglibs - Apache Standard Taglib: JSP[tm] Standard Tag Library (JSTL) implementations](https://tomcat.apache.org/taglibs/standard/)에서 다운로드 가능
- JSTL만으로 필요한 대부분의 기능의 처리가 가능하다.
- 용도에따라 크게 5가지로 나누어진다.
  - core : 기본적인 기능 제공
  - fmt : format의 약자로 형식화 관련 기능 제공
  - function : EL에서 사용가능한 문자열과 관련된 함수 제공
  - xml : xml처리와 관련한 편의 기능 제공
  - sql : sql처리와 관련한 편의 기능 제공
  - 주로 core와 fmt가 사용된다.
    - Model2 방식에서는 JSP가 뷰의 역할에 집중
    - xml이나 sql은 서비스단이나 레포지토리단에서 처리
    - function은 javascript나 컨트롤러, 서비스단에서 처리

## 참고

- [JSP 2.3 & Servlet 3.1(입문부터 모델 2 MVC 패턴까지)](http://www.hyejiwon.co.kr/?module=Goods&action=SiteGoods&sMode=VIEW_FORM&sCurrSortCd=001004&iGoodsCd=357&CurrentPage=1&sSearchField=all&sSearchValue=servlet&sort=)
- [JSP Expression Language(표현 언어 또는 익스프레션 언어)](https://gangzzang.tistory.com/entry/JSP-%ED%91%9C%ED%98%84-%EC%96%B8%EC%96%B4Expression-Language-%EB%98%90%EB%8A%94-%EC%9D%B5%EC%8A%A4%ED%94%84%EB%A0%88%EC%85%98-%EC%96%B8%EC%96%B4)
