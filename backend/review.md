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
