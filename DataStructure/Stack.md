# Stack

---

입력과 출력이 한 곳(방향)으로 제한

### LIFO (Last In First Out, 후입선출) : 가장 나중에 들어온 것이 가장 먼저 나옴

**_언제 사용?_**

함수의 콜스택, 문자열 역순 출력, 연산자 후위표기법

데이터 넣음 : push()

데이터 최상위 값 뺌 : pop()

비어있는 지 확인 : isEmpty()

꽉차있는 지 확인 : isFull()

+SP

push와 pop할 때는 해당 위치를 알고 있어야 하므로 기억하고 있는 '스택 포인터(SP)'가 필요함

스택 포인터는 다음 값이 들어갈 위치를 가리키고 있음 (처음 기본값은 -1)

```
private int sp = -1;
```

### push

```
public void push(Object o) {
    if(isFull(o)) {
        return;
    }

    stack[++sp] = o;
}
```

스택 포인터가 최대 크기와 같으면 return

아니면 스택의 최상위 위치에 값을 넣음

### pop

```
public Object pop() {

    if(isEmpty(sp)) {
        return null;
    }

    Object o = stack[sp--];
    return o;

}
```

스택 포인터가 0이 되면 null로 return;

아니면 스택의 최상위 위치 값을 꺼내옴

### isEmpty

```
private boolean isEmpty(int cnt) {
    return sp == -1 ? true : false;
}
```

입력 값이 최초 값과 같다면 true, 아니면 false

### isFull

```
private boolean isFull(int cnt) {
    return sp + 1 == MAX_SIZE ? true : false;
}
```

스택 포인터 값+1이 MAX_SIZE와 같으면 true, 아니면 false

### 동적 배열 스택

위처럼 구현하면 스택에는 MAX_SIZE라는 최대 크기가 존재해야 한다

(스택 포인터와 MAX_SIZE를 비교해서 isFull 메소드로 비교해야되기 때문!)

최대 크기가 없는 스택을 만드려면?

> arraycopy를 활용한 동적배열 사용

```java
public void push(Object o) {

    if(isFull(sp)) {

        Object[] arr = new Object[MAX_SIZE * 2];
        System.arraycopy(stack, 0, arr, 0, MAX_SIZE);
        stack = arr;
        MAX_SIZE *= 2; // 2배로 증가
    }

    stack[sp++] = o;
}
```

기존 스택의 2배 크기만큼 임시 배열(arr)을 만들고

arraycopy를 통해 stack의 인덱스 0부터 MAX_SIZE만큼을 arr 배열의 0번째부터 복사한다

복사 후에 arr의 참조값을 stack에 덮어씌운다

마지막으로 MAX_SIZE의 값을 2배로 증가시켜주면 된다.

이러면, 스택이 가득찼을 때 자동으로 확장되는 스택을 구현할 수 있음

### 스택을 연결리스트로 구현해도 해결 가능

```java
public class Node {

    public int data;
    public Node next;

    public Node() {
    }

    public Node(int data) {
        this.data = data;
        this.next = null;
    }
}
```

```java
public class Stack {
    private Node head;
    private Node top;

    public Stack() {
        head = top = null;
    }

    private Node createNode(int data) {
        return new Node(data);
    }

    private boolean isEmpty() {
        return top == null ? true : false;
    }

    public void push(int data) {
        if (isEmpty()) { // 스택이 비어있다면
            head = createNode(data);
            top = head;
        }
        else { //스택이 비어있지 않다면 마지막 위치를 찾아 새 노드를 연결시킨다.
            Node pointer = head;

            while (pointer.next != null)
                pointer = pointer.next;

            pointer.next = createNode(data);
            top = pointer.next;
        }
    }

    public int pop() {
        int popData;
        if (!isEmpty()) { // 스택이 비어있지 않다면!! => 데이터가 있다면!!
            popData = top.data; // pop될 데이터를 미리 받아놓는다.
            Node pointer = head; // 현재 위치를 확인할 임시 노드 포인터

            if (head == top) // 데이터가 하나라면
                head = top = null;
            else { // 데이터가 2개 이상이라면
                while (pointer.next != top) // top을 가리키는 노드를 찾는다.
                    pointer = pointer.next;

                pointer.next = null; // 마지막 노드의 연결을 끊는다.
                top = pointer; // top을 이동시킨다.
            }
            return popData;
        }
        return -1; // -1은 데이터가 없다는 의미로 지정해둠.

    }

}
```

## REFERENCE

---

- [https://github.com/gyoogle/tech-interview-for-developer/blob/master/Computer Science/Data Structure/Stack %26 Queue.md](https://github.com/gyoogle/tech-interview-for-developer/blob/master/Computer%20Science/Data%20Structure/Stack%20%26%20Queue.md)
