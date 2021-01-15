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
