# <div align="center">👩🏻‍💻 메인홈 개편 작업 하면서 다시 한번 공부한 JS</div>

<br>

- [**Object.keys()**](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Object/keys)
  - 객체형태를 배열로 변환해준다.
- **delete**
  - 연산자를 사용하여 배열 요소를 삭제
  - 특정 배열 요소 삭제 가능
  - 하지만 배열의 길이는 그대로 (삭제보다는 변경에 가까움)
- **Swiper JS**
  - freeMode : 슬라이드 넘길 때 위치 고정 여부
    **freeMode**를 사용하면 사용자는 슬라이드 간의 제약 없이 자유롭게 스와이프할 수 있으며,
    이는 특히 슬라이드의 크기나 위치가 동적으로 변하는 경우에 유용합니다. @
  - slidePerView : number, // 한번에 보이는 슬라이드 갯수
  - slideToClickedSlide : true, // 해당 슬라이드 클릭시 슬라이드 위치로 이동
- **스크롤 값 구하기**
  - offsetHeight : 요소의 크기 ( + padding, scrollbar, border .. ) 모두 포함된 요소의 크기
  - outerHeight : window기준의 전체 메뉴바,스크롤 포함된 높이
  - innerHeight : window기준으로 그 안에 높이
- **DOM.getBoundingClientRect()**
  - 돔의 window기준 top,right, bottom, left , width 등… 모든 값을 구할 수 있다.
- onClick 이벤트는 호출을 계속 함. 초기화 해주려면
- remove()를 써서 돔을 제거했으면 다시 노출시켜야 할 때는 append나 돔을 다시 생성해주는 메소드를 사용해서 추가해줘야한다. 잠시 없앴다가 다시 노출시켜야하는 거라면 hide(), show() 를 사용해야한다.
