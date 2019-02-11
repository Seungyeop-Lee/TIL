# HTML 전역 속성

- HTML문서에 포함 된 태그라면 공통적으로 가질 수 있는 속성에 대해 정리한다.

## `class`

- 태그에 한 개 이상의 클래스 이름을 설정한다.
- 각 클래스 이름은 공백으로 구분한다.
- 클래스 이름은 CSS적용시 사용되는 것이 일반적이다.

## `id`

- 태그에 아이디를 설정한다.
- 설정값은 그 문서에서 유일한 아이디 속성값이여야 한다.

```html
<style>
  .pTag{
    font-size: 24px;
    font-style: italic;
  }
  #name {
    color: blue;
  }
  #address {
    font-weight: bolder;
  }
</style>
<div>
  <p class="pTag" id="name">이승엽</p>
  <p class="pTag" id="address">도쿄</p>
</div>
```

[예제코드 실행 결과(codepen)](https://codepen.io/seungyeop-lee/pen/KJoGGO)

## `style`

- 태그에 inline 스타일을 정의한다.
- CSS속성을 값으로 정의하며, 두개 이상의 속성을 정의 할 경우 세미콜론(;)으로 구분짓는다.

```html
<div>
  <p style="font-size: 24px; font-style: italic; color: blue">이승엽</p>
  <p style="font-size: 24px; font-style: italic; font-weight: bolder">도쿄</p>
</div>
```

[예제코드 실행 결과(codepen)](https://codepen.io/seungyeop-lee/pen/exMPQp)

## `tabindex`

- 페이지에서 탭을 눌렀을 때 커서가 이동하는 순서를 표시한다.
- 1이 가장 먼저이며, 숫자가 낮을 수록 우선순위가 높다.
- 초기값은 0이며, 양의 정수들 보다 우선순위가 낮다.

```html
<div>
  <!--Tab 순서는 이승엽, 도쿄, 라멘 순-->
  <p tabindex="1">이승엽</p>
  <p tabindex="2">도쿄</p>
  <p tabindex="0">라멘</p>
</div>
```

[예제코드 실행 결과(codepen)](https://codepen.io/seungyeop-lee/pen/LqdgXL)

## `title`

- 태그의 제목을 설정한다.
- 제목으로 설정된 값은 그 태그에 mouse over를 했을 경우 툴팁으로 표시된다.

```html
<div>
  <p title="Lorem">Lorem ipsum dolor sit amet consectetur adipisicing elit. Ex delectus ab tenetur deserunt eius quas, culpa molestiae fuga animi rem, facilis quod nobis modi veniam doloribus maiores quae odit porro?</p>
</div>
```

[예제코드 실행 결과(codepen)](https://codepen.io/seungyeop-lee/pen/aXYRPB)

## 참고

- [w3schools.com > HTML Global Attributes](https://www.w3schools.com/tags/ref_standardattributes.asp)