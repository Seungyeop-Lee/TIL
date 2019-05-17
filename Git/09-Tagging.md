# 태그

- 태그란 특정 커밋에 이름표를 붙이는 것으로 릴리즈 할 때 버전 정보를 표기하는 용도로 사용된다.
- 태그와 관련된 명령어에 대해 정리한다.

## 태그 조회

- `git tag`명령어를 사용한다.
  - 옵션 없이 사용: 이미 만들어진 태그를 알파벳 순서로 보여준다. (`-l` 옵션을 붙인 것과 동일 결과)
  - `-l "<pattern>"`: `pattern`에 맞는 태그를 검색하여 보여준다.

```bash
$ git tag -l "v1.*"
```

## 태그 붙이기

- Git에서의 태그는 Annotated태그와 Lightweight태그 두 종류가 있다.
- 과거 커밋에 대해서도 태그를 붙이는게 가능하다.
  - 커밋을 지정하지 않으면 현재 커밋에 태그가 붙음

### Annotated 태그

- `git tag -a <tag-name> [-m "<tag-message>"]`명령어를 사용한다.
- `-m`옵션을 사용하지 않으면 설정한 편집기가 실행되고, 태그 메세지 입력 후 저장 종료하면 반영된다.
- Annotated태그에는 작성자, 작성시간, 태그 메세지가 포함되며, `git show`명령어로 확인이 가능하다.

```bash
$ git tag -a v0.0.1 -m "first version"
```

### Lightweight 태그

- `git tag <tag-name>`명령어를 사용한다.
  - 아무런 옵션도 사용하지 않는다.

```bash
$ git tag v0.0.2
```

### 과거 커밋에 태그 붙이기

- `<태그 추가 명령어> <커밋 체크섬>`으로 과거 커밋에 태그를 붙이는 것이 가능하다.

```bash
$ git tag v0.0.1-rc0 fc3b9876edfe80e9d07ee7e86b39e9c5bb4a066e
```

- 체크섬은 앞 7자리 정도만 사용해도 된다.

```bash
$ git tag v0.0.1-rc0 fc3b987
```

## 태그 공유

- `git push`를 사용하여 원격 저장소에 로컬 저장소를 공유 할 경우, 기본적으로 태그 정보는 전송되지 않는다.
- 원격 저장소에 태그 정보를 공유하는 방법은 두가지가 있다.
  - 태그만 따로 공유: `git push <remote-name> <tag-name>`
  - Push시 태그까지 같이 공유: `git push <remote-name> --tags`

```bash
git push origin v0.0.1
git push origin --tags
```

## 태그를 이용한 Checkout

- 태그를 이용하여 특정 커밋에 Checkout하는 것이 가능하다.
- `git checkout <tag-name>`명령어를 사용하면 된다.

```bash
$ git checkout v0.0.1
```

- 특정 커밋(태그)로 checkout할 경우 HEAD가 최신 상태에서 벗어난 상태(detached HEAD)가 된다.
- 브랜치의 가장 최신 커밋으로 돌아오려면 `git checkout <branch-name>`명령어를 사용하면 된다.

```bash
$ git checkout master
```

## 참고

- [Pro Git 2nd Edition > 2.6 Git의 기초 - 태그](https://git-scm.com/book/ko/v2/Git%EC%9D%98-%EA%B8%B0%EC%B4%88-%ED%83%9C%EA%B7%B8)
