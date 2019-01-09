# Closure
- 자신을 감싸고 있는 스코프(상위 스코프)에 있는 변수를 참조 할 수 있는 함수를 말한다.
- JavaScript의 함수는 전부 Closure다.

## 설명
- 일반적으로 지역변수는 스코프를 벗어났을 경우, 더 이상 접근 할 수 없다.
- 하지만 Closure는 자신이 사용한 상위 스코프의 지역변수를, 스코프를 벗어나도 참조 가능하다.
- Closure가 가지고 있는 상위 스코프의 변수 참조에 대한 정보는 [[Scopes]]에 저장되어 있다.
```javascript
function getCountFunc() {
  var insideCount = 0;
  return function() {
    return insideCount;
  }
}
var getCount = getCountFunc();

//반환된 함수가 insideCount 변수에 대한 참조를 가지고 있기 때문에 접근이 가능하다.
console.log(getCount());  //0
```

## 사용예
- 클로저를 이용 할 경우 Java에서의 private접근 제어자에 해당하는 변수와 함수를 JavaScript에서도 구현 가능하다.
```javascript
function Counter() {
//Counter안의 count와 changeCount는 스코프를 벗어나서 접근이 불가 하다.
  var count = 0;
  var changeCount = function (tempCount) {
    if(tempCount >= 0 && tempCount <= 3) {
      count = tempCount;
    }
  };

  this.increase = function() {
    changeCount(count+1);
  }
  this.decrease = function() {
    changeCount(count-1);
  }
  this.getCount = function() {
    return count;
  }
}

var counter = new Counter();
console.log(counter.getCount());  //0
counter.decrease();
console.log(counter.getCount());  //0
counter.increase();
counter.increase();
counter.increase();
console.log(counter.getCount());  //3
counter.increase();
console.log(counter.getCount());  //3
```

## Closure vs. Prototype
- Closure를 사용할 경우 여러 객체에서 공통으로 사용 될 코드도 계속 재생성 하기 때문에 Prototype에 비해 비효율적으로 보인다.
- 실제로 과거 브라우저에서는 Prototype에 추가하는 것이 Closure를 이용하는 것 보다 더 빨랐다.
- 최신의 브라우저에서는 성능의 차이가 거의 없다. (참조의 prototype vs closures에서 확인 가능)
- 하지만 Closure의 경우 메모리의 낭비가 있고, 오래된 브라우저의 대응을 위해서라도 Prototype을 사용 할 수 있다면 Prototype을 사용하는 것을 추천한다.

## 참조
- [MDN web docs : 開発者向けのウェブ技術 > JavaScript > クロージャ](https://developer.mozilla.org/ja/docs/Web/JavaScript/Closures)
- [Qiita : JavaScriptでクロージャ入門。関数はすべてクロージャ？](https://qiita.com/takeharu/items/4975031faf6f7baf077a)
- [jsperf.com : prototype vs closures](https://jsperf.com/prototype-vs-closures/20)