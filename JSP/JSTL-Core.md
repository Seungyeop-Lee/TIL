# JSTL core

- JSTL에서 기본적인 기능들을 구현해 놓은 라이브러리이다.

| 종류              | 태그                                                 |
| ----------------- | ---------------------------------------------------- |
| 문자열 출력       | `<c:out>`                                            |
| 변수 설정 및 삭제 | `<c:set>`, `<c:remove>`                              |
| 예외 처리         | `<c:catch>`                                          |
| 조건문            | `<c:if>`, `<c:choose>`, `<c:when>`, `<c:otherwise>`  |
| 반복문            | `<c:forEach>`, `<c:forTokens>`                       |
| 페이지 처리       | `<c:import>`, `<c:redirect>`, `<c:url>`, `<c:param>` |

## JSTL core 사용준비

- JSTL core를 사용하기 위해 JSP에 태그 라이브러리로 등록한다.

```jsp
<%-- JSP에 태그 라이브러리로 등록하기 위한 taglib지시어 --%>
<%@ taglib prefix="c" uri="http://java.sun.com/jsp/jstl/core" %>
```

- `prefix="c"`는 태그에 c를 사용함으로서 `uri`에 정의되어 있는 커스텀 태그로서 역할을 한다라는 의미를 나타낸다.
- JSTL의 prefix가 c로 사용되는 것은 암묵적인 약속이므로 따르는게 좋다.

## 문자열 출력

```jsp
<%-- 지정된 값을 출력하는 태그 --%>

<c:out value="출력값" default="기본값" escapeXml="true 또는 false" />
<%-- value에 설정된 값이 출력되며, value의 값이 null일 경우 default의 값이 출력된다. --%>
<%-- escapeXml은 기본값은 false이며 true를 설정할 경우 
xml형식과 관련한 특수 문자를 변경하여 출력된다. --%>
```

- escapeXml이 true일 경우 특수 문자 변경

| 문자 | 변경 후 |
| ---- | ------- |
| `<`  | `&lt;`  |
| `>`  | `&gt;`  |
| `&`  | `&amp;` |
| `'`  | `&#039` |
| `"`  | `&#034` |

## 변수 설정 및 삭제

```jsp
<%-- 변수나 객체의 프로퍼티로 값을 설정하는 태그 --%>

<c:set var="변수명" value="설정값" [scope="범위"] />
<%-- var값을 변수명으로 하고, value값을 가진 변수를 설정한다. --%>

<c:set target="객체" property="값" value="설정값" [scope="범위"] />
<%-- target객체에 property값을 키로 value값을 값으로 가진 프로퍼티를 설정한다. --%>

<%-- 생성된 변수는 EL을 통해 사용가능하다. --%>
<%-- scope는 변수의 유효 범위를 나타내며, 
`application`, `session`, `request`, `page`가 올 수 있다. 
생략 할 경우 `page`로 설정 --%>


<%-- 설정된 변수를 제거하는 태그 --%>

<c:remove var="변수명" [scope="범위"] />
<%-- scope범위에 속한 var값을 변수명으로 하는 변수를 삭제한다. --%>
<%-- scope범위를 생략 할 경우, 
모든 scope에서 var값을 변수명으로 하는 변수는 전부 삭제된다. --%>
```

## 예외 처리

```jsp
<%-- 발생된 예외를 변수에 저장하는 태그 --%>

<c:catch var="변수명">
  예외 발생 가능성이 있는 구문
</c:catch>
<%-- catch태그로 쌓여있는 부분에서 예외가 발생하였을 경우,
var값을 변수명으로 하는 변수에 예외내용이 설정된다. --%>
<%-- EL문을 통해 발생한 예외의 내용의 확인이 가능하다 --%>
```

## 조건문

```jsp
<%-- 조건에 따라 내용을 반영하는 태그 --%>

<c:if test="조건식" var="변수명" [scope="범위"]>
  내용
</c:if>
<%-- test조건식이 true이면 내용이 반영되고, false이면 반영되지 않는다. --%>
<%-- test조건식의 결과는 var값을 이름으로 갖는 변수에 저장되며, 
scope는 변수의 유효범위를 나타낸다. --%>

<c:choose>
  <c:when test="조건식"> 내용1 </c:when>
  <c:otherwise> 내용2 </c:otherwise>
</c:choose>
<%-- test조건식이 true이면 내용1이, false이면 내용2가 반영된다. --%>
<%-- when태그는 2개 이상도 가능하며, 
모든 when태그의 조건식 결과가 false일 경우 otherwise태그의 내용이 반영된다. --%>
```

