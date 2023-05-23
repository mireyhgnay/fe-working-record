# <div align="center">📝 React 모듈 내보내고 가져오기(export, import)</div>

<br>

## **리액트에서 모듈 내보내고 가져오는 방법**

### 1. 첫번쨰 방법 (export default)

- 제일 기본적으로 많이 사용하는 import/export 방법이다.

- export default 는 한 모듈당 한 개만 넣어주어야한다.

**`Module.jsx`**

```jsx
import React from "react";

const Module = () => {
  return <></>;
};

export default Module;
```

<br>

또 다른 방법으로,,

만약 모듈명을 컴포넌트마다 써주기 귀찮다면..?

함수 const 앞에 `export default` 를 붙혀주면 컴포넌트별 하단에 매번 적어주지 않아도 됩니다.

```jsx
import React from "react";

export default const Module = () => {
  return <></>;
};
```

<br>

**`index.jsx`**

```jsx
import React from "react";
import Module from "./Module";

<Module />;
```

<br>
<br>

### 2. 두번째 방법(export 모듈명)

- export 만 써줄 경우 import 할 때 { 중괄호 } 를 필수로 써서 모듈을 가져와야합니다.

- 함수를 한개만이 아닌 여러개를 내보낼 수 있습니다.

**`Module.jsx`**

```jsx
import React from "react";

export const Module = () => {
  return <></>;
};
```

<br>

**`index.jsx`**

```jsx
import React from "react";
import { Module } from "./Module";

<Module />;
```

<br>

```
✏️ 결론적으로 뭐가 더 맞다고 정해진 건 없어서 회사 컨벤션에 맞게 쓰거나 본인 기준에 따라 쓰면 되지만,
개인적으로는 export default 를 쓰는게 더 코드상 좋아보인다.
```

<br>
<br>

## **오류 잔뜩 났던 나의 실수**

**`Module.jsx`**

```jsx
import React from "react";

export const Module = () => {
  return <></>;
};
```

<br>

**`index.jsx`**

```jsx
import React from "react";
import Module from "./Module";

<Module />;
```

나는 총체적으로 오류가 와라락.. 날 수 밖에 없었다...

export 만 써서 모듈을 내보내놓고, import 할 때 중괄호도 없이 불러왔다.😂

모듈 하나만 내보내는데 export default 만 쓴 것이 아닌 export 만 쓴것..

export 를 썼으면 불러올 때 { 중괄호 }를 썼어야 했는데 그냥 불러온 점...

앞으로는 절대 이런 실수는 하지 않도록 하자^^

<br>

---

<br>

@Reference

- https://ko.javascript.info/import-export
- https://lily-im.tistory.com/21
