# <div align="center">✏️ Git-flow 전략</div>

<br>

```
회사에서 깃플로우로 브랜치 전략을 바꾸게 될 예정이다.
사용해 본적이 없어서 미리 이해하고 이슈 없도록 하자!!
추가적으로 rebase 도 알아야 브랜치 관리가 가능할 것 같다.
```

<br>

## Git-flow

GitFlow는 Git을 사용한 개발 작업 절차다.

프로그램이 아닌 약속, 규칙 같은 개념이다.

GitFlow는 완벽한 방법론이 아닌 각자 팀에 맞는 개발 환경에 따라 변형해 사용하는 게 좋다고 언급했다.

깃 플로우는 프로그램이 아니라 개발자끼리 지키는 하나의 개발 원칙같은 것이다.

<br>
<br>

## Git-flow 브랜치 구성

- **master** : 기준이 되는 브랜치로 제품을 배포하는 브랜치 입니다.⭐
- **develop** : 개발 브랜치로 개발자들이 이 브랜치를 기준으로 각자 작업한 기능들을 합(Merge)칩니다.⭐
  - 개발이 완료된 상태와 일치하는 브랜치
  - 개발이 완료되었다는 것은 다음 릴리즈를 위해 언제든 배포될 수 있는 상태를 말합니다.
- **feature** : 단위 기능을 개발하는 브랜치로 기능 개발이 완료되면 develop 브랜치에 합칩니다.
- **release** : 배포를 위해 master 브랜치로 보내기 전에 먼저 QA(품질검사)를 하기위한 브랜치 입니다.
- **hotfix** : master 브랜치로 배포를 했는데 버그가 생겼을 떄 긴급 수정하는 브랜치 입니다.

<br>

```
⚠️ **master**와 **develop**가 중요한 **매인 브랜치**이고 나머지는 필요에 의해서 운영하는 브랜치라고 보시면 됩니다.
```

<br>
<br>

## Flow

1. master 브랜치에서 feature 작업브랜치 생성 (pull 하여 최신화 필수!)
2. develop 브랜치에서도 동일한 feature 작업브랜치 생성 (pull 최신화 필수!)
3. develop 브랜치에서 딴 feature 작업브랜치에서 개발을 진행함
4. 완료된 feature 브랜치는 dev 환경에서 검토를 거쳐 다시 develop 브랜치에 Merge!
5. 모든 검증이 끝나면, develop 브랜치를 release 브랜치로 만든다. QA 검증 진행
   1. develop branch → release branch
6. 모든 검증이 최종적으로 완료되면 release branch 를 master / develop 브랜치로 보낸다.
7. 배포했는데 긴급으로 수정해야할 버그가 있을 경우 hotfix 브랜치를 생성해서 수정 배포

<br>
<br>

## Git-flow 장점

- 승인된 개발자만 코드에 접근할 수 있게 해서 안전하게 소스코드를 관리할 수 있다
- 출시된 프로그램의 코드를 안전하게 수정, 병합할 수 있다
- feature 브랜치, 풀 리퀘스트를 활용해서 새 기능 개발에 집중할 수 있다

<br>

---

<br>

@Reference

- [우린 Git-flow를 사용하고 있어요 - 우아한형제들 기술블로그](https://techblog.woowahan.com/2553/)
- [Git Flow 개념 이해하기](https://ux.stories.pe.kr/183)
- [강남언니 : GitFlow 제대로 알고 쓰기](https://blog.gangnamunni.com/post/understanding_git_flow/)
