# 되돌리기

- 마지막 커밋을 수정하거나, Staged파일을 Unstaged시키거나, Modified파일의 수정내역을 삭제하는 방법에 대해 정리한다.

## 마지막 커밋 수정

- `git commit --amend`명령어를 사용한다.
- 마지막 커밋의 수정내역은 `--amend`옵션의 커밋과 합쳐지고, 커밋 메세지는 덥어씌어 진다.

```bash
$ git commit --amend -m "<commit message>"
```

| 요소        | 마지막 커밋 | `--amend` 커밋 | 최종 반영된 커밋   |
| ----------- | ----------- | -------------- | ------------------ |
| a 파일      | 수정        | 변화 없음      | 수정               |
| b 파일      | 변화 없음   | 수정           | 수정               |
| c 파일      | 추가        | 수정           | 수정된 파일이 추가 |
| 커밋 메세지 | 메세지1     | 수정 메세지2   | 수정 메세지2       |

## Staged파일을 Unstaged시키기

- `git reset HEAD <file name>`명령어를 사용한다.
  - Staged된 파일이 있을 경우 `git status`로 조회하였을 경우 힌트로 나타난다.

```bash
$ git reset HEAD README.md
```

## Modified파일의 수정내역을 삭제하기

- `git checkout -- <file name>`명령어를 사용한다.
  - Modified된 파일이 있을 경우 `git status`로 조회하였을 경우 힌트로 나타난다.
- 수정내역은 전부 사라지므로, 이 방법보다는 Stash와 Branch를 사용하는 것을 권장한다.

```bash
$ git checkout -- README.md
```

## 참고

- [Pro Git 2nd Edition > 2.4 Git의 기초 - 되돌리기](https://git-scm.com/book/ko/v2/Git%EC%9D%98-%EA%B8%B0%EC%B4%88-%EB%90%98%EB%8F%8C%EB%A6%AC%EA%B8%B0)
