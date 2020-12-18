## 인터넷이란?
- Inter network의 약자로 네트워크들을 연결시켜주는 기술

## 웹이란?
- 하이퍼텍스트로 요청하는 문서를 전달하는 서비스

## HTML 3요소
- 컨텐츠
  - 문장 / 표 / 목록 / 폼
- 구조
- 스타일

## 메타 데이터
- 데이터를 위한 데이터(데이터를 설명하는 데이터)

## 시맨틱 태그
- <div id="header"></div> -> <header></header>

## 블록태그와 인라인태그
  - 블록태그는 너비, 높이 지정 가능 -> 무엇을 담기 위한 박스의 용도
  - 인라인태그는 너비, 높이 지정이 불가능 -> 컨텐츠끼리 구분하기 위한 용도
  
## 브라우저마다 달라서 쓰면 안되는 input 속성들
- https://developer.mozilla.org/ko/docs/Web/HTML/Element/Input 여기에서 Spec 부분에 Html5 써있는 것들은 쓰면 안되는 것들(자바스크립트를 이용하자)

## 정규표현식
- ^01[01678]-\d{3,4}-\d{4}$ 
  - 휴대폰 번호 
---
## CSS 선택자
- [x] [MDN 참고 링크](https://developer.mozilla.org/ko/docs/Web/CSS/Reference)
  - header > h1(자식 결합자)
    - header 자식만 선택
  - header h1(자속 결합자)
    - header 자식 뿐만 아니라 자손까지
  - A + B(인접 형제 결합자)
  - A ~ B(일반 형제 결합자)

- [x] 우선순위
  - id -> 속성 지정 -> class -> 태그
- [x] 속성을 갖고있는지 가지고 있지 않는지 판단하는 법
  - h1[class]
    - class 속성을 갖고 있는 h1 태그만 선택한다.
- [x] ul에 blue, li에 red를 먹이면 콕 집은 li가 우선순위가 더 높다 -> 범위가 더 좁은게 우선순위가 높기 때문이다.
- [x] h1[lang="ko"] vs .h1 중에 왼쪽의 우선순위가 더 높다(태그가 클래스보다 우선순위가 낮지면 콕 집었기 때문에 더 높다)

## 블록
- [x] 컨텐츠가 블록 크기를 넘으면 튀어나온다. overflow 옵션을 통해 해결한다.

## 가변 크기 / 고정 
- [x] **em**
  - **em은 현재 박스가 적용된 폰트 크기의 배수이다. 부모 영역에 할당된 폰트 크기도 영향을 받는다. 부모의 부모로부터 영향도 받는다.**
  - 기본 폰트의 크기는 16px이다.
  - 기준이 왜 폰트 크기일까?
    - 비율이 커지거나 작아지는 환경을 구성할 때 적절하게 이용할 수 있다.
- [x] **rem**
  - rem은 폰트 크기에 영향을 받기는 한다.
  - r은 root이다. root에 적용된 폰트 크기에 영향을 받는다.
    - root는 html에 적용된 폰트 크기를 의미한다.
    - css에서 html { font-size: 1px } 이런식에서만 적용된다.

## min-width, min-height
- [x] 컨텐트가 박스 영역을 벗어나려하면 자동으로 박스 영역이 늘어난다. 
- [x] 부모의 속성이 min-width 또는 min-height인 경우에 자식은 어떻게 해야할까
  - 자식이 만약 width: 100%; hieght: 100%를 하면 적용이 안된다. 
  - 부모가 min-width 또는 min-height라면 자식도 min-width, min-height를 적용해야 한다.
  - 그런데 min-height: 100%라고 하면 적용이 안된다. 십년째 해결안되는 버그이다. **min-height: inherit;** 속성을 줘야 해결할 수 있다.

## background
- [x] 꿀팁
  - body에 배경을 깔때는 1px짜리 이미지를 background로 넣어서 repeat-y를 하면 컨텐츠의 크기가 커져도 동적으로 배경도 같이 늘어난다
- [x] **background-size**
  - **contain**
    - 흘러 넘치지 않게 블록 크기에 맞게 이미지를 딱 넣어준다
  - **cover**
    - 블록 크기에 꽉 차게 이미지를 넣어준다. 흘러넘치는 것을 허용한다.
- [x] **background-attachment**
  - 블록 크기보다 컨텐츠가 길면 블록 크기를 벗어난다. 
  - **scroll**
    - 기본값
  - **fixed**
    - 홈페이지에서 스크롤할때 배경은 고정되고 컨텐츠만 움직이는 것을 구현할 때
  - **local**
    - ?
  
## overflow
- [x] **hidden**
  - 컨텐츠가 블록 크기보다 크면 넘어가는 부분은 숨겨진다. 아예 볼 수 없다.
- [x] **scroll**
  - 컨텐츠가 블록 크기보다 크던 작던 스크롤이 생긴다
- [x] **auto**
  - 컨텐츠가 블록 크기보다 클때만 스크롤이 생긴다.
  
## Pseudo(추가 예정)
- [x] :nth-child(숫자), :first-child
  
## Flex
- [x] 부모의 display가 flex이면 자식이 block이든 inline이든 item으로 판단한다.

- [x] **flex-basis**
  - 아이템들에 max-width, max-height를 준다. flex가 수평이면 width, 수직이면 height을 의미한다.
  - main 축을 의미한다. flex-direction: column;일 경우 main축은 수직방향이다.
  - **flex-basis는 width, height보다 우선순위가 높다.**
  - 컨테이너가 아닌 아이템들에 속성을 부여한다.
    - flex-basis: 200px;
      - 각 아이템들이 200px을 넘어갈 수 없다(max-width와 비슷하다)
      - 크기가 줄어들 수는 있다.
    - flex-basis: 0; 이면 컨텐트 크기만큼만 갖는다.
    
- [x] **flex-grow**
  - **남아있는 여백을 등분해서 배치한다.**
  - 모든 아이템에 flex-grow: 0을 주고 그 중 하나의 아이템만 flex-grow:1을 주면 남아있는 여백을 해당 아이템이 다 가져간다.
  - 모든 아이템에 flex-grow: 1을 주고 그 중 하나의 아이템만 flex-grow:3을 주면 3을 가진 아이템은 다른 아이템보다 여백을 3배 크게 차지한다.
  
- [x] **flex-shrink**
  - **크기가 줄어들 때 "야, 몇 번 아이템! 너가 다른애들보다 몇 배 빠르게 줄어들어라!"**
  -모든 아이템에 shrink: 0을 주면 아예 줄어들지 않는다. 크기가 고정된다.
  - 모든 아이템에 shrink: 0을 주고 그 중 하나의 아이템만 shrink: 1을 주면 크기가 줄어들 때 shrink: 1 해당 아이템만 줄어든다.
  - 모든 아이템에 shrink: 1을 주고 그 중 하나의 아이템만 shrink: 3을 주면 크기가 줄어들 때 3을 가진 아이템은 다른 아이템보다 3배 빠르게 줄어든다.
  
- [x] **flex-wrap**
  - 컨테이너에 flex-wrap: wrap;을 주고 main 축이 수평방향일 때, 컨텐트의 크기가 컨테이너의 크기보다 커져버리면 넘어가는 부분이 아래쪽으로 내려간다. 
  - 그런데 수직 방향일 때 flex-wrap: wrap;을 주면 먹히지 않는다. 먹히게 하기 위해서 컨테이너에 높이를 지정해줘야 한다.
  - wrap-reverse; 속성도 존재한다.
  
- [x] **order**
  - 어떤 아이템에 order: -1을 주면 해당 아이템이 가장 우선이 되어서 맨 앞으로 간다.
  - 보통 아이템이 갖고 있는 order 값은 0이다.
  
## Flex의 축약 표현(Flex는 여러 가지로 표현할 수 있다)
- [x] 아래 세 문장은 flex: 0 0 100px;로 표현이 가능하다. 순서를 꼭 지키자.
  - flex-grow: 0;
  - flex-shrink: 0;
  - flex-basis: 100px;
  
- [x] 만약 flex: 100px;를 하면 flex: 1 1 100px;를 의미한다. grow, shrink를 자동으로 채워준다.

- [x] flex: 1; 이것은 grow: 1, shrink: 1, basis: 0%를 의미한다.

- [x] 자주 쓰는 값들의 조합(잘 쓰이진 않지만, 다른 사람들이 이렇게 작성했을 경우 이해할 수 있어야 한다)
  - flex: 0 0 auto;
    - flex: none;
  - flex: 1 1 auto;
    - flex: auto;
  - flex: 0 1 auto;
    - flex: initial;
  - flex: 1 1 100px;
    - flex: ?
    
- [x] **flex-flow**
  - flex-direction, flex-wrap의 축약형이다.
    - flex-flow: "flex-direction" || "flex-wrap"
    - 기본값은 flex-flow: row nowrap;
  - Flex의 Line을 결정한다. 컨테이너에 적용한다.
    
## Flex의 정렬 방법
- [x] Main 축은 justify-content
  - flex-start
  - flex-end
  - center
  - space-between
    - 끝 여백이 없고 중간 여백은 
  - space-around
    - 끝 여백이 다르고 중간 여백은 동일
  - space-evenly (반응형에서 많이 사용)
    - 완전 여백이 동일
    - margin: auto를 통해 나머지 여백을 활용 가능
    
- [x] Cross 축은 align-items
  - flex lines마다 정렬을 한다.
  - 높이가 100%가 아니라 여분이 있을 경우
  - stertch (기본값) 
    - 아이템들이 박스의 높이를 따라간다
  - flex-start
    - 아이템들이 박스의 높이를 따라가지 않고 해당 컨텐트의 높이를 따라간다. 그리고 박스 위쪽에 붙는다.
  - flex-end
    - 아이템들이 박스의 높이를 따라가지 않고 해당 컨텐트의 높이를 따라간다. 그리고 박스 아래쪽에 붙는다.
  - center
    - 아이템들이 컨텐트의 높이를 따르고 가운데 수직 정렬한다.
      
- [x] align-content
  - flex line을 무시하고 패킹해버린다
    
- [x] align-self
  - 컨테이너가 아닌 아이템에 속성을 부여한다. 해당 아이템만 적용되는 정렬 기법이다.

## 컨텐트 블록 꾸미기
- [x] inline-block
  - block 속성을 컨텐트가 갖고 있는 크기 만큼으로 변경한다.
  - 한 줄에 여러 개의 block 속성을 쓸 수 있다.

## 폰트(Font)
- [x] font-family
  - 여러 개를 콤마로 구분해서 사용가능. 우선순위임
- [x] font-size
- [x] font-style
- [x] font-weight
- [x] color

## 텍스트 위치에 따라 이미지를 수직 정렬하는 방법
- [x] vertical-align
  - 텍스트 옆에 이미지가 있으면 이미지와 텍스트 배치가 맞지 않아 보인다.
  - 이를 해결하기 위해 이미지 부분에 vertical-align을 사용하면 된다. **텍스트에다 적용하는 것이 아니다.**

## 글자를 박스 가운데 수직 정렬하는 방법(한 줄일 경우)
- [x] line-height를 부모 박스의 높이와 똑같이 하면 된다.

## 포지셔닝
- [x] position: absolute;
  - relative가 부모에 적용되면 부모기준으로, 부모가 relative가 아니면 전체화면 기준
- [x] position: relative;
  - 얘의 위치에 따라 absolute 위치가 결정된다.
- [x] position: static;
  - 고정값이므로 left, top 등 적용이 되지 않음
- [x] position: fixed;
  - 헤더를 고정할 때 많이 사용하는데 컨텐츠를 가림
- [x] position: sticky;
  - fixed가 컨텐츠를 가리는 문제를 해결하기 위해 
  
## Table 
- [x] tr에는 border가 먹히지 않는다.
- [x] table 태그에 border-collapse: collapse; 속성을 주면 왼쪽 방과 오른쪽 방이 뭉개진다.
  - 디폴트는 border-collapse: seperate;
- [x] border-spacing: <length> <length>
  - 테이블에서만 사용하는 margin 기능 
- [x] table-layout: fixed
  - 테이블의 기본적인 레이아웃 방식은 **컨텐츠가 커지면 td도 같이 늘어난다.** 이를 방지하기 위함
  - 컨텐츠가 커지면 td의 너비는 고정되고 컨텐츠가 밖으로 나간다.
  - table 태그에 적용시켜야 한다.
  
## transition, transform, translate
- [x] transition은 부여한 시간 동안 천천히 움직이게 한다.
- [x] tranform은 rotate 등 속성이 있다.
- [x] translate는 포지셔닝을 하지않고 아이템들이 x, y방향으로 움직일 수 있도록 한다.
```css
.box {
    width: 200px;
    height: 100px;
    background: blue;
    transition: transform 1s, border-radius 5s; /* transform은 1초, border-radius는 5초에 걸쳐 변경된다 */
}

.box:hover {
    border-radius: 20px;
    transform: rotate(90deg);
    transform-origin: right top; /* 회전축을 가운데가 아닌 오른쪽 상단으로 변경 */
}
```
## object-fit
- [x] 새로 나온 css 문법
- object-fit: fill;
  - 이미지를 부모 컨테이너에 꽉 채우기(이미지가 늘어지는것을 감안하고)


## 이벤트 
- [x] Event Notification(Capturing)과 Event Bubbling이 있다.
  - ul > li > img 가 있다고 하자. 그리고 ul과 img에 클릭 이벤트가 각각 걸려있다고 하자.
  - 기본적인 동작은 img를 누르면 Notification 과정에서는 부모의 이벤트가 걸리지 않고 최하단인 img의 이벤트에 클릭이벤트가 걸리고 버블링이 되면서 부모의 클릭이벤트가 동작한다.
  - 지금은 자식 -> 부모 순이지만 이러한 순서를 뒤집으려면 addEventListener('click', function() {});을 사용해야 한다. 그리고 세 번째 인자에 true를 주면 순서가 바뀐다.

## 이벤트 버블링
- [x] 이벤트는 부모로 버블링된다.
  - 부모에 이벤트를 걸고 클릭을 하면 자식에게 걸린다. 자식이 이벤트를 받으면 버블링으로 인해 부모로 이벤트를 전달한다. 
  - 예를들어 ul > li > img 가 있다고 하자. ul에 클릭 이벤트를 걸고 클릭을 했을 때 다음과 같다.
    - event.target은 이벤트를 유발하는 객체를 찾는다. (ul)
    - event.currentTarget은 이벤트를 처리하고 있는 객체를 찾는다. (li)
  - 그런데 실수로 li를 누를수도 있으니 이를 방지하기 위해 e.target.nodeName != 'IMG'가 아니면 return을 해준다.
- [x] 이벤트 버블링에 대한 문제와 해결 방법(부모, 자식 간의 서로 다른 이벤트를 각각 갖고 있을 때 발생)
  - 자식에 e.stopPropagation()을 걸어준다.
- [x] onclick과 addEventListener('click')의 차이
  - onclick은 이벤트가 누적된다.
  - addEventListener는 이벤트가 갱신된다.
    - 세 번째 인자를 사용할 수 있다. 기본값은 false이다.
    - 세 번째 인자는 Notification(Capturing)의 순서를 바꿔준다.
## preventDefault
- [x] a태그를 만들어서 이벤트 타겟을 사용할 경우 a태그의 기본행위(드래그, 링크클릭 등)을 막는 행위
  - 또는 submit 버튼의 기본 행위를 막는 것
- [x] 예전에는 return false를 하면 preventDefault행위와 비슷하게 동작을 했다. 근데 이건 너무 옛날이기 때문에 좋지 않다. 
    
## Ajax(블로그에 남겨놓음)
- [x] Ajax 순서는 다음과 같다. (동기화일 때)
  - var request = XMLHttpRequest();
  - request.open();
  - 세번째 인자는 비동기를 뜻하는데 기본값은 true이다.
  - request.send();
  - reuqest.responseText;
  
- [x] request.open의 세번째 인자가 true이면 비동기인데 순서대로 실행되지는 않는다.
  - 비동기는 통지 또는 위임을 해야하는데 자바스크립트에서는 **위임** 방식을 사용한다.
  - 위임할 때 사용하는 함수 function() { if(request.readyState == 4) ~~ }는 **콜백함수**이다.
    - 서버로부터 받아온 데이터를 사용할때는 readyState가 3 또는 4일때이다. 3은 데이터가 미완성일 수도 있으므로 4를 사용하는 것이 좋다.

- [x] request.onreadystatechange 말고 request.onload를 쓰면 if문으로 request.readyState를 확인할 필요없이 데이터가 잘 로드된 이후에 콜백함수가 실행된다.

- cross origin ?