## 반복문

```jsp
<%-- 조건에 따라 반복적으로 동작하는 태그 --%>

<%-- 정해진 수 만큼의 반복 --%>
<c:forEach var="변수명" begin="시작 인덱스" end="끝 인덱스" [step="증감식"] [varStatus="상태변수"]></c:forEach>

<%-- 배열 반복 --%>
<c:forEach var="변수명" items="객체명" [begin="시작 인덱스" end="끝 인덱스"] [step="증감식"] [varStatus="상태변수"]></c:forEach>

<%-- Map객체 반복 --%>
<c:forEach var="변수명" items="객체명" [varStatus="상태변수"]></c:forEach>

<%-- var값은 반복 중일 때 현재 반복하고 있는 값이다. --%>
<%-- (items가 없을 경우 반복 중인 현재의 인덱스, items가 있을 경우 반복 중인 객체의 값) --%>
<%-- step은 생략 할 경우 1로 설정된다. --%>
<%-- items가 있을 경우 begin과 end를 생략하면 전체 인덱스가 반복의 대상이 된다. --%>
<%-- varStatus는 반복의 상태를 갖는 객체이다. 
(속성값은 index, count, begin, end, step, first, last, current) --%>


<%-- 문자열을 배열로 만들어 반복하는 태그 --%>
<c:forTokens items="문자열" delims="구분자" var="변수명" [varStatus="상태변수"]></c:forTokens>
<%-- items에 설정된 문자열을 delims로 나누어 배열을 만든 후, 배열의 크기만큼 반복한다. --%>
<%-- var값은 반복 중일 때 현재 반복하고 있는 인덱스에 저장되어 배열 값이다. --%>
```

## 페이지 처리

```jsp
<%-- 페이지 관련 --%>

<c:import url="URL" var="변수명" scope="범위" charEncoding="인코딩값">
  [<c:param name="파라미터명" value="값">]
</c:import>
<%-- var값을 변수명으로 하는 변수에 url값에서 읽어들인 데이터를 설정한다. --%>
<%-- 읽어들인 데이터는 charEncoding에 설정한 인코딩값으로 인코딩하며, 
생략 할 경우 ISO-8859-1로 인코딩한다. --%>
<%-- var를 생략 할 경우 태그위치에 url에서 읽어들인 데이터 결과를 출력한다. --%>
<%-- param태그를 이용하여 url에 전송 할 파라미터를 설정 할 수 있다. --%>

<c:url var="변수명" scope="범위" value="URL">
  [<c:param name="파라미터명" value="값">]
</c:url>
<%-- value값의 url을 var값을 변수명으로 하는 변수에 설정한다. --%>
<%-- var를 생략하면 현재 위치에 value값의 url을 출력한다. --%>
<%-- value로 지정한 url은 상대경로, 절대경로 모두 사용 가능하다. 
(상대경로 사용 시, Context Root경로가 자동으로 삽입--%>
<%-- param태그를 이용하여 url에 전송 할 파라미터를 설정 할 수 있다. --%>

<c:redirect url="URL">
  [<c:param name="파라미터명" value="값">]
</c:redirect>
<%-- url값에 해당하는 페이지로 리다이렉트 시킨다. --%>
<%-- redirect태그 이후에 기술된 태그는 실행되지 않는다. --%>
<%-- param태그를 이용하여 url에 전송 할 파라미터를 설정 할 수 있다. --%>
```

## 참고

- [JSP 2.3 & Servlet 3.1(입문부터 모델 2 MVC 패턴까지)](http://www.hyejiwon.co.kr/?module=Goods&action=SiteGoods&sMode=VIEW_FORM&sCurrSortCd=001004&iGoodsCd=357&CurrentPage=1&sSearchField=all&sSearchValue=servlet&sort=)
- [JSP JSTL(JSP Standard Tag Library) - 코어 태그(core)](https://gangzzang.tistory.com/entry/JSP-JSTLJSP-Standard-Tag-Library-%EC%BD%94%EC%96%B4-%ED%83%9C%EA%B7%B8)