# 객체 탐색방법 비교(for-in, Object.keys(), Object.getOwnPropertyNames())
탐색방법 | enumerable | prototype
------ | ----------- | ---------
for-in | true인 요소만 | 검색됨
Object.keys() | true인 요소만 | 검색 안됨
Object.getOwnPropertyNames() | true, false 모두 | 검색 안됨

```JavaScript
function objTemplate() {}

//prototype에 속성 설정
Object.defineProperties(objTemplate.prototype, {
  'enumT_proto': {
    value: "enumT_proto",
    enumerable: true
  },
  'enumF_proto': {
    value: "enumF_proto",
    enumerable: false
  }
});

var obj = new objTemplate();

//obj객체에 속성 설정
Object.defineProperties(obj, {
  'enumT': {
    value: "enumT",
    enumerable: true
  },
  'enumF': {
    value: "enumF",
    enumerable: false
  }
});

var resultArray = [];

//for-in 탐색
for(key in obj) {
  resultArray.push(key);
}
console.log(resultArray); //["enumT", "enumT_proto"]

//Object.keys() 탐색
resultArray = Object.keys(obj);
console.log(resultArray); //["enumT"]

//Object.getOwnPropertyNames() 탐색
resultArray = Object.getOwnPropertyNames(obj);
console.log(resultArray); //["enumT", "enumF"]
```

## 참고
- [stackoverflow : Object.getOwnPropertyNames vs Object.keys](https://stackoverflow.com/questions/22658488/object-getownpropertynames-vs-object-keys)
- 직접 실험 (Chrome 개발자 모드)