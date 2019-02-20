# 기타 폼 관련 태그

- `<input>`태그, 다중 데이터 관련 폼 요소로 분류하지 않은 기타 폼 태그에 대해 정리한다.

## `<button>`

- `<input>`태그의 `type`속성 값 중, `submit`, `reset`, `button`의 역할과 동일한 태그이다.

### `<input>`태그와의 차이점

- 버튼의 내용(텍스트)를 `value`속성값이 아닌, 태그 내부에 위치시켜 나타낸다.

```html
<input type="button" value="버튼입니다.">
<button type="button">버튼입니다.</button>
```

- 태그 내부에 택스트가 있으면 일반버튼, 이미지가 있으면 이미지 버튼이 된다.

```html
<button type="button">
  <p>택스트 버튼입니다.</p>
</button>
<button type="button">
  <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/1/1b/Suitcase_icon_green.svg/1024px-Suitcase_icon_green.svg.png" alt="이미지 버튼입니다." width="200px">
</button>
```

### `<button>`태그의 장점

- 태그이름 자체로 버튼임을 인지 할 수 있다.
  - 화면낭독기에서 버튼임을 인식 가능하다.
- 버튼에 CSS를 입혀서 mouse over 같은 이벤트 발생 시 스타일을 바꾸는 등의 효과를 주기 편하다.

### `<button>`태그의 `type`속성

- `type`속성값에 따라 디폴트 이벤트가 달라진다.

속성값 | 설명
------|------
`submit` | `<input>`태그의 `submit`과 동일한 역할을 수행. 미지정시 기본 설정값
`reset` | `<input>`태그의 `reset`과 동일한 역할을 수행. 
`button` | `<input>`태그의 `button`과 동일한 역할을 수행. 

## `<progress>`

- 작업의 진행상태를 나타내는 태그이다.
- 막대바로 표시되며, 진행 시작을 0으로 하여 `value`속성값과 `max`속성값을 기준으로 진행률을 가시화 한다.
- 닫힘태그를 생략 할 수 없음에 주의!

```html
<progress max="100" value="50"></progress>
```

### `<progress>`태그의 속성

속성 | 설명
----|------
`value` | 작업 진행 상태를 실수로 표현. 수치는 0보다 크고 `max`속성값보다 작아야 함.
`max` | 작업 완료시의 수치를 실수로 표현. 0보다 커야하며, 초기값을 1.0

## `<meter>`

- 전체 크기 중에 얼마만큼 차지하는지를 나타내는 태그이다.
- `<progress>`하고 비슷한 막대바로 표시된다.
- 속성값을 사용하여 낮음, 보통, 높음의 상태를 시각적으로 표현 할 수 있다.
- 닫힘태그를 생략 할 수 없음에 주의!

```html
<meter value="19" min="0" max="100" low="20" high="80" optimum="50"></meter>
<meter value="50" min="0" max="100" low="20" high="80" optimum="50"></meter>
<meter value="81" min="0" max="100" low="20" high="80" optimum="50"></meter>
```

### `<meter>`태그의 속성

속성 | 설명
----|------
`min` | 표시 범위의 최소값을 지정. 초기값은 0
`max` | 표시 범위의 최대값을 지정. 초기값은 1
`value` | 현재 상태를 나타낸는 수치 지정
`low` | 낮은 상태의 기준 수치를 지정
`high` | 높은 상태의 기준 수치를 지정
`optimum` | 적당한 상태의 기준 수치를 지정

## 참고

- [Do it! HTML5+CSS3 웹 표준의 정석 <개정판>, 2017, 고경희](http://www.easyspub.co.kr/20_Menu/BookView/119/PUB)