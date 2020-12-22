## 자바스크립트의 개념
- 자바스크립트에서 사용되는 대표적인 API는 사용자 입/출력이다.
- Document 객체를 사용하여 동적으로 웹 페이지를 바꿀 수 있다.
- Window 객체를 사용하여 웹 브라우저를 제어할 수 있다.

## Array
- [x] push, pop
- [x] shift, unshift
  - shift는 맨 앞에 요소 뽑기
  - unshift는 맨 앞 인덱스에 요소 넣기
- [x] indexOf
- [x] splice
  - splice(i)
    - 배열의 i번째 인덱스부터 끝까지 삭제
  - splice(i, j)
    - 배열의 i번째 인덱스부터 j개 삭제
  - splice(i, j, k)
    - 배열의 i번째 인덱스부터 j개를 지우고 i번째 인덱스에 k라는 값을 삽입
    
## eval()
```javascript
var code = "var x = 30;";
eval(code);
console.log(x); // 30

///////////////////////////////////////////////////////////////
var json = '{"kor": 30, "eng": 40, "math": 60}';
//eval("var exam = " + json + ";"); // eval은 복잡하고 보안에 취약해 JSON.parse를 사용한다.
var exam = JSON.parse(json);

///////////////////////////////////////////////////////////////////
var notices = [
    {id: 1, title: "JS란 무엇인가?"},
    {id: 2, title: "JSON"},
    {id: 3, title: "어떻게 사용해?"},
]
var json JOSN.stringify(notices);
console.log(json);
```

## for in, for of
- [x] 다루고자 하는 대상이 **배열**인 경우
  - for in문은 배열의 index를 뽑는다.
  - for of문은 배열의 원소를 뽑는다.
- [x] 다루고자 하는 대상이 **객체**인 경우
  - for in문은 객체의 key를 뽑는다.
  - for of문도 마찬가지로 객체의 key를 뽑는다.
  
## 전역변수
- 전역공간에서 var a = 1;을 하든 a = 1;을 하든 똑같다.
  - window.a라는 의미이다. window가 생략되어 있음.
  
## 함수선언식과 함수표현식
- [x] 함수 선언식(**선언적 함수**라고도 한다)
```javascript
function 함수명() {
    실행문;
}
```
- [x] 함수 표현식(**익명 함수**라고도 한다)
```javascript
var 변수 = function() {
    실행문;
}
```
- [x] 함수선언식과 함수표현식은 호이스팅 부분에서 차이가 있다.
  - 함수 선언식(선언적 함수)은 어떠한 지점에서 함수 호출이 가능하다.
    ```javascript
    compute(); // 호이스팅에 의해 정상적으로 호출된다.
    function compute() {
        console.log('선언적 함수');
    }
    compute(); // 정상적으로 호출된다.
    ```
  - 함수 표현식(익명 함수)은 변수 선언 이후에 호출해야 한다.
    ```javascript
    compute(); // 에러발생
    var compute = function() {
      console.log('익명 함수');
    }
    compute(); // 정상적으로 호출된다.
    ```
- [x] 함수 표현식은 함수 선언식과 비교했을 때 변수를 다른 함수의 인자로 넘길 수 있다(**콜백 함수**) 는 장점이 있다.

## 클로저(Closure) - 녹화 참고
- [x] 클로저는 함수가 대상이다.

## setTimeout, setInterval, setClear
- setTimeout은 사용자가 ms 단위로 설정한 초를 기준으로 딱 한 번만 실행하는 함수이다.
- setInterval은 사용자가 ms 단위로 설정한 초를 기준으로 반복 실행하는 함수이다.
- clearInterval은 setInterval로부터 timer id값을 받아 이를 종료시키면 interval을 종료시킬 수 있는 함수이다.

## opener, open
- html에서 open을 통해 동적으로 링크를 연결할 수 있다.
- 링크를 여는 부모 입장은 opener가 된다. 그래서 자식 입장에서 opener.document.getElement~ 메서드를 사용하여 조작할 수 있다.

## Inner Frame
- 문서를 고립화하기 위해 사용하는 영역
- InnerFrame 바깥은 parent로 칭한다.

## Node
- [x] childNodes
  - 텍스트까지 포함한다. 그래서 childNodes보다는 엘리먼트만 가리키는 children을 사용하는 것이 좋다.

## 노드 생성, 삭제, 교체
- [x] 생성
  - append는 appendChild와 다르게 생성까지해주면서 부모에 꽂아준다.
- [x] 삭제
  - removeChild
  - remove
- [x] 교체
  - replaceChild
  - replaceWith
    - 둘다 엘리먼트를 바꾸는게 아니라 덮어씌우는 것이다.


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
