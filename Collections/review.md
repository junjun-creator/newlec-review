## 래핑과 클래스
- [x] Object 클래스가 존재하는 이유가 무엇일까?
  - 모든 것을 참조할 수 있어야 하는 최상위 자료구조가 필요(공통 자료형이 필요)
  - Object는 만능 참조형이다.
  - Object 배열을 통해 자료형이 다른 모든 것들을 한 번에 담을 수 있다.
```java
Object[] data = new Object[10];
    data[0] = "ssdfs";
    data[1] = 3;
    data[2] = 'd';
    data[3] = 1.5;
    data[4] = "vvvvvv";
```
```java
Object obj = new Exam(); // 가능하다
Object obj = 3; // 3은 값이기 때문에 불가능하다.
```
- [x] 박싱(Boxing)
  - Object obj = 3;이 불가능하므로 과거에는 Object x = new Integer(3);으로 해결을 했다.
    - Integer는 새로 생긴 클래스로 원시형(기본형)을 담아낼 수 있는 클래스이다.
    - 현재 JDK 버전에서는 Object x = 3; 하면 에러가 안난다. 왜냐하면 자동으로 박싱을 해주기 때문이다. 그래서 우리는 Object x = 3; 이런식으로 써야 한다.
    - Integer x = 3;과 int x = 3; 중에 전자가 메모리가 더 많이 먹는다. 내부적으로 new Integer(3);을 생성하므로.
- [x] 언박싱(UnBoxing)

## 컬렉션의 열거 서비스
```java
while (list.hasNext()) 
    System.out.println(list.next());
```

## 열거 서비스로 인한 쓰레드의 안전성 문제
