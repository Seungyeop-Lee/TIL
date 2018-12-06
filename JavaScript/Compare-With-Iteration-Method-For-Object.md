# 객체 탐색방법 비교(for-in, Object.keys(), Object.getOwnPropertyNames())
탐색방법 | enumerable | prototype
------ | ----------- | ---------
for-in | true인 요소만 | 검색됨
Object.keys() | true인 요소만 | 검색 안됨
Object.getOwnPropertyNames() | true, false 모두 | 검색 안됨

```JavaScript
//TODO 예제코드 작성
```

## 참고
- [stackoverflow : Object.getOwnPropertyNames vs Object.keys](https://stackoverflow.com/questions/22658488/object-getownpropertynames-vs-object-keys)
- 직접 실험 (Chrome 개발자 모드)