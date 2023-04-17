# <div align="center">👩🏻‍💻 URLSearchParams로 객체를 구현하여 for…of 문을 사용해 키/값을 추출하기</div>

<br>

> URLSearchParams / for...of문 사용하여 객체 생성 / new URL() / jquery.parse

<br>

## **URLSearchParams 란?**

URL의 쿼리 문자열(url에서 물음표 뒤에 오는 문자열)을 대상으로 작업할 수 있는 유틸리티 메서드입니다.

`URLSearchParams` 를 구현하는 객체는 for…of 문을 사용해서 직접 키/값 쌍을 순회할 수 있습니다. 키/값을 추출해낼 수 있다는 것!

**https://stackabuse.com/search/?q=url**

주소에서 ? 뒤에 오는 쿼리 스트링을 추출하여 원하는 정보를 가져와야하는 상황에서

자바스크립트에서 복잡한 쿼리스트링을 파싱할 수 있도록 `URLSearchParams` 객체를 제공합니다.

<br>

## **URLSearchParams 객체 생성 방법**

- search 는 쿼리스트링을 추출한다.

  ```jsx
  var urlObj = new URL("https://stackabuse.com/search/?q=url&type=article");
  var urlSearchObj = new URLSearchParams(urlObj.search);

  console.log(urlObj.search); // '?q=url&type=article'
  ```

- 실무에서 URL을 객체로 변환하여 key, value 를 생성하는 함수

  ```jsx
  function urlToJSON(url) {
    let paramResult = {}; // 객체를 담을 변수
    const url = new URL(url);

    if (url.search) {
      const param = new URLSearchParams(url.search);
      for (let [key, value] of param) {
        paramResult[key] = value;
      }
    }
    return paramResult;
  }
  ```

  - 함수에서 인자로 받은 url주소를 new URL 객체로 생성
  - `url.search` (쿼리 스트링)이 있는 경우, 쿼리스트링을 `URLSearchParams` 를 사용해 객체로 변환
  - 객체로 변환한 것들을 순회하면서 key, value 쌍으로 추출하여 객체로 설정해주고
  - 그 객체를 반환한다.

<br>

## **new URL() 이란?**

Javascript에는 url을 간편하게 다룰 수 있도록 URL객체가 마련되어 있다.

이것을 사용하면 프로토콜, 파라미터, 호스트 네임 변경과 같은 작업을 편하게 할 수 있다.

```jsx
var url = new URL("http://testurl.co.kr:8080/path/main.html?param1=1&param2=3");

hash: ""
host: "testurl.co.kr:8080"
hostname: "testurl.co.kr"
href: "http://testurl.co.kr:8080/path/main.html?param1=1&param2=3"
origin: "http://testurl.co.kr:8080"
password: ""
pathname: "/path/main.html"
port: "8080"
protocol: "http:"
search: "?param1=1&param2=3"
searchParams: URLSearchParams {}
username: ""
```

위의 코드는 javascript로 URL객체를 생성한 것이다.

URL객체를 생성하기 위해서는 생성자에 기본적인 URL을 입력해주어야 한다. (http형식으로만!!)

참고 : [https://joalog.tistory.com/112](https://joalog.tistory.com/112)

<br>

## **jQuery Parse 를 사용하여 Object 로 변환하는 방법**

`jquery.parse` 를 사용하여 json 객체로 변환시키는 방법

parse 와 정규식을 사용해서 객체로 변환해줄 수 있지만, 위에 적어둔 U**RLSearchParams 방법이 훨씬 좋은 방법이라고 생각한다.**

String → Object

```jsx
const object = parseJSON(
  '{"' + value.replace(/&/gi, '","').replace(/=/gi, '":"') + '"}'
);
```

<br>

Object → String

```jsx
const string =
  "?" +
  JSON.stringify(htParam)
    .replace(/["{}]/gi, "")
    .replace(/:/g, "=")
    .replace(/,/g, "&"); // JSON을 URL Parameter 형태로 변형
```

<br>

---

<br>

search 외에도 다양한 값을 추출해 낼 수 있습니다. 아래 링크 참고

[https://developer-talk.tistory.com/822](https://developer-talk.tistory.com/822)
