# Array vs ArrayList vs LinkedList

세 자료구조를 한 문장으로 정의하면 아래와 같이 말할 수 있다.

https://camo.githubusercontent.com/30d51427a6a8b40896aa70554a9db341f5b4742815dc334ab435b95d360b84dc/68747470733a2f2f74312e6461756d63646e2e6e65742f6366696c652f746973746f72792f393935453636333935423143464437443130

https://camo.githubusercontent.com/6ad98d232096eb764e6feb58d6fa0716791502d3c9534fb366fd615405d70f1e/68747470733a2f2f74312e6461756d63646e2e6e65742f6366696c652f746973746f72792f393932353041333435423143464436393043

- **Array**는 index로 빠르게 값을 찾는 것이 가능함
- **LinkedList**는 데이터의 삽입 및 삭제가 빠름
- **ArrayList**는 데이터를 찾는데 빠르지만, 삽입 및 삭제가 느림

좀 더 자세히 비교하면?

우선 배열(Array)는 **선언할 때 크기와 데이터 타입을 지정**해야 한다.

```
int arr[10];
String arr[5];
```

이처럼, **array**은 메모리 공간에 할당할 사이즈를 미리 정해놓고 사용하는 자료구조다.

따라서 계속 데이터가 늘어날 때, 최대 사이즈를 알 수 없을 때는 사용하기에 부적합하다.

또한 중간에 데이터를 삽입하거나 삭제할 때도 매우 비효율적이다.

4번째 index 값에 새로운 값을 넣어야 한다면? 원래값을 뒤로 밀어내고 해당 index에 덮어씌워야 한다. 기본적으로 사이즈를 정해놓은 배열에서는 해결하기엔 부적합한 점이 많다.

대신, 배열을 사용하면 index가 존재하기 때문에 위치를 바로 알 수 있어 검색에 편한 장점이 있다.

이를 해결하기 위해 나온 것이 **List**다.

List는 array처럼 **크기를 정해주지 않아도 된다**. 대신 array에서 index가 중요했다면, List에서는 순서가 중요하다.

크기가 정해져있지 않기 때문에, 중간에 데이터를 추가하거나 삭제하더라도 array에서 갖고 있던 문제점을 해결 가능하다. index를 가지고 있으므로 검색도 빠르다.

하지만, 중간에 데이터를 추가 및 삭제할 때 시간이 오래걸리는 단점이 존재한다. (더하거나 뺄때마다 줄줄이 당겨지거나 밀려날 때 진행되는 연산이 추가, 메모리도 낭비..)

그렇다면 **LinkedList**는?

연결리스트에는 단일, 다중 등 여러가지가 존재한다.

종류가 무엇이든, **한 노드에 연결될 노드의 포인터 위치를 가리키는 방식**으로 되어있다.

> 단일은 뒤에 노드만 가리키고, 다중은 앞뒤 노드를 모두 가리키는 차이

이런 방식을 활용하면서, 데이터의 중간에 삽입 및 삭제를 하더라도 전체를 돌지 않아도 이전 값과 다음값이 가르켰던 주소값만 수정하여 연결시켜주면 되기 때문에 빠르게 진행할 수 있다.

이렇게만 보면 가장 좋은 방법 같아보이지만, `List의 k번째 값을 찾아라`에서는 비효율적이다.

array나 arrayList에서 index를 갖고 있기 때문에 검색이 빠르지만, LinkedList는 처음부터 살펴봐야하므로(순차) 검색에 있어서는 시간이 더 걸린다는 단점이 존재한다.

따라서 상황에 맞게 자료구조를 잘 선택해서 사용하는 것이 중요하다.

## REFERENCE

---

- [https://github.com/gyoogle/tech-interview-for-developer/blob/master/Computer Science/Data Structure/Array vs ArrayList vs LinkedList.md](https://github.com/gyoogle/tech-interview-for-developer/blob/master/Computer%20Science/Data%20Structure/Array%20vs%20ArrayList%20vs%20LinkedList.md)
