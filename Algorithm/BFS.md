# BFS

---

> 루트 노드 또는 임의 노드에서 인접한 노드부터 먼저 탐색하는 방법

**큐**를 통해 구현한다. (해당 노드의 주변부터 탐색해야하기 때문)

- 최소 비용(즉, 모든 곳을 탐색하는 것보다 최소 비용이 우선일 때)에 적합

https://camo.githubusercontent.com/d6b4eaeb5084a831b45f71a2d620764d18c3278562d7087997a8717432ef371d/68747470733a2f2f75706c6f61642e77696b696d656469612e6f72672f77696b6970656469612f636f6d6d6f6e732f352f35642f427265616474682d46697273742d5365617263682d416c676f726974686d2e676966

### 시간 복잡도

- 인접 행렬 : O(V^2)
- 인접 리스트 : O(V+E)

### Code

```java
#include <stdio.h>

int map[1001][1001], bfs[1001];
int queue[1001];

void init(int *, int size);

void BFS(int v, int N) {
	int front = 0, rear = 0;
	int pop;

	printf("%d ", v);
	queue[rear++] = v;
	bfs[v] = 1;

	while (front < rear) {
		pop = queue[front++];

		for (int i = 1; i <= N; i++) {
			if (map[pop][i] == 1 && bfs[i] == 0) {
				printf("%d ", i);
				queue[rear++] = i;
				bfs[i] = 1;
			}
		}
	}

	return;
}

int main(void) {

	init(map, sizeof(map) / 4);
	init(bfs, sizeof(bfs) / 4);
	init(queue, sizeof(queue) / 4);

	int N, M, V;
	scanf("%d%d%d", &N, &M, &V);

	for (int i = 0; i < M; i++)
	{
		int start, end;
		scanf("%d%d", &start, &end);
		map[start][end] = 1;
		map[end][start] = 1;
	}

	BFS(V, N);

	return 0;
}

void init(int *arr, int size) {
	for (int i = 0; i < size; i++)
	{
		arr[i] = 0;
	}
}
```

## REFERENCE

---

- [https://github.com/gyoogle/tech-interview-for-developer/blob/master/Algorithm/DFS %26 BFS.md](https://github.com/gyoogle/tech-interview-for-developer/blob/master/Algorithm/DFS%20%26%20BFS.md)
