# 목록 관련 스타일

- 목록에 관련된 스타일에 대해 정리한다.

## `list-style-type` 속성

- 목록의 불릿 또는 번호 스타일을 지정하는 속성이다.
- 기본형은 `list-style-type: none | <불릿 관련 속성값> | <번호 관련 속성값>;`이다.

```css
list-style-type: none;
```

### 불릿 관련 속성값

- 순서가 없는 목록(`<ul>`)의 불릿 스타일에 대한 속성값은 아래와 같다.

속성값 | 설명
------|------
disc | 채운 원 (●), 기본값
circle | 빈 원 (〇)
square | 채운 사각형 (■)
none | 불릿 무표시

### 번호 관련 속성값

- 순서가 있는 목록(`<ol>`)의 번호 스타일에 대한 속성값은 아래와 같다.

속성값 | 설명
------|------
decimal | 1로 시작하는 십진수, 기본값
decimal-leading-zero | 앞에 0이 붙는 1부터 시작하는 십진수
lower-roman | 소문자 로마 숫자
upper-roman | 대문자 로마 숫자
lower-alpha | 소문자 알파벳
lower-latin | 소문자 알파벳
upper-alpha | 대문자 알파벳
upper-latin | 대문자 알파벳
none | 번호 무표시

## `list-style-image` 속성

- 순서가 없는 목록의 불릿으로 사용 할 이미지를 지정하는 속성이다.
- 기본형은 `list-style-image: url(이미지 파일 경로의 문자열) | none;`이다.

```css
list-style-image: url("images/dot.png");
```

속성값 | 설명
------|------
none | `list-style-type`의 속성값으로 지정된 형태를 사용
url(경로) | 불릿으로 사용 할 이미지를 지정

## `list-style-position` 속성

- 불릿이나 번호가 실제 내용의 안에 존재하게 할지 밖에 존재하게 할지 지정하는 속성이다.
- 불릿이나 번호가 내용의 안에 존재 할 경우 내용이 밀려서 들여쓰기 효과를 줄 수 있다.
- 기본형은 `list-style-position: inside | outside;`이다.

```css
list-style-position: inside;
```

속성값 | 설명
------|-------
inside | 불릿이나 번호가 내용 안에 존재
outside | 불릿이나 번호가 내용 밖에 존재. 기본값

## `list-style` 속성

- 목록 관련 속성(`list-style-type`, `list-style-image`, `list-style-position`)을 한번에 정의 가능한 속성이다.
- 각 속성값은 콤마(,)로 구분한다.

```css
list-style: disc, inside;
```

## 참고

- [Do it! HTML5+CSS3 웹 표준의 정석 <개정판>, 2017, 고경희](http://www.easyspub.co.kr/20_Menu/BookView/119/PUB)