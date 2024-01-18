# Spring MVC Framework

> 스프링 MVC 프레임워크가 동작하는 원리를 이해하자

### MVC 패턴의 특징

---

- Spring은 DI나 AOP같은 기능뿐만 아니라, Servlet 기반의 WEB 개발을 위한 MVC 프레임워크를 제공한다.
- Spring MVC는 Model2 아키텍처와 Front Controller 패턴을 Framework 차원에서 제공한다.
- Spring MVC 프레임워크는 Spring을 기반으로 하고 있기 때문에 Spring이 제공하는 Transaction처리나 DI 및 AOP등을 손쉽게 사용가능하다.

### MVC 패턴의 장단점

---

- 장점
  - 화면과 비즈니스 로직을 분리해서 작업 가능.
  - Model, View, Controller 영역별 개발로 인하여 확장성이 뛰어나다.
- 단점
  - 개발과정이 복잡해 초기 개발 속도가 늦다.

![Spring MVC 요청 흐름](../resources/springMVC.png)
Spring MVC 요청 흐름

![MVC Model2(Web MVC) 요청 흐름](../resources/springMVC2.png)
MVC Model2(Web MVC) 요청 흐름

### Spring MVC의 실행순서

---

1. DispatcherServlet이 요청을 수신한다.
   - 단일 Front Controller Servlet
   - 요청을 수신하여 처리를 다른 컴포넌트에 위임한다.
   - 어느 Controller에 요청을 전송할지 결정한다.
2. DispatcherServlet은 Handler Mapping에 어느 Controller를 사용할 것인지 문의한다.
   - URL과 Mapping 한다.
3. DispatcherServlet은 요청을 Controller에게 전송하고 Controller는 요청을 처리한 후 결과를 리턴한다.
   - Business Logic을 수행하고 결과 정보(Model)가 생성되어 JSP와 같은 view에서 사용된다.
4. ModelAndView Object에 수행결과가 포함되어 DispatcherServlet에 리턴된다.
5. ModelAndView는 실제 JSP 정보를 갖고 있지 않으며, ViewResolver가 논리적 이름을 실제 JSP 이름으로 변환한다.
6. View는 결과정보를 사용하여 화면을 표현한다.

### Spring MVC의 구성요소

---

1. DispatcherServlet(Front Controller)
   - 모든 클라이언트의 요청을 전달받는다.
   - Contrller에게 클라이언트의 요청을 전달하고, Controller가 리턴 한 결과값을 View에게 전달하여 알맞은 응답을 생성한다.
2. HandlerMaping
   - 클라이언트의 요청 URL을 어떤 Controller가 처리할지를 결정한다.
   - URL과 요청 정보를 기준으로 어떤 핸들러 객체를 사용할지 결정하는 객체이며, DispatcherServlet은 하나 이상의 핸들러 매핑을 가질 수 있다.
3. Controller
   - 클라이언트의 요청을 처리한 뒤, Model을 호출하고 그 결과를 DispatcherServlet에 알려준다.
4. ModelAndView
   - Controller가 처리한 데이터 및 화면에 대한 정보를 보유한 객체를 말한다.
5. ViewResolver
   - Controller가 리턴 한 View 이름을 기반으로 Controller의 처리 결과를 보여줄 View를 결정한다.
6. View

   - Controller의 처리결과를 보여줄 응답화면을 생성한다.

   ### **REFERENCE**

   ***

   - [https://velog.io/@alkwen0996/Spring-MVC-패턴의-특징과-요청흐름](https://velog.io/@alkwen0996/Spring-MVC-%ED%8C%A8%ED%84%B4%EC%9D%98-%ED%8A%B9%EC%A7%95%EA%B3%BC-%EC%9A%94%EC%B2%AD%ED%9D%90%EB%A6%84)
