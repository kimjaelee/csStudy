---

> 파라미터 타입이나 리턴 타입에 대한 정의를 외부로 미룸
타입에 대해 유연성과 안정성을 확보
**런타임 환경에 아무런 영향이 없는 컴파일 시점의 전처리 기술**
> 

>> 타입을 유연하게 처리, 런타임에 발생할 수 있는 타입 에러를 컴파일 전에 검출할 수 있다.

>> **데이터 형식에 의존하지 않고, 하나의 값이 여러 다른 데이터 타입들을 가질 수 있도록 하는 방법**

## 대중적인 통상적 선언

| 타입 | 설명 |
| --- | --- |
| <T> | Type |
| <E> | Element |
| <K> | Key |
| <V> | Value |
| <N> | Number |

## 제네릭의 특징

1. 클래스 혹은 메소드에 선언할 수 있다
2. 동시에 여러 타입을 선언할 수 있다
3. 와일드 카드를 이용해 타입에 대해 유연한 처리를 가능하게 한다
4. 제네릭 선언 및 정의 시에 타입의 상속관계를 지정할 수 있다

## 제네릭 사용법

## 1. **클래스 혹은 메소드에 선언할 수 있다.**

### 클래스에 제네릭 파라미터를 선언하는 방법 *(클래스 인스턴스화 시점에서 제네릭 파라미터를 통해 타입 전달)*

- 인스턴스애서 타입을 공유할 경우에 사용되며, 컬렉션에서 자주볼수 있는 유형이다.
사용법은 클래스 우측에 제네릭 파라미터를 선언한다.

```java
**class** **Sample<**T**>** **{
	private** T anonyTypeData**;
}**
```

### 메소드에 제네릭 파라미터 선언하는 방법 *(메소드 수행 시점에서 파라미터 타입과 비교하여 타입 전달)*

제네릭 타입이 메소드 호출시점에 결정되야 할 경우 사용되며, 파라미터 타입에 따라 제네릭 타입이 결정되기 때문에 다이나믹한 처리를 가능케 한다.

사용법은 메소드의 반환타입 앞부분에 제네릭 파라미터를 선언한다.

```java
 */**
  *
  * @param supplier java8의 함수형 인터페이스중 하나로 구현시점에 리턴값을 결정하며 타입이 정의된다.
  * @param <T> test2메소드 호출시 전달받을 타입 파라미터로 supplier의 반환타입이자 test2의 반환타입으로 정의한다.
  * @return
  */*
**public** **<**T**>** T **test2(Supplier<**T**>** supplier**){
	System.**out**.**println**(**"supplier 인터페이스의 반환타입에 따라서 test2의 반환타입이 결졍된다."**);
	return** supplier**.**get**();
}**
```

## 2. 동시에 여러 타입을 선언할 수 있다.

### 제네릭 파라미터를 정의하는곳에 콤마를 기준으로 여러 타입을 선언하여 사용이 가능하다

```java
*/**
 *
 * @param p Function 메소드에서 소비될 P타입의 인자이다.
 * @param function Function 제네릭 인자의 첫번째 타입의 파라미터를 소비하여 두번째 타입의 리턴값을 반환한다.
 * @param <P> Function 메소드의 소비 파라미터 타입으로 정의한다.
 * @param <R> Function 메소드의 리턴 타입으로 정의한다. test메소드의 리턴타입으로 정의한다.
 * @return
 */*
**public** **<**P**,** R**>** R **test(**P p**,** **Function<**P**,** R**>** function**){
	return** function**.**apply**(**p**);
}

class** **AnonyMap<**K**,** V**>** **implements** **Map<**K**,** V**>{
	....
}**
```

## 3. 와일드 카드를 이용해 타입에 대해 유연한 처리를 가능하게 한다

**와일드 카드는 대입연산 수행시 유연한 처리를 돕는다.**

JAVA 컴파일러는 대입연산을 수행할 때 left-value의 제네릭타입과 right-value의 제네릭타입이 정확하게 일치하지 않을 경우 컴파일 에러를 발생시킨다. 하지만, 와일드 카드를 사용한다면 컴파일러가 유연하게 대처하도록 할 수 있다.

```java
@Test**public** **void** **test(){List<String>** example **=** **new** **ArrayList<>();**
method1**(**example**);** *// 제네릭 타입이 일치하지 않기 때문에 컴파일 에러 발생*
method2**(**example**);** *// 모든 제네릭 타입을 허용하기 때문에 컴파일 에러 없음***}
public** **void** **method1(List<Object>** param**){**    *// List의 제네릭타입으로 Object만 허용한다.
	// ...*
**}
public** **void** **method2(List<?>** param**){**    *// List의 제네릭타입으로 모든 타입을 허용한다.
	// ...*
**}**
```

