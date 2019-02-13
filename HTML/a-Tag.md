# 앵커 태그

- `<a>`태그와 관련된 내용을 정리한다.

## `<a>`

- 링크를 나타내는 태그이다.
- `<a>`태그 내부에 텍스트를 위치시키면 텍스트링크, 이미지를 위치시키면 이미지 태그가 된다.

```html
<div>
  <a href="">Link</a>
  <a href=""><img src="https://upload.wikimedia.org/wikipedia/commons/thumb/1/1b/Suitcase_icon_green.svg/1024px-Suitcase_icon_green.svg.png" height="50px"></a>
<div>
```

[예제코드 실행 결과(codepen)](https://codepen.io/seungyeop-lee/pen/xMJrqO)

### `href`속성

- 링크의 목적지를 나타내는 속성이다.

```html
<div>
  <a href="https://www.google.com">Google</a>
<div>
```

[예제코드 실행 결과(codepen)](https://codepen.io/seungyeop-lee/pen/gqjRme)

### `target`속성

- 링크가 열릴 프레임을 나타내는 속성이다.

속성값 | 위치
------|-------
`_blank` | 새 윈도우 또는 새 탭
`_parent` | 부모 프레임
`_self` | 현재 프레임(링크가 위치한 프레임), 기본값
`_top` | 최상단 프레임, 부모 프레임이 없을 경우 `_self`와 동일
framename | 프레임의 name속성이 속성값과 일치하는 프레임에서 열림

```html
<div>
  <p><a href="https://www.google.com" target="_blank">Google(target="_blank")</a></p>
  <p><a href="https://www.google.com" target="_self">Google(target="_self")</a></p>
  <p><a href="https://www.google.com" target="_top">Google(target="_top")</a></p>
  <p><a href="https://www.google.com" target="frame1">Google(target="frame1")</a></p>
  <p><a href="https://www.google.com" target="_parent">Google(target="_parent")</a></p>
</div>
<iframe name="frame1" width="500px" height="500px" src="#"></iframe>
```

[예제코드 실행 결과(codepen)](https://codepen.io/seungyeop-lee/pen/exjRWY)

### `download`속성

- `href`속성에 설정된 URI의 자원을 다운로드 함을 나타내는 속성이다.
- 속성값을 지정해주면 다운로드 시 속성값을 이름으로 하여 다운로드된다. 속성값이 없어도 된다.
- 사용제 제약이 있다. 자세한 사항은 [stackoverflow](https://stackoverflow.com/questions/23872902/chrome-download-attribute-not-working/35290284)를 참조

```html
<div>
  <p>Click to download:<p>
  <a href="https://www.w3schools.com/jsref/horse.mp3" download="test">horse.mp3 download</a>
</div>
```

### `rel`속성

- 현재페이지와 링크의 목적지가 어떤 관계인지를 나타내는 속성이다.
- 검색엔진의 페이지 정보 전달, 보안 강화 목적으로 사용된다.
- 속성값으로 두 개 이상의 단어가 설정 될 수 있으며, 공백으로 구분된다.

속성값 | 설명
------|-------
`alternate` | 링크가 현재 페이지의 대체표현임을 나타냄
`author` | 링크가 현재 페이지의 저자를 설명하는 페이지이거나 저자의 연락처임을 나타냄
`bookmark` | 링크가 현재 페이지를 북마크 함을 의미
`external` | 링크가 외부로 연결되는 링크임을 나타님
`help` | 링크가 현재 페이지의 도움말이라는 것을 나타임
`licence` | 링크가 현재 페이지의 라이센스 관련 내용임을 나타냄
`next` | 링크가 현재 페이지의 다음에 와야 될 페이지임을 나타냄
`prev` | 링크가 현재 페이지의 전 페이지임을 나타냄
`search` | 링크가 현재 페이지 연관 자원을 검색하는 페이지임을 나타냄
`tag` | 링크가 현재 페이지의 태그(키워드)와 연관된 페이지임을 나타냄
`nofollow` | 링크가 현재 페이지와 관계 없음을 나타냄<br>검색엔진이 페이지 분석 시 분석대상에서 제외함
`noreferrer` | 링크에 현재 페이지의 HTTP referrer header를 전송하지 않도록 요청 함을 나타냄
`noopener` | 링크에 현재 페이지의 정보를 넘겨주지 않도록 요청 함을 나타냄<br>즉, 링크로 이동한 페이지의 `window.opener`값이 비어있는 상태가 됨.<br>악의를 가진 페이지를 링크로 접속 시, 현재 페이지가 공격당할 위험을 줄여줌

## 동일문서 안에서 이동

- 이동하고 싶은 태그에 `id`속성값과 `<a>`태그의 `href`속성값의 #이후의 값을 일치시켜주면 된다. (`id`가 abc라면 `href`속성값은 #abc)

```html
<div>
  <a href="#p">go to p tag</a>
  <br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>
  <p id="p">this is p tag</p>
</div>
```

[예제코드 실행 결과(codepen)](https://codepen.io/seungyeop-lee/pen/BMPZRP)

## 그림의 일부분에 링크적용

- `<map>`과 `<area>`태그를 이용하면 그림의 일부분에만 링크를 적용시킬 수 있다.

### 적용방법

1. 부분적으로 링크를 적용시킬 `<img>`태그의 속성으로 `usemap`을 추가하고 속성값으로 `#임의의 이름`을 추가한다.
2. `<img>`태그 후에 `<map>`태그를 위치시킨다.
3. `<map>`태그의 속성으로 `name`을 추가하고 속성값으로 `usemap의 속성값이 #을 제외한 값`을 추가한다.
4. `<map>`태그 내부에 `<area>`태그를 위치시킨다.(`<area>`태그에 닫는 태그는 없다.)
5. `<area>`태그의 필요한 속성들을 추가시킨다.

### `<area>`태그의 속성

- `<a>`태그에서 사용 가능한 속성은 전부 동일하게 사용가능하다.

#### `<area>`태그의 `shape`속성

일부분으로 적용 할 링크의 모양을 나타냄

속성값 | 링크 적용 부분 또는 모양
--------|--------------------------------------
`default` | 해당 그림영역 전체
`rect` | 사각형
`circle` | 원
`poly` | 다각형

```html
<div>
  <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/1/1b/Suitcase_icon_green.svg/1024px-Suitcase_icon_green.svg.png" width="300px" usemap="#bag">
  <map name="bag">
    <area shape="default" href="https://upload.wikimedia.org/wikipedia/commons/thumb/1/1b/Suitcase_icon_green.svg/1024px-Suitcase_icon_green.svg.png">
  </map>
</div>
```

[예제코드 실행 결과(codepen)](https://codepen.io/seungyeop-lee/pen/aXjwwN)

#### `<area>`태그의 `coords`속성

링크의 범위(크기)를 나타냄

속성값 | 설명
------|------
x1, y1, x2, y2 | 왼쪽 상단 꼭지점(x1, y1)과 우측하단 꼭지점(x2, y2)로 사각형 범위를 표현<br>`shape="rect"`인 경우 사용
x, y, radius | 원의 중심(x, y)와 반지름(radius)로 원 범위를 표현<br>`shape="circle"`인 경우 사용
x1, y1, x2, y2, ..., xn, yn | 각 좌표를 꼭지점으로 하는 다각형 범위를 표현<br>`shape="poly"`인 경우 사용

## 참고

- [Do it! HTML5+CSS3 웹 표준의 정석 <개정판>, 2017, 고경희](http://www.easyspub.co.kr/20_Menu/BookView/119/PUB)
- [w3schools.com > HTML \<a\> Tag](https://www.w3schools.com/tags/tag_a.asp)
- [SYNCER > web制作 > HTML > リファレンス > 属性 > 曖昧さ回避 > rel属性](https://lab.syncer.jp/Web/HTML/Reference/Attribute/rel/2/)