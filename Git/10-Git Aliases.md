# 명령어 별칭

- Git은 명령어를 완벽하게 입력하지 않으면 작동하지 않는다.
- 그렇기에 주로 쓰이는 명령어는 별칭을 정하여 사용이 가능하다.
- 명령어 별칭과 관련한 내용을 정리한다.

## 명령어 별칭 설정

- 명령어 별칭은 설정 파일에 설정이 가능하다.
  - `git config alias.<alias-name> "<command>"`명령어로 설정이 가능하다.

```bash
$ git config --global alias.last "log -1 HEAD"
```

- 외부 명령어를 별칭으로 사용 하는 것도 가능하다.
  - `<command>`에 `!`로 시작하게 만들면 된다.

```bash
$ git config --global alias.visual "!gitk"
```

## 명령어 별칭 사용

- 등록한 명령어 별칭은 `git <alias-name>`으로 사용이 가능하다.

```bash
$ git last
```

## 참고

- [Pro Git 2nd Edition > 2.7 Git의 기초 - Git Alias](https://git-scm.com/book/ko/v2/Git%EC%9D%98-%EA%B8%B0%EC%B4%88-Git-Alias)
