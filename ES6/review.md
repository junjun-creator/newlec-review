## let, const
- [x] let은 변수명 중복 해결, 지역화 해결
- [x] const는 값을 재할당 하지 못하도록 막는다.

## template String
- [x] escape 구문(ex. \n 등)을 쓰고 싶다면 String.raw를 붙인다.

## Enhanced Object Literal Syntax
- [x] 변수를 가지고 속성을 정의하던 방식이 개선
```javascript
let kor = 30;
let eng = 40;
let math = 50;
let exam = {kor, eng, math}; // 이렇게 표현이 가능하다.
```
- [x] 객체가 함수를 포함하는 식이 편해졌다.
```javascript
let exam = {
    kor: 30,
    eng: 40,
    math: 50,
    total() {
        return kor + eng + math; (X)
        return this.kor + this.eng + this.math; (O)
    }
}
```

## Destructuring Assignment
- [x] 객체, 배열을 쉽게 할당할 수 있다.
```javascript
//=================== 객체====================
const student {
    name: 'jaehee',
    age: 26
};

// 기존 방식
const name = student.name;
const age = student.age;

// ES6 방식
const {name, age, total = 0} = student; // 'jaehee', 26, 0

// 도중에 name, age가 바뀐다면? 괄호를 감싸주자!
student.name = 'minsu';
student.age = 30;

({name, age} = student); // 'minsu', 30

// 별칭도 가능하다.
let {name: studentName, age: studentAge} = student;
console.log(`name: ${studentName}, age: ${studentAge}`); // 'jaehee', 26

//==================== 배열 ===================
const animals = ['dog', 'cat'];

// 기존방식
const dog = animals[0];
const cat = animals[1];

// ES6 방식
const [dog, cat] = animals;
```

## Collections
Set, Map


## REST Parameter
- [x] 자바스크립트에서 함수의 매개변수는 별칭이다.
  - 함수에 전달되는 값은 arguments라는 컬렉션이 받는다.
```javascript
function print(x, y, ...rest) {
    console.log(x);
    console.log(y);
    console.log(rest);
    console.log(rest.length);
}
print(1, 2, 3, 4, 5, 6);
```


## Spread Operator
- [x] 배열을 쉽게 복사할 수 있다.
```javascript
let array1 = [1, 2, 3, 4, 5, 6, 7, 8];
let array2 = [...array1];            // [1, 2, 3, 4, 5, 6, 7, 8]
let array3 = [...array1, 9, 10];     // [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
let array4 = [...array1, ...array2]; // [1, 2, 3, 4, 5, 6, 7, 8, 1, 2, 3, 4, 5, 6, 7, 8];
```
- [x] 함수를 호출할 때 대신 뽀개기를 해준다.
```javascript
function print(x, y, z) {
    console.log(x);
    console.log(y);
    console.log(z);
}

let nums = [2, 4, 5];
print(nums); 이렇게 넘길 수 없다.
print(nums[0], nums[1], nums[2]); 이렇게 넘기는 것보다 print(...nums); 이렇게 넘길 수 있다.
```

## Default Value
```javascript
{
    console.log('===================Default Value===================');
    
    function add(x = 0, y = 0) { // 고수
        // if (x == null || x == undefined)   // 하수
            // x = 0;

        // x = x || 0;          // 중수
        // y = y || 0;

        return x + y;

        //let temp = 3 || null; --> 3
        //let temp = undefined || 0 || null || 3;  --> 3

        // console.log(temp);
    }


    function getValue() {
        return 20;
    }

    function add2(x = 1, y = getValue()) {
        return x + y;
    }

    console.log(add()); // 0
    console.log(add2()); // 21
}
```


## Arrow Function
- [x] 화살표 함수가 필요한 이유는?!
  - No this, No arguments, No super, No new.target !!!
  - 일반적인 function은 지역화가 가능하지만, 화살표 함수는 지역화가 없다.
  
```javascript
{
    window.addEventListener("load", () => {
        console.log("loaded");
    });

    let nums = [13, 23, 3, 5, 19, 45];

    nums.sort(function(x, y) {return x - y});   // 오름차순( [3, 5, 13, 19, 23, 45] )
    nums.sort((x, y) => x - y);                 // 오름차순( [3, 5, 13, 19, 23, 45] )
}
```

