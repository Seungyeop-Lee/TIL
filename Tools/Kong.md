# [Kong](https://github.com/Kong/kong)

- nginx 기반의 오픈소스 API Gateway
- 무료버전의 경우 REST API를 통한 설정 및 관리가 제공
- [konga](https://github.com/pantsel/konga)를 이용하여 GUI로 관리 가능
- Kong v1.3 기준

## 구성요소

- Route
  - 외부에서 받은 request에 따라 라우팅
- Service
  - 라우팅 받은 서비스, 논리적 서비스 관리단위
  - 하나 이상의 Route와 매핑가능
- Upstream
  - 모듈의 모음, 서비스에서 request를 받아 Target에 전달
  - Load Balancing
  - Target의 Health Check
    - 이메일, slack으로 통지 가능
- Target
  - 실제 모듈의 집합
- Consumer
  - 서비스를 사용하는 사용자
  - 즉, API를 호출하는 호출자
  - 사용자라기보다는 역할로 이해하는 것이 좋을듯
  - Consumer 별 credential부여 가능

## 플러그인

- Global 및 Route, Service, Consumer 별 등록도 가능
  - 각 항목 당 등록 가능한 플러그인의 종류가 상이

### Authentication

- 인증관련 플러그인 모음
- Route 또는 Service에 등록하여 사용
  - 글로벌 등록도 가능
- Consumer에 해당 인증 정보를 등록

#### Basic Auth

- consumer에 등록한 id와 password를 사용하는 기본 인증
  - consumer의 id와 Basic Auth의 id는 다른 id로 할 것!

#### Key Auth

- consumer에 등록한 api-key를 명시한 key이름으로 header나 body에 넣었는지를 확인하는 인증

#### Hmac Auth, Jwt

- Hmac와 Jwt를 사용한 인증방법
- Jwt의 경우 Kong은 Token을 확인하는 역할만 하므로 Token Provider가 따로 필요하다.

### Security

- 대부분 white list와 black list방식으로 접근에 대한 설정 가능

#### Bot Detection

- User-Agent header의 값을 기준으로 접근/금지 정책 설정

#### IP RESTRICTION

- IP를 기준으로 접근/금지 정책 설정

#### Cors

- Cross-Origin Resource Sharing 관련 설정

### Traffic Control

#### Access Control List(ACL)

- consumer를 그룹으로 묶어서 접근/금지 정책 설정

#### Rate Limiting

- 일정 시간 (초, 분, 시, 일, 월, 년) 동안 일정 이상의 request가 발생 할 경우 차단

#### Request Size Limiting

- request의 body의 최대 크기 제한

#### Request Termination

- 해당 service나 route의 접근 제한
- 제한 시 응답을 customize 가능
  - status code
  - message
  - content type
  - body

### Transformations

- request와 response에 대한 수정 관련 플러그인

#### Request Transformer

- request의 Query, Header, Body(JSON)에 대한 조작을 수행
- 단순히 key기준으로 일치 여부 판단 후 조작
  - remove: 삭제
  - rename: 이름변경
  - replace: 바꿈
  - add: 추가
  - append: 이어붙이기
- http method별 설정도 가능

#### Response Transformer

- response의 Body(JSON), Header에 대한 조작을 수행
- 단순히 key기준으로 일치 여부 판단 후 조작
  - remove: 삭제
  - replace: 바꿈
  - add: 추가
  - append: 이어붙이기

#### Correlation Id

- Request에서 받은 Correlation Id를 헤더에 담아 가지고 다니게 한다.
  - Request에서 받지 않으면 Kong이 자동 생성
- MSA에서 logging이나 transaction관리 쪽에 저장되며 Transaction Tracing에 사용된다.

### Monitoring

#### Prometheus

- Kong의 vital motioring 도구인 Prometheus와 연결하는 플러그인
- prometheus와 granfana를 이용하여 모니터링 및 시각화 가능
  - prometheus plugin -> prometheus(모니터링) -> granfana(시각화)

#### Zipkin

- service내의 작업시간 추적 monitoring 도구인 Zipkin과 연결하는 플러그인
- zipkin 컨테이너와 연결하여 사용

#### Datadog

- Datadog와 연결하는 플러그인
- 더 조사 필요

### Loggin

#### Udp Log

- request와 response 로그를 전부 UDP 서버로 전송
- logstash, elasticsearch, kibana를 사용하여 로그 분석 및 시각화 가능
  - Udp Log Plugin -> logstash(저장) -> elasticsearch(분석) -> kibana(시각화)

## Secure Admin API

### Consumer와 API Key를 이용한 Secure

1. admin api에 접근가능한 service와 route를 설정
2. 관리자에 해당하는 consumer 생성
3. consumer에 credentials -> api keys에서 key등록
4. (option) groups에서 접근 가능 설정한 그룹을 등록
5. Konga의 Connections -> 접속 된 Kong connection 선택 -> key auth -> api key에 consumer에 등록한 key 입력
6. service에 `key-auth`플러그인 설치 후 key name 설정
7. (option) service에 `acl`플러그인 설치 후 접근 가능 그룹 설정
