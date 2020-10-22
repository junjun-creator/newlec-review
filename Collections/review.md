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
---
## 컬렉션(Collection)
- [x] **컬렉션**은 *가변 길이 저장소*이다. 길이에 신경쓸 필요가 없다.
- [x] **열거 서비스**는 *인덱스를 사용하지 않고 반복적으로 꺼내는 서비스* next()/hasNext()
- [x] **반복자**란 *스레드에 안전한 열거 서비스를 제공하기 위한 열거 객체*
- [x] **forEach 구문**은 *컬렉션을 순회해주는 반복구조*
```java
while (list.hasNext()) 
    System.out.println(list.next());
```
---
## 컬렉션의 종류
- [x] Set
  - 별도의 key가 없고 **값**이 식별자이다.
  - 중복 허용 X
  - Set을 구현하고 있는 클래스 중 HashSet을 주로 사용하고 내부적으로 튜닝할 때 Linked, Abstract 등 골라서 사용한다.
  - Set은 Collection<E>와 Iterable<E> 부모들을 갖고 있다.
  - Set은 특별한 위치의 값을 꺼낼 수 없다. 이터레이터나 forEach문을 사용해 꺼내야 한다.
- [x] List
  - 
- [x] Map

```java
Set set = new HashSet();
List list = new ArrayList();
Map map = new HashMap();
		
set.add("Haha");
set.add(3);
set.add(3);
set.add(3.0);
	
for (Object o : set)
    System.out.println(o);
		
list.add("Haha");
list.add(3);
list.add(3);
list.add(3.0);
		
System.out.println(list.get(2));
		
map.put("번호", 1);
map.put("제목", "오늘의 시작은 콜렉션~!!");
		
// key를 통째로 가져오기
for (Object key : map.keySet()) {
    // key만 출력
    //System.out.println(key);
			
    // key를 통해 value를 가져오기
    System.out.println("key: " + key + " value: " + map.get(key) );
}
		
// value를 통째로 가져오기
for (Object value : map.values())
System.out.println(value);
```
---
## 열거 서비스로 인한 쓰레드의 안전성 문제
