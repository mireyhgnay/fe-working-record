# <div align="center">📖 혼합콘텐츠(Mixed Contents)</div>

<br>

## Mixed Contents(혼합콘텐츠) 란?

최초 HTML이 안전한 HTTPS 연결을 통해 로드될 때 혼합 콘텐츠가 발생하지만

다른 리소스(예: 이미지, 동영상, 스타일시트, 스크립트)는 안전하지 않은 HTTP 연결을 통해 로드 됩니다.

이는 HTTP 콘텐츠와 HTTPS 콘텐츠가 함께 로드되어 동일한 페이지를 표시하므로 혼합 콘텐츠라고 하는데, 최초의 요청은 HTTPS 연결을 통해 보안 처리되었습니다.

최신 브라우저는 이 유형의 콘텐츠에 대한 경고를 표시하여 해당 페이지에 보안되지 않은 리소스가 포함되어 있음을 사용자에게 알려 줍니다.

<br>

## HTTP, HTTPs (SSL) 로 혼합컨텐츠 (Mixed Content) 가 되었을 때

HTTP를 이용하여 일반 텍스트 (Plain Text) 기반으로 웹을 운영하다가

SSL 로 전환하게 될 때 여러가지 문제점을 발생 할 수 있는데,

그 중 빈번하게 발생 할 수 있는 문제가 HTTP와 HTTPs 가 혼합된 페이지가 되어 버리는 것입니다.

<br>

SSL 기반의 웹컨텐츠에서 중간에 암호화 되지 않은 HTTP 기반의 컨텐츠가 발생 할 경우 브라우저는 HTTP 컨텐츠를 로딩하지 않습니다.

HTTPs 기반의 웹사이트에서 HTTP컨텐츠가 혼용 (Mixed) 되어 있을때

크롬이나 파이어폭스 브라우저에서는 HTTP컨텐츠는 차단하고 경고메세지를 보여줍니다.

<br>

## 해결 방법

사이트의 소스에서 혼합 콘텐츠가 포함된 위치를 찾은 후에

https://를 https:// 로 변경하고 https를 통해 사용 가능한지 확인해서

http:// 로 변경한 주소로도 리소스가 잘 나타난다면

URL를 http://에서 https://로 변경 하고 원본파일을 저장하고 필요한 경우 업데이트 파일을 다시 배포 합니다.

---

<br>

@reference

https://rsec.kr/?p=137

https://cert.crosscert.com/%EF%BB%BFhttps-%ED%81%AC%EB%A1%AC%EA%B3%BC-%ED%8C%8C%EC%9D%B4%EC%96%B4%ED%8F%AD%EC%8A%A4-%ED%98%BC%ED%95%A9-%EC%BB%A8%ED%85%90%EC%B8%A0mixed-content-%EC%B0%A8%EB%8B%A8/
