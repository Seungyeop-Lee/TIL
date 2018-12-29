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

- *자주쓰이는 Request Header*

타입 | 설명
----|-----
Content-type | request의 body에 쓰여질 데이터의 MIME-type 정보를 표현한다.
Accept | response로 받고자 하는 데이터의 MIME-type 정보를 표현한다. `setRequestHeader`메소드로 Accept 헤더 값을 설정하지 않은 경우, `send`메소드를 실행 할 때 Accept 헤더 값은 */*으로 자동 설정된다.

- *자주쓰이는 MIME-type*

메인 타입 | 설명 | 메인 타입/서브 타입
---------|------|---------------------
text | 사람이 읽을 수 있는 문자를 포함 한 문서 | text/plain, text/html, text/javascript, text/markdown
application | 바이너리 데이터 | application/json, application/x-www-form-urlencode, application/xml, application/pdf
multipart | 두 개 이상의 MIME-type으로 이루어진 타입, 일반적으로 파일 업로드 시 사용 | multipart/formed-data

#### `send`메소드
- request를 서버에 송신하는 메소드이다.

구문 | `XMLHttpRequest.send(body)`
----|-----------------------------
`body` | request의 body에 쓰여질 데이터, 기본값은 null, Http Request method가 GET이나 HEAD처럼 body를 사용하지 않는 method가 설정되 있는 경우는 값이 있어도 null로 치환되어 실행된다.

- *`open`메소드의 인수인 `async`값에 따른 실행차이*
  
`async` | 실행거동
--------|---------
`true` | 서버에 request를 송신 후 자바스크립트 상의 다음 구문을 바로 실행한다. (서버의 응답을 기다리지 않는다.)
`false` | 서버에 request를 송신 후 response를 수신 할 때까지 자바스크립트의 실행을 중단한다. (서버의 응답을 기다린다.)

```javascript
function pullDataFromServer(reqInfo) {

  //XMLHttpRequest 객체 생성
  var xhReq = new XMLHttpRequest();

  //xhReq 초기화
  xhReq.open('POST', reqInfo.url, reqInfo.async);

  //Http Request Header 설정
  xhReq.setRequestHeader('Content-type', reqInfo.contentType);
  
  //request 송신
  xhReq.send(reqInfo.body);

}
```



## 참고
- [PoiemaWeb : JavaScript > 비동기식 처리 모델과 Ajax](https://poiemaweb.com/js-ajax)
- [MDN web docs : 開発者向けのウェブ技術 > ウェブデベロッパーガイド > AJAX > 始めましょう](https://developer.mozilla.org/ja/docs/Web/Guide/AJAX/Getting_Started)
- [MDN web docs : 開発者向けのウェブ技術 > Web API > XMLHttpRequest](https://developer.mozilla.org/ja/docs/Web/API/XMLHttpRequest)
- [MDN web docs : 開発者向けのウェブ技術 > HTTP > HTTPの基本 > MIME タイプ](https://developer.mozilla.org/ja/docs/Web/HTTP/Basics_of_HTTP/MIME_types)