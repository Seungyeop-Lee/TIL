# HTML의 기본적인 텍스트 취급 규칙 및 특수기호 삽입 방법

## 텍스트 취급 규칙

- 단어 사이의 공백이 여러개가 있어도 하나로 취급한다.
- 줄 바꿈이 있으면 공백 1칸으로 취급한다.
- 웹 브라우저의 폭을 넘어갈 경우 자동으로 줄 바꿈이 된다.  
  단, 1개의 행에 1개의 단어가 존재하고, 그 단어가 폭을 넘어갈 경우에는 줄 바꿈이 되지 않는다.

```html
<div style="border: 2px solid black; padding: 10px">
  공백이 여러개가 있어도 하나로 취급
  <div>abc     def</div>
  <br>
  줄 바꿈이 있으면 공백 1칸으로 취급
  <div>abc
  def</div>
  <br>
  웹 브라우저의 폭을 넘어갈 경우 자동으로 줄 바꿈
  <div>
    Lorem ipsum dolor sit, amet consectetur adipisicing elit. Illo quisquam similique sed nostrum veritatis qui ducimus nihil labore obcaecati temporibus iusto, sit ab, dignissimos natus eveniet recusandae voluptate neque amet?
  </div>
</div>
```

<div style="border: 2px solid black; padding: 10px">
  공백이 여러개가 있어도 하나로 취급
  <div>abc     def</div>
  <br>
  줄 바꿈이 있으면 공백 1칸으로 취급
  <div>abc
  def</div>
  <br>
  웹 브라우저의 폭을 넘어갈 경우 자동으로 줄 바꿈
  <div>
    Lorem ipsum dolor sit, amet consectetur adipisicing elit. Illo quisquam similique sed nostrum veritatis qui ducimus nihil labore obcaecati temporibus iusto, sit ab, dignissimos natus eveniet recusandae voluptate neque amet?
  </div>
</div>

## 특수기호 삽입 방법

- HTML에서 공백이나 특수기호를 텍스트 그 자체로 인식시키고 싶을 때 사용한다.

특수기호 | HTML코드에서 표현 방법
:------:|:---------------------:
\& | `&amp;`
(공백 한 칸) | `&nbsp;`
(탭) | `&emsp;` or `&ensp;`
\< | `&lt;`
\> | `&gt;`
\" | `&quot;`
\| | `&#124;`
\( | `&#40;`
\) | `&#41;`
\, | `&#44;`
\- | `&#45;`

```html
<div style="border: 2px solid black; padding: 10px">
  <p>[&amp;] : <code>[&amp;amp;]</code><p>
  <p>[&nbsp;] : <code>[&amp;nbsp;]</code><p>
  <p>[&emsp;] : <code>[&amp;emsp;]</code><p>
  <p>[&emsp;] : <code>[&amp;emsp;]</code><p>
  <p>[&lt;] : <code>[&amp;lt;]</code><p>
  <p>[&gt;] : <code>[&amp;gt;]</code><p>
  <p>[&quot;] : <code>[&amp;quot;]</code><p>
  <p>[&#124;] : <code>[&amp;#124;]</code><p>
  <p>[&#40;] : <code>[&amp;#40;]</code><p>
  <p>[&#41;] : <code>[&amp;#41;]</code><p>
  <p>[&#44;] : <code>[&amp;#44;]</code><p>
  <p>[&#45;] : <code>[&amp;#45;]</code><p>
</div>
```

<div style="border: 2px solid black; padding: 10px">
  <p>[ &amp; ] : <code>[ &amp;amp; ]</code><p>
  <p>[ &nbsp; ] : <code>[ &amp;nbsp; ]</code><p>
  <p>[ &emsp; ] : <code>[ &amp;emsp; ]</code><p>
  <p>[ &emsp; ] : <code>[ &amp;emsp; ]</code><p>
  <p>[ &lt; ] : <code>[ &amp;lt; ]</code><p>
  <p>[ &gt; ] : <code>[ &amp;gt; ]</code><p>
  <p>[ &quot; ] : <code>[ &amp;quot; ]</code><p>
  <p>[ &#124; ] : <code>[ &amp;#124; ]</code><p>
  <p>[ &#40; ] : <code>[ &amp;#40; ]</code><p>
  <p>[ &#41; ] : <code>[ &amp;#41; ]</code><p>
  <p>[ &#44; ] : <code>[ &amp;#44; ]</code><p>
  <p>[ &#45; ] : <code>[ &amp;#45; ]</code><p>
</div>

## 참고

- [Do it! HTML5+CSS3 웹 표준의 정석 <개정판>, 2017, 고경희](http://www.easyspub.co.kr/20_Menu/BookView/119/PUB)