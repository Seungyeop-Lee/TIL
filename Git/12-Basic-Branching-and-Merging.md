# 브랜치와 Merge의 기초

- Merge란 갈라진 브랜치를 합치는 작업을 뜻한다.
- Merge대상이 되는 두 브랜치의 상태에 따라 Fast-Forward, 3-way Merge로 Merge의 종류가 나뉜다.

## Merge의 종류

### Fast-Forward Merge

- A브랜치에서 B브랜치를 Merge할 때 B브랜치의 시작 commit이 A브랜치의 commit 커밋과 동일 할 경우 발생한다.
- 이 경우 A브랜치는 B브랜치의 현재 commit으로 이동하며, Merge 커밋이 발생하지는 않는다.

![Fast-Forward Merge 전](https://git-scm.com/book/en/v2/images/basic-branching-4.png)

> Fast-Forward Merge전 (master에서 hotfix를 Merge)

![Fast-Forward Merge 후](https://git-scm.com/book/en/v2/images/basic-branching-5.png)

> Fast-Forward Merge후 (master에서 hotfix를 Merge)

### 3-way Merge

- A브랜치에서 B브랜치를 Merge할 때 B브랜치의 시작 commit과 A브랜치의 현재 commit이 상이 할 경우 발생한다.
- 이 경우 git은 A브랜치와 B브랜치의 공통 조상과 비교(3-way)하여 자동으로 Merge를 수행한다.
  - 공통 조상을 기초로 A브랜치와 B브랜치의 변경사항을 적용하여 Merge한다.

![3-way Merge 전](https://git-scm.com/book/en/v2/images/basic-merging-1.png)

> 3-way Merge 전 (master에서 iss53을 Merge)

![3-way Merge 후](https://git-scm.com/book/en/v2/images/basic-merging-2.png)

> 3-way Merge 후 (master에서 iss53을 Merge)

## 충돌(Conflict)

- 3-way Merge시 동일 파일의 동일 부분의 수정이 상이하게 이루어져 자동으로 Merge가 되지 않는 상태를 나타낸다.
- 충돌이 발생하면, 사용자가 직접 충돌을 해결해 줌으로서 Merge가 가능하다.

## Merge와 관련된 명령어

### `git merge`

- A브랜치에 B브랜치를 Merge하고 싶은 경우
  1. A브랜치로 이동한다. `git checkout A`
  2. B브랜치를 Merge한다. `git merge B`
  3. Merge가 끝난 브랜치는 삭제한다. `git merge -d B`

### 충돌 해결 관련 명령어

- 충돌이 발생 한 경우
  1. `git status`명령어로 충돌발생 파일을 확인한다.
  2. 해당 파일 내부에 충돌이 발생한 부분을 수정한다.
     - `<<<<<< HEAD:<파일명>`이하의 부분은 현재 브랜치의 내용
     - `>>>>>> <브랜치이름>:<파일명>`이상의 부분은 Merge하려는 브랜치의 내용
  3. `git add`명령어로 다시 Git에 저장한다. (Staging 시킨다)
  4. `git status`명령어로 충돌이 해결되었는지 확인한다.
  5. `git commit`명령어로 commit한다.

## 참고

- [Pro Git 2nd Edition > 3.2 Git 브랜치 - 브랜치와 Merge 의 기초](https://git-scm.com/book/ko/v2/Git-%EB%B8%8C%EB%9E%9C%EC%B9%98-%EB%B8%8C%EB%9E%9C%EC%B9%98%EC%99%80-Merge-%EC%9D%98-%EA%B8%B0%EC%B4%88)
