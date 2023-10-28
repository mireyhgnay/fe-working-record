# <div align="center">👩🏻‍💻 pnpm 이란?</div>

<br>

## pnpm이란? (Performent Node Package Manager)

pnpm이란 한마디로 표현하면 "빠르고 효율적인 javscript 패키지 매니저"라고 할 수 있습니다.

<br>

## pnpm 설치방법

```bash
npm install -g pnpm
```

<br>

## pnpm 사용방법

```bash
pnpm install #의존성 패키지 인스톨
pnpm add  #패키지 추가
pnpm  # 명령어 실행
```

<br>

## pnpm사용이유, pnpm 특징

pnpm을 사용하는 가장 큰 이유는 빠르고, 효율적인 디스크 사용이 가능하기 때문입니다.

각 내용에 대한 상세 내용은 아래에서 설명하겠습니다.

그 외에도 모노레포 지원 등 여러 장점이 있긴 하지만, 가장 큰 장점에 대해서만 설명해보겠습니다.

<br>

## pnpm특징 - 빠르다 : pnpm 속도 비교, benchmark, 벤치마크

pnpm 공식 github 레포에 따르면,

pnpm은 다른 javascript 패키지매니저에 비해 최대 2배이상 빠릅니다.

왜 이렇게 빠르냐면, 아래 그림과 같이 각 dependency마다 설치가 병렬적으로 수행되기 때문입니다.

<br>

최근 회사에서 모노레포를 사용하게 되면서 pnpm으로 관리하게 되어서

사용하는 이유에 대해 찾아보았다.

앞으로 모노레포 저장소로 이전하면서 더... 공부하고 이해해야할 것 같다.

---

<br>

@Reference

https://devscb.tistory.com/135
