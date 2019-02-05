# 블록 레벨 텍스트 관련 태그(Block level Text Tag)

- 태그의 default CSS의 속성 중 `display`의 값이 `block`인 텍스트 관련 태그를 정리한다.

## `<h*n*>`

- 제목을 나타내는 태그이다.
- `n`은 1부터 6까지의 정수가 사용가능하다.  
  숫자가 커질수록 텍스트의 크기는 작아진다.

```html
<div>
  <h1>h1 title</h1>
  <h2>h2 title</h2>
  <h3>h3 title</h3>
  <h4>h4 title</h4>
  <h5>h5 title</h5>
  <h6>h6 title</h6>
</div>
```

[예제코드 실행 결과(codepen)](https://codepen.io/seungyeop-lee/pen/dazwLq)

## `<p>`

- 단락을 나타내는 태그이다.

```html
<div>
  <p>단락을 나타내는 태그입니다.</p>
  <p>block 레벨이기 때문에 태그가 닫히면 자동 줄 바꿈이 됩니다.</p>
</div>
```

[예제코드 실행 결과(codepen)](https://codepen.io/seungyeop-lee/pen/MLvZdp)

## `<br>`

- 줄바꿈을 나타내는 태그이다.
- 닫힘 태그가 없다.

```html
<div>
  문장이 이어지다가 <code>&lt;br&gt;</code>를 만나면
  <br>
  줄 바꿈이 됩니다.
</div>
```

[예제코드 실행 결과(codepen)](https://codepen.io/seungyeop-lee/pen/rPzoEz)

## `<hr>`

- 수평선 삽입을 나타내는 태그이다.
- 닫힘 태그가 없다.

```html
<div>
  수평선을 삽입하는 <code>&lt;hr&gt;</code>를 만나면
  <hr>
  줄이 생깁니다.
</div>
```

[예제코드 실행 결과(codepen)](https://codepen.io/seungyeop-lee/pen/ZwJVgK)

## `<blockquote>`

- 다른 블로그나 문헌을 인용했음을 나타내는 태그이다.
- `cite`속성을 이용해 인용 사이트 주소를 표시 할 수있다.  
  (웹 브라우저에는 표시되지 않으나, 검색엔진에 태그의 자세한 정보 전달의 목적 등으로 사용된다.)

```html
<div>
  <blockquote cite="blockquoteTest.com">
    인용문장을 나타내는 태그입니다. cite속성에 인용 url을 넣습니다. cite속성은 표시되지 않습니다.
  </blockquote>
</div>
```

[예제코드 실행 결과(codepen)](https://codepen.io/seungyeop-lee/pen/QYMYLN)

## `<pre>`

- 열림 태그와 닫힘 태그 사이의 텍스트를 그대로 표시함을 나타내는 태그이다.  
  즉, 여러개의 공백 및 줄 바꿈을 그대로 표현한다.
- `<code>`태그를 이용 할 경우, 코드의 형태를 그대로 보여줘야 하기 때문에 자주 같이 쓰인다.
- 웹 문서를 소리로 읽어주는 기계나 점자로 표시해 주는 기계는 `<pre>`태그를 만날경우 무시하기 때문에 사용에 주의가 필요하다.

```html
<div>
  <pre>텍스트를 그대로 표시합니다. 예를들어: 
뛰어쓰기를          많이하거나
줄바꿈을 해도 그대로 적용됩니다.</pre>
</div>
```

[예제코드 실행 결과(codepen)](https://codepen.io/seungyeop-lee/pen/OdjdJJ)

## 참고

- [Do it! HTML5+CSS3 웹 표준의 정석 <개정판>, 2017, 고경희](http://www.easyspub.co.kr/20_Menu/BookView/119/PUB)