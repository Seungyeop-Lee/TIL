# REST

## REST 란

- **RE**presentational **S**tate **T**ransfer의 약자이다.
  - 직역하면 표현적 상태 전달인데, 단어 만으로는 무엇을 뜻하는지 알기 쉽지 않다.
- 분산 하이퍼미디어 시스템(ex. 웹)을 위한 아키텍쳐 스타일 중 하나이다.
  - 아키텍쳐 스타일이란 제약조건의 모음을 의미한다.

## REST의 제약조건

- REST에 만족하기 위해서는 6가지의 제약조건(필수 5개 + 옵션 1개)을 지켜야 한다.
- 필수 제약조건 중 1가지라도 만족하지 않으면 엄밀한 의미에서 REST하다라고 할 수 없다.

### 1. client-server

- 클라이언트-서버 모델을 가져야 한다.
- 클라이언트-서버 모델
  - 클라이언트(client)와 서버(server)간의 작업을 분리해주는 분산 애플리케이션 구조이자 네트워크 아키텍처를 나타낸다.
    - client: 서비스 요청자
    - server: 서비스 제공자

### 2. stateless

- 서버는 클라이언트 요청에 대해 무상태성을 가지고 있어야 한다.
- 무상태성이란 작업을 위한 상태정보를 따로 저장하지 않음을 의미한다.

### 3. cacheable

- 클라이언트는 응답을 캐싱 할 수 있어야 한다.
- 캐싱(cacheing)
  - 캐싱이란 데이터를 임시로 저장해 두는 것을 뜻한다. 
  - 캐싱한 데이터는 빠른 속도로 접근이 가능하기 때문에 전체적인 처리 속도를 향상 시킨다.

### 4. uniform interface

- 4가지의 제약조건을 포함한 아키텍쳐 스타일이다.
  - identification of resources
    - 리소스는 식별자로 나타내어야 한다.
  - manipulation of resources through representations
    - 표현을 통해 리소스의 조작을 해야 한다.
  - self-descriptive messages
    - 메시지는 스스로 설명 할 수 있어야 한다.
  - hypermedia as the engine of application state (HATEOAS)
    - 애플리케이션의 상태는 Hyperlink를 이용해 전이되야 한다.

### 5. layered system

- 계층화된 시스템을 가져야 한다.
- 즉, 클라이언트는 서버를 호출하며, 서버는 다중 계층으로 이루어 질 수 있다.

### 6. code-on-demand (optional)

- 옵션 제약조건이다. (지키지 않아도 됨)
- 서버가 클라이언트에게 실행가능 한 코드 전송이 가능하다. (ex. JavaScript코드, Java Applet코드)

## REST의 장점

- REST를 따르면 서버와 클라이언트의 어느 한쪽이 변경되어도, 다른 한쪽을 변경 할 필요가 없다.
  - 예: 웹 서버와 웹 브라우져가 각각 독립적으로 진화하고 있지만 웹은 잘 돌아간다.(잘 돌아간다는 것은 기능적으로 잘 돌아감을 의미)

## 참고

- [[부스트코스] 웹 프로그래밍 : Rest API란?](https://www.edwith.org/boostcourse-web)
- [그런 REST API로 괜찮은가](https://slides.com/eungjun/rest#/)
- [위키피디아 > REST](https://ko.wikipedia.org/wiki/REST)
- [TOAST Meetup! > REST API 제대로 알고 사용하기](https://meetup.toast.com/posts/92)
- [위키피디아 > 클라이언트 서버 모델](https://ko.wikipedia.org/wiki/%ED%81%B4%EB%9D%BC%EC%9D%B4%EC%96%B8%ED%8A%B8_%EC%84%9C%EB%B2%84_%EB%AA%A8%EB%8D%B8)
- [위키피디아 > 캐시](https://ko.wikipedia.org/wiki/%EC%BA%90%EC%8B%9C)