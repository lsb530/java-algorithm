## Graph (그래프)

## 그래프 정의

현실세계의 사물이나 개념 간의 **연결 관계**를 수학적 모델로 단순화하여 표현한 것

- V : 정점 (Vertex / Node)
- E : 간선 (Edge / Link / Arc)
- 그래프 G = (V, E)

## 그래프 용어

1. **정점, 노드 (Vertex, Node)**
2. **간선 (Edge)**
    - 무향 간선 (Undirected Edge) : 방향이 존재하지 않는 간선, 양방향
    - 유향 간선 (Directed Edge) : 방향이 존재하는 간선
3. **인접 (Adjacent)** : (정점 관점) 두 정점 A, B 사이에 간선이 존재한다면 A, B는 인접한다.
4. **부속 (Incident)** : (간선 관점) 두 정점 A, B 사이에 간선 e가 존재한다면 간선 e는 정점 A, B에 부속한다.
5. **차수 (Degree)** : 한 정점에 연결된 간선의 수
    - (방향 그래프) in-degree : 정점에 들어오는 간선의 수, out-degree : 나가는 간선의 수
6. **자기 간선과 다중 간선**
    - 자기 간선 (Self-loop) : 자신으로 다시 돌아오는 간선
    - 다중 간선 (Multiple / Parallel edges) : 두 개 이상의 간선이 똑같은 두 정점에 부속할 때
7. **경로 (Path)** : 정점 + 간선이 교대로 구성된 sequence
    - 단순 경로 (Simple Path) : 같은 정점을 두 번 이상 가지 않는 경로
8. **회로 (Cycle)** : A 정점에서 출발했을 때 다시 A 정점으로 돌아오는 경로
    - 단순 회로 (Simple Cycle) : 같은 정점을 두 번 이상 가지 않는 싸이클
9. **연결됨 (Connected)** : 정점 A에서 정점 B로의 경로가 존재할 때 A와 B는 연결되어 있다.

## 그래프 종류

1. **무향 그래프 (Undirected Graph)** : 무방향 간선으로 이루어진 그래프
2. **유향 그래프 (Directed Graph)** : 방향 간선으로 이루어진 그래프
3. **가중치 그래프 (Weighted Graph)** : 가중치(비용)를 갖는 간선들로 이루어진 그래프
4. **정규 그래프 (Regular Graph)** : 모든 정점이 동일한 차수를 가지는 그래프
5. **완전 그래프 (Complete Graph)** : 모든 정점이 서로 인접해있는 그래프, 완전 그래프는 정규 그래프
6. **연결 그래프 (Connected Graph)** : 모든 정점이 연결되어 있어서 모든 정점끼리 경로가 존재하는 그래프
7. **부분 그래프** : 어떤 그래프의 부분 부분
8. **트리 그래프** : 싸이클을 가지지 않는 연결 그래프, 모든 정점에 대해서 경로가 정확히 1개 존재한다.

## 그래프 표현

그래프의 표현 방식에는 **간선 리스트, 인접 행렬, 인접 리스트** 3가지 방식이 있다.

> 정점 개수 : V개, 간선 개수 : E개

### 간선 리스트 (Edge List)

- E x 2 (or E x 3) 이차원 배열 A에 정보를 저장한다.
- 두 정점 x, y 를 연결하는 간선 k에 대해서 A[k][0] = x, A[k][1] = y
- 가중치 그래프의 경우 A[k][2] 에 가중치 정보를 저장한다.

![간선리스트](./img/그래프.001.jpeg)


### 인접 행렬 (Adjacency Matrix)

- V x V 이차원 배열 A에 정보를 저장한다.
- Vi, Vj를 연결하는 간선이 존재한다면 A[i][j] = 1, 존재하지 않는다면 A[i][j] = 0
- 가중치 그래프의 경우 1 대신 가중치 정보를 저장한다.

> 메모리 복잡도가 V<sup>2</sup> 이기 때문에 V의 값이 클 경우 쓰지 않는 것이 좋다.
> 100 이하의 값일 때 사용하는 것이 좋다.

![인접행렬](./img/그래프.002.jpeg)

### 인접 리스트 (Adjacent List)

- V 개의 Linked List로 그래프 정보를 저장한다.
- 가중치 그래프의 경우 (정점 정보, 가중치 정보)를 함께 저장한다. (C++ : pair, Java : class)

![인접리스트](./img/그래프.003.jpeg)

### 그래프 표현 방식 비교

> 정점 개수 : V개, 간선 개수 : E개

|       | 간선 리스트 |    인접 행렬      |    인접 리스트    |
| :---: | :------: | :-------------: | :------------: |
|  공간  |    E     |  V<sup>2</sup>  |     V + E      |
|  정점 Va 의 부속 간선  |    E     |     V     |   Va 차수   |
| 정점 Va, Vb 의 인접 여부 |    E     |     1     | min(Va 차수, Vb 차수) |
|  정점 삽입  |    1     |  V<sup>2</sup>  |     1     |
|  간선 삽입  |    1     |    1    |     1     |