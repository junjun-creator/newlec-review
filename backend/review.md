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


## 파일 업로드
- [x] form 속성에 enctype="multipart/form-data"을 넣어준다.
  - [x] web.xml
    - 모든 서블릿에 적용된다.
  - [x] annotation(@MultipartConfig)
    - 서블릿 하나에 적용된다.
    - location
      - 지정하지 않는 것이 좋다. 왜냐하면 운영체제가 알아서 사용하는 임시 공간이 있기 때문에.
      - 그래서 보통 이 속성은 넣지 않는다.
    - fileSizeThreshold(Byte)
      - 클라이언트가 파일을 보냈을 때 저장하기 전에 잠깐 파일을 올려놓는 공간의 크기이다.
    - maxFileSize
      - 페이지에서 파일을 여러 개 선택할 수 있다.
      - 파일을 선택하는 박스가 여러 개일 수도 있다. 각각의 파일 크기의 max크기를 의미한다.
      - 예를들어 1024*1024*5 이면 각각 파일이 5메가가 넘을 수 없다.
    - maxRequestSize
      - 전체 요청할 때의 모든 파일의 크기의 합의 max크기를 의미한다.
      - 예를들어 1024*1024*5*5이면 모든 파일의 크기의 합이 25메가를 못 넘는다.
      - 어노테이션은 자바 파일이기 때문에 1024*1024*5*5처럼 곱셈 형식을 할 수 있지만, xml로 할때는 계산결과를 써야 한다.(ex. 418018841)
  - [x] 업로드한 파일을 컨트롤러에서 갖고 오기
    - request.getParameter로는 불가능하고 request.getPart("name") 또는 request.getParts()로 받아올 수 있다. 둘의 차이는 단일 파일, 다중 파일이다.
  - [x] 업로드한 파일을 저장하는 방법
    - 상대경로에 저장해야 한다. 근데 자바에서는 한 번에 상대적인 경로에 저장할 수 있는 메서드가 없다. 그래서 물리경로를 알아야 하는데 이를 알기 위해서 원하는 request.getServletContext().getRealPath("상대경로");를 넣어주면 물리경로를 String 자료형으로 뽑아낼 수 있다.
    - 
