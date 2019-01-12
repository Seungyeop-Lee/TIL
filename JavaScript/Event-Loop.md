# Event Loop(이벤트 루프)
- JavaScript는 싱글 스레드로 움직이므로 병렬처리는 불가능하다.
- Event Loop와 Queue를 이용하면 비동기 처리를 통한 병행처리가 가능하다. (Event Loop와 Queue는 브라우저가 제공한다.)

## JavaScript Runtime
- 런타임 메모리 공간은 스택(Stack), 힙(Heap), 큐(Queue)로 이루어져 있다.

![JavaScript Runtime 구성 요소 그림](https://developer.mozilla.org/files/4617/default.svg)

## 스택
- 콜 스택(Call Stack)으로도 불린다.
- 실행 시 함수의 내용이 호출 순서대로 쌓이는 메모리 영역을 뜻한다.
- 함수 내에서 새롭게 호출 된 함수는 현재 스택의 상위에 push되고, 함수의 처리가 끝날 경우 pop된다.

## 힙
- 객체를 저장하기 위해 할당된 메모리 영역을 뜻한다.

## 큐
- 메시지 큐(Message Queue) 또는 콜백 큐(Callback Queue)라고도 불린다.
- 처리되는 메시지의 리스트를 큐 자료형으로 저장 한 메모리 영역을 뜻한다.

## Event Loop의 역할
- 스택이 비어있을 경우 큐에 메시지가 있는지 확인하고, 있으면 스택에 이동시키는 역할을 한다.


## 자바스크립트의 코드실행 흐름
1. 코드를 한 줄, 한 줄 읽어들여 함수단위로 스택에 쌓고 실행한다.
2. 코드 중 콜백함수(web api등)을 사용하는 구문을 만나면, 콜백함수를 큐에 메시지로서 저장한다.
3. 코드의 실행이 끝나 스택이 비게 된다.
4. 이벤트 루프가 큐를 확인하고, 큐에 메시지가 있는 경우 메시지에 해당하는 함수를 스택으로 이동시킨다. 메시지가 없는 경우 종료한다.
5. 스택에 함수가 생겼으므로 실행한다.
6. 실행이 끝나고 스택이 비게된다.
7. 4~6을 반복한다.

![Javascript Event Loop Visual Representation](https://cdn-images-1.medium.com/max/1000/1*-MMBHKy_ZxCrouecRqvsBg.png)
- 가시적으로 확인 가능한 사이트가 있다.
- http://latentflip.com/loupe 에서 코드를 실행 해보는 것을 추천한다.

## 참고
- [MDN web docs : 開発者向けのウェブ技術 > JavaScript > 並列モデルとイベントループ](https://developer.mozilla.org/ja/docs/Web/JavaScript/EventLoop)
- [Qiita : JavaScriptの同期、非同期、コールバック、プロミス辺りを整理してみる](https://qiita.com/YoshikiNakamura/items/732ded26c85a7f771a27)
- [Understanding Javascript Function Executions — Call Stack, Event Loop , Tasks & more](https://medium.com/@gaurav.pandvia/understanding-javascript-function-executions-tasks-event-loop-call-stack-more-part-1-5683dea1f5ec)