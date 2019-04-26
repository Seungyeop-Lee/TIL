# Git 설정

- Git 설치 후 사용 환경을 적절히 설정해야 한다.
- Git에서 사용하는 설정파일은 3군데에 나누어져 있다.
- Git의 `config`명령어로 접근이 가능하다.

## 설정 파일

1. 시스템 설정 파일

- 시스템의 모든 사용자와 모든 저장소에 적용되는 설정
- `git config --system`으로 접근 가능

2. 글로벌 설정 파일

- 현재 사용자의 모든 저장소에 적용되는 설정
- `git config --global`로 접근 가능

3. 로컬 설정 파일

- 특정 저장소에 적용되는 설정
- `git config --local`로 접근 가능(--local은 기본값이므로 생략해도 됨)

| 설정        | 설정 파일 위치(윈도우 10)                    |
| ----------- | -------------------------------------------- |
| 시스템 설정 | `C:\Program Files\Git\mingw64\etc\gitconfig` |
| 글로벌 설정 | `C:\ProgramData\Git\config`                  |
| 로컬 설정   | `(저장소 디렉토리)\.git\config`              |

- 동일 키를 가진 설정이 있을 경우, 로컬 > 글로벌 > 시스템 순으로 우선 시 한다.

## 사용자 정보 설정

- Git을 설치하자마자 해야 한다.
  - Git을 이용해 커밋 할 때마다 사용되는 정보이다.
- 일반적으로는 글로벌 설정 파일에 설정한다.
  - 사용자가 같으면 같은 이름을 쓰는 경우가 대부분이기 때문

```bash
$ git config --global user.name "<이름>"
$ git config --global user.email "<이메일>"
```

## 설정 확인

- 설정 된 목록을 확인하려면 `--list`옵션을 이용하면 된다.

```bash
$ git config --list
```

- 특정 키의 설정 값만을 보고 싶을 경우에는 `--list`대신 키값을 넣으면 된다.

```bash
$ git config <key>
```

- 여러 파일에서 동일한 키가 설정되어 있고, 최종적으로 어떤 파일에 있는 어떤 값이 설정되었는지 확인하기 위해서는 `--show-origin`옵션을 이용하면 된다.

```bash
$ git config --show-origin <key>
```

## 참고

- [Pro Git 2nd Edition > 1.6 시작하기 - Git 최초 설정](https://git-scm.com/book/ko/v2/%EC%8B%9C%EC%9E%91%ED%95%98%EA%B8%B0-Git-%EC%B5%9C%EC%B4%88-%EC%84%A4%EC%A0%95)