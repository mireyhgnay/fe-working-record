# <div align="center">👩🏻‍💻 `querySelectorAll` 메서드는 DOM 요소를 선택하고 NodeList를 반환한다.</div>

<br>

**`querySelectorAll`** 메서드는 DOM 요소를 선택하고 NodeList를 반환합니다.

```jsx
const element = document.querySelectorAll(".className");
```

<br>

**`element`**은 DOM 요소가 아닌 NodeList이기 때문에 **`html`** 메서드를 사용할 수 없습니다.

NodeList는 배열 유사 객체로, 각 요소에 대한 참조를 포함하고 있지만 DOM 요소의 메서드인 **`html`**을 사용할 수 없습니다.

대신에, 각 요소에 대한 작업을 수행하려면 NodeList를 순회하고 각 요소에 대해 원하는 작업을 수행해야 합니다.

<br>

### 결론은! .className 의 돔 요소를 선택하지만 element가 반환하는 것은 NodeList 이기 때문에 메서드를 잘 사용해야 한다!!!
