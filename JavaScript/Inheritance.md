# 상속(Inheritance)
- 자바스크립트에서 ES5까지는 정해진 상속 방법이 없다.
- 가장 문제가 적다고 알려진 방법 중 개인 적으로 마음에 드는 방법은 아래와 같다.

## 생성자 함수의 상속
```javascript
function Human(name) {
  this.name = name;
}
Human.prototype.getName = function() {
  return this.name;
}

function Student(name, age) {
  Human.call(this, name);
  this.age = age;
}

//IE11 까지 지원
Object.setPrototypeOf(Student.prototype, Human.prototype);

//IE9 까지 지원
// Student.prototype = Object.create(Human.prototype);
// Object.defineProperty(Student.prototype, 'constructor', {
//   value : Student
// });

var student = new Student();
console.log(student instanceof Student);  //true
console.log(student instanceof Human);  //true
```

## 객체 리터럴의 상속
```javascript
var parentObj = {
  var1 : 10,
  var2 : 20
}

var childObj = Object.create(parentObj);
childObj.var3 = 30;

var keys = [];

for(key in childObj) {
  keys.push(key);
}
console.log(keys);  //["var3", "var1", "var2"]
```


## 참고
- [POSTD : JavaScriptにおける継承のパターン4種類の概要と対比](https://postd.cc/javascript-inheritance-patterns/)
- [zerocho blog : JavaScript > 객체 상속](https://www.zerocho.com/category/JavaScript/post/573d812680f0b9102dc370b7)
- [PoiemaWeb : JavaScript > 자바스크립트 객체지향 프로그래밍](https://poiemaweb.com/js-object-oriented-programming)