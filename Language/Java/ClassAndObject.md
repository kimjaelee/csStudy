# 클래스와 객체
> 객체의 이해<br>
> 객체란 우리 주변의 모든것(사물, 사람 등)을 의미한다. 객체들은 자신만으 고유한 특성, 행동을 가지며 다른 객체들에게 행동을 요청하거나, 정보를 주고받는 등 상호작용하며 존재한다. <br>
> #### _객체 지향 언어는 실세계의 객체를 프로그램 내 표현하기 위해 **클래스**와 **객체** 개념을 도입했다._

<br>

# 객체 지향 언어의 특성
## 1. 캡슐화 (Encapsulation)
객체를 캡슐로 싸 내부를 보호하고 볼 수 없게 하는 것. 객체의 가장 본질적 특성이다. 외부와의 접촉을 위해 몇 부분만 공개 노출한다.

```Class```라는 캡슐을 사용하고, ```필드(멤버변수)```와 ```메소드(멤버 함수)```로 구성된다.
    
## 2. 상속 (Inheritance)
_자식 클래스가 부모 클래스의 속성을 물려받고 기능을 추가하여 확장(extends)하는 개념이다.<br>_

ㄴ부모 클래스 : super Class<br>
ㄴ자식 클래스 : sub Class<br>

코드 재사용성 증가 👉 코드 작성에 드는 시간, 비용 절감
    
## 3. 다형성 (Polymorphism)
_같은 이름의 메소드가 클래스 혹은 객체에 따라 다르게 동작하도록 구현하는 것을 의미한다._ <br>

```오버라이딩(overriding)```, ```오버로딩(overloading)```

<br>

## 객체 지향 언어의 목적
 - 절차 지향 언어의 단점을 보완하고 다음의 목적을 달성하기 위해 탄생했다.
> 1. 소프트웨어 생산성 향상 👉 코드 재사용 및 부분 수정 등
> 2. 실세계에 대한 쉬운 모델링 👉 요소의 객체화 및 객체간 상호작용의 표현을 통한 효과적 프로그래밍

<br>

---

<br>

# 클래스 구성
 - 필드
 - 메소드
 - ```new``` 연산자
 - 래퍼런스 변수

## 접근 지정자
 - ```public```
 - ```protected```
 - ```default```
 - ```private```

## 생성자

## ```static``` 멤버
- static 멤버 (클래스 멤버)
- non-static 멤버 (인스턴스 멤버)
- 전역 변수와 전역 함수
- ```static``` 메소드 제약 조건
  - static 메소드는 static 멤버만 접근 가능 (static 메소드는 객체 없이도 존재하기 때문에, 객체와 함께 생성되는 non-static멤버를 사용할 수 없다.)
  - static 메소드는 this 사용 불가

## ```final``` 클래스, 필드


## ```this```, ```this()```

## ```super```, ```super()```

## ```overloading```, ```overriding```

<br>
<br>

## **REFERENCE**
- Java Programming (생능출판, 황기태/김효수)
