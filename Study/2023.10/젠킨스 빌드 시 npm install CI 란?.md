# <div align="center">👩🏻‍💻 젠킨스 빌드 시 npm install CI 란?/div>

<br>

CI는 의존성의 버전들을 고정한다.

CI를 쓰지 않으면 버전이 바뀌면서 빌드가 실패할 수 있다.

CI는 pcakage-lock.json 파일에 정의된 의존성 버전으로 빌드를 진행한다.

install할 시에 package.json에 정의된 의존성의 버전을 따르는데,

버전 앞에 ~, ^ 와 같은 것들을 붙이는데

만약 ^1.2.3 버전으로 package.json 에 설정해놓고 install하면 `1.2.3 <= version < 2.0.0` 이 사이 버전들 어떤 것이든 들어갈 수 있다.

package-lock.json 파일은 npm i 명령을 실행할 때마다 없으면 만들거나 수정이 되는데

빌드해서 문제 업슨 시점의 package-lock.json에 정의된 버전으로 빌드를 하는게 CI 이다.

### 그래서 최대한 고정버전으로 처음에 설치해서 쓰는 것이 좋다.
