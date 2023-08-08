# <div align="center">📝 React : a태그 target 속성 사용 시 에러 해결하기</div>

<br>

## **리액트에서 a태그 활용해서 새로운 탭 띄우기**

리액트에서 html 코드를 작성하던 중,,,

`<a>`태그를 사용했을 때 `href` 속성은 외부 링크를 설정하고 `target` 속성을 `"\_blank"`로 설정 해야하는 상황이였다.

근데 처음엔 `href="#"` 으로만 작성해서 에러가 나는 줄 알았는데

링크를 주소로 제대로 넣어도 `target` 때문에 에러가 계속 나고있었다.

<br>
<br>

## **해결방법은?**

찾아보니 `rel` 속성으로 `noopener noreferrer` 을 넣어줘야한다고 한다고한다.
결론적으로는 보안 때문에 작성해줘야 하는 것 같다.

- `noopener` : 현재 활성화된 페이지와 새로운 탭에서 활성화되는 페이지를 별개의 프로세스로 취급합니다.
- `noreferrer` : 현재 활성화된 페이지의 정보를 새로운 탭에서 활성화되는 페이지에 전달하지 않습니다.

```jsx
import React from "react";

const App() {
  return (
    <div className="App">
      <a
        href="https://www.example.com/"
        target="_blank"
        rel="noopener noreferrer">
        이동하기
      </a>
    </div>
  );
}
export default App;
```

<br>

---

<br>

@Reference

- ⭐️ https://github.com/jsx-eslint/eslint-plugin-react/blob/master/docs/rules/jsx-no-target-blank.md
- https://developer-talk.tistory.com/862
