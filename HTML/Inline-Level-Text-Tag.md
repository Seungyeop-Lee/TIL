# 인라인 레벨 텍스트 관련 태그(Inline level Text Tag)

- CSS의 속성 중 `display`의 값이 `inline`인 텍스트 관련 태그를 정리한다.
- 일반적으로 블록 레벨 태그 안에서 사용된다.

## `<strong>`, `<b>`

- 택스트를 굵게 나타내는 태그이다.
- `<b>`는 보이기에만 굵게 나타낸다.
- `<strong>`은 '그 부분을 강조'라는 의미도 가지고 있다.

```html
<div>
  <p>b태그를 쓰면 <b>이렇게!</b> 굵게 표시된다.</p>
  <p>strong태그를 쓰면 <strong>이렇게!</strong> 굵게 표시된다.</p>
</div>
```

[예제코드 실행 결과(codepen)](https://codepen.io/seungyeop-lee/pen/NoaJjw)

## `<em>`, `<i>`

- 텍스트를 이텔릭체로 나타내는 태그이다.
- `<i>`는 보이기에만 이텔릭체로 나타낸다.
- `<em>`은 그 부분을 가조라는 의미도 가지고 있다.

```html
<div>
  <p>i태그를 쓰면 <i>이렇게!</i> 이텔릭체로 표시된다.</p>
  <p>em태그를 쓰면 <em>이렇게!</em> 이텔릭체로 표시된다.</p>
</div>
```

[예제코드 실행 결과(codepen)](https://codepen.io/seungyeop-lee/pen/BMwbdZ)

## `<q>`

- 다른 블로그나 문헌을 인용 했음을 나타내는 태그이다.
- `<blockquote>`와 다른 점은 인라인 레벨 태그이기 때문에 줄 바꿈없이 다른 내용과 함께 사용 가능한 점이다.
- 브라우저에서는 따옴표("")로 감싸져서 표현된다.

```html
<div>
  <p>어디선가 <q>수학의 시작은 구구단이다.</q>라는 말을 들었다.</p>
</div>
```

[예제코드 실행 결과(codepen)](https://codepen.io/seungyeop-lee/pen/aXLMyg)

## `<mark>`

- 노란색 형광펜으로 그어놓은 듯한 효과를 나타내는 태그이다.

```html
<div>
  <p>밑줄을 <mark>쫙~!!!!</mark> 쳐보았다.</p>
</div>
```

[예제코드 실행 결과(codepen)](https://codepen.io/seungyeop-lee/pen/KJXEXe)

## `<span>`

- 가지고있는 의미는 없다.
- 줄 바꿈 없이 일부 텍스트를 묶을 때 사용한다.
- 보통 일부의 텍스트만 CSS를 적용시키고 싶을 때 사용한다.

```html
<style>
  .red-color {
    color: red;
  }
</style>

<div>
  <p><span class="red-color">사</span>자<span class="red-color">성</span>어</p>
</div>
```

[예제코드 실행 결과(codepen)](https://codepen.io/seungyeop-lee/pen/vbePWK)

## `<ruby>`

- 글자에 주석을 다는 용도로 사용한다. (ex: 일본어의 요미가나)
- `<ruby>`태그 안에 `<rt>`로 주석을 나타낸다.

```html
<div>
  <ruby>質問<rt>しつもん</rt></ruby>
</div>
```

[예제코드 실행 결과(codepen)](https://codepen.io/seungyeop-lee/pen/MLExOP)

## `<abbr>`

- 약어임을 나타내는 태그이다.
- `title`속성을 이용해 약어의 본래 용어를 표현 할 수 있다.
- `title`속성을 사용 할 경우, 약어에 점선이 그어지고 mouse over 할 경우 `title`의 값이 툴팁으로 나타난다.

```html
<div>
  <p><abbr title="Hyper Text Markup Language">HTML</abbr></p>
</div>
```

[예제코드 실행 결과(codepen)](https://codepen.io/seungyeop-lee/pen/VgMRye)

## `<cite>`

- 책이나 노래, 영화, 예술 작품이름 등임을 나타내는 태그이다. (사람 이름은 대상 외)
- 포함된 텍스트는 이텔릭체로 표현된다.

```html
<div>
  <p><cite>Do it! HTML5+CSS3 웹 표준의 정석 &lt;개정판&gt;</cite>, 2017, 고경희</p>
</div>
```

[예제코드 실행 결과(codepen)](https://codepen.io/seungyeop-lee/pen/jdGJYx)

## `<code>`

- 컴퓨터 프로그래밍 코드를 나타내는 태그이다.
- 코드 자체를 표현하기위해 `<pre>`태그와 같이 사용된다.

```html
<div>
  <pre><code>
public static void main(String[] args) {
  System.out.println("Hello World!");
}
  </code></pre>
</div>
```

[예제코드 실행 결과(codepen)](https://codepen.io/seungyeop-lee/pen/omGVEj)

## `<samp>`

- 컴퓨터 프로그램이 실행 된 결과를 나타내는 태그이다.

```html
<div>
  <p><samp>Hello World!</samp></p>
</div>
```

[예제코드 실행 결과(codepen)](https://codepen.io/seungyeop-lee/pen/yZzwvR)

## `<kbd>`

- 사용자의 키보드 조작을 나타내는 태그이다. (ex: F5)

```html
<div>
  <p><kbd>Alt</kbd> + <kbd>F4</kbd>를 누르면 창이 닫힙니다.</p>
</div>
```

[예제코드 실행 결과(codepen)](https://codepen.io/seungyeop-lee/pen/VgMRXa)

## `<small>`

- 상대적으로 작게 표현 할 텍스트를 나타낸다.
- 포함된 텍스트의 font-size는 "smaller"로 설정된다.

## `<sup>`

- 윗 첨자로 표현 할 텍스트를 나타낸다.

## `<sub>`

- 아래 첨자로 표현 할 텍스트를 나타낸다.

```html
<div>
  <p>일반 텍스트, <small>작은 텍스트</small>, <sup>윗 첨자</sup>, <sub>아래 첨자</sub></p>
</div>
```

[예제코드 실행 결과(codepen)](https://codepen.io/seungyeop-lee/pen/KJXEoB)

## `<s>`

- 포함한 텍스트에 취소선을 표시한다.

## `<u>`

- 포함한 텍스트에 밑줄을 표시한다.

```html
<div>
  <p><s>취소 쫙!</s></p>
  <p><u>밑줄 쫙!!</u></p>
</div>
```

[예제코드 실행 결과(codepen)](https://codepen.io/seungyeop-lee/pen/mvBoLR)

## 참고

- [Do it! HTML5+CSS3 웹 표준의 정석 <개정판>, 2017, 고경희](http://www.easyspub.co.kr/20_Menu/BookView/119/PUB)
- [w3schools > HTML \<cite\> Tag](https://www.w3schools.com/tags/tag_cite.asp)
- [w3schools > HTML \<samp\> Tag](https://www.w3schools.com/tags/tag_samp.asp)
- [w3schools > HTML \<small\> Tag](https://www.w3schools.com/tags/tag_small.asp)
- [w3schools > HTML \<kbd\> Tag](https://www.w3schools.com/tags/tag_kbd.asp)
- [w3schools > HTML \<code\> Tag](https://www.w3schools.com/tags/tag_code.asp)