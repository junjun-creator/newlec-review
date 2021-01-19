## ES6와 Babel의 차이
- [x] 

## HTML과 JSX의 차이
- [x] JSX는 단일태그일 경우 반드시 /으로 닫아줘야한다.
  - ex) <input />
```javascript
let root = document.querySelector('#root');

// element 내부는 JSX영역이다.
// element ~ ReactDom.render까지 전체는 Babel 영역이다.
const element = (
    <div>
        <h1>Hello, World!</h1>
        <h2>It is {new Date().toLocaleTimeString()}.</h2>
    </div>
);

ReactDOM.render(element, root);
```
## 특징
- [x] 단방향(one way) mvc는 지원하지만 양방향(two way) mvc는 지원하지 않는다.
- [x] 단방향 방식이 사용자의 입력이 쏟아지는 것에 유리하다.

## 컴포넌트란?

## props란?

## state란? 사용하는 이유는?
- [x] 


## 리액트의 라이프사이클
- [x] constructor 생성자는 아직 화면에 뿌려지기 전에 실행되는 것이다. 즉, 화면이 뜨기 전에 초기화할 것은 여기서 작업한다.
- [x] componentDidMount()
  - render된 후 (화면에 뜬 후) 실행되는 함수
  - 딱 한 번만 실행된다. setInterval 함수를 실행해도 마찬가지이다.
- [x] componentWillUnmount()
  - 화면에서 사라진 후 실행되는 함수