## OOP
- [x] class 키워드로 객체를 생성하면 비교 가능하다.(같은 형식인지)
- [x] function 키워드로 객체를 생성하면 비교가 불가능하다.
```javascript
// 구버전 방식
function Exam(kor, eng, math) {
    this.kor = kor;
    this.eng = eng;
    this.math = math;

    this.total = function() {
        return this.kor + this.eng + this.math;
    }
}

var exam = new Exam(10, 10, 10);
var exam1 = new Exam(20, 20, 20);

console.log(typeof exam); // object
console.log(`total is ${exam.total()}`); // 30
console.log(exam.total === exam1.total); // === : 참조하고 있는 대상이 같은지 비교 (false출력)
```
```javascript
// 구버전 방식
function Exam(kor, eng, math) {
    this.kor = kor;
    this.eng = eng;
    this.math = math;
}

// 이것도 가능하고
Exam.prototype.total = function() {
    return this.kor + this.eng + this.math;
}

// 이것도 가능하다.
Exam.prototype = {
    total: function() {
        return this.kor + this.eng + this.math;
    }
}

var exam = new Exam(10, 10, 10);
var exam1 = new Exam(20, 20, 20);

console.log(exam.total === exam1.total); // true출력
```
- [x] 위 내용의 문제점은 private 키워드가 존재하지 않기 때문에 캡슐화가 되지 않았다.

- [x] 클래스를 사용한 예시
```javascript
// 새로운 클래스 정의
{
    console.log('================새로운 OOP 방식===============');
    class Exam {
        // private으로 사용할 키워드는 미리 선언해야 한다.
        #kor; 
        #eng;
        #math;
        static count = 0;

        constructor(kor = 0, eng = 0, math = 0) {
            this.#kor = kor;
            this.#eng = eng;
            this.#math = math;

            Exam.count++;
        }

        get count() {
            return Exam.count;
        }

        get kor() {
            return this.#kor;
        }

        set kor(v) {
            this.#kor = v;
        }

        get eng() {
            return this.#eng;
        }

        set eng(v) {
            this.#eng = v;
        }

        get math() {
            return this.#math;
        }

        set math(v) {
            this.#math = v;
        }

        #tot() {
            return 10000000;
        }

        total() {
            return this.#kor + this.#eng + this.#math;
        }
    }

    Exam.count = 30;

    var exam = new Exam(10, 10, 10);
    //exam.#kor = 100; // 에러난다
    console.log(`kor: ${exam.kor}`); // getter 사용
    exam.kor = 100; // setter 사용
    console.log(`kor: ${exam.kor}`); // getter 사용
    console.log(exam.total());


    // 상속
    class NewlecExam extends Exam {
        #com;
        constructor(kor, eng, math, com) {
            super(kor, eng, math);
            this.#com = com;
        }
    }

    let exam2 = new NewlecExam(1, 1, 1, 1);
    console.log(`exam2.kor: ${exam2.kor}`);
    console.log(`exam2.total: ${exam2.total()}`);


    console.log('');
}
```

## apply, call, new.target
- [x] apply는 객체만 전달
- [x] call은 객체와 매개변수도 전달
  - call은 쌩둥맞은 객체를 넘겨서 전달해도 출력이 잘된다. 이는 버그를 유발할 수도 있으며 이를 방지하기 위해서 instanceof를 사용한다.
- [x] new.target을 출력했을 때 true가 나오면 해당 객체는 new 연산자로 만들어진 것이다. false라면 해당 객체는 new로 만들어지지 않았다.(버그를 유발할 수 있음)
  - static / instance(instanceof) / constructor(new.target) 
```javascript
function Alert(selector) { // 객체니까 그냥 호출되면 안된다.
    this.section = document.querySelector(selector);
    this.btn1 = this.section.querySelector('input');
    this.span = this.section.querySelector('div');

    this.btn1.onclick = this.btn1Click;
    this.x = 30;
}

Alert.prototype = {
    btn1Click: function() {
        //this.span.innerHTML = 'Hello';
        console.log('aa');
    },
    test: function(a, b) {
        console.log(`x: ${this.x}, a: ${a}`);
    }
}

{
    window.addEventListener('load', function() {
        let alert = new Alert('.s1');
        alert.test(3); // x: 30, a: 3
        let onclick = alert.test; // 함수 위임
        onclick(3); // 호출 (x: undefined, a: 3)
        onclick.apply(alert); // x: 30, a: undefined
        onclick.call(alert, 4); // x: 30, a: 4

        let obj = {x: 1000, y: 3000};
        onclick.call(obj, 5); // 쌩둥맞은 객체를 인자로 넣어도 작동이 잘된다.
    });
}
{
    function Exam(kor, eng, math) {
        console.log(this instanceof Exam);
        
        // function의 3가지 종류에 따른 체크 사항과 무기
        // static / instance(instanceof) / constructor(new.target)
    }
}
```

