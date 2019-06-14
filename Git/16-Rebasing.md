# Rebase

- 브랜치의 병합 방법 중 하나인 Rebase에 대해 정리한다.

## Rebase란

- 현재 브랜치의 시작 커밋(조상)을 떨어져 나온 브랜치의 최신 커밋으로 이동시키는 것을 의미한다.
- Git은 시작 커밋을 이동시키면서 변경 점들을 전부 현재 브랜치에 자동 병합시킨다.
- 결론적으로 Merge와 동일한 효과를 얻지만 브랜치의 시작 커밋이 최신 커밋으로 변경되면서 브랜치를 최종 Merge할 때 Merge 커밋이 남지 않는다.(Fast-Forward)

![Merge를 이용한 병합](https://git-scm.com/book/en/v2/images/basic-rebase-2.png)

> Merge를 이용한 병합

![Rebase를 이용한 병합](https://git-scm.com/book/en/v2/images/basic-rebase-3.png)

> Rebase를 이용한 병합

## Rebase방법 후 Fast-Forward방법

1. Rebase할 브랜치로 이동: `git checkout <branch>`
2. 현재 브랜치가 분리되었던 브랜치를 대상으로 Rebase: `git rebase <upstream-branch>`
3. 분리되었던 브랜치로 이동: `git checkout <upstream-branch>`
4. Rebase된 브랜치를 현재 브랜치에 병합(Fast-Forward): `git merge <branch>`

```bash
$ git checkout experiment
$ git rebase master
$ git checkout master
$ git merge experiment
```

## 시작 커밋을 다른 브랜치로 이동

- Rebase의 대상을 분리된 브랜치가 아닌 다른 브랜치로 변경하는 것이 가능하다.
  - 브랜치 B1에서 B2가 갈라져나오고, B2에서 B3가 갈라져 나왔을 때
  - B3를 B1에 대해 Rebase하는 것이 가능하다.
- rebase명령어에 `--onto`옵션을 사용하면 된다.
  - `git rebase --onto <newbase-branch> <upstream-branch> <branch>`
  - 이 명령어는 어떤 브랜치에서 작동시키든 상관없다. (현재 브랜치의 정보가 필요치 않음)
- 예를 들어 아래와 같은 상황일 경우를 생각해보자.

![다른 토픽 브랜치에서 갈라져 나온 토픽 브랜치](https://git-scm.com/book/en/v2/images/interesting-rebase-1.png)

- 이 때, client브랜치를 master브랜치에 대해 rebase하고 싶을때는 아래와 같은 명령어를 실행시키면 된다.

```bash
$ git rebase --onto master server client
```

![다른 토픽 브랜치에서 갈라져 나온 토픽 브랜치를 Rebase 하기](https://git-scm.com/book/en/v2/images/interesting-rebase-2.png)

## Rebase의 주의점

- push한 커밋이 Rebase 대상이 되지 않도록 해야한다.
  - Rebase를 할 경우, 내용은 같지만 체크섬은 다르므로 Git은 다른 커밋으로 인식하기 때문
  - 변경된 리모트 저장소를 받아쓰는 로컬의 리모트 트래킹 브랜치의 히스토리가 꼬이게 되는 경우가 발생
- pull한 커밋에 대해 리모트 저장소에서 누군가 Rebase를 하여, 리모트 트래킹 브랜치의 히스토리가 꼬이게 되는 경우, 리모트 트래킹 브랜치의 정리가 가능하다.
  - pull을 할 경우 `--rebase`옵션을 사용
  - fetch후 merge명령어 대신 rebase 명령어로 병합하는 것과 동일한 결과

```bash
$ git pull --rebase
```

```bash
$ git fetch origin
$ git rebase origin/master
```

## Rebase vs. Merge

- Rebase는 엄밀히 말하면 히스토리를 수정하는 것과 동일하다.
- 하지만 히스토리 자체를 깔끔하고, 보기 좋게 만드는 효과를 낸다.
- 버전관리의 목적성에 따라 Rebase와 Merge를 골라 사용하는 것을 추천

## 참고

- [Pro Git 2nd Edition > 3.6 Git 브랜치 - Rebase 하기](https://git-scm.com/book/ko/v2/Git-%EB%B8%8C%EB%9E%9C%EC%B9%98-Rebase-%ED%95%98%EA%B8%B0)
