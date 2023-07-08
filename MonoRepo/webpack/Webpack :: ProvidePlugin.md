# <div align="center">🌈 Webpack :: ProvidePlugin</div>

<br>

자주 사용되는 모듈을 미리 등록하여 매번 작성하지 않게 해줍니다.

<br>

예시

```jsx
import React from "react";
import $ from "jquery";
```

<br>

웹팩에 내장된 플러그인이기 때문에 별도 설치할 필요 없습니다.

```jsx
// ...
  plugins:[
    new webpack.ProvidePlugin({
      React: 'react',
      $:'jquery'
    })
    ],
//...
```

<br>
<br>

## 기본 문법

모듈을 `import` 또는 `require` 할 필요 없이 자동으로 로드합니다.

```jsx
new webpack.ProvidePlugin({
  identifier: "module1",
  // ...
});
```

<br>

기본적으로, 모듈 해석 경로는 현재 폴더 `(./**)`와 `node_modules`입니다.

또한 전체 경로도 지정할 수 있습니다.

```jsx
const path = require("path");

new webpack.ProvidePlugin({
  identifier: path.resolve(path.join(__dirname, "src/module1")),
  // ...
});
```

<br>
<br>

## Usage:jQuery

`jquery`를 자동으로 로드하려면 해당 노드 모듈에 노출되는 두 변수를 모두 가리킬 수 있습니다.

```jsx
new webpack.ProvidePlugin({
  $: "jquery",
  jQuery: "jquery",
});
```

<br>

아래 소스코드처럼 어느것으로도 사용가능 합니다.

```jsx
// 모듈에서
$("#item"); // <= 동작합니다.
jQuery("#item"); // <= 이 또한 동작합니다.
// $는 모듈 "jquery" exports로 자동 설정되었습니다.
```

<br>

---

<br>

@Reference

https://webpack.kr/plugins/provide-plugin/
