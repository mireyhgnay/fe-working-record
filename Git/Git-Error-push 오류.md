# <div align="center">🚨 git push :: 'Note about fast-forwards' in 'git push --help' for detail</div>

### 오류 화면
![pusherror](https://user-images.githubusercontent.com/111990266/209424795-3800ef9f-3701-4a6d-8e72-d8db3f8c0543.png)

### 해결 방법
pull 분명 했던 것 같은데 커밋푸시 과정에서 충돌이 났는지 push가 되지않고 오류가 났다.    
그래서 commit 되돌리고 다시 pull하는 방법으로 해결했다.

```bash
# 가장 최근의 commit을 취소
$ git reset HEAD^
```