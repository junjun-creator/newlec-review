## Virtual DOM
- [x] 변화가 일어나면 실제로 브라우저의 돔에 새로운 것을 넣는 것이 아니라 자바스크립트로 이루어진 가상의 돔에 한 번 렌더링을 하고 기존의 돔과 비교한 이후 정말 변화가 필요한 부분만 업데이트를 해준다.

## HTML과 JSX의 차이
- [x] JSX는 태그가 두 개이면 반드시 하나의 태그로 감싸주어야 한다. 즉, 하나의 최상위 부모가 꼭 존재해야 한다.
  - 그런데 최상위 부모가 존재하면 개발자도구로 볼 때 불필요하게 최상위 부모태그가 나오니 보기 안좋다. 이를 해결하기 위해 리액트 v16.2부터는 <Fragment> 태그를 사용할 수 있다.
- [x] 주석 사용법
  - {/* 주석 */} 이렇게 사용해야 한다. // 또는 /* */을 그대로 사용하면 그냥 뷰에 그대로 렌더링이 된다.
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
        <input type="text" className="width" value={this.state.변수} /> // 클래스는 className, value에는 큰 따옴표를 제거해야 한다.
        <img style={{width: "100px"}} src="../../images/logo.png" />
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
