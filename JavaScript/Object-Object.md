# Object object
- 빌트 인 객체로서 constructor이다.
- 객체에 대한 여러 메소드를 지원한다.

## 객체 생성 메소드 (`Object.create(prototype)`)
- `prototype`에 설정한 객체를 prototype으로서 가지고 있는 새로운 객체를 생성한다.

```javascript
var parent = Object.create(null);
var child = Object.create(parent);

console.log(Object.getPrototypeOf(child) == parent);  //true
```

## 프로토타입 관련 메소드

역할 | 구문 | 설명
----|------|------
반환 | `Object.getPrototypeOf(obj)` | `obj`에 설정된 객체의 prototype을 반환한다.
설정 | `Object.setPrototypeOf(obj, prototype)` | `obj`에 설정된 객체의 prototype을 `prototype`에 설정된 객체로 덮어쓴다.
존재확인 | `Object.prototype.isPrototypeOf(obj)` | 현재 객체가 `obj`에 설정된 객체에 prototype으로 존재하는지를 검사하여 반환한다. (상속관계 포함)

```javascript
var parent1 = new (function Parent1() { this.num = 1 })();
var parent2 = new (function Parent2() { this.num = 2 })();

var child = Object.create(parent1);
console.log(Object.getPrototypeOf(child).num);  //1

Object.setPrototypeOf(child, parent2);
console.log(Object.getPrototypeOf(child).num);  //2

console.log(parent1.isPrototypeOf(child)); //false
console.log(parent2.isPrototypeOf(child)); //true
```

## 속성 기술자 관련 메소드

구문 | 설명
----|------
`Object.defineProperty(obj, prop, descriptor)` | `obj`에 설정된 객체에 `prop`에 설정된 키와 `descriptor`에 설정된 속성 기술자를 가진 속성을 정의한다.
`Object.getOwnPropertyDescriptor(obj, prop)` | `obj`에 설정된 객체에 `prop`에 설정된 키를 가진 속성의 속성 기술자를 반환한다. 해당하는 속성이 없으면 `null`을 반환한다.

```javascript
var obj = {};

Object.defineProperty(obj, 'num', {
  value: 1,
  writable: true
});

var numPd = Object.getOwnPropertyDescriptor(obj, 'num');
console.log(numPd); //{value: 1, writable: true, enumerable: false, configurable: false}
```

## 속성 관련 메소드

구문 | 설명
----|------
`Object.prototype.hasOwnProperty(prop)` | `prop`에 설정된 키값을 가진 속성유무를 반환한다.
`Object.prototype.propertyIsEnumerable(prop)` | `prop`에 설정된 키값을 가진 `enumerable`값을 반환한다. 해당하는 속성이 없으면 `false`를 반환한다.

```javascript
var obj = { num: 1 };

console.log(obj.hasOwnProperty('num')); //true
console.log(obj.propertyIsEnumerable('num')); //true
```

## 객체 제한 관련 메소드

- *객체제한 설정 및 확인 메소드*

상태 | 상태 설정 메소드 | 상태 확인 메소드
----|-----------------|-----------------
동결 | `Object.frezze(obj)` | `Object.isFrozen(obj)`
봉인 | `Object.seal(obj)` | `Object.isSealed(obj)`
확장방지 | `Object.preventExtensions(obj)` | `Object.isExtensible(obj)`

- *객체 제한 비교*

상태 | 확장가능 | 속성 기술자의 `configurable` | 속성 기술자의 `writable`
----|----------|-----------------------------|------------------------
동결 | `false` | `false` | `false`
봉인 | `false` | `false` | `true`
확장방지 | `false` | `true` | `true`

```javascript
/*---동결 상태---*/
var obj1 = { num: 1 };

Object.freeze(obj1);
console.log(Object.isFrozen(obj1)); //true

//확장 방지
obj1.temp = 2;
console.log(obj1.temp); //undefined

//속성 삭제 및 유형변경 불가
delete obj1.num;
console.log(obj1.num);  //1

//속성 값 수정 불가
obj1.num = 10;
console.log(obj1.num);  //1


/*---봉인 상태---*/
var obj2 = { num: 1 };

Object.seal(obj2);
console.log(Object.isSealed(obj2)); //true

//확장 방지
obj2.temp = 2;
console.log(obj2.temp); //undefined

//속성 삭제 및 유형변경 불가
delete obj2.num;
console.log(obj2.num);  //1

//속성 값 수정 가능
obj2.num = 2;
console.log(obj2.num);  //2


/*---확장방지 상태---*/
var obj3 = { 
  num: 1, 
  str: 'a' 
};

Object.preventExtensions(obj3);
console.log(Object.isExtensible(obj3)); //false

//확장 방지
obj3.temp = 2;
console.log(obj3.temp); //undefined

//속성 삭제 및 유형변경 가능
delete obj3.num;
console.log(obj3.num);  //undefined

//속성 값 수정 가능
obj3.str = 'b';
console.log(obj3.str);  //b
```

## 객체 순회관련 메소드
- `Object.keys()`, `Object.getOwnPropertyNames()`
- Compare-With-Iteration-Method-For-Object.md 참고

## 참고
- [MDN web docs : 開発者向けのウェブ技術 > JavaScript > JavaScript リファレンス > 標準ビルトインオブジェクト > Object](https://developer.mozilla.org/ja/docs/Web/JavaScript/Reference/Global_Objects/Object)
- [Nerdworks Blogorama : preventExtensions, seal and freeze](https://blogorama.nerdworks.in/preventextensionssealandfreeze/)