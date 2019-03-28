# REST API

## REST API란

- REST + API의 합성어로 REST 아키텍쳐 스타일을 따르는 API를 지칭하는 용어이다.
- 여기서 말하는 API란 일반적으로 웹 API를 지칭한다.
- REST를 따르는 API라는 의미에서 RESTful API로도 불린다.
- 일반적으로 사용되는 REST API는 엄밀한 의미에서 REST API가 아니다.
  - uniform interface 제약조건을 완벽히 만족 시키지 못하는 REST API가 대부분
    - self-descriptive messages 미충족
    - hypermedia as the engine of application state (HATEOAS) 미충족
- 완벽히 REST를 지키지 못한 API를 Web API 또는 HTTP API라고도 부른다.

## REST API의 구성요소

### 자원(Resource)

- HTTP URI를 식별자로 사용하여 모든 자원을 구분한다.
- uniform interface 제약조건의 identification of resources를 만족시킨다.

### 행위(Verb)

- HTTP Method를 통해 행위를 나타낸다.

HTTP Method | CRUD
------------|------
GET | Read
POST | Create
PUT | Update
PATCH | Partial Update
DELETE | Delete

- uniform interface 제약조건의 manipulation of resources through representations를 만족시킨다.

### 표현(Representation)

- HTTP Message Pay Load를 통해 표현을 나타낸다.
  - Pay Load란 서버에서 받은 Response 중 핵심이 되는 데이터의 덩어리를 의미한다.

## REST API에서의 REST 제약조건 충족

### 1. client-server

- 웹 API는 클라이언트-서버 모델로 구성되어 있다.
- 서버
  - API 제공 및 비지니스 로직 처리, 저장을 수행한다.
- 클라이언트
  - 사용자 인증 및 세션, 로그인 정보를 관리한다.

### 2. stateless

- HTTP 프로토콜이 무상태 프로토콜이다.

### 3. cacheable

- HTTP 프로토콜의 캐싱기능을 사용한다.

### 4. uniform interface

- REST API 구성 요소를 통해 4가지 제약조건 중 2가지를 만족 시킬 수 있다.
  - identification of resources 충족
  - manipulation of resources through representations 충족
- self-descriptive messages
  - 기존 JSON을 매개로 하는 표현방법은 내용의 정의를 스스로 표현하지 못한다.
  - self-descriptive messages 충족 방법
    - 미디어 타입 을 IANA에 등록한다.
    - API 문서의 링크를 제공하여야 한다.
- hypermedia as the engine of application state (HATEOAS)
  - 기존 JSON을 매개로 하는 표현방법은 다음 상태로 전이 가능한 Hyperlink를 제공하지 않는다.
  - hypermedia as the engine of application state (HATEOAS) 충족 방법
    - 데이터에 다양한 방법으로 링크를 표현한다.
    - HTTP 헤더의 Location, Link를 이용한다.

### 5. layered system

- 클라이언트-서버 모델이 계층적 시스템을 나타낸다.
- 서버의 다중 계층 구성이 가능하다.
  - 보안, 로드벨런싱, 암호화, 사용자 인증 등의 역할을 하는 서버를 계층적으로 구성
- 네트워크 기반의 중간 매체를 이용하여 계층을 구성한다.
  - 프록시, 게이트웨이

### 6. code-on-demand (optional)

- HTTP Message Pay Load로 클라이언트에서 실행 할 코드 전송이 가능하다.

## 참고

- [그런 REST API로 괜찮은가](https://slides.com/eungjun/rest#/)
- [Heee's Development Blog > [Network] REST란? REST API란? RESTful이란?](https://gmlwjd9405.github.io/2018/09/21/rest-and-restful.html)
- [poiemaweb > REST(Representational State Transfer) API](https://poiemaweb.com/js-rest-api)
- [혜빈파파의 좌충우돌 인생 & 개발 스토리 > [HTTP METHOD] PUT vs PATCH 차이점](https://papababo.tistory.com/269)