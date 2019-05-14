# 원격 저장소

- 구축되어있는 리모트 저장소와 관련하여 로컬 저장소에서의 명령어를 정리한다.
- 원격 저장소는 꼭 어딘가 멀리 떨어져 있을 필요는 없다.
  - 로컬에 원격 저장소를 구축하는 것도 가능

## 원격 저장소 확인

- `git remote`명령어를 사용해 확인이 가능하다.
  - 옵션 없이 사용: 설정된 원격 저장소의 이름이 출력된다.
  - `-v`: 설정된 원격 저장소의 이름과 URL이 출력된다.

```bash
$ git remote -v
```

## 원격 저장소 추가

- `git clone`을 통해 원격 저장소에서 저장소를 복제 할 경우, 자동으로 추가가 된다.
- 따로 추가하고 싶을 경우 `git remote add <remote-name> <url>`명령어를 사용한다.

```bash
$ git remote add til https://github.com/seungyeop-lee/til.git
```

## Fetch, Pull

- Pull이나 Fetch는 로컬에는 없지만, 리모트 저장소에 있는 데이터를 모두 가져오는 작업을 말한다.
  - Fetch는 가져오기만 할 뿐, 현재 브런치와 Merge하지는 않는다.
  - Pull은 가져온 후, 현재 브런치와 자동으로 Merge작업을 수행한다.
    - Pull == Fetch + Merge
- 명령어는 각각 `git fetch <remote-name>`, `git pull <remote-name>`이다.

```bash
$ git fetch til
$ git pull til
```

## Push

- Push란 원격 저장소에 로컬 저장소를 업로드하는 작업을 말한다.
- 명령어는 `git push <remote-name> <branch-name>`이다.

```bash
$ git push til master
```

## 원격 저장소 살펴보기

- `git remote show <remote-name>`명령어를 사용하면 살펴볼 수 있다.

```bash
$ git remote show til
```

## 원격 저장소 이름변경

- `git remote rename <remote-name> <new-remote-name>`명령어를 사용한다.

```bash
$ git remote rename til til-origin
```

## 원격 저장소 삭제

- `git remote remove <remote-name>`명령어를 사용한다.
- 원격 저장소를 삭제 할 경우, 로컬에 저장되어 있던 해당 원격 저장소에 관련 된 데이터가 모두 삭제된다.

```bash
$ git remote remove til-origin
```

## 참고

- [Pro Git 2nd Edition > 2.5 Git의 기초 - 리모트 저장소](https://git-scm.com/book/ko/v2/Git%EC%9D%98-%EA%B8%B0%EC%B4%88-%EB%A6%AC%EB%AA%A8%ED%8A%B8-%EC%A0%80%EC%9E%A5%EC%86%8C)
