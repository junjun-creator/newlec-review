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
  
## 스프링에서 말하는 Bean 객체란?
```java
@Autowired
    ApplicationContext applicationContext;

public void example() {
    A a = new A();  // Bean 객체가 아니라 일반적인 객체이다.
    A a = applicationContext.getBean(A.class); // Bean 객체이다.
}
```
  
## IoC(Inversion of Control)
- [x] IoC란?
  - 역순으로 객체를 생성하는 것?
  - 객체가 조립되어지는 방향이 반대! 작은 부품부터 차례차례 역순으로.

## Annotation
- [x] **@Autowired**
  - 상황에 맞는 IoC 컨테이너에 들어있는 Bean을 자동으로 주입한다.
  - 스프링 setting xml에 <context:annotation-config/>을 넣어줘야 한다.
  - reuqired=false
    - 인젝션하고자 하는 객체가 없으면 null을 넣는다.
  - [x] @Autowired를 생성자에다 붙이기 (Constructor Injection)
    - 스프링 레퍼런스에서 가장 권장하는 방법이다. 필수적으로 사용해야하는 레퍼런스 없이는 해당 인스턴스를 만들 수 없도록 강제할 수 있기 때문이다. 나머지 아래의 방법은 인위적으로 해당 인스턴스를 만들 수 있다.
    - ※ 스프링 4.3부터 어떠한 클래스에 생성자가 딱 하나 뿐이고 그 생성자로 주입받는 레퍼런스 변수들이 Bean으로 등록되어 있다면 그 Bean을 자동으로 주입하도록 기능이 추가되었다. 따라서 @Autowired를 붙이지 않아도 위의 경우에는 동작한다.
  - [x] @Autowired를 필드에 붙이기 (Field Injection)
  - [x] @Autowired를 Setter에 붙이기 (Setter Injection)
    
    
- [x] **@Qualifier**
    - 인젝션하고자 하는 객체가 두 개 이상인 경우 우선순위를 설정한다.
    
- [x] **@ComponentScan("경로")**
  - 입력된 패키지 경로에서 @Component(@Service, @Controller, @Repository, @Configuration)를 찾아 bean 객체로 등록해주는 역할을 한다.
  - xml방식에서 <context:component-scan base-package="경로"/> 역할과 같다.
    
- [x] **@Component**(밑에 @Bean과 차이점 알아두기)
  - @Component를 달아주면 Bean으로 등록되기 위한 클래스(IoC 컨테이너에 저장되기 위한 클래스)를 의미한다.
  - @Bean과의 차이점은 @Component는 개발자 직접 작성한 클래스를 Bean으로 등록하기 위한 어노테이션이다.
  - 스프링 setting xml에 <context:component-scan base-package="루트부터 해당 패키지까지의 경로"/>를 넣어줘야 한다.
    - 이것을 넣어주면 <context:annotation-config/>은 없어도 된다.
    
- [x] **@Configuration**
  - 스프링은 xml방식, 어노테이션 방식이 있는데 @Configuration은 어노테이션 방식으로 사용하기 위한 것이다.
  - 얘는 스프링 IoC 컨테이너에게 해당 클래스를 Bean 구성 클래스임을 알려준다.
  - @Configuration도 @Component이기 때문에 @ComponentScan에 의해 스캔되어 @Bean으로 정의한 객체들이 IoC컨테이너 안에 담긴다.
    
- [x] **@Bean**(위의 @Component와 차이점 알아두기)
  - 1.@Bean은 개발자가 직접 제어가 불가능한 외부 라이브러리 등을 Bean으로 만들려할 때 사용된다.
  - 2.@Bean은 개발자가 작성한 메서드를 통해 반환되는 객체를 Bean으로 만들려할 때 사용된다.
  - @Bean이 달린 주체는 IoC 컨테이너에 담긴다.
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

- [x] **@RestController**
  - /api/notice/와 같이 데이터를 가공해서 보낼때 사용되는 컨트롤러
  - @ResponseBody를 사용하지 않아도 문자열을 리턴하면 그대로 문자열을 리턴한다. 뷰랑 연관짓는 것이 아니다.
  - 문자열을 JSON 형식으로 변환을 해주기도 하는데 이는 MessageConverter가 내장되어서 그렇다. annotation-driven 태그에 utf-8을 지원하는 컨버터가 있는데 그 위치에 JSON 변환 컨버터가 미리 추가되어 있기 때문이다.

- [x] **@Controller**
  - 뷰가 사용되는 컨트롤러
  - JSP를 return하는 경우에만 사용한다.
  - @Controller를 달아주면 Bean으로 등록되기 위한 클래스(IoC 컨테이너에 저장되기 위한 클래스)를 의미한다.
  - @Autowired가 붙어있는애가 @Controller가 붙어있는 클래스를 사용한다.
  
