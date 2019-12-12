# Golang에서의 인증, 인가관련 조사

## 인증과 인가

- 인증(Authentication)
	- 사용자 확인
- 인가(Authorization)
	- 권한부여 및 허가 작업유무 확인

## 패스워드 인증

- 패스워드는 단방향 암호인 해시로 변환하여 관리한다.
- MD5, SHA-1, SHA-256, SHA-512 등의 해시 함수는 취약점이 존재하므로 패스워드 인증에는 사용하지 말아야 한다.
	- Adaptive key derivation function을 사용
- Adaptive key derivation function들은 공통적으로 솔팅과 키 스트레칭을 반복하여 보안 강도를 높인 해시를 생성한다.
	- 그러므로 해시와 솔트를 같이 저장해야 한다.

### PBKDF2

- 가장 많이 사용된다.
- 아주 가볍고 구현하기 쉬우며, SHA와 같이 검증된 해시 함수만을 사용한다.
- ISO-27001의 보안 규정을 준수하고, 서드파티의 라이브러리에 의존하지 않으면서 사용자 패스워드의 다이제스트를 생성하고 싶을 경우 사용한다.
- golang에서는 `"golang.org/x/crypto/pbkdf2"`라는 라이브러리로 공식지원
	- 해시 함수를 원하는대로 지정이 가능하다.

### Bcrypt

- 패스워드 암호화에 특화된 함수이다.
	- 솔트 값을 따로 저장하지 않는다.
	- 같은 암호로 해시 값을 반복적으로 생성해도, 다른 해시 값이 생성된다.
- 매우 강력한 패스워드 다이제스트를 생성하는 시스템을 쉽게 구현하고 싶을때 사용한다.
- golang에서는 `"golang.org/x/crypto/bcrypt"`라는 라이브러리로 공식지원
	- 해시 값과 패스워드를 비교해 주는 메소드를 지원한다.

### Scrypt

- PBKDF2와 유사하나, 비용이 더 소모된다.
- 구현하려는 시스템이 매우 민감한 정보를 다루고, 보안 시스템을 구현하는 데 많은 비용을 투자할 수 있을 경우 사용한다.
- golang에서는 `"golang.org/x/crypto/scrypt"`라는 라이브러리로 공식지원
	- 내부적으로는 sha256기반의 pbkdf2를 사용한다.

### Benchmark 결과

| Benchmark Name                        | Total Repetitions achieved | Single Repetition Duration |
| ------------------------------------- | -------------------------- | -------------------------- |
| BenchmarkPBKDF2Generate-8             | 340                        | 3470757 ns/op              |
| BenchmarkBcryptGenerate-8             | 18                         | 63301273 ns/op             |
| BenchmarkBcryptCompareHash-8          | 18                         | 63219123 ns/op             |
| BenchmarkScryptGenerate-8             | 13                         | 87118118 ns/op             |
| BenchmarkPBKDF2GenerateMulticore-8    | 1369                       | 862311 ns/op               |
| BenchmarkBcryptGenerateMulticore-8    | 130                        | 9309674 ns/op              |
| BenchmarkBcryptCompareHashMulticore-8 | 132                        | 9134176 ns/op              |
| BenchmarkScryptGenerateMulticore-8    | 51                         | 20747252 ns/op             |

- PBKDF2와 scrypt는 SHA256 해시 함수를 사용

## 마이크로 서비스의 인증과 인가

- 과거에는 서버 기반 인증을 사용
	- 클라이언트의 인증 정보를 서버의 세션에서 관리
	- stateful 서버
	- 세션 이용에 따른 확장성의 어려움과 과부하 문제가 발생
- 최근에는 토큰 기반 인증이 대두됨
	- 클라이언트의 인증 정보를 토큰 형태로 클라이언트 쪽에서 저장
	- stateless 서버
	- 상태가 없으므로 확장이 유리하며, 세션유지가 필요 없으므로 과부하 문제 완화

## JWT

- 토큰 기반 인증 시스템의 구현체이다.
	- 웹 표준 RFC 7519 에 등록이 되어있다.
- 가볍고 자가수용적인 (self-contained) 방식으로 구현되어 있다.

### JWT의 서명 알고리즘(Signature Algorithm)

| Algorithm         | SHA-256 | SHA-384 | SHA-512 | 비고   |
| ----------------- | ------- | ------- | ------- | ---- |
| HMAC              | HS256   | HS384   | HS512   | 대칭키  |
| RSASSA-PKCS1-v1_5 | RS256   | RS384   | RS512   | 비대칭키 |
| ECDSA             | ES256   | ES384   | ES512   | 비대칭키 |
| RSASSA-PSS        | PS256   | PS384   | PS512   | 비대칭키 |

#### 밴치마크 결과

| Benchmark Name          | Total Repetitions achieved | Single Repetition Duration |
| ----------------------- | -------------------------- | -------------------------- |
| BenchmarkHS256Signing-8 | 1000000                    | 1036 ns/op                 |
| BenchmarkHS384Signing-8 | 1000000                    | 1160 ns/op                 |
| BenchmarkHS512Signing-8 | 995658                     | 1179 ns/op                 |
| BenchmarkRS256Signing-8 | 3440                       | 335839 ns/op               |
| BenchmarkRS384Signing-8 | 3607                       | 335480 ns/op               |
| BenchmarkRS512Signing-8 | 3598                       | 334980 ns/op               |

- jwt-go 라이브러리의 내장 밴치마크

### golang에서의 JWT

#### jwt-go([Github](https://github.com/dgrijalva/jwt-go))

- 예제 사이트
	- [Implementing JWT based authentication in Golang](https://www.sohamkamani.com/blog/golang/2019-01-01-jwt-authentication/)
	- [Authentication in Golang](https://blog.usejournal.com/authentication-in-golang-c0677bcce1a8)

#### JWT Middleware for Gin Framework([Github](https://github.com/appleboy/gin-jwt))

- 내부적으로는 jwt-go를 사용
- Gin 프레임워크의 middleware용으로 wrapping
- 예제 사이트
	- [Github Readme](https://github.com/appleboy/gin-jwt/blob/master/README.md)

#### oauth2

- golang에서 지원하는 oauth2용 공식 라이브러리
	- `"golang.org/x/oauth2"`
- 예제 사이트
	- [Go에서 OAuth2 인증하기](https://mingrammer.com/getting-started-with-oauth2-in-go/)

## 참고

- [인증(Authentication) VS 인가(Authorization)](https://m.blog.naver.com/PostView.nhn?blogId=taeyoun795&logNo=220588115319&proxyReferer=https%3A%2F%2Fwww.google.com%2F)
- [안전한 패스워드 저장](https://d2.naver.com/helloworld/318732)
- [[JWT] JSON Web Token 소개 및 구조](https://velopert.com/2389)
- [OAuth Access Token Implementation](https://medium.com/@darutk/oauth-access-token-implementation-30c2e8b90ff0)