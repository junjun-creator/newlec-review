## 인터넷이란?
- Inter network의 약자로 네트워크들을 연결시켜주는 기술

## 웹이란?
- 하이퍼텍스트로 요청하는 문서를 전달하는 서비스

## HTML 3요소
- 컨텐츠
  - 문장 / 표 / 목록 / 폼
- 구조
- 스타일

## 메타 데이터
- 데이터를 위한 데이터(데이터를 설명하는 데이터)

## 시맨틱 태그
- <div id="header"></div> -> <header></header>

## 블록태그와 인라인태그
  - 블록태그는 너비, 높이 지정 가능 -> 무엇을 담기 위한 박스의 용도
  - 인라인태그는 너비, 높이 지정이 불가능 -> 컨텐츠끼리 구분하기 위한 용도
  
## 브라우저마다 달라서 쓰면 안되는 input 속성들
- https://developer.mozilla.org/ko/docs/Web/HTML/Element/Input 여기에서 Spec 부분에 Html5 써있는 것들은 쓰면 안되는 것들(자바스크립트를 이용하자)

## 정규표현식
- ^01[01678]-\d{3,4}-\d{4}$ 
  - 휴대폰 번호 

## CSS
- [x] [MDN 참고 링크](https://developer.mozilla.org/ko/docs/Web/CSS/Reference)
  - header > h1(자식 결합자)
    - header 자식만 선택
  - header h1(자속 결합자)
    - header 자식 뿐만 아니라 자손까지
  - A + B(인접 형제 결합자)
  - A ~ B(일반 형제 결합자)

- [x] 우선순위
  - id -> 속성 지정 -> class -> 태그
- [x] 속성을 갖고있는지 가지고 있지 않는지 판단하는 법
  - h1[class]
    - class 속성을 갖고 있는 h1 태그만 선택한다.
- [x] ul에 blue, li에 red를 먹이면 콕 집은 li가 우선순위가 더 높다
- [x] h1[lang="ko"] vs .h1 중에 왼쪽의 우선순위가 더 높다(태그가 클래스보다 우선순위가 낮지면 콕 집었기 때문에 더 높다)