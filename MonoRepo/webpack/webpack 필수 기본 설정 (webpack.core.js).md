# <div align="center">🌈 webpack 필수 기본 설정 (webpack.core.js)</div>

<br>

```
모노레포를 구축하면서 기존에 설정되어있던 웹팩 내용을 그대로 유지하면서
업데이트되는 부분들을 체크해가면서 설정하는 것이 어렵다..
파일 하나하나, 옵션 하나하나 공부해가면서 설정하려니 세월아 네월아~ 지만 화.이.팅
```

<br>

## Entry, Output, Loader, Plugin 설정

웹팩의 4가지 핵심 개념은 공식 홈페이지에서 **`Entry`, `Output`, `Loader`, `Plugin`** 를 Core Concepts 라고 소개합니다. (webpack.core.js 파일에 설정하면 될 것 같다)

<br>

## 1) Entry 설정

webpack이 어디를 출발 지점으로 해서 그려나가면 좋을지 알려주어야한다.

config파일에서 entry 속성을 설정해서 우베팩이 어떤 모듈로부터 시작해서 디펜던시 그래프를 거려나갈지 명시해 줄 수 있다.

entry 속성의 기본값은 ‘./src/index.js’ 이지만 다른 엔트리 포인트를 지정할 수 있다. (여러개도 가능)

```jsx
const config = {
	entry: './src/js/index.js';
}
```

<br>

## 2) Output 설정

웹팩이 번들을 꾸리고 나서 결과물을 어디로 보낼지 지정하는 속성이다.

대체로 기본값으로는 main.js파일은 ./dist/main.js 에 보내지고 그 외 파일들은 ./dist 폴더에 내보내진다.

파일 이름(filename), 경로(path)를 별도로 지정할 수 있고,

clean 을 true 로 설정하면 지정한 결과물이 내보내지는 디렉토리 안에 (dist) 사용하지 않는 파일을 알아서 정리해준다.

```jsx
const config = {
  output: {
    filename: "main.js",
    path: path.resolve(dirname, "dist"),
    clean: true,
  },
};
```

<br>

## 3) Loader 설정

웹팩은 기본적으로 JavaScript와 JSON 파일만 이해할 수 있다.

그 외 리소스를 번들링하기 위해서는 Loader 가 필요하다. Loader를 설정ㅎ애주면 다른 포맷의 리소스도 디펜던시 그래프에 추가할 수 있게 된다.

Loader를 설명하려면 test와 use 두 가지 필수 속성을 적어주어야한다.

- test : 어떤 파일을 변환할지 지정하는 속성으로, 보통 `/\.txt$/`과 같이 정규식으로 작성한다.
  따옴표 없이 **정규식**으로 작성해야한다. (따옴표 넣으면 빌드가 제대로 안됨)
- use : 파일을 변환할 떄 어떤 로더를 사용해야하는지 명시하는 속성이다.

<br>

즉, 웹팩 컴파일러에세 아래와 같이 말하는 것이다.

> 웹팩 컴파일러야!
> 디펜던시 그래프를 그리다가 test 에 지정된 파일 형식을 발견하잖아?
> 그러면 번들에 넣기 전에 내가 use에 지정한 로더로 꼭 변환해줘!!

<br>

---

<br>

@Reference

- https://365kim.tistory.com/35

- https://webpack.kr/guides/getting-started/#creating-a-bundle

- https://v4.webpack.js.org/loaders/eslint-loader/
