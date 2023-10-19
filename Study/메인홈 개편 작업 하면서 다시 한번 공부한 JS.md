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
- 무조건 변수를 선언할 필요가 없다.  
  깔끔히 하려고 하다보니 모든 요소 선택을 변수로 설정해서 하려고 하는걸 버리자! 한번만 사용 되는 애는 바로 선택해서 사용하자.
- [Element: insertAdjacentHTML()](https://developer.mozilla.org/ko/docs/Web/API/Element/insertAdjacentHTML)

  - 지정된 텍스트를 HTML로 파싱하고 결과 노드들을 지정된 위치의 dom 트리에 삽입합니다.
  - **`insertAdjacentHTML(position, text);`**
  - `position` 매개변수
    - beforebegin :
      - 요소 이전에 위치합니다. 오직 요소가 DOM 트리에 있고 부모 요소를 가지고 있을 때만 유효합니다.
    - beforeend :
      - 요소 바로 안에서 마지막 자식 이후에 위치합니다.
    - afterbegin :
      - 요소 바로 안에서 처음 자식 이전에 위치합니다.
    - afterend :
      - 요소 이후에 위치합니다. 오직 요소가 DOM 트리에 있고 부모 요소를 가지고 있을 때만 유효합니다.
  - `text` 매개변수
    - HTML 혹은 XML로 파싱되고 트리에 삽입되는 문자열입니다.

- innerHTML VS appendChild VS html

  - innerHTML
    - DOM.innerHTML = ' ' 형태
    - innerHTML은 교체 - 내부 HTML을 완전히 교체해버린다.
    - innerHTML이 appendChild보다 빠르다. (약 2배 정도)
  - appendChild
    - DOM.appendChild(' ') 형태
    - appendChild는 추가 - 완전한 DOM 객체를 (맨 뒤에) 삽입한다.
  - .html()
    - 제이쿼리 문법이다.
    - html()을 활용하면 해당 태그 하위의 html 내용을 가져올 수 있고 그 내용을 새로운 내용으로 변경할 수도 있습니다.

- **Scroll Event**
  - [IntersectionObserver](https://github.com/mireyhgnay/fe-working-record/blob/main/Study/IntersectionObserver.md)
  - [DOM.getBoundingClientRect()]()
