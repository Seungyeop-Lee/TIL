# 날짜와 시간 관련 input태그

- `<input>`태그의 `type`속성 값 중 날짜 및 시간 입력과 관련된 속성값에 대해 정리한다.
- 공통적으로 사용자의 타임존을 기준으로 한 날짜 및 시간을 입력한다.

## 날짜 및 시간 관련 `<input>`태그의 공통속성

속성 | 설명
----|------
`max` | 허용 가능 최대 날짜 또는 시간을 설정
`min` | 허용 가능 최소 날짜 또는 시간을 설정
`step` | 화살표를 눌렀을 때 수치가 움직이는 간격을 설정

## `max`, `min`, `value` 속성값 형식 및 입력가능 범위

type | 속성값 형식 | 입력가능 범위
-----|------------|--------------
`datetime-local` | yyyy-MM-ddThh:mm | 년, 월, 일, 시, 분
`date` | yyyy-MM-dd | 년, 월, 일
`month` | yyyy-MM | 년, 월
`week` | yyyy-Www | 년, 주
`time` | hh:mm | 시, 분

## 참고

- [MDN web docs > \<input type="datetime-local"\>](https://developer.mozilla.org/ja/docs/Web/HTML/Element/input/datetime-local)
- [MDN web docs > \<input type="date"\>](https://developer.mozilla.org/ja/docs/Web/HTML/Element/input/date)
- [MDN web docs > \<input type="month"\>](https://developer.mozilla.org/ja/docs/Web/HTML/Element/input/month)
- [MDN web docs > \<input type="week"\>](https://developer.mozilla.org/ja/docs/Web/HTML/Element/input/week)
- [MDN web docs > \<input type="time"\>](https://developer.mozilla.org/ja/docs/Web/HTML/Element/input/time)