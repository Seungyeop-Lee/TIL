# Ajax
**A**synchoronous **Ja**vaScript + **X**ML의 약자로 웹 페이지 상에서 비동기적으로 서버와 통신하는 기술을 뜻한다.
<br>
<br>
- 일반적인 웹 페이지의 경우 웹 브라우저(클라이언트)가 서버에 request 신호를 보내고, 서버는 request 신호에 대한 처리 후 response로 웹 브라우저에 결과를 전달한다. 웹 브라우저는 response의 내용을 바탕으로 렌더링 작업을 거쳐 웹 페이지를 표시한다.
- 이 경우 동기적 통신이기 때문에 웹 브라우저는 서버의 응답을 기다리는동안 아무런 처리도 하지 못한다. 
- 또한 웹 페이지 갱신으로 인한 화면의 깜빡임이 발생하고, 변경이 필요없는 부분까지 전부 서버에서 다시 받아서 렌더링 해야하는 자원낭비도 있다.
<br>
<br>
- 이런 단점을 해결하기 위해 나온 기술이 Ajax이다.
- Ajax는 비동기적 통신 기술이기 때문에 서버의 응답을 기다리지 않고, 클라이언트에서 다른 처리를 수행하는 것이 가능하다.
- 또한 Ajax로 수신받은 response의 내용을 바탕으로 자바스크립트 및 DOM HTML을 이용하여 동적으로 웹 페이지를 갱신하는 것이 가능하다. 그러므로 갱신에 의한 깜빡임 발생이 없고, 변경이 필요한 부분의 데이터만 받아 변경이 가능하다.

![전통적인 웹 애플리케이션 모델과 Ajax를 사용한 애플리케이션의 비교](https://upload.wikimedia.org/wikipedia/commons/0/0b/Ajax-vergleich-en.svg)

**Fig1. 전통적인 웹 애플리케이션 모델과 Ajax를 사용한 애플리케이션의 비교 (출처:DanielSHaischt, via Wikimedia Commons [CC BY-SA 3.0 (https://creativecommons.org/licenses/by-sa/3.0)], via Wikimedia Commons)**

- Ajax의 약자에도 나타나 있듯이 데이터 전송은 XML을 사용하는 것으로 보이나, 실제로는 JSON형태가 가장 많이 사용된다. 그 이외에 HTML, 텍스트 파일을 비롯하여 모든 데이터 형식의 전송이 가능하다.

## 참고
- [ウィキペディア（Wikipedia）: Ajax](https://ja.wikipedia.org/wiki/Ajax)