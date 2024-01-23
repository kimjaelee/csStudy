# DFS

---

그래프 알고리즘으로, 문제를 풀 때 상당히 많이 사용한다.

경로를 찾는 문제 시, 상황에 맞게 DFS와 BFS를 활용하게 된다.

### DFS

> 루트 노드 혹은 임의 노드에서 다음 브랜치로 넘어가기 전에, 해당 브랜치를 모두 탐색하는 방법

**스택 or 재귀함수**를 통해 구현한다.

- 모든 경로를 방문해야 할 경우 사용에 적합

https://camo.githubusercontent.com/ae274bb863dc2a518621095fc9e793df0baa7f109638e984c768ae5d6f02763a/68747470733a2f2f75706c6f61642e77696b696d656469612e6f72672f77696b6970656469612f636f6d6d6f6e732f372f37662f44657074682d46697273742d5365617263682e676966

### 시간 복잡도

- 인접 행렬 : O(V^2)
- 인접 리스트 : O(V+E)

> V는 접점, E는 간선을 뜻한다

### Code

```java
#include <stdio.h>

int map[1001][1001], dfs[1001];

void init(int *, int size);

void DFS(int v, int N) {

	dfs[v] = 1;
	printf("%d ", v);

	for (int i = 1; i <= N; i++) {
		if (map[v][i] == 1 && dfs[i] == 0) {
			DFS(i, N);
		}
	}

}

int main(void) {

	init(map, sizeof(map) / 4);
	init(dfs, sizeof(dfs) / 4);

	int N, M, V;
	scanf("%d%d%d", &N, &M, &V);

	for (int i = 0; i < M; i++)
	{
		int start, end;
		scanf("%d%d", &start, &end);
		map[start][end] = 1;
		map[end][start] = 1;
	}

	DFS(V, N);

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
