## 객체지향 프로그래밍의 특징
* [x] 객체지향 프로그래밍은 **프로그래밍의 기본 단위를 객체로 바라보고 이를 중심으로 프로그래밍을 구성하는 것**
- **캡슐화**는 데이터구조와 기능을 묶는 것을 의미한다.
  - 데이터는 변수를 의미하고 기능은 메서드를 의미한다.
- **은닉화**(캡슐의 은닉화)는 캡슐이 깨져나가는 것을 막는 도구이다.
  - private, getters, setters
---
## 상속의 종류
* [x] 상속은 has a 상속 관계와 is a 상속 관계로 나뉜다.
- has a 상속 관계는 클래스에 private 키워드(아니어도됨)로 선언된 변수들, 즉 부품들을 의미한다.
- is a 상속 관계는 extends 키워드로 상속받은 것을 의미한다.

* [x] 자바에서는 참조형식의 함수보다 객체형식의 함수를 우선으로 한다.
~~~
class NewlecExam extends Exam {
    Exam exam = new NewlecExam(); // 가능
    NewlecExam exam = new Exam(); // 불가능
	
    exam.f1(); // exam이 아닌 NewlecExam 클래스의 f1 함수를 먼저 호출한다.
}
~~~
---
* [x] Service 클래스가 Entity 클래스를 조작한다. 감싼다.
