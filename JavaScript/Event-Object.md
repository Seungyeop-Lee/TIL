# Event Object
- 이벤트 타겟에 이벤트 핸들러로 등록된 메소드가 실행 될 경우, 매개변수로 이벤트 객체가 자동으로 설정된다.
- 이벤트 객체는 일어난 이벤트에 대한 정보 및 이벤트 제어 관련 메소드를 제공한다.  
  또한 새로운 이벤트 객체를 만들어 이벤트 강제 발생에 이용할 수 있다.

## 이벤트 정보 관련

### `Event.target`
- 실제 이벤트가 일어난 이벤트 타겟을 참조한다.

### `Event.currentTarget`
- 현재 실행되고있는 이벤트 핸들러가 등록된 이벤트 타겟을 참조한다.

### `Event.type`
- 발생한 이벤트 종류를 문자열로 저장하고 있다.

### `Event.cancelable`
- 실행되고 있는 이벤트의 디폴트 이벤트 핸들러의 취소가능 여부를 `boolean`값으로 저장하고 있다.

```html
<!-- 예제코드 작성 -->
```

## 이벤트 제어 관련

### `Event.preventDefault()`
- `Event.target`의 디폴트 이벤트 핸들러의 실행을 억제한다.
- `Event.cancelable`이 `false`일 경우 해당 메소드를 실행해도 억제되지 않는다.

### `Event.stopImmediatePropagation()`
- `Event.target`에 등록되어 있는 다른 이벤트 핸들러의 실행을 억제한다.
- 디폴트 이젠트 핸들러의 실행은 억제하지 않는다.

```html
<!-- 예제코드 작성 -->
```

## 이벤트 전달 관련

### `Event.eventPhase`
- 이벤트 핸들러가 실행 될 때의 이벤트 상태에 해당하는 숫자를 반환한다.

상수 | 값 | 상태
----|----|------
`Event.NONE` | 0 | 이벤트가 일어나지 않음
`Event.CAPTURING_PHASE` | 1 | 캡처링 중
`Event.AT_TARGET` | 2 | 실제 이벤트가 발생한 이벤트 타겟에서 실행 중
`Event.BUBBLING_PHASE` | 3 | 버블링 중

```html
<!-- 예제코드 작성 -->
```

### `Event.stopPropagation()`
- 이벤트 전달을 중단한다.

```html
<!-- 예제코드 작성 -->
```

## 이벤트 강제 발생
- 강제 발생시킬 이벤트의 정보를 담은 `Event`객체 생성 후 `EventTarget.dispatchEvent()`메소드를 이용해 이벤트를 발생시킨다.

### `Event` 객체 생성

구문 | `new Event(typeArg [, eventInit])`
----|---------------------------------
`typeArg` | 발생 시킬 이벤트의 종류를 가리키는 문자열
`eventInit` | 이벤트 객체의 초기화 조건 정보를 가진 객체
`eventInit.bubbles` | 이벤트 버블링 유무를 설정(`true`이면 이벤트 버블링, `false`이면 이벤트 캡쳐링), 초기값은 `false`
`eventInit.cancelable` | 이벤트 취소 가능유무 설정, 초기값은 `false`
반환값 | 이벤트의 정보를 담은 `Event`객체

### `EventTarget.dispatchEvent(event)`

구문 | `target.dispatchEvent(event)`
----|------------------------------
`target` | 이벤트를 발생시킬 이벤트 타겟
`event` | 발생 시킬 이벤트의 정보를 담은 `Event`객체
반환값 | 이벤트 발생 후 등록되 있던 이벤트 핸들러 실행 시, `Event.preventDefault()`가 실행되었을 경우 `false`, 그렇지 않으면 `true`를 반환

```html
<!-- 예제코드 작성 -->
```

## 참고
- [MDN web docs : 開発者向けのウェブ技術 > Web API > Event](https://developer.mozilla.org/ja/docs/Web/API/Event)
- [MDN web docs : 開発者向けのウェブ技術 > Web API > EventTarget > EventTarget.dispatchEvent()](https://developer.mozilla.org/ja/docs/Web/API/EventTarget/dispatchEvent)