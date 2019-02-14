# input 태그

- `<input>`태그에 대하여 정리한다.

## `<input>`

- `<form>`태그 내부에서 사용되는 폼 요소이다.
- 폼에서 사용자의 입력을 받기위해 사용된다.
- 폼 요소 중 가장 많이 쓰이며, `type`속성으로 실제적인 입력 요소의 종류를 설정한다.
- `<input>`태그는 닫힘 태그가 없다.

### `<input>`공통 속성

- `type`속성값과 상관없이 `<input>`태그가 가질 수 있는 속성을 정리한다.

속성 | 설명
----|------
`disable` | 해당 태그를 비활성 시킨다. 속성값은 없다.
`name` | 해당 태그의 이름을 설정한다. 서버에서 각 `<input>`의 데이터를 구별하는 기준
`value` | 해당 태그가 가지고 있을 값을 설정한다.
`type` | 해당 태그의 `input`타입을 설정한다. 기본값은 `text`
`autocomplete` | 해당 태그의 자동완성 기능 사용 유무를 설정한다. 기본값은 해당 태그가 속해있는 `<form>`태그의 `autocomplete`속성값을 따른다.
`form` | `<form>`태그 외부에 해당 `<input>`태그가 존재 할 경우, `<form>`태그와 연결 할 때 사용. 속성값으로는 연결시킬 `<form>`태그의 `id`를 설정한다.
`readonly` | 해당 태그의 값을 읽기 전용으로 설정한다. 속성값은 없다.
`required` | 해당 태그를 필수 입력항목으로 지정한다. 속성값은 없다.
`autofocus` | 페이지 로딩 후 해당 태그에 포커스를 설정한다. 속성값은 없다.

### `<input>`의 `type`속성 종류

#### 텍스트 관련

`type`속성값 | 종류
------------|------
`text` | 한 줄짜리 텍스트 입력 필드
`email` | 메일 주소 입력 필드
`password` | 비밀번호 입력 필드
`search` | 검색용 입력 필드
`tel` | 전화번호 입력 필드
`url` | URL주소 입력 필드

#### 버튼 형태

`type`속성값 | 종류
------------|------
`file` | 파일 첨부 버튼
`submit` | 서버 전송 버튼
`image` | `submit`버튼 대신 사용 할 이미지
`button` | 디폴트 이벤트가 없는 버튼
`reset` | 폼의 `<input>`태그들의 내용 초기화 버튼

#### 날짜 관련

`type`속성값 | 종류
------------|------
`datetime-local` | 사용자 지역 기준의 날짜와 시간 입력 필드 (연,월,일,시,분)
`date` | 사용자 지역 기준의 날짜 입력 필드 (연,월,일)
`month` | 사용자 지역 기준의 날짜 입력 필드 (연,월)
`week` | 사용자 지역 기준의 날짜 입력 필드 (연,주)
`time` | 사용자 지역 기준의 시간 입력 필드 (시,분)

#### 그 외 관련

`type`속성값 | 종류
------------|------
`hidden` | 사용자에게는 보이지 않지만 서버로 념겨지는 값
`number` | 숫자를 조절 할 수 있는 화살표를 포함한 입력필드
`checkbox` | 체크박스 (다중 선택 가능)
`radio` | 라디오 버튼 (1개만 선택 가능)
`range` | 숫자를 조절 할 수있는 슬라이드 막대
`color` | 색상 입력 표

## 참고

- [Do it! HTML5+CSS3 웹 표준의 정석 <개정판>, 2017, 고경희](http://www.easyspub.co.kr/20_Menu/BookView/119/PUB)
- [w3schools.com > HTML \<input\> Tag](https://www.w3schools.com/tags/tag_input.asp)
- [w3schools.com > HTML \<input\> type Attribute](https://www.w3schools.com/tags/att_input_type.asp)