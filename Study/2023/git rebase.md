# <div align="center">✏️ Git rebase</div>

<br>

## Git rebase

공통 베이스를 가진 A와 B Branch 두개가 있을 때

한 브랜치의 내용을 다른 브랜치의 최신 커밋 브랜치로 옮기는 작업입니다.

<br>
<br>

## 장점

### 1. 공유 브랜치의 최신 변경사항을 즉각 반영할 수 있습니다.

`git merge` 는 공유 브랜ㅊ니에 대한 변경사항을 즉각 대응하기 어렵습니다.

반면 `Git rebase`를 사용한다면, 동료 개발자들이 올린 커밋들의 수정사항을

내가 작업하고 있는 브랜치에 즉각 반영할 수 있습니다.

<br>

예를들어 release 브랜치의 최신 commit을 반영하면서 작업을 해야할 떄

`git rebase`를 사용한다면 **작업 branch에서 항상 최신 변경사항을 적용한 commit을 유지**할 수 있습니다.

<br>
<br>

### 2. rebase는 커밋이력을 남기지 않으므로 commit History 가 깔끔합니다.

git merge 로 최신이력을 가녀올 경우 복잡한 커밋 히스토리가 됩니다.

반면 git rebase로 만들어진 히스토리는 두, 세줄의 깔끔하고 직관적인 히스토리로 프로젝트를 관리할 수 있습니다.

<br>

특히, `git-flow`를 사용할 때 `Rebase and Merge` 전략으로 깔끔한 History로 작업할 수 있습니다.

rebase 후에 merge를 해보자!

```bash
git checkout feature/my-branch
git rebase develop
# feature 브랜치를 develop 브랜치에 머지하기
# develop 브랜치에 두고!
git merge feature/my-branch
```

- feature/my-branch 를 develop의 최신 커밋으로 옮긴 것이다.
- feature브랜치의 커밋들에도 최신 변경사항들이 반영된 커밋들로 존재하게 된다.

<br>
<br>

## 단점

merge는 충돌이 발생하면 한번만 처리하면 되지만 `rebase`는 나의 branch의 각각의 commit마다 충돌처리를 해주어야 합니다.

하지만 이게 단점이자 장점인 점!

git-flow 전략에서 develop의 이전 커밋들과 내 브랜치의 커밋들을 어느 커밋에서 충돌이 난건지도 모른채로

하나의 커밋에서 충돌을 해결하는 것은 바람직한 방법은 아니라고 생각합니다.

<br>

오히려 feature 브랜치의 모든 커밋이 전부 정상적으로 동작하도록

각각의 커밋마다 충돌을 해결하는 것이 코드 에러를 줄이고 품질을 높이는 방법이 더 좋은 방향이라고 생각합니다.

<br>
<br>

## 연습해보기

**branch 생성**

- dev branch
  - ㄴ feature/test1
  - ㄴ feature/test2

1. feature/test2(작업브랜치)를 우선 수정 변경하여 dev branch 에 Merge

2. git pull origin dev 하여 최신화 후,

   2-1. feature/test1 에서 작업 전 git rebase dev 하면 → 작업 브랜치 최신화 됨

   2-2. feature/test1 에서 작업 중에! git rebase dev 하기 → 스테시 해야해서 안됨

   2-3. 작업하던 것 feature/test1 작업브랜치에 푸시하고, git rebase dev 하면 기존 작업에 feature/test2 내용 들어옴!

3. feature/test2 들어온 상태에서 다시 feature/test1 에 작업 추가해서 —force 로 강제 푸시

<br>

### rebase & merge !!

```bash
git checkout dev
git pull origin _dev #최신화
git checkout feature/test1
git rebase dev
# feature 브랜치를 dev 브랜치에 머지하기
# dev 브랜치에 두고!
git merge feature/test1
```

<br>
<br>

곧 회사에서도 git-flow 전략을 사용할 예정이다.

rebase 에 대해 명확히 이해하고 사용하자!

<br>

---

<br>

@Reference

https://seosh817.tistory.com/240#%EB%82%B4%20%EC%9E%91%EC%97%85%20branch%EC%9D%98%20%EA%B0%81%EA%B0%81%20commit%EB%A7%88%EB%8B%A4%20conflict%EB%A5%BC%20%ED%95%B4%EA%B2%B0%ED%95%B4%EC%95%BC%20%ED%95%9C%EB%8B%A4.-1
