# Git 저장소 만들기

- Git 저장소를 얻는 방법은 두 가지이다.
  1. 디렉토리를 지정하여, Git 저장소를 작성하는 방법
  2. 다른 어딘가의 Git 저장소를 Clone하는 방법

## 기존 디렉토리를 Git 저장소로 만들기

- Git 저장소로 작성할 디렉토리로 이동 한 후 이하의 명령어를 실행한다.

```bash
$ git init
```

- 해당 명령어가 실행된 폴더와 그 하위폴더는 전부 Git 저장소로서 다루어 진다.

## 기존 저장소를 Clone하기

- 다른 저장소를 Clone하여 저장 할 디렉토리로 이동 한 후 이하의 명령어를 실행한다.

```bash
$ git clone <url> [<dir>]
```

- `url`에 저장소의 주소를 적으면 url의 가장 오른쪽의 `/`뒤의 이름을 디렉토리명으로 한 디렉토리에 저장소가 복제된다.
- 저장소의 디렉토리 명을 변경하고 싶으면 `<dir>`자리에 디렉토리 명을 지정해주면 된다.
- 실제로는 clone 명령어를 실행시키면, 다른 저장소를 복제하여 로컬에 저장 후 가장 최근 버전을 checkout시켜서 working directory로 복제시킨다.

## 참고

- [Pro Git 2nd Edition > 2.1 Git의 기초 - Git 저장소 만들기](https://git-scm.com/book/ko/v2/Git%EC%9D%98-%EA%B8%B0%EC%B4%88-Git-%EC%A0%80%EC%9E%A5%EC%86%8C-%EB%A7%8C%EB%93%A4%EA%B8%B0)
