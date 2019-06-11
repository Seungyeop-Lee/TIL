# 리모트 브랜치

- 리모트 저장소에 존재하는 브랜치를 리모트 브랜치라고 한다.

## 리모트 Refs

- 리모트 Refs를 조회하는 것으로 리모트 브랜치의 정보를 확인하는 것이 가능하다.
  - 리모트 Refs란 리모트 저장소에 있는 포인터의 참조
  - 브랜치, 태그 등을 가리키고있다.
- 보통은 리모트 Refs대신 리모트 트래킹 브랜치를 사용한다.

### 리모트 Refs 확인 방법

- `git ls-remote <remote>` 명령어를 이용하면 모든 리모트 Refs의 조회가 가능하다.

```bash
$ git ls-remote origin
```

- `git remote show <remote>` 명령어를 이용하면 모든 리모트 브랜치와 그 정보의 조회가 가능하다.

```bash
$ git remote show origin
```

## 리모트 트래킹 브랜치

- 리모트 브랜치를 추적하는 로컬 브랜치를 의미한다.
- 로컬에서 임의로 수정하는 것이 불가하며, 리모트 브랜치의 업데이트 내용에 따라 자동 갱신된다.
- 이름은 `<remote>/<branch>`형식으로 되어있다.
  - `<remote>`: 리모트 저장소의 이름
  - `<branch>`: 해당 리모트 저장소에 존재하는 트래킹 중인 브랜치의 이름

### 리모트 저장소와 리모트 트래킹 브랜치

- 리모트 트래킹 브랜치는 리모트 저장소를 clone 할 경우 자동으로 생성된다.
  - 리모트 트래킹 브랜치의 이름은 일반적으로 `origin/master`
- 로컬 저장소에 리모트 저장소를 연결 시키고 싶으면 `git remote add <remote-name> <url>`명령어를 사용하면 된다.

```bash
$ git remote add origin http://xxxxxxx.xxx/xxxxxxxx
```

### 리모트 트래킹 브랜치의 추가

- 로컬 브랜치에 리모트 트래킹 브랜치를 추가하는 것이 가능하다.
  - `git branch -u <remote>/<branch>`명령어 사용

```bash
$ git branch -u origin/master
```

- 로컬 저장소의 브랜치와는 별개로 리모트 트래킹 브랜치를 만드는 것도 가능하다.
  - `git checkout --track <remote>/<branch>`명령어 사용
  - 입력한 브랜치가 있는 리모트가 딱 하나 있고, 로컬에는 존재하지 않는다면 `git checkout <branch>`명령어를 사용해도 동일하게 작동

```bash
$ git checkout --track origin/master
```

### 리모트 트래킹 브랜치 동기화 및 로컬에 저장

- 리모트 트래킹 브랜치와 로컬 브랜치를 동기화하기 위해서는 두 단계를 거친다.
  1. `git fetch <remote>`명령어를 이용해 리모트 저장소의 변경사항을 갱신
  2. `git merge <remote>/<branch>`명령어를 이용해 로컬 브랜치에 병합

```bash
$ git fetch origin
$ git merge origin/master
```

- `pull`명령어를 사용하면 `fetch`와 `merge`를 함께 수행한다.
  - `git pull [<remote>]`명령어를 사용, 트래킹하고있는 리모트 저장소가 1개만 있다면 `<remote>`는 생략가능
  - `pull`보다는 `fetch`와 `merge`를 나눠서 수행하는 것을 추천
- `fetch`명령어를 이용해 가져온 리모트 저장소의 변경사항을 로컬 브랜치에 병합하지 않고, 따로 로컬 브랜치로 만드는 것도 가능하다.
  - `git checkout -b <branch-name> <remote>/<branch>`명령어 사용

```bash
$ git fetch origin
$ git checkout -b remote-master origin/master
```

### 리모트 저장소에 로컬 브랜치 업로드

- `git push <remote> <branch>`명령어를 이용하면 현재 브랜치를 리모트 저장소에 업로드하는 것이 가능하다.
  - `<remote>`: 로컬에서 사용하는 리모트 저장소의 이름
  - `<branch>`: 업로드 할 브랜치의 이름

```bash
$ git push origin master
```

- 리모트 트래킹 브랜치가 추가되어 있는 로컬 브랜치의 변경내용을 업로드 하고 싶은경우 `git push`명령어를 사용하면 된다.

```bash
$ git push
```

### 리모트 브랜치 삭제

- merge된 후 필요성이 사라진 리모트 브랜치의 삭제는 `git push <remote> --delete <branch>`명령어를 사용하면 된다.

```bash
$ git push origin --delete develop
```

## 참고

- [Pro Git 2nd Edition > 3.5 Git 브랜치 - 리모트 브랜치](https://git-scm.com/book/ko/v2/Git-%EB%B8%8C%EB%9E%9C%EC%B9%98-%EB%A6%AC%EB%AA%A8%ED%8A%B8-%EB%B8%8C%EB%9E%9C%EC%B9%98)
- [これで完璧! git remote でリポジトリを【追加,削除,確認,変更】](https://www.sejuku.net/blog/71492)
