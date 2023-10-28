# <div align="center">👩🏻‍💻 카카오톡 공유 URL 디버깅 : 이미지 반영 확인하기</div>

<br>

## 📍 상황

meta 태그의 property 속성 `og:image` 를 사용해서 특정 URL을 카카오톡에 공유했을 때

이미지 변경이 잘 안됨을 확인하여 카카오톡 공유 디버깅이라는 것을 알게되었다.

우리가 직접 캐시를 초기화 할 수도 있고,

이미지가 바꾸고자 하는 것으로 잘 반영됐는지 확인할 수 있다.

(너무 좋은것...!!!)

<br>

## 카카오톡 디버깅

카카오톡 대화창이나 페이스북 글 등럭시에 URL 을 입력하면 자동으로 썸네일이 생성된다.

이때 새로 등록한 이미지를 제대로 불러오지 못하거나 이슈가 있을 때 디버깅이 필요하다.

아래 페이지에서 공유 디버거에 들어가서 디버깅이 가능하다.

[🔗 Kakao developers 바로가기](https://developers.kakao.com/tool/debugger/sharing)

카카오 외에도 페이스북도 디버깅 페이지가 있다.

두 페이지 모두 회원가입만 하면 사용할 수 있다.

[🔗 Facebook developers 바로가기](https://developers.facebook.com/tools/debug/?locale=ko_KR)

<br>

## 👩🏻‍💻 Code

```jsp
<meta property="og:title" content="site name" />
<meta property="og:image" content="https://img.example.com/example.jpg" />
<meta property="og:description" content="카카오톡 공유 이미지" />
```