## Iterator & Generator
```javascript
// iterator를 너희는 한 줄의 코드도 없이 구현하게 해주겠다. 나의 이름은 제너레이터.
// Generator : iterator를 구현해주는 기능, 도구 (function *)
    
let data = [20, 10, 23, 4, 45, 6];

// 제너레이터로 이터레이터를 구현하는 예제
function *iterator() {
    for (let i = 0; i < data.length; i++)
        yield data[i];
}

let it = iterator();
// it.next() : {value: ?, done: ?}

let result = it.next();
while (!result.done) {
    console.log(result.value);
    result = it.next();
} 
```

## Symbol
- [x] 심볼이 만들어진 이유는?
  - 심볼은 고유값을 만들어낸다. so what?
    - 자바스크립트는 태생이 다형성이다. 다형성은 일부 코드를 다른 코드로 대체하면 : 함수로 꽂아서
```javascript
// ------- Symbol --------
{
    console.log('================Symbol===============');

    let print2 = Symbol('print'); // 인자를 비워도되고 써도된다. 설명 느낌?

    class A {
        constructor() {

        }

        print() {
            console.log('일반적인 함수의 print');
        }

        [print2]() {
            console.log('심볼 함수의 print');
        }
    }

    class B {
        constructor() {

        }

        print() {
            console.log('일반적인 함수의 print');
        }

        [print2]() {
            console.log('심볼 함수의 print');
        }
    }

    console.log(A.prototype.print === B.prototype.print); // false (각각의 print함수가 다르므로)
    console.log(A.prototype.print2 === B.prototype.print2); // true (유니크한 심볼을 참조하고 있으므로)
```
- [x] 현재 위의 예시에서는 심볼을 지역변수로 사용하고 있다. 하지만, 심볼은 전역에서도 사용할 수 있다.
  - Symbol.for()로 선언하면 된다.
  
  
  
## Promise
- [x] 자바스크립트에서 비동기 작업의 성공, 실패 여부를 알려준다
- [x] pending, fulfilled, rejected
```javascript
{
    console.log('================Promise===============');

    // 비동기식2 : promise를 이용한 비동기
    function getNotice(id) {
        console.log('promise 비동기식 get 요청이 이루어졌습니다.');

        return new Promise(resolve => {
            // 3초 후 다음로직을 실행함
            setTimeout(function() {
                let notice = {id: 1, title: "title 1", content: "hehe"};
                resolve(notice);
                console.log('resolve: ', resolve);
            }, 3000);
        });
        
    }

    // aa는 promise 객체 {then: ~, catch: ~, 등}가 담긴다. promise state도 담긴다(fulfilled, rejected ...)
    let aa = getNotice(2); 
    console.log('aa: ', aa);

    // then에는 콜백함수를 넣어준다. 콜백 지옥을 벗어났으니 보기 깔끔하다.
    aa.then(function(notice) {
        console.log(notice.title);
    });

    console.log('메인스레드는 계속 된다,');

    /*
    // 비동기식 getNotice 요청
    function getNotice(id, callback) {
        console.log('비동기식 get 요청이 이루어졌습니다.');

        // 3초 후 다음로직을 실행함
        setTimeout(function() {
            let notice = {id: 1, title: "title 1", content: "hehe"};
            callback(notice);
        }, 3000);
    }

    let notice = getNotice(2, function(notice) {
        console.log(notice.title); // 결과값을 가져오면 실행한다.
    });

    console.log('메인스레드는 계속 된다,');
    */



    /*
    // 동기식 getNotice 요청
    function getNotice(id) {
        console.log('동기식 get 요청이 이루어졌습니다.');

        return {id: 1, title: "title 1", content: "hehe"};
    }

    let notice = getNotice(2); // 리턴이 될 때까지 멈춰있는 상태가 된다.(오랜 시간을 먹는 함수라 가정)
    console.log(notice.title);

    console.log('메인스레드는 계속 된다,');
    */
    console.log('');
}
```
