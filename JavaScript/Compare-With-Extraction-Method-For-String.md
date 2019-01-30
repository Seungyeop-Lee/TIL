# 문자열 추출 메소드 비교
- `str.slice()`, `str.substring()`, `str.substr()` 문자열을 추출 하는 메소드이다.
- 각 조건에 따른 문자열 추출 범위를 확인하여 각 메소드의 특징을 비교하였다.
- 추출 범위 확인에 따른 각 메소드의 특징을 설명한 후, 실제 추출 범위 확인 테이블을 제시한다.

## `slice(a, b)`
- 무조건 `a`부터 `b`-1까지의 문자열을 반환한다.
- `a`와 `b`-1의 위치가 역전되면 빈 문자열을 반환한다.
- `a`와 `b`는 음수이면 문자열 끝부터 index를 계산한다. (`-1` == `length-1`)

## `substring(a, b)`
- 작은 숫자 index부터 큰 숫자 index-1까지의 문자열을 반환한다.
- `a`와 `b`는 음수이면 0으로 치환하여 index를 계산한다.

## `substr(a, b)`
- `a`는 음수이면 문자열 끝부터 index를 계산한다. (`-1` == `length-1`)
- `b`는 음수이면 0으로 치환되여 계산한다.

## 문자열 추출 범위 확인

- *문자열 추출 범위 (글로 설명)*

조건 | `slice(a, b)` | `substring(a, b)` | `substr(a, b)`
-----|---------------|-------------------|---------------
`a`≤`b`, `a`≥0, `b`≥0 | `a`부터 `b`-1까지 | `a`부터 `b-1`까지 | `a`부터 `b`개 만큼
`b` 생략 | `a`부터 문자열 끝까지 | `a`부터 문자열 끝까지 | `a`부터 문자열 끝까지
`a`>`b`, `a`≥0, `b`≥0 | 빈 문자열 | `b`부터 `a`-1까지 | `a`부터 `b`개 만큼
`a`<0, `b`≥0 | 빈 문자열 | 0부터 `b`-1까지 | 문자열 끝에서 왼쪽으로 -`a`개 짹부터 `b`개 만큼
`b`<0, `a`≥0 | `a`부터 문자열 끝에서 왼쪽으로 -`b`-1번째 까지 | 0부터 `a`-1까지 | 빈 문자열
`a`<0 & `b`<0 | 빈 문자열 | 빈 문자열 | 빈 문자열

- *문자열 추출 범위 (간략 표현)*

조건 | `slice(a, b)` | `substring(a, b)` | `substr(a, b)`
-----|---------------|-------------------|---------------
`a`≤`b`, `a`≥0, `b`≥0 | `a` ~ `b`-1 | `a` ~ `b`-1 | `a` ~ `a`+`b`-1
`b` 생략 | `a` ~ length-1 | `a` ~ length-1 | `a` ~ length-1
`a`>`b`, `a`≥0, `b`≥0 | `""` | `b` ~ `a`-1 | `a` ~ `a`+`b`-1
`a`<0, `b`≥0 | `""` | 0 ~ `b`-1 | length+`a` ~ length+`a`+`b`-1
`b`<0, `a`≥0 | `a` ~ length+`b`-1 | 0 ~ `a`-1 | `""`
`a`<0 & `b`<0 | `""` | `""` | `""`