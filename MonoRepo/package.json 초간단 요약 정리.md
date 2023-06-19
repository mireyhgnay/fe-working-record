# <div align="center">🌈 package.json 초간단 요약 정리</div>

<br>

현재 프로젝트에 관한 정보와 패키지 매니저(npm, yarn)을 통해 설치한 모듈들의 의존성을 관리하는 파일이다.

<br>

## name

가장 중요한 항목인 name과 version

필수로 입력되어야 하며 이 항목들이 누락되면 당신의 패키지는 설치할 수 없습니다.

<br>

## version

필수 항목!

name 과 version을 통해 각 패키지의 고유성을 판별하게 됩니다.

따라서 패키지의 내용을 변경하려면 version 을 변경해야만 한다.

<br>

## description

설명을 문자열로 기술한다.

npm search 로 검색된 리스트에 표시되기 때문에 사람들이 당신이 만든 패키지를 찾아내고 이해하는데 도움이 됩니다.

<br>

## keywords

키워드를 문자열 배열로 설명한다.

description 과 동일한 기능을 합니다.

<br>

## license

패키지 사용자들이 당신이 만든 패키지를 사용하기 위해 어떻게 권한을 얻는지,

또 어떤 금기사항이 있는지 알게하기 위해 라이센스를 명시해야 한다.

비공개로 사용하거나 어떤 조건에서도 패키지를 퍼블리싱하지 않을 경우 아래와 같이 명시해줍니다.

```json
"license": "UNLICENSED"
```

<br>

## scripts

패키지의 생명주기 중 다양한 타이밍에서 실행되는 스크립트 명령들을 포함하고 있는 사전이다.

scripts 항목 객체에서 키는 이벤트이고, 값은 이때 실행될 커맨드이다.

🔗 npm-scripts https://docs.npmjs.com/cli/v9/using-npm/scripts

<br>

## dependencies

의존성을 규정하는 것은 패키지의 이름과 해당 패키지의 버전 범위를 지정한 객체를 통해 이루어진다.

버전 범위는 하나 혹은 여러개의 공백으로 분리된 설명자 문자열이다.

테스트 관련 모듈이나 트랜스 파일러 관련 모듈을 dependencies 개체에 추가하면 된다.

운영이 아닌 개발 단계에서만 필요한 의존성 모듈들은 devDependencies 에 설치해야한다.

<br>

---

<br>

@Reference

https://programmingsummaries.tistory.com/385
