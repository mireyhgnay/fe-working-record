# <div align="center">👩🏻‍💻 yargs.argv</div>

<br>

## 상황

모노레포 구축 후, 기존 저장소 작업 이관 중..

webpack 설정을 처음부터 새로 싹 재설정하는데 device 를 구분하기 위해서 yargs.argv 를 사용하려고 했다.

명확히 어떤 용도로 쓰이는지 제대로는 알지 못해서 스터디!!

<br>
<br>

## yargs 란?

yagrs는 Node.js에서 명령줄 인터페이스(CLI) 애플리케이션을 작성하기 위한 라이브러리입니다.

yargs.argv는 yargs를 사용하여 병령줄에서 전달된 인수를 구문 분석하고 접근할 수 있는 객체입니다.

<br>

일반적으로 CLI 애플리케이션은 사용자가 터미널에서 명령을 실행할 때 인수와 옵션을 함께 전달합니다.

이때 yargs.argv는 전달된 인수와 옵션의 값을 가져올 수있는 도구입니다.

<br>

구조분해 할당을 사용해서 yargs 모듈에서 argv 객체를 가져온다.

```jsx
const { argv } = require("yargs");
```

<br>

구조 분해 할당은 객체나 배열에서 필요한 값을 추출하여 개별 변수에 할당하는 JavaScript의 기능입니다.

이를 통해 require(’yargs’) 에서 반환된 객체 중 argv 프로퍼티를 추출하여 argv 라는 변수에 할당하고 있습니다.

<br>

**`yargs.argv`**와 **`const { argv } = require('yargs');`**는 동일한 역할을 합니다.

**`yargs.argv`**는 전체 **`yargs`** 모듈을 통해 **`argv`** 객체에 접근하는 방법이고,

**`const { argv } = require('yargs');`**는 구조 분해 할당을 사용하여 **`argv`** 객체를 바로 추출하는 방법입니다.

이렇게 구조 분해 할당을 사용하면 **`argv`**를 직접 사용할 수 있게 됩니다.

<br>

일반적으로 **`const { argv } = require('yargs');`**와 같은 구문을 사용하여 **`argv`** 객체를 가져온 후에는 **`argv`**를 사용하여 사용자의 입력을 구문 분석하고 필요한 작업을 수행할 수 있습니다

<br>
<br>

### 내가 사용한 코드

`package.json`

```jsx
"webpack-customproxy-dev-p": "...(생략) device=p",
"webpack-customproxy-qa-p": "...(생략) device=p",
"webpack-customproxy-stage-p": "...(생략) device=p"
```

- scripts 설정에서 device=p 로 설정하여 프록시를 pc 디바이스로 돌리도록 명령어 설정

<br>
<br>

```jsx
const TARGET =
  argv.device === "m"
    ? `https://${DEVICE_TYPE}-benefit-${PHASE}.tmon.co.kr/`
    : `https://benefit-${PHASE}.tmon.co.kr/`;
const FROM = `https://resource-dev.tmon.co.kr/${PHASE}/${SERVICE_ID}/m/js/bundle/${SERVICE_ID}.bundle.js`;
```

- argv.device 를 통해서 p / m 각각 로컬 주소를 설정해주었다.

<br>

**`argv.device`**는 **`yargs.argv`** 객체에서 **`device`** 속성에 저장된 값에 접근하는 것입니다.

이를 통해 사용자가 입력한 디바이스와 관련된 정보를 프로그램에서 활용할 수 있습니다.
