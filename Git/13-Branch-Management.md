# 브랜치 관리

## `git branch`

- `git branch`명령어로 브랜치와 관련된 정보를 얻거나 브랜치의 삭제 등이 가능하다.

### 옵션 없음

- 현재 저장소의 브랜치 목록을 보여준다.

```bash
$ git branch
```

- 목록 중 `*`가 이름 왼쪽에 붙어있는 브랜치가 현재 브랜치(HEAD)이다.

### `-v`옵션

- 현재 저장소의 브랜치 목록과 각 브랜치의 현재 commit 메세지를 보여준다.

```bash
$ git branch -v
```

### `--merged`옵션

- 현재 브랜치를 기준으로 Merge가 된 브랜치의 목록을 보여준다.

```bash
$ git branch --merged
```

- 특정 브랜치를 기준으로 Merge가 된 브랜치의 목록을 보고 싶으면 특정 브랜치의 이름을 붙여준다.
  - `git branch --merged <branch-name>`형태로 사용

```bash
$ git branch --merged master
```

- `*`가 붙어있는 브랜치 이외의 브랜치는 Merge가 되었기 때문에 삭제해도 된다.

### `--no-merged`옵션

- 현재 브랜치를 기준으로 Merge되지 않은 브랜치의 목록을 보여준다.

```bash
$ git branch --no-merged
```

- 특정 브랜치를 기준으로 Merge되지 않은 브랜치의 목록을 보고 싶으면 특정 브랜치의 이름을 붙여준다.
  - `git branch --no-merged <branch-name>`형태로 사용

```bash
$ git branch --no-merged master
```

### `-D`옵션

- Merge되지 않은 브랜치를 삭제 할 때 사용된다.
  - `git branch -D <branch-name>`형태로 사용

```bash
$ git branch -D develop
```

## 참고

- [Pro Git 2nd Edition > Git 브랜치 - 브랜치 관리](https://git-scm.com/book/ko/v2/Git-%EB%B8%8C%EB%9E%9C%EC%B9%98-%EB%B8%8C%EB%9E%9C%EC%B9%98-%EA%B4%80%EB%A6%AC)
