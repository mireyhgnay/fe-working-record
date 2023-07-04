# <div align="center">🌈 dependencies와 devDependencies 차이점</div>

<br>

## dependencies와 devDependencies 차이점은?

- dependencies 에는 애플리케이션 동작과 직접적으로 연관된 라이브러리를 설치한다.
- devDependencies 에는 개발할 때 필요한 라이브러리를 설치한다.

<br>

### 왜 나눠서 설치하는가?

- devDependencies에 포함된 라이브러리는 실제 배포할 때 포함되지 않기 때문에 빌드 시간을 줄일 수 있다.
- 애플리케이션에 필요한 라이브러리가 아니라면 dev에다가 설치하도록 한다!
- 예를들어, eslint, prettier와 같은 라이브러리들은 dev에 설치하는 것이 좋다.

<br>

```json
"lint-": {
    "src/**/*staged.{js,jsx}": [
      "eslint --ext .js,.jsx src/ --fix"
    ]
  },
  "husky": {
    "hooks": {
      "pre-commit": "lint-staged"
    }
  },
```

모노레포 작업전에 무조건 부분체크아웃 한 후에 작업하기!

부분체크아웃 하고나서 루트에서 pnpm -F 프로젝트네임 i 로 하면 패키지 설치

<br>

- 기존 stamp 설정들 유지하면서 최대한 가져오기 (마이그레이션)
- eslint
- react v6에 맞춰서!
- 번들돌아가고 실행 잘 되지만 서버가 닫혀서인지 로컬에서 뜨지않음.
  - 환경별 링크주소도 잘못되어있어서 다시 설정해야함
