# Stream
> 배열 또는 컬렉션 인스턴스에 저장된 데이터를 꺼내 파이프에 흘려보낸다.
> **스트림은 중간 연산과 최종 연산을 조합하여 데이터를 처리하기 위한 편리하고 유연한 구조를 제공하는데, 중간 연산과 최종 연산을 조합하여 원하는 결과를 얻을 수 있다.** 이러한 연산들은 스트림에 대한 ***파이프라인**을 구성합니다.

<br>

| 중간연산 | - 마지막이 아닌 위치에서 진행이 되어야 하는 연산 <br>- 중간 연산은 스트림의 요소를 변환하거나 필터링하는 등의 작업을 수행<br>- 이러한 연산들은 스트림을 리턴하며, 여러 개의 중간 연산이 연속적으로 체이닝될 수 있음 <br>- 중간 연산들은 지연 연산의 특성을 가짐. <br> 즉, 중간 연산이 호출되어도 실제로 처리되지 않고, 최종 연산이 호출될 때에만 중간 연산이 수행됨 |
| :---: | :--- |
| **최종연산** | **- 마지막에 진행이 되어야 하는 연산 <br> - 최종 연산 시 스트림의 처리를 시작하고, 최종 결과를 생성하거나 반환 <br> - 최종 연산이 호출되어야 중간 연산이 실제로 수행되며, 최종 연산이 한 번 호출되면 스트림은 소비되어 재사용할 수 없음 <br> - 예시: forEach, toArray, reduce, collect, sum, min, max 등** |

<br>

## 예제

```java
public class stream {
	
	public static void main(String[] args) {
		int [] ar = {1, 2, 3, 4, 5};
		
		int sum = Arrays.stream(ar)		// 스트림 생성
				.filter(n -> n%2 == 1)	// filter 통과
				.sum();					// sum을 통과시켜 그 결과를 반환
		
		System.out.println(sum);
	}
	
}
```

`public static InStream stream(int[] array)`

`IntStream filter(InPredicate predicate)`

filter와 sum 메소드는 InStream 인스턴스의 메소드이다.

스트림 연산은 “지연 처리” 방식으로 동작하는데, 위 예제에서는 sum이 호출될 때까지 filter의 호출 결과는 스트림에 반영되지 않는다.

💡 **즉 스트림의 중간 연산은 최종 연산이 호출되기 전까지 실행되지 않는다. 따라서 `filter`를 포함한 중간 연산들은 최종 연산이 호출되면서 동작하며, 최종 결과를 생성한다.** 중간 연산을 통해 걸러진 값들은 최종 연산에 의해 처리되어야 실제로 나타납니다.


_*지연처리 : 우선순위가 낮거나 나중에 처리해도 큰 지장이 없는 작업을 대기시켰다가 컴퓨터의 작업량이 많지 않을 때 처리하도록 하는 일_


<br>

## 예제 더 보기

```java
class StringStream {
    public static void main(String[] args) {
        String[] names = {"YOON", "LEE", "PARK"};
        
        // 스트림 생성
        Stream<String> stm = Arrays.stream(names);
        
        // 최종 연산 진행
        stm.forEach(s -> System.out.println(s));
    }
}
```

<br>
<br>

## **REFERENCE**
- [https://velog.io/@new_wisdom/Java-스트림#스트림의-중간-연산](https://velog.io/@new_wisdom/Java-%EC%8A%A4%ED%8A%B8%EB%A6%BC#%EC%8A%A4%ED%8A%B8%EB%A6%BC%EC%9D%98-%EC%A4%91%EA%B0%84-%EC%97%B0%EC%82%B0)
