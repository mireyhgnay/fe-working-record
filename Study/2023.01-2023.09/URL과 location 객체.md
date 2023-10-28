# <div align="center">👩🏻‍💻 URL과 location 객체</div>

<br>

## location 객체

자바스크립트에서 URL과 관련된 정보를 담고있는 객체 "location 객체"

생각보다 웹 프론트엔드 개발 업무를 하면서 location 객체를 꽤나 유용하게 사용하고 테스트하는 것 같습니다.

<br>
<br>

## URL 파트

URL에서 어떤 부분이 어떤 역할을 하는지! 알고 있어야 업무에 많은걸 테스트해보고 오류를 막을 수 있더라구요!!

- Protocol : 프로토콜 (http, https)
- User information : 사용자 로그인 정보 / 콜론으로 구분해 "아이디:패스워드"와 같은 형식으로 입력
- Hostname : 호스트명 / 도메인
- Port : 포트 / 80, 443 과 같이 연결 포트를 지정
- Path : 도메인 하위 경로 ?로 시작하는 쿼리스트링 앞까지 해당
- Query String : ?로 시작해 #해시 앞까지 해당
- Anchor(Hash) : 앵커 / 해시 / 현재 웹 페이지 안에 위치를 id 값으로 표시

<br>

```jsx
"http://www.example.com:8080/test?search=iphone#123";
```

- Protocol : http://
- Host : www.example.com:8080
- Domain : example.com
- Path : /test
- Query String : ?search=iphone
- Hash :

<br>
<br>

## location 객체 속성

- location.href : URL 전체
- location.protocol : http, https
- location.host : hostname + port, URL에 포트가 명시되지 않은 경우 Hostname 으로 반환
- location.hostname : 도메인
- location.pathname : "/" 로 시작하고 # 해시 전까지만 출력
- location.origin : protocol + hostname + port
- location.search : Query String (?물음표 뒤에 오는 애들)
- location.hash : # 뒤에 오는 애들

<br>

```jsx
"https://aport.kr:443/post/write/form?id=110#content";
```

위와 같은 url이 있다면,

- location.href : https://aport.kr:443/post/write/form?id=110#content
- location.protocol : https:
- location.host : aport.kr:443
- location.hostname : aport.kr
- location.pathname : form
- location.origin : https://aport.kr:443
- location.search : ?id=110
- location.hash : #content

<br>

---

<br>

[🔗 Location 객체와 URL을 이해하자](https://blogpack.tistory.com/105)

[🔗 [Javascript] URL 파라미터 값 가져오기 (쿼리스트링 값)](https://hianna.tistory.com/465)

[🔗 웹 데이터 분석의 기본, 파라미터를 아시나요?](https://www.beusable.net/blog/?p=3798)
