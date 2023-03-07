# <div align="center">🚨 pull 오류 :: Not possible to fast-forward, aborting</div>


## 오류 내용
`git pull origin <branch Name>`을 했는데 pull이 받아지지 않았다.

오류 메시지
```bash
Not possible to fast-forward, aborting
```

## 오류 원인
git global 옵션에 pull.ff=only 옵션이 있었는데    
이는 pull을 받을 때 늘 fast-foward 방식으로 받겠다는 뜻이며        
이 방식으로 받는다면 다른 사람이 나와 다른 브랜치를 따서 먼저 develop에 머지를 했을 때 fast-foward 관계가 형성되지 않아 pull이 중단되는 것이였다. 

## 오류 해결
* 해결1: global 옵션을 없앰.    
`git config --unset --global pull.ff`

* 해결2: `git config --global pull.rebase=true` 추가하고 터미널 재실행 후 pull 받기

* 해결3: 해결2를 진행했는데 해결이 안됐다면 `git pull --rebase origin <branch name>`로 pull 받기

---
@reference https://velog.io/@dev_crystal/pull이-받아지지-않았던-오류