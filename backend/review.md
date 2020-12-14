## JDBC
- 드라이버 로드 -> 연결 생성 -> 문장 -> 결과집합 활용

## WAS/웹서버
- 사용자로부터(client) url 요청을 웹 서버가 받음
- 정적인 문서(html,css 등)는 웹서버에서 사용자에게 제공 가능.
- 하지만, 실행파일(.class 등)들은 제공하는 것이 아니라 이것을 실행해서 결과를 제공해줘야함.
- 이런 실행파일들을 실행할 수 있는 환경이 WAS 이다.
- 모든 실행파일(.class)들은 Server Application 이다. >> 각각의 .class들은 servlet(Server Application let[조각])이다.
- 각 servlet에서 모든 html 태그를 사용하기엔 좋은 방법이 아니다 >> 다른 방법을 배울것이다.

## PrintStream, PrinterWriter
- PrintStream
  - 영어만 지원하는 객체(문자열 출력도구)
- PrintWriter
  - 다국어 지원용 PrintSream 객체(문자열 출력도구)

## pageContext, request, session, application
- pageContext 현재 페이지에서 사용할 수 있는 저장소
- request는 두 서블릿간의 관계에서 사용할 수 있는 저장소
- session은 웹 브라우저가 종료될 때까지 사용할 수 있는 저장소
- application은 톰캣이 종료될 때까지 사용할 수 있는 저장소

## Dispatcher
- [x] forward방식은 A 서블릿이 하던 작업을 B 서블릿에게 위임하는 것(너가 대신해라)
  - 서블릿은 서블릿을 호출할 수 있다.
  - request.getRequestDispatcher("/admin/board/notice/detail.jsp").forward(request, response);
    - 위의 코드는 com.newlecture.web.controller.admin.notice에 있는 서블릿이 admin/board/notice/detail.jsp에게 request, response에 담긴 정보를 넘기는 것이다.

## DAO
- [x] 파일을 사용하는 파일 서비스라고 생각하자. 파일에서 데이터를 가져다 쓸 수 있게 해주는 것이라 생각하자. 
- [x] **DAO는 CRUD만 사용한다. open(int id), hitUp(int id)와 같은 메서드는 DAO로 넘기는 것이 아니라 서비스에서 직접 처리를 해야 한다.** 
  - **서비스는 업무! DAO는 CRUD!**
- [x] update는 전체 컬럼을 대상으로 업데이트를 한다.
  - 만약 hitUp(int id), open(int id)를 업데이트 한다면 각각 업데이트를 하는 것이 아니다.
- [x] DAO를 사용하는 이유
  1. 협업
  2. 재사용
  3. 데이터(소스)를 숨기는 것

## Service
- [x] 서비스쪽은 sql을 모른다. 그래서 DAO쪽에 데이터를 달라고 요청해야 한다.

## 데이터 딕셔너리
- [x] 오라클의 데이터를 보관하는 창고
  - 우리가 직접 사용하지 않는다.
