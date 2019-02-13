# 이미지 태그

- `<img>`태그와 관련된 내용을 정리한다.

## `<img>`

- 그림을 나타낸다.
- `src`속성을 통해 표시 할 그림파일의 경로를 지정한다.
- 닫힘 태그는 없다.

```html
<img src="https://upload.wikimedia.org/wikipedia/commons/thumb/1/1b/Suitcase_icon_green.svg/1024px-Suitcase_icon_green.svg.png">
```

[예제코드 실행 결과(codepen)](https://codepen.io/seungyeop-lee/pen/ZwrmpK)

### `alt`속성

- 이하의 상황이 발생하여 로딩에 실패하였을 경우 대신해서 표시 할 텍스트를 나타낸다.
  - 인터넷 속도가 느려 그림파일이 로딩되지 않음
  - 지정 경로를 통해 파일을 불러오는데 실패 함
- 웹 페이지를 읽어주는 화면 낭독기가 `<img>`태그를 만날 경우 `alt`속성의 값을 읽어준다.  
  그러므로 `alt`속성에 되도록 그림을 설명하는 텍스트를 삽입하는 것을 추천한다.

```html
<img src="#" alt="서류 가방">
```

[예제코드 실행 결과(codepen)](https://codepen.io/seungyeop-lee/pen/exVQBR)

### `width`, `height`속성

- 그림의 폭과 길이를 나타낸다.
- 둘 중에 한 개만 사용 할 경우, 지정하지 않은 부분의 길이는 원본의 비율에 맞춰서 자동으로 조절된다.

```html
<img src="https://upload.wikimedia.org/wikipedia/commons/thumb/1/1b/Suitcase_icon_green.svg/1024px-Suitcase_icon_green.svg.png" height="300" width="500">
```

[예제코드 실행 결과(codepen)](https://codepen.io/seungyeop-lee/pen/VgQVmV)

### `<figure>`, `<figcaption>`

- `<figure>`태그는 그림 뿐 아니라 멀티미디어, 코드, 표 등에 설명을 붙이고 싶을 때 사용된다.
- `<figure>`로 `<img>`태그를 감싸고, 설명을 삽입하고 싶은 부분(`<img>`의 전이나 후)에 `<figcaption>`을 위치시킨다.

```html
<figure>
  <figcaption>
    <p>서류 가방</p>
  </figcaption>
  <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/1/1b/Suitcase_icon_green.svg/1024px-Suitcase_icon_green.svg.png" height="300" width="300">
</figure>
```

[예제코드 실행 결과(codepen)](https://codepen.io/seungyeop-lee/pen/NoyEdG)

## 참고

- [Do it! HTML5+CSS3 웹 표준의 정석 <개정판>, 2017, 고경희](http://www.easyspub.co.kr/20_Menu/BookView/119/PUB)