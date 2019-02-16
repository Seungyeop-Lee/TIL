# 텍스트 입력 관련 input 태그

- `<input>`태그의 `type`속성값 중 텍스트 입력과 관련된 속성값에 대해 정리한다.

## 텍스트 입력 관련 `<input>`태그의 공통 속성

속성 | 설명
----|-------
`value` | 필드의 초기 설정 값을 지정한다.
`maxlength` | 입력 가능한 최대 글자수 지정, 0 그리고 minlength보다 큰 값을 가져야한다. 지정된 글자수를 넘었을 경우 submit이 되지 않는다.
`minlength` | 입력 가능한 최소 글자수 지정, 0보다 크고 maxlength보다 작은 값을 가져야한다. 지정된 글자수에 미달 될 경우 submit이 되지 않는다.
`placeholder` | 입력란에 표시될 힌트를 지정한다.
`size` | 화면에 보이게 할 글자수를 지정한다.
`pattern` | 유효성 검사를 할 정규표현식을 지정한다. 정규표현식에 만족하지 않는 글자가 입력되었을 경우 submit이 되지 않는다.

## `type="text"`

- 한 줄짜리 일반 텍스트를 입력하는 필드를 나타낸다.

속성 | 설명
----|-------
`spellcheck` | 철자확인 유무를 지정한다. 속성 값으로 `true`, `false`가 올 수 있다.

## `type="password"`

- 암호를 입력하는 필드를 나타낸다.
- 이 필드에 입력된 값은 `*`이나 `●`으로 표시된다.
- `value`속성을 가지고 있지 않다.

## `type="tel"`

- `type="text"`와 동일하나, 클라이언트(브라우저)가 입력된 값이 전화번호라고 인식한다.

## `type="url"`

- `type="text"`와 동일하나, `urlscheme://restofurl`형태의 절대경로 URL 또는 상대경로 URL을 입력해야 한다.

속성 | 설명
----|-------
`spellcheck` | 철자확인 유무를 지정한다. 속성 값으로 `true`, `false`가 올 수 있다.

## `type="email"`

- `type="text"`와 동일하나, 이메일 형식이 맞게 입력해야 한다. (@유무 확인 등)

속성 | 설명
----|-------
`spellcheck` | 철자확인 유무를 지정한다. 속성 값으로 `true`, `false`가 올 수 있다.
`multiple` | 2개 이상의 이메일 입력 가능 유무를 지정한다. 이 속성이 설정되었을 경우, 이메일은 콤마(,) 또는 공백으로 구분한다. 속성값은 없다.

## `type="search"`

- `type="text"`와 동일하나, 텍스트 필드의 우측에 X가 표시되어 입력값을 손쉽게 삭제 할 수 있다.

속성 | 설명
----|-------
`spellcheck` | 철자확인 유무를 지정한다. 속성 값으로 `true`, `false`가 올 수 있다.

## 참고

- [MDN web docs > \<input type="text"\>](https://developer.mozilla.org/ja/docs/Web/HTML/Element/input/text)
- [MDN web docs > \<input type="password"\>](https://developer.mozilla.org/ja/docs/Web/HTML/Element/input/password)
- [MDN web docs > \<input type="tel"\>](https://developer.mozilla.org/ja/docs/Web/HTML/Element/input/tel)
- [MDN web docs > \<input type="url"\>](https://developer.mozilla.org/ja/docs/Web/HTML/Element/input/url)
- [MDN web docs > \<input type="email"\>](https://developer.mozilla.org/ja/docs/Web/HTML/Element/input/email)
- [MDN web docs > \<input type="search"\>](https://developer.mozilla.org/ja/docs/Web/HTML/Element/input/search)