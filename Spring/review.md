## spring-boot
- [x] 톰캣을 설치할 필요가 없다.
- 웹개발하기 위한 환경을 신경쓸 필요가 없다.
- starter << 얘가 jdbc, jsp 등에 필요한 라이브러리를 다 함축하고 있다.
- config에 대한 설정을 할 필요없다.


## Annotation
- [x] @RestController
  - /api/notice/와 같이 데이터를 가공해서 보낼때 사용되는 컨트롤러
  - JSON 형식으로 변환하지 않아도 알아서 return할때 변환해준다.

- [x] @Controller
  - 뷰가 사용되는 컨트롤러
  - JSP를 return하는 경우에만 사용한다.

## REST(Representational state transfer)
