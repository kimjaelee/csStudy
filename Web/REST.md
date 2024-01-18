# REST
> **Representational State Transfer, 자원을 이름으로 구분하여 해당 자원의 상태를 주고받는 모든 것을 의미.**
1. HTTP URL를 통해 자원을 명시하고,
2. HTTP Method를 통해
3. 해당 자원에 대한 CRUD Operation을 적용하는 것을 의미

<br>

### ⚙ 구성요소

---

- _자원(Resource) : HTTP URI_
- _자원에 대한 행위(Verb) : HTTP Method_
- _자원에 대한 행위의 내용 (Representations) : HTTP Message Pay Load_

<br>

### ⚙ **REST의 특징**

---

1. _Server-Client (서버-클라이언트 구조)_
2. _Stateless (무상태)_
3. _Cacheable (캐시 처리 가능)_
4. _Layered System (계층화)_
5. _Uniform Interface (인터페이스 일관성)_

<br>

### ⚙ **REST의 장단점**

---

**장점**

- _HTTP 프로토콜의 인프라를 그대로 사용하므로 REST API 사용을 위한 별도의 인프라 구축 불필요_
- _HTTP 프로토콜의 표준을 최대한 활용하여 여러 추가적인 장점을 함께 가져갈 수 있음_
- _HTTP 표준 프로토콜에 따르는 모든 플랫폼에서 사용이 가능_
- _Hypermedia API의 기본을 충실히 지키면서 범용성을 보장_
- _REST API 메시지가 의도하는 바를 명확하게 나타내므로 의도하는 바 쉽게 파악 가능_
- _여러 가지 서비스 디자인에서 생길 수 있는 문제를 최소화_
- _서버와 클라이언트의 역할을 명확하게 분리_

**단점**

- _표준이 존재하지 않아 정의가 필요_
- _HTTP Method 형태가 제한적_
- _브라우저를 통해 테스트할 일이 많은 서비스라면 쉽게 고칠 수 있는 URL보다 Header 정보의 값을 처리해야 하므로 전문성이 요구됨_
- _구형 브라우저에서 호환이 되지 않아 지원해주지 못하는 동작이 존재함 (익스폴로어)_

<br>
<br>

### **REFERENCE**

---

- [https://khj93.tistory.com/entry/네트워크-REST-API란-REST-RESTful이란](https://khj93.tistory.com/entry/%EB%84%A4%ED%8A%B8%EC%9B%8C%ED%81%AC-REST-API%EB%9E%80-REST-RESTful%EC%9D%B4%EB%9E%80)
