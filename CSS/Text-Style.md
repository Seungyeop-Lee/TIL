# 텍스트 스타일

- 글꼴 관련 스타일을 제외한 텍스트 스타일에 대해 정리한다.

## `color` 속성

- 글자의 색상을 지정하는 속성이다.
- 속성값으로는 16진수나 rgb, rgba, hsl, hsla, 색상 이름을 설정 할 수 있다.
- 기본형은 `color: <색상>;`이다.

```css
color: black;
```

## `text-decoration` 속성

- 텍스트의 줄을 표시하거나 없앰을 지정하는 속성이다.
- 기본형은 `text-decoration: none | underline | overline | line-through;`이다.

```css
text-decoration: none;
```

| 속성값       | 설명                          |
| ------------ | ----------------------------- |
| none         | 텍스트에 줄을 표시하지 않음   |
| underline    | 밑줄을 표시 함                |
| overline     | 텍스트 영역 위에 줄을 표시 함 |
| line-through | 취소선을 표시 함              |

- `<a>`태그의 밑줄을 없앨 때 사용한다.

## `text-transform` 속성

- 영문자 표기시 대/소문자 표기를 지정하는 속성이다.
- 기본형은 `text-transform: none | capitalize | uppercase | lowercase | full-width;`이다.

```css
text-transform: capitalize;
```

| 속성값     | 설명                                                 |
| ---------- | ---------------------------------------------------- |
| none       | 문서에 적힌 그대로 표현. 기본값                      |
| capitalize | 시작하는 첫 번째 글자를 대문자로 변환                |
| uppercase  | 모든 글자를 대문자로 변환                            |
| lowercase  | 모든 글자를 소문자로 변환                            |
| full-width | 전각 문자로 변환 가능한 모든 문자는 전각 문자로 변환 |

## `text-shadow` 속성

- 텍스트에 그림자 효과를 지정하는 속성이다.
- 속성값에 두 개이상의 그림자 효과를 지정하는 것도 가능하며, 콤마(,)로 구분한다.
- 기본형은 `text-shadow: none | <가로 거리> <세로 거리> [<번짐 정도>] [<색상>] [, ...];`이다.

```css
text-shadow: 10px 5px;
```

| 속성값    | 설명                                                                                       |
| --------- | ------------------------------------------------------------------------------------------ |
| none      | 그림자를 표시하지 않음. 기본값                                                             |
| 가로 거리 | 텍스트부터 그림자까지의 가로 거리 지정. 양수는 오른쪽, 음수는 왼쪽에 그림자를 표현         |
| 세로 거리 | 텍스트부터 그림자까지의 세로 거리 지정. 양수는 위쪽, 음수는 아래쪽에 그림자를 표현         |
| 번짐 정도 | 그림자의 번짐 정도를 지정. 클 수록 번짐 정도가 심해져서 그림자의 범위가 늘어남. 초기값은 0 |
| 색상      | 그림자의 색상을 지정. 여러 색상 지정 가능(공백으로 구분). 초기값은 현재 글자 색상          |

## `white-space` 속성

- 공백 처리에 대한 규칙을 지정하는 속성이다.
- 기본형은 `white-space: normal | nowrap | pre | pre-line | pre-wrap;`이다.
- normal이 기본값이다.

```css
white-space: pre-line;
```

| 속성값   | 여러 개의 공백 처리 | 영역을 넘어가는 텍스트 |
| -------- | ------------------- | ---------------------- |
| normal   | 공백 하나로 변환    | -                      |
| nowrap   | 공백 하나로 변환    | 한줄 표시              |
| pre      | 그대로 표시         | 한줄 표시              |
| pre-line | 공백 하나로 변환    | 자동 개행              |
| pre-wrap | 그대로 표시         | 자동 개행              |

## `letter-spacing` 속성

- 글자와 글자 사이의 간격을 지정하는 속성이다.
- 기본형은 `letter-spacing: normal | <크기>;`이다.

```css
letter-spacing: 0.2em;
```

## `word-spacing` 속성

- 단어와 단어 사이의 간격을 지정하는 속성이다.
- 기본형은 `word-spacing: normal | <크기>;`이다.

```css
word-spacing: 0.3em;
```

## 참고

- [Do it! HTML5+CSS3 웹 표준의 정석 <개정판>, 2017, 고경희](http://www.easyspub.co.kr/20_Menu/BookView/119/PUB)