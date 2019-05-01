# 수정 후 저장소에 저장하기

- 파일 수정 후 Git을 이용한 저장소에 저장하는 명령어에 대해 정리한다.

## Git에서의 파일 라이프사이클

![Git의 파일 라이프사이클](https://git-scm.com/book/en/v2/images/lifecycle.png)

- Untracked : 저장소 영역에는 있지만, Git이 관리하지 않는 파일
- Tracked : Git이 관리하는 파일
  - Unmodified : 현재 버전의 파일과 동일한 파일
  - Modified : 현재 버전의 파일에서 수정이 일어난 파일
  - Staged : Modified 중 다음 버전의 스냅샷의 구성요소가 될 것을 지정한 파일 (Staged가 된 시점에서의 파일)
- 일반적인 흐름
  1. 파일이 생성 (Untracked)
  2. `add`명령어로 다음 버전 추가 파일로 설정 (staged)
  3. `commit`명령어를 통해 만들어진 버전에 속하게 됨. 즉, 관리가 시작 됨 (Unmodified)
  4. 파일 수정 발생 (Modified)
  5. 2~4가 반복

## 파일의 상태 확인

- `git status`명령어를 사용한다.
  - `-s`옵션을 사용하면 파일의 상태를 요약한 버전으로 확인 가능

```bash
$ git status
$ git status -s
```

- `-s`옵션을 사용 할 경우 파일명의 왼쪽에 상태정보 컬럼에는 두 가지 정보가 표시
  - 왼쪽은 Staging Area에서의 상태
  - 오른쪽은 Working Tree에서의 상태
- `M`은 변경, `A`는 추가, `D`는 삭제, `R`은 이름변경, `??`는 Untracked를 나타냄

## 파일을 새로 추적 및 기존 파일 Stage

- `git add`명령어를 사용한다.
  - Untracked -> Staged, Modified -> Staged로 변경
  - `-A`옵션을 사용하면 저장소 내의 모든 Modified, Untracked 파일이 Staged로 변경

```bash
$ git add <file>
$ git add -A
```

## 파일 무시하기

- Git이 관리 할 필요가 없는 파일이 다수 존재 할 경우 `.gitignore`을 저장소의 root에 만들고, 그 안에 무시할 파일 패턴을 기재한다.
- `.gitignore`파일에 입력하는 패턴은 아래의 규칙을 따른다.
  - 빈 라인, `#`으로 시작하는 라인은 무시
  - 표준 Glob 패턴을 사용
  - `/`로 시작하면 하위 디렉토리는 적용되지 않음
  - `/`로 끝나면 디렉토리를 의미
  - `!`로 시작하는 패턴의 파일은 무시하지 않음

| Glob패턴 기호 | 설명                                      |
| ------------- | ----------------------------------------- |
| `*`           | 0개 이상의 임의의 문자                    |
| `?`           | 1개의 임의의 문자                         |
| `[abc]`       | 대괄호 안의 문자중 하나의 문자와 일치     |
| `[a-z]`       | 대괄호의 범위에 속하는 하나의 문자와 일치 |

## 변경 내용 확인

- `git diff`을 사용한다.
  - 옵션 없이 사용: Modified와 Staged를 비교, Staged가 없으면 Unmodified(Commited)와 비교
  - `--staged`, `--cached`: Staged와 Unmodified(Commited)를 비교
    - `--staged`와 `--cached`는 완벽히 동일한 역할을 한다. [git diff: what is the difference between --cached and --staged](https://stackoverflow.com/questions/39877748/git-diff-what-is-the-difference-between-cached-and-staged)참고

```bash
$ git diff
$ git diff --staged
$ git diff --cached
```

## 커밋하기

- `git commit`을 사용하면 Staged인 파일이 전부 커밋된다.
  - 옵션 없이 사용: 디폴트로 설정 한 에디터로 커밋 메세지를 입력, 저장 후 종료를 하면 커밋 됨
  - `-m`: 커밋 메세지를 옵션 뒤에 인라인으로 작성
  - `-a`: 저장소 내 모든 Modified을 Staging 후 커밋 (Untracked는 제외)

```bash
$ git commit
$ git commit -m "<commit message>"
$ git commit -a
```

## 파일 삭제하기

- `git rm`을 사용한다.
  - 옵션 없이 사용: 해당 파일을 삭제하고, 삭제한 내용을 add한다. (staging 시킨다)
  - -f: Modified이거나 Staged인 파일을 강제 삭제
  - --cached: 옵션 없이 사용하는 것과 동일하나 해당 파일이 삭제되진 않는다.

```bash
$ git rm <file>
$ git rm -f <file>
$ git rm --cached <file>
```

- git명령어가 아닌 파일 명령어로 파일을 삭제 할 경우
  - 해당 파일이 삭제
  - 삭제된 내용은 Modified로 존재
  - Modified를 staging시키면 `git rm`과 동일한 결과

## 파일 이름 변경 및 이동하기

- `git mv`을 사용하면 해당 파일을 이름 변경 및 이동하고, 변경 내용을 add한다. (staging 시킨다)

```bash
$ git mv <original> <target>
```

- git명령어가 아닌 파일 명령어로 파일을 변경 할 경우
  - 이하의 내용이 Modified로 존재
    - `<original>`이 삭제
    - `<target>`이 추가
  - Modified를 전부 staging시키면 `git mv`와 동일한 결과

## 참고

- [Pro Git 2nd Edition > 2.2 Git의 기초 - 수정하고 저장소에 저장하기](https://git-scm.com/book/ko/v2/Git%EC%9D%98-%EA%B8%B0%EC%B4%88-%EC%88%98%EC%A0%95%ED%95%98%EA%B3%A0-%EC%A0%80%EC%9E%A5%EC%86%8C%EC%97%90-%EC%A0%80%EC%9E%A5%ED%95%98%EA%B8%B0)
- [위키피디아 > 글로브 (프로그래밍)](<https://ko.wikipedia.org/wiki/%EA%B8%80%EB%A1%9C%EB%B8%8C_(%ED%94%84%EB%A1%9C%EA%B7%B8%EB%9E%98%EB%B0%8D)>)