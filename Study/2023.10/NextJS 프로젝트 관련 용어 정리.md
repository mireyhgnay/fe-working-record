# <div align="center">👩🏻‍💻 NextJS 프로젝트 관련 용어 정리</div>

<br>

1. CP 조직의 **CP**(Company Package) : Company Package를 통해 → 통합관리 기능을 통한 장애대응, 향상된 기술셋 변화를 통한 시스템 안정화, 협업 개발을 효율적으로 하기위한 프로젝트를 진행중.

2. **POC** : Proof of Concept, 개념증명, 새로운 프로젝트가 실제로 실현가능성이 있는지 효과와 효용, 기술적인 관점에서 부터 검증을 하는 과정을 의미
3. **Eureka** : 유레카
   - Eureka Server : 마이크로서비스의 IP/FQDN과 PORT정보를 저장하고 제공하는 Service Discovery
     → 필요 이유 : kubernetes와 다른 runtime환경(App)이 함께 사용 되는 경우 모두를 지원 할 수 있는 service discovery가 필요함
     (Kubernetes는 컨테이너화된 애플리케이션을 자동으로 배포, 스케일링 및 관리하기 위한 오픈소스 플랫폼이다. 간단히 말해, 애플리케이션을 관리하기 쉽게 만들어 준다.)
   - **Kubernetes** : 쿠버네티스 : 는 컨테이너를 쉽고 빠르게 배포/확장하고 관리를 자동화해주는 오픈소스 플랫폼입니다. (https://subicura.com/2019/05/19/kubernetes-basic-1.html)
   - Front End에서는 Eureka-js-client 패키지로 eureka-server를 호출하여 ip/domain을 리턴 받을수 있다.
4. **스캐폴딩** : 영어 단어로 '뼈대' 혹은 '비계'를 의미한다. 즉, 어휘의 뼈대를 구축해줌으로써 언어 능력이 뒤처지는 학습자들로 하여금 혼자 해결할 수 없는 문제들까지 해결할 수 있게 도와주는 교수 기법이다.
5. **스플렁크** : 로그를 수집하고 사용자가 원하는 결과를 추출하는 대용량 로그 수집/분석 시스템.
6. **Perf**(Performance Counter for Linux) : 리눅스 시스템 성능 프로 파일링하는 도구
7. **미들웨어**(middleware) : 공통 서비스 및 기능을 애플리케이션에 제공하여 개발자와 운영자가 애플리케이션을 더욱 효율적으로 구축하고 배포하도록 돕는 소프트웨어 및 클라우드 서비스입니다.
8. **CI/CD**
   - **CI** (Continuous Integration[지속적인 통합] : 새로운 코드 변경 사항이 정기적으로 빌드 및 테스트 되어 공유 레포지토리에 통합히는 것을 의미
   - **CD** (Continuous Delivery[지속적인 서비스 제공] & Continuous Deployment[지속적인 배포]) : 개발자의 변경 사항이 레포지토리를 넘어, 고객의 프로덕션(Production) 환경까지 릴리즈 되는 것
     - Continuous Delivery : **공유 레포지토리**로 자동으로 Release 하는 것
     - Continuous Deployment : **Production** 레벨까지 **자동으로** deploy 하는 것
   - https://artist-developer.tistory.com/24
9. **Skeleton** : 초기 프로젝트 구조나 기반이 되는 코드 와 프레임워크를 의미, 이러한 프로젝트 skeleton은 프로젝트의 기본 구조를 정의하고, 개발 팀이 프로젝트를 시작할 때 빠르게 출발할 수 있도록 돕는 역할
10. **BFF** (Backend For Frontend) : 프론트엔드를 요구사항에 맞게 구현하기 위한 도움을 주는 보조 서버, CP 프로젝트에서는 'API를 BFF로 제공 할 것인가' 에 대한 논의가 있다.
11. **코드컨벤션** (Code Convention) : 작성한 코드를 다른사람들도 쉽게 이해할 수 있게 가독성 있는 코드를 작성하는법에 대한 규칙이다.
    - CP조직의
      ![스크린샷 2023-11-03 오전 10.23.55.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/106b7c1d-b64b-4b8a-aa9c-96bd1b3260c9/7afee6b6-baa5-409b-8e0a-364c09d1dbd3/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2023-11-03_%E1%84%8B%E1%85%A9%E1%84%8C%E1%85%A5%E1%86%AB_10.23.55.png)
    - 이 코드컨벤션에 대해 반대의견...(폴더에 폴더를 파고드는 방식이 맞는것인가?, 안에서 다른 파일로 빼지 않고 원자 컴퍼넌트성 파일만 폴더구조로 하는게 좋을것 같다.)
12. **SonarQube** : 조직에서 개발된 코드의 지속적인 인스펙션을 통해 품질 목표를 달성할 수 있게 해주는 플랫폼. 소스 코드 품질 현황을 가시화, 리스크 분석, 소스 코드에서 발생하는 문제를 해결함으로써 소프트웨어 비즈니스를 위해 반드시 필요한 **솔루션**
    - 정적 코드 분석 : 코드를 실행하지 않고 분석하며 메모리 누수 또는 버퍼 오버플로우 등 일반적으로 알려진 오류 및 취약점 파악 및 표준 코딩 적용에 관한 내용을 분석
13. **JEST :** 페이스북에서 만들어서 React와 더불어 많은 자바스크립트 개발자들에게 사랑받고 있는 **테스팅 라이브러리**. 출시 초기에는 프론트엔드에서 주로 쓰였지만 최근에는

    백엔드에서도 기존의 자바스크립트 테스팅 라이브러리를 대체

14. **RTL**(React Testing Library) : **Behavior Driven Test**(행위 주도 테스트) 방법론이 대두 되면서 함께 주목 받기 시작한 테스팅 라이브러리. 행위 주도 테스트는 기존에 관행이던 **Implementation Driven Test**(구현 주도 테스트)의 단점을 보완하기 위한 방법론
15. **CSRF**(Cross-Site Request Forgery) : \
16. next.js **middleware API** : request를 기반으로 response를 조작하고 구성하는 방법을 더 잘 제어할 수 있게 제공 되는 API( 특정 url 에 접근 했을 때 관련된 requset를 기반으로 response를 조절됨)
17. **Swagger** : REST API를 설계, 빌드, 문서화 및 사용하는 데 도움이되는 OpenAPI 사양을 중심으로 구축 된 오픈 소스 도구 세트

**Skeleton 에서 사용중인 라이브러리**

1. **Emotion :** Emotion 은 JS 로 css 스타일을 작성하도록 설계된 라이브러리.

   스타일을 inline으로 작성하면 class로 따지고 자동으로 css파일에 추가된다.

2. **ReactQuery :** 기존의 client state를 다루는 상태관리 라이브러리들과 다르게 server state를 Fetching, Caching, 비동기적으로 업데이트 하는데 도움을 주는 라이브러리.
   - Hydration:
     - Server Side 단에서 먼저 정적 페이지를 렌더링하고 JS파일들도 번들링한 후에 둘다 Client Side로 보내주는 생각을 해냈다.
     - 하지만 그 DOM에는 동적인 이벤트가 하나도 없는 메마를 상태일 것이다. 그래서 이 메마른 뼈대에 수분을 보충해서, 즉 HTML 코드와 JS 코드를 서로 매칭시켜 동적인 웹사이트를 브라우저에 랜더링하는 기술이 등장했는데 이게 바로 **Hydratation**이다.
     - 그래서 Hydration을 한글로 직역하면 수분 보충이라고 말 할 수 있다.
     - https://velog.io/@huurray/React-Hydration-%EC%97%90-%EB%8C%80%ED%95%98%EC%97%AC
3. **PM2** : Node.js 어플리케이션을 쉽게 관리할 수 있게 해주는 Process Manager, 멀티스레드를 통해 무중단 재시작, 무중단 배포가 가능
4. **edge-csrf :** Edge-CSRF는 Edge 런타임에서 실행되는 [Next.js](https://nextjs.org/) middleware 에 대한 CSRF 보호
