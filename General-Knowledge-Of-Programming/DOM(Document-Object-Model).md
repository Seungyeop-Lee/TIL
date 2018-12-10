# DOM (Document Object Model)
- HTML이나 XML문서를 파싱한 후 브라우저가 이해할 수 있는 모델로 바꾼 것
- 전체 구조가 노드(Node)로 표현되며 각각의 노드는 객체로 구성되어 있다.

## DOM Tree
- 문서(Document) 노드, 요소(Element) 노드, 속성(Attribute) 노드, 텍스트(Text) 노드로 이루어져 있다.
- 문서 노드 (Document Node)
  - 트리의 최상위에 존재한다.
  - 다른 노드에 접근하기 위해 꼭 통해야 한다.
  - JavaScript에서는 `document`로 이용가능하다.
- 요소 노드 (Element Node)
  - HTML 태그 요소를 표현한다.
  - 속성 노드와 텍스트 노드에 접근하기 위해 꼭 통해야 한다.
  - JavaScript에서는 `HTMLElement` 객체를 상속한 객체로 구성되어 있다.
- 속성 노드 (Attribute Node)
  - HTML 태그 내의 속성을 표현한다.
  - 요소 노드의 구성체로서 존재한다.
- 텍스트 노드 (Text Node)
  - HTML의 텍스트를 표현한다.
  - 자식노드를 가질 수 없는다. (트리의 최하위 노드)

![DOM Tree](https://upload.wikimedia.org/wikipedia/commons/5/5a/DOM-model.svg)

**Fig1. DOM Tree (출처:Birger Eriksson [<a href="https://creativecommons.org/licenses/by-sa/3.0">CC BY-SA 3.0</a>], <a href="https://commons.wikimedia.org/wiki/File:DOM-model.svg">from Wikimedia Commons</a>)**
## 참고
- [ウィキペディア（Wikipedia）: Document Object Model](https://ja.wikipedia.org/wiki/Document_Object_Model)
- [PoiemaWeb : 문서 객체 모델(Document Object Model)](https://poiemaweb.com/js-dom)