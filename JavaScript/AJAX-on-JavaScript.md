# AJAX (JavaScript)
- 자바스크립트 상에서는 `XMLHttpRequest`객체를 이용하여 서버와 AJAX통신이 가능하다.

## `XMLHttpRequest`객체의 사용법
- `XMLHttpRequest`객체는 자바스크립트 상에서 서버와 통신을 하기위한 기능을 제공한다.
- 메소드의 인수 값을 통해 동기적, 비동기적 통신 모두 지원한다.

### 송신 방법
- `XMLHttpRequest`객체의 `open`메소드와 `send`메소드를 이용하여 서버에 request를 송신하는 것이 가능하다.<br>
- `setRequestHeader`메소드를 사용하여 송수신시 데이터의 형식지정이 가능하다.

#### `open`메소드
- 새롭게 생성 된 request의 초기화 및 기존의 request의 재초기화를 수행하는 메소드이다.

구문 | `XMLHttpRequest.open(method, url [, async [, user [, password]]])`
-----|-------
`method` | 사용할 HTTP Request method (ex: 'GET', 'POST')
`url` | request를 송신 할 URL
`async` | 비동기 통신 유무를 boolean으로 설정, 기본값은 true
`user` | 임의의 인증 프로세스에 사용 할 유저이름, 기본값은 null
`password` | 임의의 인증 프로세스에 사용 할 패스워드, 기본값은 null

#### `setRequestHeader`메소드
- HTTP Request Header 값을 설정한다.
- `open`메소드 뒤, `send`메소드 앞에서 실행해야 한다.
- 같은 헤더에 대해 `setRequestHeader`메소드를 두 번이상 실행하는 경우, 실행 될 때마다 기존의 헤더 값의 말미에 값이 추가된다.

구문 | `XMLHttpRequest.setRequestHeader(header, value)`
-----|-------
`header` | 값을 설정 할 헤더의 이름
`value` | 헤더에 설정 할 값

#### 자주쓰이는 Request Header

타입 | 설명
----|-----