method2처럼 제네릭 타입을 와일드 카드로 모든 타입에 대하여 허용하게 될 경우 param의 제네릭은 최상위 클래스인 Object로 정의되기 때문에 메소드 내부에서 특정 타입으로 캐스팅하여야 된다는 단점이 존재한다. 그래서 JAVA는 제네릭 파라미터 대입 연산시 left-value와 right-value간의 캐스팅이 가능하도록 **super** 와 **extends** 라는 키워드로 지원하고 있다.

## 4. 제네릭 선언 및 정의 시에 타입의 상속관계를 지정할 수 있다

1. **제네릭 타입 정의시 상속관계를 명시하는 방법** (와일드카드를 사용한다)
    
    ```java
    *// List의 제네릭 인자를 Runnable을 상속받은 모든 타입에 대하여 허용하도록 정의*
    **public** **void** **method4(List<?** **extends** **Runnable>** param**){
    	for(Runnable** runnable **:** param**){**
    		runnable**.**run**();
    	}
    }**
    
    @FunctionalInterface**interface** **RunnableWrapp1** **extends** **Runnable** **{
    void** **_run();**
    
    @Override**default** **void** **run()** **{
    	System.**out**.**println**(**"====== BEFORE ======"**);**
    	_run**();
    	System.**out**.**println**(**"====== AFTER  ======"**);}
    }**
    
    @Test**public** **void** **test4(){
    	List<RunnableWrapp1>** list1 **=** **new** **ArrayList<>();**
    	list1**.**add**(()->** **System.**out**.**println**(**"run1"**));**
    	list1**.**add**(()->** **System.**out**.**println**(**"run2"**));**
    	list1**.**add**(()->** **System.**out**.**println**(**"run3"**));**
    	method4**(**list1**);**
    
    	*/**********************
    	      * ====== BEFORE ======
    	      * run1
    	      * ====== AFTER  ======
    	      * ====== BEFORE ======
    	      * run2
    	      * ====== AFTER  ======
    	      * ====== BEFORE ======
    	      * run3
    	      * ====== AFTER  ======
    	      **********************/*
    **}
    
    class** **AnotherSample** **{}
    
    class** **AnotherSampleChild** **extends** **AnotherSample** **{}
    
    class** **AnotherSampleChildOfChild** **extends** **AnotherSampleChild** **{}***// List의 제네릭 인자를 AnotherSampleChild 클래스의 상위클래스만 허용토록 정의*
    
    **public** **void** **genericSample(List<?** **super** **AnotherSampleChild>** list**){**
    	*/****************************************************************************************
    	 * list 의 제네릭 와일드카드는 AnotherSampleChild 클래스의 상위 클래스이기 때문에
    	 * JAVA 컴파일러가 타입을 특정할 수 없기 때문에 list의 반환 요소타입은 Object로 추론한다.
    	 * **************************************************************************************/*
    	**Object** a **=** list**.**get**(**0**);**
    	list**.**add**(new** **AnotherSampleChild());AnotherSampleChild** b **=** list**.**get**(**0**);** *// 컴파일 에러 발생*
    **}**
    
    	@Test**public** **void** **test5(){
    	List<AnotherSample>** sample1 **=** **new** **ArrayList<>();
    	List<AnotherSampleChild>** sample2 **=** **new** **ArrayList<>();
    	List<AnotherSampleChildOfChild>** sample3 **=** **new** **ArrayList<>();
    	List<Runnable>** sample4 **=** **new** **ArrayList<>();**
    	genericSample**(**sample1**);**
    	genericSample**(**sample2**);**
    	genericSample**(**sample3**);** *// sample3의 리스트 타입은 AnotherSampleChildOfChild 이며, AnotherSampleChild의 상위 클래스가 아니기 때문에 컴파일 에러가 발생한다.*
    	genericSample**(**sample4**);** *// sample4의 리스트 타입은 Runnable 이며, 마찬가지로 AnotherSampleChild의의 상위 클래스가 아니기 때문에 컴파일 에러가 발생한다.*
    **}**
    ```
    
2. **제네릭 타입 선언시 상속관계를 명시하는 방법**
    
    ```java
     */**
      *
      * @param number T 타입의 인자
      * @param <T> Number를 상속받은 어떤 타입을 T로 정의한다.
      */*
    **public** **<**T **extends** **Number>** **void** **test6(**T number**){
    	System.**out**.**println**(**number**.**intValue**());
    }**
    
    @Test**public** **void** **test6(){**
    	test6**(**100**);**test6**(**200.912**);**
    	test6**(**100L**);**test6**(BigDecimal.**valueOf**(**1234.948**));**
    
    */*****************
          * 100
          * 200
          * 100
          * 1234
          *****************/*
    **}**
    ```
    

## **REFERENCE**

---

- http://www.tcpschool.com/java/java_generic_concept
- https://st-lab.tistory.com/153
- https://jehuipark.github.io/java/java-generic
