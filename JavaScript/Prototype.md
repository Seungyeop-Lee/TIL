# 프로토타입 (Prototype)
- 모든 자바 스크립트 객체들은 프로토타입으로부터 속성과 메소드를 상속받는다. 예를 들어, `Array`객체는 `Array.prototype`으로부터 상속받으며, `Element`객체는 `Element.prototype`으로부터 상속받는다.
- `Object.prototype`은 모든 프로토타입 상속 체인의 최상위에 위치하고 있다. 그렇기 때문에 `Array`객체나 `Element`객체 전부 `Object.prototype`으로부터 속성과 메소드를 상속받는다.

```javascript
//TODO 예제코드 작성
```

- 상속받은 프로토타입은 객체의 `__proto__`로 접근 가능하며, `__proto__`는 `null`(부모객체가 존재하지 않을 경우)이거나 프로토타입 객체가 저장되어 있다.
- 객체의 `__proto__`에 접근 할 경우 내부적으로는 `Object.getPrototypeOf()`가 호출되어 프로토타입 객체가 반환된다.

```javascript
//TODO 예제코드 작성
```

- `prototype` 속성은 함수 객체에만 존재한다.
- `prototype` 속성의 내용을 수정 할 경우 프로토타입을 상속받은 모든 객체가 즉시 영향을 받는다.

```javascript
//TODO 예제코드 작성
```

- `prototype` 속성의 값 자체를 다른 객체로 변경이 가능하다.
- `prototype` 변경 시 변경 이전에 생성된 객체는 기존의 `prototype`을, 변경 이후에 생성된 객체는 변경된 `prototype`을 상속 받는다.

```javascript
//TODO 예제코드 작성
```

- 프로토타입 객체에 constructor 속성은 상속받은 부모 객체를 가리킨다. (참조한다.)

```javascript
//TODO 예제코드 작성
```

- 객체가 가지고있는 속성과 상속받은 프로토타입이 가지고 있는 속성의 키 값이 동일한 경우, 객체가 가지고 있는 속성의 값을 우선시한다.
- 즉, 객체에 접근하려는 기 값이 존재하지 않을 경우에 한하여 프로토타입을 검사한다.

```javascript
//TODO 예제코드 작성
```

- 내장 객체의 프로토타입은 새로운 자바스크립트 기능과 호환성을 갖기 위한 이유 (ex. polyfill)가 아닌 이상 절대 수정하여서는 안된다.

## 참고
- [w3schools.com : JavaScript Object Prototypes](https://www.w3schools.com/js/js_object_prototypes.asp)
- [PoiemaWeb : JavaScript > 프로토타입](https://poiemaweb.com/js-prototype)
- [MDN web docs : Web technology for developers > JavaScript > Inheritance and the prototype chain](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Inheritance_and_the_prototype_chain)