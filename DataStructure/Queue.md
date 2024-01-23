# Queue

---

### 입력과 출력을 한 쪽 끝(front, rear)으로 제한

### FIFO (First In First Out, 선입선출) : 가장 먼저 들어온 것이 가장 먼저 나옴

**_언제 사용?_**

버퍼, 마구 입력된 것을 처리하지 못하고 있는 상황, BFS

큐의 가장 첫 원소를 front, 끝 원소를 rear라고 부름

큐는 **들어올 때 rear로 들어오지만, 나올 때는 front부터 빠지는 특성**을 가짐

접근방법은 가장 첫 원소와 끝 원소로만 가능

데이터 넣음 : enQueue()

데이터 뺌 : deQueue()

비어있는 지 확인 : isEmpty()

꽉차있는 지 확인 : isFull()

데이터를 넣고 뺄 때 해당 값의 위치를 기억해야 함. (스택에서 스택 포인터와 같은 역할)

이 위치를 기억하고 있는 게 front와 rear

front : deQueue 할 위치 기억

rear : enQueue 할 위치 기억

### 기본값

```
private int size = 0;
private int rear = -1;
private int front = -1;

Queue(int size) {
    this.size = size;
    this.queue = new Object[size];
}
```

### enQueue

```
public void enQueue(Object o) {

    if(isFull()) {
        return;
    }

    queue[++rear] = o;
}
```

enQueue 시, 가득 찼다면 꽉 차 있는 상태에서 enQueue를 했기 때문에 overflow

아니면 rear에 값 넣고 1 증가

### deQueue

```
public Object deQueue(Object o) {

    if(isEmpty()) {
        return null;
    }

    Object o = queue[front];
    queue[front++] = null;
    return o;
}
```

deQueue를 할 때 공백이면 underflow

front에 위치한 값을 object에 꺼낸 후, 꺼낸 위치는 null로 채워줌

### isEmpty

```
public boolean isEmpty() {
    return front == rear;
}
```

front와 rear가 같아지면 비어진 것

### isFull

```
public boolean isFull() {
    return (rear == queueSize-1);
}
```

rear가 사이즈-1과 같아지면 가득찬 것

---

일반 큐의 단점 : 큐에 빈 메모리가 남아 있어도, 꽉 차있는것으로 판단할 수도 있음

(rear가 끝에 도달했을 때)

이를 개선한 것이 **'원형 큐'**

논리적으로 배열의 처음과 끝이 연결되어 있는 것으로 간주함!

원형 큐는 초기 공백 상태일 때 front와 rear가 0

공백, 포화 상태를 쉽게 구분하기 위해 **자리 하나를 항상 비워둠**

```
(index + 1) % size로 순환시킨다

```

### 기본값

```
private int size = 0;
private int rear = 0;
private int front = 0;

Queue(int size) {
    this.size = size;
    this.queue = new Object[size];
}
```

### enQueue

```
public void enQueue(Object o) {

    if(isFull()) {
        return;
    }

    rear = (++rear) % size;
    queue[rear] = o;
}
```

enQueue 시, 가득 찼다면 꽉 차 있는 상태에서 enQueue를 했기 때문에 overflow

### deQueue

```
public Object deQueue(Object o) {

    if(isEmpty()) {
        return null;
    }

    front = (++front) % size;
    Object o = queue[front];
    return o;
}
```

deQueue를 할 때 공백이면 underflow

### isEmpty

```
public boolean isEmpty() {
    return front == rear;
}
```

front와 rear가 같아지면 비어진 것

### isFull

```
public boolean isFull() {
    return ((rear+1) % size == front);
}
```

rear+1%size가 front와 같으면 가득찬 것

원형 큐의 단점 : 메모리 공간은 잘 활용하지만, 배열로 구현되어 있기 때문에 큐의 크기가 제한

이를 개선한 것이 '연결리스트 큐'

### 연결리스트 큐는 크기가 제한이 없고 삽입, 삭제가 편리

### enqueue 구현

```
public void enqueue(E item) {
    Node oldlast = tail; // 기존의 tail 임시 저장
    tail = new Node; // 새로운 tail 생성
    tail.item = item;
    tail.next = null;
    if(isEmpty()) head = tail; // 큐가 비어있으면 head와 tail 모두 같은 노드 가리킴
    else oldlast.next = tail; // 비어있지 않으면 기존 tail의 next = 새로운 tail로 설정
}
```

> 데이터 추가는 끝 부분인 tail에 한다.기존의 tail는 보관하고, 새로운 tail 생성큐가 비었으면 head = tail를 통해 둘이 같은 노드를 가리키도록 한다.큐가 비어있지 않으면, 기존 tail의 next에 새로만든 tail를 설정해준다.

### dequeue 구현

```
public T dequeue() {
    // 비어있으면
    if(isEmpty()) {
        tail = head;
        return null;
    }
    // 비어있지 않으면
    else {
        T item = head.item; // 빼낼 현재 front 값 저장
        head = head.next; // front를 다음 노드로 설정
        return item;
    }
}
```

> 데이터는 head로부터 꺼낸다. (가장 먼저 들어온 것부터 빼야하므로)head의 데이터를 미리 저장해둔다.기존의 head를 그 다음 노드의 head로 설정한다.저장해둔 데이터를 return 해서 값을 빼온다.

이처럼 삽입은 tail, 제거는 head로 하면서 삽입/삭제를 스택처럼 O(1)에 가능하도록 구현이 가능하다.

## REFERENCE

---

- [https://github.com/gyoogle/tech-interview-for-developer/blob/master/Computer Science/Data Structure/Stack %26 Queue.md](https://github.com/gyoogle/tech-interview-for-developer/blob/master/Computer%20Science/Data%20Structure/Stack%20%26%20Queue.md)
