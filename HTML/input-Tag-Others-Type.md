# 기타 타입의 input태그

- `<input>`태그의 `type`속성값 중 분류되지 않은(텍스트 입력, 버튼 형식, 날짜 관련을 제외 한) 속성값에 대해 정리한다.

## `type="hidden"`

- 표시되지 않는 `<input>`태그를 나타낸다.
- 서버에 전송 할 데이터지만, 사용자에게 보이게하고 싶지 않을때 사용한다.
- 화면에는 보이지 않아도 개발자 도구를 통해 확인이 가능하므로 보안에 관련된 데이터의 전송에는 사용하지 않는것이 바람직하다.

### `type="hidden"`시 사용가능 속성

속성 | 설명
----|------
`name` | 폼에 데이터 전송 시 키의 역할을 할 이름을 지정

## `type="checkbox"`

- 다중선택이 가능한 체크박스를 나타낸다.
- 체크가 된 요소의 `name`속성값을 키로, `value`속성값을 값으로 하여 서버에 전송한다.
- `name`속성값이 동일한 2개 이상의 체크박스를 체크하여 서버에 전송 할 경우, 값은 `value`속성값으로 구정되어 있는 배열로 전달된다.  
  (웹 서버에서 자동으로 배열로 만들어 주는듯하나 **확인 필요**)

### `type="checkbox"`시 사용가능 속성

속성 | 설명
----|------
`checked` | 체크박스의 체크유무의 초기값이 체크되어 있음으로 지정. 속성값은 없음
`value` | `<input>`태그 공통 속성. 체크박스의 경우 초기값이 on으로 설정되어 있음

## `type="radio"`

- 한 개만 선택가능한 라디오 버튼을 나타낸다.
- `name`속성값이 동일한 라디오 버튼에 한하여 1개만 선택이 가능하다.
- 체크가 된 요소의 `name`속성값을 키로, `value`속성값을 값으로 하여 서버에 전송한다.

### `type="radio"`시 사용가능 속성

속성 | 설명
----|------
`checked` | 라디오 버튼의 선택유무 초기값을 선택되어 있음으로 지정. 속성값은 없음

## `type="range"`

- 수치를 입력 할 수 있는 막대바를 나타낸다.
- 정해진 수치의 입력을 강제 할 수있는 장점이 있다.
- `list`속성 및 `<datalist>`태그를 이용하면 막대바의 커스터마이징이 가능하다.

### `type="range"`시 사용가능 속성

속성 | 설명
----|------
`max` | 막대바의 최대값을 지정, 초기값은 100
`min` | 막대바의 최소값을 지정, 초기값은 0
`step` | 막대바의 조절가능 간격을 지정, 초기값은 1

## `type="color"`

- 색상 입력 인터페이스를 나타낸다.

### `type="color"`시 사용가능 속성

속성 | 설명
----|------
`value` | 색상을 나타내는 #rrggbb의 16진수 표현으로 지정된 색의 값이 설정

## `type="number"`

- 숫자를 입력할 수 있는 필드를 나타낸다.

### `type="number"`시 사용가능 속성

속성 | 설명
----|------
`max` | 입력 가능 최대값 지정
`min` | 입력 가능 최소값 지정
`placeholder` | 입력란에 힌트로 표시 할 문자열
`step` | 화살표를 눌렀을 때 수치가 움직이는 간격 지정, 초기값은 1

## 참고

- [MDN web docs > \<input type="hidden"\>](https://developer.mozilla.org/ja/docs/Web/HTML/Element/input/hidden)
- [MDN web docs > \<input type="checkbox"\>](https://developer.mozilla.org/ja/docs/Web/HTML/Element/input/checkbox)
- [MDN web docs > \<input type="radio"\>](https://developer.mozilla.org/ja/docs/Web/HTML/Element/input/radio)
- [MDN web docs > \<input type="range"\>](https://developer.mozilla.org/ja/docs/Web/HTML/Element/input/range)
- [MDN web docs > \<input type="color"\>](https://developer.mozilla.org/ja/docs/Web/HTML/Element/input/color)
- [MDN web docs > \<input type="number"\>](https://developer.mozilla.org/ja/docs/Web/HTML/Element/input/number)