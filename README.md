기관명 : 하이미디어컴퓨터학원  
강사명 : 박용우 강사님  
날짜   : 2020.09.01 ~ 2021.02.16(예정)  

---
자료 저장소입니다

---
09.18  
String은 불변하는 성격을 갖고 있다.  
String a = "hello";  
String b = a;  
b = "hi";를 하면 a가 바뀌지 않는다. 왜?  
String은 불변하는 성격이기때문. 그래서 새로운 "hi"문자열이 heap 영역에 만들어지고 b가 그것을 가리킨다.  
그럼 아예 원본을 못바꾸나요? replace 함수가 있는데?  
replace 함수는 원본을 사본으로 바꾸어서 만드는 것. 원본은 그대로 메모리에 남아있다.  
계속 replace를 남발하면 사본이 계속 남아서 메모리 낭비가 되는건가요?  
No. 사본이 필요없어지면 가비지가 되어 가비지콜렉터에 의해 사라진다.
