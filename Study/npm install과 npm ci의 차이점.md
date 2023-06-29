# <div align="center">✏️ npm install과 npm ci의 차이점</div>

<br>

## 상황

오늘 한 저장소에서 npm install 과 npm ci 를 사용하여 다른 결과를 맞이했다..

<br>

## npm install

npm install은 패키지와 패키지가 의존하는 모듈을 설치하는 명령어이다.

- 개별적으로 패키지를 설치할 때위와 같은 방법으로 사용하면 package.json과 package-lock.json이 없는 경우에는 이 2개의 파일이 생성되고, package.json과 package-lock.json이 존재한다면 dependencies에 패키지가 추가된다.

- `npm install 패키지_이름` 으로 설치한다.

- pacakge.json의 dependencies에 나열되어 있는 패키지를 설치할 때이때 package.json의 요구 사항(dependencies)을 만족해야 package-lock.json을 적용된다. 만약 요구 사항을 만족하지 않는다면 pacakge를 업데이트하고 package-lock.json 파일의 내용이 변경된다.

<br>

## npm ci

npm ci는 npm install 과 유사하지만, npm install과 달리 같은 개발 환경을 구축해 줄 수 있기 때문에 테스트 플랫폼, 지속적인 통합 및 배포(CI와 CD)와 같은 자동화된 환경이나 dependencies를 새로 설치해야 하는 모든 상황에서 사용할 수 있는 명령어이다.

- npm ci는 pacakge-lock.json 기반으로 설치가 진행되기 때문에 package-lock.json이나 npm-shrinkwrap.json 파일이 꼭 존재해야 한다.

- npm ci는 npm install 처럼 `npm ci 패키지_이름` 와 같이 사용할 수 없다. npm ci는 한 번에 전체 프로젝트만 설치할 수 있기 때문에 개별적으로 패키지를 설치하는 것이 불가능하다.

- 이미 node_modules 폴더가 존재하는 경우에 npm ci를 실행시키면 기존 node_modules 폴더를 삭제하고 다시 설치한다.

<br>

## npm install 과 npm ci의 속도 비교

npm ci가 npm install 보다 더 빠르다.

npm ci가 npm install 보다 빠른 이유는 지정된 버전의 패키지만 설치하면 돼서 최신 호환 버전을 확인하는 과정이 필요 없기 때문이다.

참고로, npm ci는 다음과 같은 경우에 훨씬 더 빠를 것이다.

- package-lock.json 혹은 npm-shrinkwrap.json 파일이 있을 때

- node_modules 폴더가 없거나 비었을 때

<br>
<br>

## 회고록...

package.json 파일에서 패키지별로 고정버전이 아닌 캐럿이 붙어있는 버전들이 많은데

npm ci 로 설치할 경우 딱 지정한 버전의 패키지만 설치하기 떄문에 빠르고 좋은 것이다.

작업의 상황에 따라 무조건 npm i 로 설치해야하는 경우도 있겠지만,

상황별로 잘 판단하여 npm install 과 npm ci 를 유용하게 사용하자!!

<br>

---

<br>

@Reference

https://calssess.tistory.com/139
