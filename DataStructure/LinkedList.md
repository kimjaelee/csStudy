# Linked List

---

https://camo.githubusercontent.com/4416c7dfefc1120916c907b28647273c19b2172960f9630a00a76a49338e0ce4/68747470733a2f2f7777772e6765656b73666f726765656b732e6f72672f77702d636f6e74656e742f75706c6f6164732f67712f323031332f30332f4c696e6b65646c6973742e706e67

연속적인 메모리 위치에 저장되지 않는 선형 데이터 구조

(포인터를 사용해서 연결된다)

각 노드는 **데이터 필드**와 **다음 노드에 대한 참조**를 포함하는 노드로 구성

**왜 Linked List를 사용하나?**

> 배열은 비슷한 유형의 선형 데이터를 저장하는데 사용할 수 있지만 제한 사항이 있음
>
> 1. 배열의 크기가 고정되어 있어 미리 요소의 수에 대해 할당을 받아야 함
> 2. 새로운 요소를 삽입하는 것은 비용이 많이 듬 (공간을 만들고, 기존 요소 전부 이동)

**장점**

> 동적 크기삽입/삭제 용이

**단점**

> 임의로 액세스를 허용할 수 없음. 즉, 첫 번째 노드부터 순차적으로 요소에 액세스 해야함 (이진 검색 수행 불가능)포인터의 여분의 메모리 공간이 목록의 각 요소에 필요

노드 구현은 아래와 같이 데이터와 다음 노드에 대한 참조로 나타낼 수 있다

```java
// A linked list node
struct Node
{
  int data;
  struct Node *next;
};
```

**Single Linked List**

노드 3개를 잇는 코드를 만들어보자

```
      head         second         third
        |             |             |
        |             |             |
    +---+---+     +---+---+     +----+----+
    | 1  | o----->| 2 | o-----> |  3 |  # |
    +---+---+     +---+---+     +----+----+
```

[소스 코드](https://github.com/gyoogle/tech-interview-for-developer/blob/master/Computer%20Science/Data%20Structure)

**노드 추가**

- 앞쪽에 노드 추가

```java
void push(struct Node** head_ref, int new_data){
    struct Node* new_node = (struct Node*) malloc(sizeof(struct Node));

    new_node->data = new_data;

    new_node->next = (*head_ref);

    (*head_ref) = new_node;
}
```

- 특정 노드 다음에 추가

```java
void insertAfter(struct Node* prev_node, int new_data){
    if (prev_node == NULL){
        printf("이전 노드가 NULL이 아니어야 합니다.");
        return;
    }

    struct Node* new_node = (struct Node*) malloc(sizeof(struct Node));

    new_node->data = new_data;
    new_node->next = prev_node->next;

    prev_node->next = new_node;

}
```

- 끝쪽에 노드 추가

```java
void append(struct Node** head_ref, int new_data){
    struct Node* new_node = (struct Node*)malloc(sizeof(struct Node));

    struct Node *last = *head_ref;

    new_node->data = new_data;

    new_node->next = NULL;

    if (*head_ref == NULL){
        *head_ref = new_node;
        return;
    }

    while(last->next != NULL){
        last = last->next;
    }

    last->next = new_node;
    return;

}
```

- 소스코드

  ```java
  class LinkedList
  {
      Node head;

      class Node
      {
          int data;
          Node next;
          Node(int d) {data = d; next = null; }
      }

      public void push(int new_data)
      {
          Node new_node = new Node(new_data);

          new_node.next = head;

          head = new_node;
      }

      public void insertAfter(Node prev_node, int new_data)
      {
          if (prev_node == null)
          {
              System.out.println("The given previous node cannot be null");
              return;
          }

          Node new_node = new Node(new_data);

          new_node.next = prev_node.next;

          prev_node.next = new_node;
      }

      public void append(int new_data)
      {
          Node new_node = new Node(new_data);

          if (head == null)
          {
              head = new Node(new_data);
              return;
          }

          new_node.next = null;

          Node last = head;
          while (last.next != null)
              last = last.next;

          last.next = new_node;
          return;
      }

      public void printList()
      {
          Node tnode = head;
          while (tnode != null)
          {
              System.out.print(tnode.data+" ");
              tnode = tnode.next;
          }
      }

      public static void main(String[] args)
      {
          LinkedList llist = new LinkedList();

          //6->NUllist
          llist.append(6);

          // 7->6->NUllist
          llist.push(7);

          // 1->7->6->NUllist
          llist.push(1);

          // 1->7->6->4->NUllist
          llist.append(4);

          // 1->7->8->6->4->NUllist
          llist.insertAfter(llist.head.next, 8);

          System.out.println("\nCreated Linked list is: ");
          llist.printList();
      }
  }
  ```

## REFERENCE

---

- [https://github.com/gyoogle/tech-interview-for-developer/blob/master/Computer Science/Data Structure/Linked List.md](https://github.com/gyoogle/tech-interview-for-developer/blob/master/Computer%20Science/Data%20Structure/Linked%20List.md)
