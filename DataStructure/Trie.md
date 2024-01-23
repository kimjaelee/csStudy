# Trie

---

> 문자열에서 검색을 빠르게 도와주는 자료구조

```
정수형에서 이진탐색트리를 이용하면 시간복잡도 O(logN)
하지만 문자열에서 적용했을 때, 문자열 최대 길이가 M이면 O(M*logN)이 된다.

트라이를 활용하면? → O(M)으로 문자열 검색이 가능함!
```

https://camo.githubusercontent.com/eeb565f36ecbfd45c738f3038c144938462c840dfaeeaab466b9ea741b441704/68747470733a2f2f74312e6461756d63646e2e6e65742f6366696c652f746973746f72792f323433353445333335383333413743463137

> 예시 그림에서 주어지는 배열의 총 문자열 개수는 8개인데, 트라이를 활용한 트리에서도 마지막 끝나는 노드마다 '네모' 모양으로 구성된 것을 확인하면 총 8개다.

해당 자료구조를 풀어보기 위해 좋은 문제 : [백준 5052(전화번호 목록)](https://www.acmicpc.net/problem/5052)

### 문제에서 Trie를 java로 구현한 코드

```java
static class Trie {
    boolean end;
    boolean pass;
    Trie[] child;

    Trie() {
        end = false;
        pass = false;
        child = new Trie[10];
    }

    public boolean insert(String str, int idx) {

        //끝나는 단어 있으면 false 종료
        if(end) return false;

        //idx가 str만큼 왔을때
        if(idx == str.length()) {
            end = true;
            if(pass) return false; // 더 지나가는 단어 있으면 false 종료
            else return true;
        }
        //아직 안왔을 때
        else {
            int next = str.charAt(idx) - '0';
            if(child[next] == null) {
                child[next] = new Trie();
                pass = true;
            }
            return child[next].insert(str, idx+1);
        }

    }
}
```

## REFERENCE

---

- [https://github.com/gyoogle/tech-interview-for-developer/blob/master/Computer Science/Data Structure/Trie.md](https://github.com/gyoogle/tech-interview-for-developer/blob/master/Computer%20Science/Data%20Structure/Trie.md)
