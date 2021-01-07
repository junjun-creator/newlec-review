## 스프링과 스프링 부트의 차이점
- [x] 스프링 부트는 스프링 + 부트이다.
  - 부트를 포함시키면 

## spring-boot
- [x] 톰캣을 설치할 필요가 없다.
- 웹개발하기 위한 환경을 신경쓸 필요가 없다.
- starter << 얘가 jdbc, jsp 등에 필요한 라이브러리를 다 함축하고 있다.
- config에 대한 설정을 할 필요없다.

## DI(부품 조립)
- [x] DI란?
  - 의존성(종속성) 주입이다.
  - 부품 조립이라고도 한다.
- [x] DI를 하는 이유는?
  - DI를 하지 않으면 객체와 객체간의 결합력이 강하기 때문에 객체를 바꿔 끼우는 과정에서 많은 수정을 해야하는 번거로움이 있다.
- [x] DI의 종류
  - Setter Injection
  - Constructor Injection
- [x] 데이터의 결합관계를 설정의 변경으로 
- [x] 부품을 조립하는 용어를 Dependency Injection(DI)라 한다.
  - 설정만 바꾸면 다른 객체로 바꿔 끼
  
## IoC(Inversion of Control)
- [x] IoC란?
  - 역순으로 객체를 생성하는 것?
  - 객체가 조립되어지는 방향이 반대! 작은 부품부터 차례차례 역순으로.

## Annotation
- [x] @Autowired
  - 자동으로 객체를 인젝션한다.
  - 스프링 setting xml에 <context:annotation-config/>을 넣어줘야 한다.
  - reuqired=false
    - 인젝션하고자 하는 객체가 없으면 null을 넣는다.
- [x] @Qualifier
    - 인젝션하고자 하는 객체가 두 개 이상인 경우 우선순위를 설정한다.

- [x] @Component
  - 컴포넌트 어노테이션을 통해 객체를 생성할 수 있다.
  - 스프링 setting xml에 <context:component-scan base-package="루트부터 해당 패키지까지의 경로"/>를 넣어줘야 한다.
    - 이것을 넣어주면 <context:annotation-config/>은 없어도 된다.
    
- [x] @Configuration
  - 스프링은 xml방식, 어노테이션 방식이 있는데 @Configuration은 어노테이션 방식으로 사용하기 위한 것이다.
    
- [x] @ComponentScan("경로")
  - 어노테이션 방식으로 생성하고자 하는 객체가 위한 패키지명을 찾는 역할을 한다.
  - xml방식에서 <context:component-scan base-package="경로"/> 역할과 같다.
    
- [x] @Bean
  - @Bean을 달면 내가 만든 객체(return하는 객체)를 IoC 컨테이너에 넣어준다.
```java
@ComponentScan("spring.di.ui")
@Configuration
public class NewlecAppConfig {

    @Bean
    public Exam exam() { // exam은 함수명으로 보면 안된다. 명사형인 이유는 IoC 컨테이너에 담겨질 때 부여되는 이름이라 생각하자.
        return new NewlecExam(); // 리턴하는 객체는 IoC 컨테이너에 담긴다.
    }
}
```

- [x] @RestController
  - /api/notice/와 같이 데이터를 가공해서 보낼때 사용되는 컨트롤러
  - JSON 형식으로 변환하지 않아도 알아서 return할때 변환해준다.

- [x] @Controller
  - 뷰가 사용되는 컨트롤러
  - JSP를 return하는 경우에만 사용한다.
  
- [x] @Service
  - 서비스 클래스에 붙이는 어노테이션
  
- [x] @Repository
  - Dao를 실제로 구현하는 클래스에 붙이는 어노테이션

- [x] @RequestMapping
  - 사용자가 입력하는 url을 매핑시켜주는 어노테이션

- [x] @PathVariable
  - /customer/notice/detail?id=3 -> 쿼리스트링으로 값을 전달할 수도 있지만 /customer/notice/3처럼 할 수도 있다.
  - id를 후자와 같이 받아왔을 때 @PathVariable을 써줘야만 파라미터로 인식하지 않고 url에 적힌 값으로 인식한다.
```java
@RequestMapping("{id}")
public String detail(Model model, @PathVariable("id") Integer id) {
    Notice notice = service.get(id);
    model.addAttribute("n", notice);
		
    return "customer.notice.detail";
}
```

- [x] @RequestParam
  - 파라미터로 어떠한 값이 넘어오는 것을 받는 어노테이션
  - 이것의 장점은 servlet에서 하나하나 null, 공백처리를 했던 부분을 안해도 된다.
  - 또한, 파라미터로 넘어온 name을 그대로 변수로 사용하지 않고 다르게 변수를 지정할 수 있다.
```java
@RequestMapping("list")
public String list(Model model, 
    @RequestParam(name="p", defaultValue="1") int page) { // view 페이지에 데이터를 전달하기 위해서는 model을 추가한다.
		
    List<NoticeView> list = service.getViewList(1, 10, "title", "");
		
    model.addAttribute("list", list);
    return "customer.notice.list"; // 디스패처한테 리턴값을 전달한다. 포워딩을 프론트엔드 컨트롤러가 대신한다.
}
```

- [x] @Mapper
  - Dao 인터페이스에 마이바티스를 직접 구현할 때 사용하는 어노테이션
  - 만약 마이바티스를 Dao 인터페이스가 아닌 구현부로 따로 뺀다면 지워야 한다.
  
- [x] @Results, @Result
  - Dao 인터페이스에 마이바티스를 직접 구현하고 DB 컬럼명과 엔티티 변수명이 다를 때 DB 컬럼명을 엔티티 변수명으로 맞춰주는 역할을 한다.
  - @Results는 @Result가 두 개 이상일 때 사용한다.
```java
@Results(value= {
    @Result(property = "writerId", column = "WRITER_ID"),
    @Result()~~
})
```



## Model(model)이 어떻게 동작되는가
- 우리가 매개변수에 Model이든 뭐든 넣어주면 프론트 컨트롤러가 그것을 알아서 인식한다.
- 그래서 우린 그냥 Model model만 넣어놓고 사용하면 된다.

## mybatis
- [x] dao에 직접 구현하는 것과 구현 클래스, xml을 따로 두는 두 가지 방법이 있다.
  - dao에 직접 구현할 때는 @Mapper를 사용한다. @Select, @Insert, ... , @Results, @Result를 사용한다.
  - 구현 클래스, xml을 따로 둘 때는 
- [x] SqlSession
  - IoC 컨테이너에 마이바티스가 담아놓았다.
  - Factory한테 매퍼객체 내놓으라고 명령한다.(session.getMapper(~Dao.class)) 그러면 Factory는 모든 맵퍼 객체를 반환한다
