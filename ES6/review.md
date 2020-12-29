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

## Spread Syntax
- [x] 배열을 쉽게 복사할 수 있다.
```javascript
let array1 = [1, 2, 3, 4, 5, 6, 7, 8];
let array2 = [...array1];            // [1, 2, 3, 4, 5, 6, 7, 8]
let array3 = [...array1, 9, 10];     // [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
let array4 = [...array1, ...array2]; // [1, 2, 3, 4, 5, 6, 7, 8, 1, 2, 3, 4, 5, 6, 7, 8];
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
const {name, age} = student;

//==================== 배열 ===================
const animals = ['dog', 'cat'];

// 기존방식
const dog = animals[0];
const cat = animals[1];

// ES6 방식
const [dog, cat] = animals;
```









