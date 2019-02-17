# 버튼 관련 input 태그

- `<input>`태그의 `type`속성값 중 버튼과 관련된 속성값에 대해 정리한다.

## `type="file"`

- 업로드 할 파일은 선택 할 수 있는 창을 나타낸다.
- 파일을 전송하기 위해서는 `<form>`태그에 `enctype="multipart/form-data"`속성을 추가해야 한다.

### `type="file"`시 `<input>`태그의 사용가능 속성

속성 | 설명
----|------
`accept` | 선택 가능 파일의 종류를 정의
`capture` | `accept`에서 오디오나 비디오를 정의하였을 경우 사용가능<br>파일이 아닌 장치를 이용해 데이터를 습득 함
`multiple` | 2개 이상의 파일선택이 가능함을 나타냄. 속성값은 없음

#### `accept`속성의 선택가능 속성값

속성값 종류 | 설명 | 속성값 예시
-----------|-----|--------------
파일 확장자 | 유효한 파일 확장자, 대소문자 구문이 없으며 마침표를 포함해야 한다. | .txt, .pdf, .doc
MIME 타입 | 유효한 MIME 타입으로 확장자가 아닌것 | image/png
오디오 | 임의의 오디오 파일 | audio/*
비디오 | 임의의 비디오 파일 | vidio/*
이미지 | 임의의 이미지 파일 | image/*

#### `capture`속성의 선택가능 속성값

속성값 | 설명
------|------
user | 유저가 사용하는 내장 카메라나 마이크를 지정
environment | 외부 카메라나 마이크를 지정
(생략) | 어떤 장치를 쓸지 클라이언트 쪽에서 임의로 결정

### 선택파일의 정보 확인

- 사용자가 선택한 파일의 정보는 자바스크립트의 DOM API를 이용해 확인하는 것이 가능하다.
- `type`속성값이 file인 `<input>`태그의 element에 접근 후, `files`속성에 선택한 파일의 정보가 `FileList`객체로 담겨있다.

## `type="submit"`

- 폼 요소에 입력된 데이터의 전송을 실행하는 버튼을 나타낸다.

### `type="submit"`시 사용가능 속성

- 각 속성은 `<form>`태그에 동일역할 속성이 있지만 `<input>`태그 속성이 우선순위가 더 높다.

`<input>`태그 속성 | 동일한 `<form>`태그 속성
------------------|-------------------------
`formaction` | `action`
`formmethod` | `method`
`formtarget` | `target`

## `type="image"`

- 폼 요소에 입력된 데이터의 전송을 실행하는 그림을 나타낸다.
- `type="submit"`시 사용가능 속성 전부 사용가능하다.
- `<img>`태그의 속성 전부 사용가능하다.

## `type="button"`

- 디폴트 이벤트가 정의되지 않은 버튼을 나타낸다.
- 버튼이 눌렸을 때의 동작은 자바스크립트에서 정의하는 것이 일반적이다.

## `type="reset"`

- 폼 요소의 입력치를 전부 초기화한다.

## 참고

- [MDN web docs > \<input type="file"\>](https://developer.mozilla.org/ja/docs/Web/HTML/Element/input/file)
- [MDN web docs > \<input type="submit"\>](https://developer.mozilla.org/ja/docs/Web/HTML/Element/input/submit)
- [MDN web docs > \<input type="image"\>](https://developer.mozilla.org/ja/docs/Web/HTML/Element/input/image)
- [MDN web docs > \<input type="button"\>](https://developer.mozilla.org/ja/docs/Web/HTML/Element/input/button)
- [MDN web docs > \<input type="reset"\>](https://developer.mozilla.org/ja/docs/Web/HTML/Element/input/reset)