- [x] **@Service**
  - 서비스 클래스에 붙이는 어노테이션
  - @Service를 달아주면 Bean으로 등록되기 위한 클래스(IoC 컨테이너에 저장되기 위한 클래스)를 의미한다.
  - @Autowired가 붙어있는애가 @Service가 붙어있는 클래스를 사용한다.
  
- [x] **@Repository**
  - Dao를 실제로 구현하는 클래스에 붙이는 어노테이션
  - @Repository를 달아주면 Bean으로 등록되기 위한 클래스(IoC 컨테이너에 저장되기 위한 클래스)를 의미한다.
  - @Autowired가 붙어있는애가 @Repository가 붙어있는 클래스를 사용한다.

- [x] **@RequestMapping**
  - 사용자가 입력하는 url을 매핑시켜주는 어노테이션

- [x] **@PathVariable**
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

- [x] **@RequestParam**
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

- [x] **@Mapper**
  - Dao 인터페이스에 마이바티스를 직접 구현할 때 사용하는 어노테이션
  - 만약 마이바티스를 Dao 인터페이스가 아닌 구현부로 따로 뺀다면 지워야 한다.
  
- [x] **@Results**, **@Result**
  - Dao 인터페이스에 마이바티스를 직접 구현하고 DB 컬럼명과 엔티티 변수명이 다를 때 DB 컬럼명을 엔티티 변수명으로 맞춰주는 역할을 한다.
  - @Results는 @Result가 두 개 이상일 때 사용한다.
```java
@Results(value= {
    @Result(property = "writerId", column = "WRITER_ID"),
    @Result()~~
})
```
- [x] **@RequestBody**
  - @Controller를 사용하면서 뷰 페이지 단에 보내는 것이 아닌 그 자체를 넘겨줄 때 해당 메서드에 붙이는 어노테이션
  - @RestController를 사용하면 @RequestBody를 붙이지 않아도 return 값이 문자열이면 그대로 문자열을 출력한다. 뷰랑 연결되지 않는다.
  
## AOP(Aspect Oriented Programming)
- [x] AOP이란?
  - 관점 지향 프로그래밍
  - 사용자, 개발자, 운영자 등의 관점으로 어떻게 분리하고 결합시켜서 프로그래밍을 하는 방법론
  - 비즈니스 로직 = 주업무, 인프라 로직 = 곁다리 업무
  - 인프라 로직(로깅, 트랜잭션 등)을 별도로 만들고 기존 소스코드를 손대지 않고 필요에 따라 꽂았다 뺐다 할 수 있는 프로그래밍 방식
- [x] **Before Advice**
  - core concern 앞에만 필요한 인프라 로직
  - MethodBeforeAdvice 인터페이스를 구현하는 클래스를 만들어서 처리한다.
- [x] **After returnning Advice**
  - core concern 뒤에만 필요한 인프라 로직
  - AfterReturningAdvice 인터페이스를 구현하는 클래스를 만들어서 처리한다.
- [x] **After throwing Advice**
  - 예외를 처리하는 인프라 로직
  - ThrowsAdvice 인터페이스를 구현하는 클래스를 만들어서 처리한다.
- [x] **Around**
  - core concern 앞, 뒤 모두에 필요한 인프라 로직
  - MethodInterceptor 인터페이스를 구현하는 클래스를 만들어서 처리한다.

- [x] **Weaving**
  - Cross-cutting Concern이랑 Core Concern부분을 연결(뜨개질)시켜주는 과정

- [x] **JoinPoint**
  - 인프라 로직이 대상으로 삼고 있는 메서드를 조인 포인트라 한다.
  
- [x] **Point Cut**
  - 조인 포인트를 컷 하는 것
  - 특정한 메서드만 위빙하기 위해 설정할 수 있는 별도의 정보


## Model(model)이 어떻게 동작되는가
- 우리가 매개변수에 Model이든 뭐든 넣어주면 프론트 컨트롤러가 그것을 알아서 인식한다.
- 그래서 우린 그냥 Model model만 넣어놓고 사용하면 된다.

## mybatis
- [x] dao에 직접 구현하는 것과 구현 클래스, xml을 따로 두는 두 가지 방법이 있다.
  - dao에 직접 구현할 때는 @Mapper를 사용한다. @Select, @Insert, ... , @Results, @Result를 사용한다.
  - 구현 클래스, xml을 따로 둘 때는 
- [x] SqlSession 클래스
  - sql문을 실제 호출해주는 역할(필요할 때 open하고 close해줘야 함)
  - 스프링에서는 mybatis가 SqlSession을 빈으로 등록하고 유지한다.
  - Factory한테 매퍼객체 내놓으라고 명령한다.(session.getMapper(~Dao.class)) 그러면 Factory는 모든 맵퍼 객체를 반환한다
- [x] SqlSessionFactoryBuilder 클래스
  - 설정파일을 읽어서 SqlSessionFactory 객체를 생성한다.
- [x] SqlSessionFactoryFactory 클래스
  - SqlSession을 만드는 역할
