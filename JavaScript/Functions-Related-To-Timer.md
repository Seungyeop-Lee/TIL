# 타이머 관련 함수

- 타이머 관련 함수에 대해 정리한다.

## 타이머 관련 함수의 특징

- 지정한 시간이 흐른 후, 지정한 함수를 실행시키는 역할을 한다.
- 타이머 관련 함수가 실행되면 바로 타이머가 작동한다.
- 지정된 시간에 도달하면 지정한 함수는 큐에 등록되어 자바스트립트의 실행이 끝날 때 까지 기다린다.
- 자바스크립트의 실행이 끝나면 큐에 등록된 함수가 순차적으로 실행된다.
- **지정한 시간 후 큐에 등록되는 것이지, 지정한 시간 후 바로 실행되는 것이 아님을 주의!**

## `setTimeout()`

- 지정한 시간이 흐른 후, 지정한 함수를 한번 실행한다.

구문 | `window.setTimeout(function[, delay[, param1[, param2[, ...]]]]);`
----|-------------------------------------------------------------------
`function` | 타이머 만료 후 실행 될 함수
`delay` | 실행을 기다릴 타이머 시간. 단위는 밀리초. 초기값은 0
`param` | `function`이 실행 될 때 인수로 설정 할 값
반환값 | timeoutID. `clearTimeout()`으로 타이머를 취소 할 때 사용

```javascript
```

## `setInterval()`

- 지정한 시간 간격으로, 지정한 함수를 반복적으로 실행한다.

구문 | `window.setInterval(func, delay[, param1[, param2[, ...]]]);`
----|--------------------------------------------------------------
`function` | `delay`의 시간 간격마다 실행 될 함수
`delay` | 실행 간격. 단위는 밀리초
`param` | `function`이 실행 될 때 인수로 설정 할 값
반환값 | intervalID. `clearInterval()`으로 타이머를 취소 할 때 사용

```javascript
```

## `clearTimeout()`, `clearInterval()`

- 각각 `setTimeout()`이나 `setInterval()`로 인해 등록 된 타이머를 취소시킨다.

구문 | `window.clearTimeout(timeoutID)`
----|-------------------------------
`timeoutID` | 타이머를 취소 시킬 timeoutID

구문 | `window.clearInterval(intervalID)`
----|-------------------------------
`intervalID` | 타이머를 취소 시킬 intervalID

```javascript
```

## 참고

- https://developer.mozilla.org/ja/docs/Web/API/WindowTimers/setTimeout
- https://developer.mozilla.org/ja/docs/Web/API/Window/setInterval
- https://developer.mozilla.org/ja/docs/Web/API/WindowTimers/clearTimeout
- https://developer.mozilla.org/ja/docs/Web/API/WindowTimers/clearInterval