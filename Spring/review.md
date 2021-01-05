## 스프링과 스프링 부트의 차이점
- [x] 스프링 부트는 스프링 + 부트이다.
  - 부트를 포함시키면 

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

## IoC
- [x] 객체가 만들어지는 순서는 상관이 없지만, 객체가 조립되어지는 방향ㅇ
스프링은 객체 생성과 인젝션을 도와준다.

## DI
- [x] 데이터의 결합관계를 설정의 변경으로 
- [x] 부품을 조립하는 용어를 Dependency Injection(DI)라 한다.
  - 설정만 바꾸면 다른 객체로 바꿔 끼

## Model(model)이 어떻게 동작되는가
- 우리가 매개변수에 Model이든 뭐든 넣어주면 프론트 컨트롤러가 그것을 알아서 인식한다.
- 그래서 우린 그냥 Model model만 넣어놓고 사용하면 된다.

## mybatis
