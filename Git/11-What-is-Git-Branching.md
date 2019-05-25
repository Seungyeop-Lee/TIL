# 브랜치란 무엇인가

- 코드를 통째로 복사하여, 원래 코드와 상관없이 독립적으로 개발을 진행 할 수 있게 해주는 것을 뜻한다.

## Git에서 데이터를 저장하는 방법

1. 변경이 생긴 파일을 Staging시킬 경우
   1. Staging된 파일을 blob 객체로서 Git 저장소에 저장
   1. Staging Area에 해당 blob 객체의 체크섬을 저장
1. Staging된 파일을 commit하는 경우
   1. Staging Area가 tree 객체로 생성 (tree 객체에는 blob객체가 저장되어 있음)
   1. commit객체가 만들어지고, 작성자, 커미터, 메세지 등이 저장
   1. 만들어진 commit객체에 해당 tree 객체의 체크섬을 저장
1. 이전 commit이 있을 경우
   1. 해당 commit에 이전커밋의 체크섬을 저장

![commit과 트리 데이터](https://git-scm.com/book/en/v2/images/commit-and-tree.png)

> commit과 트리 데이터

![commit과 이전 commit](https://git-scm.com/book/en/v2/images/commits-and-parents.png)

> commit과 이전 commit

## Git 브랜치

- Git은 다른 VCS와 달리 빠르며, 쉽게 사용 가능하다.
- Git에서는 브랜치를 사용하여 작업 후, Merge하는 방법을 권장한다.
- 브랜치는 커밋 사이를 이동할 수 있는 포인터 같은 것이다.
  - 브랜치의 시작 commit정보와 현재의 commit정보를 가지고 있다.
- master브랜치는 `git init`명령으로 초기화 할 때 자동으로 만들어지는 브랜치이며, 모든 commit은 commit이 생성되는 시점에 어떠한 브랜치가 그 commit을 가리키게 되어있다.

## HEAD

- Git에는 HEAD라는 특수한 포인터가 있다.
- 이 포인터는 현재의 브랜치를 가리키며, 다른 브랜치로 이동하는 것이 가능하다.

![브랜치와 commit history](https://git-scm.com/book/en/v2/images/branch-and-history.png)

> 브랜치와 commit history

## 브랜치와 관련된 명령어

### `git branch`

- 브랜치를 만들 때 사용하는 명령어이다.
  - `git branch <branch-name>`으로 사용가능
- 브랜치 작성 후 HEAD가 작성된 브랜치로 이동하지는 않는다.

```bash
$ git branch develop
```

### `git checkout`

- HEAD가 가리키는 브랜치를 이동 할 때 사용하는 명령어이다.
  - `git checkout <branch>`으로 사용가능

```bash
$ git checkout develop
```

### 현재 HEAD확인

- `git status`나 `git log`명령어를 사용하면 현재 HEAD의 확인이 가능하다.
- `git log --oneline --decorate --graph --all`명령을 이용하면 현재 HEAD뿐 아니라 다른 브랜치나 브랜치의 갈라짐 정보등을 한눈에 알아볼 수 있다.

## 참고

- [Pro Git 2nd Edition > 3.1 Git 브랜치 - 브랜치란 무엇인가](https://git-scm.com/book/ko/v2/Git-%EB%B8%8C%EB%9E%9C%EC%B9%98-%EB%B8%8C%EB%9E%9C%EC%B9%98%EB%9E%80-%EB%AC%B4%EC%97%87%EC%9D%B8%EA%B0%80)
