# <div align="center">🚨 협업 시 하위브랜치끼리 머지 충돌난 경우</div>

### 상황
```
대형프로젝트 진행의 경우 여러사람이 협업으로 진행하는 경우가 있다.    
내가 했던 경우에는 메인브랜치 생성해두고    
각자 서브브랜치에서 작업 후, 작업이 완료되는대로 머지시키는 작업을 반복했다.    
작업 중 각각 서브브랜치에서 작업 후, 메인브랜치으로 머지시킬때
한명이 먼저 머지시키면 같은 파일을 수정한 경우에는 다음에 머지하는 사람은  자연스럽게 머지 충돌 발생한다.    
```
그 때 해결하는 방법~~~~!!

### 1. 서브브랜치에서 충돌 해결하는 경우
```bash
$ git checkout mainBranch
$ git pull origin mainBranch
$ git checkout subBranch
$ git pull origin mainBranch
------- 충돌발생(conflict) => 수동 해결 -------
$ git add .
$ git commit -m "충돌해결"
$ git push origin subBranch
```
👉 서브브랜치에서 충돌 해결되면, 메인브랜치로 머지시키면 성공~

### 2. 메인브랜치에서 충돌 해결하는 경우
```bash
$ git checkout mainBranch
$ git pull origin mainBranch
$ git merge subBranch
------- 충돌발생 => 해결 -------
$ git add .
$ git commit -m "충돌해결"
$ git push origin mainBranch

충돌나있던 sub -> main PR 은 자동으로 머지되어 있다.
```