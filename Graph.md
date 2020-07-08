# Graph



## 개념

> 노드와(node) 노드를 연결하는 간선(edge)을 하나로 모아놓은 자료구조

## 용어

- 정점(Vertex, Node) : 값 또는 어떤 대상으로 표현되는 개념
- 간선(Edge) : 임의의 두 정점을 잇는 선
-  방향그래프(Directed Graph)와 양방향 그래프
  - 방향이 있는 그래프 : 1 → 2 로 갈 수 있지만 2 → 1 로 갈 수 없음
  - 방향이 없는 그래프(양방향 그래프) : 1 → 2 와 2 → 1 모두 갈 수 있음
    - 그래프를 저장할 때 방향이 없는 그래프는 모두 방향이 있는 그래프로 바꿔서 저장하게 됨
- 경로(Path)와 사이클(Cycle)
  - 경로(Path) : 임의의 정점 `V1`에서 `V2`로 가는 연속된 간선의 모음 
  - 사이클(Cycle) : 시작점과 도착점이 같은 경로
  - 단순 경로와 단순 사이클 : 경로 또는 사이클에 같은 `간선`이 중복되지 않는 것
  - 단일 경로와 단일 사이클 : 경로 또는 사이클에 같은 `정점`이 중복되지 않는것
- 루프
  - 간선의 시작점과 도착점이 같은 것
- 가중치(Weight)
  - 간선의 양 끝 정점 `V1` 에서 `V2`로 이동하는데 필요한 비용, 거리, 시간 등을 나타내는 값
  - 가중치가 별도로 표시되지 않으면 1을 나타냄
- 차수(Degree) 
  - 정점에 연결되어 있는 간선의 개수
  - 방향 있는 그래프에서는 In-degree, Out-degree로 나눔
    - In-degree : 해당 정점으로 들어오는 방향의 간선의 수
    - Out-degree : 해당 정점에서 나가는 방향의 간선의 수
- 연결요소(Connected Component)와 연결 그래프(Connected Graph)
  - 요소(Commponent) : 원래 그래프에서 정점 및 간선을 공유하지 않는 각각의 부분 그래프
  - 연결요소(Connected Component) : 각각의 요소가 간선에 의해 모두 연결되어 있는 것
  - 연결 그래프(Connected Graph) : 연결 요소가 1개인 그래프. 임의의 정점에서 시작하여 모든 정점을 방문할 수 있다
  - `DFS` 또는  `BFS` 를 사용하여 연결요소의 개수를 구할 수 있다.
- 이분 그래프(Bipartite Graph)
  - 정점을 두 그룹으로 나눌 수 있고, 같은 그룹에 속한 정점들 사이에 간선이 존재하지 않는 그래프
  - `DFS` 또는 `BFS` 를 사용하여 주어진 그래프가 이분 그래프인지 판별할 수 있다.
- 인접 행렬(Adjacent Matrix)
  - `V` 개의 정점에 대해 임의의 두 정점을 각각 row와 column으로 하는 2차원 배열의 간선의 유무를 저장
    - 가중치가 없는 그래프 : 간선의 유무를 **0/1** 또는 **true/false**
    - 가중치가 있는 그래프 : 간선이 없으면 0, 있으면 **가중치**를 저장
- 인접 리스트(Adjacent List)
  - **V**개의 정점에 대해 임의의 정점 `V1`과 연결되어있는 정점 `V2`를 연결 리스트의 형태로 저장
    - 임의의 정점에 연결되어 있는 정점이 몇개 인지 알 수 없으므로, 연결된 정점을 찾을 때 마다 추가하여 실제 정점의 개수 만큼만 메모리 사용
    - 가중치가 없는 그래프 : 연결된 정점을 저장
    - 가중치가 있는 그래프 : 연결된 정점과 간선의 가중치를 함께 저장



## 그래프의 표현

### 인접 행렬(Adjacent Matrix)

- **V**개의 정점에 대해 임의의 두 정점을 각각 row와 column으로 하는 2차원 배열에 간선의 유무를 저장

  - 가중치가 없는 그래프 : 간선의 유무를 0과 1 또는 true/false로 저장
  - 가중치가 있는 그래프 : 간선이 없으면 0, 있으면 **가중치**를 저장

- 방향이 없는 그래프에서는 간선을 통해 양방향으로 이동할 수 있으므로 (r, c)와(c, r) 모두 표시

- 행렬의 크기 **V²**

- 하나의 정점과 연결된 모든 간선을 구하는 시간 **O(V)**

- 임의의 두 정점 사이에 간선의 유무를 구하는 시간 **0(1)**

- 구현

  ```swift
  let V = 5
  let edges = [[0, 1], [0, 2], [1, 2], [1, 3], [1, 4], [2, 4], [3, 4]]
  
  var adjacentMatrix = [[Bool]](repeating: [Bool](repeating: false, count: V), count: V)
  for edge in edges {
    let node1 = edge[0]
    let node2 = edge[1]
    adjacentMatrix[node1][node2] = true
    adjacentMatrix[node2][node1] = true
  }
  ```




### 인접 리스트(Adjacent List)

- **V**개의 정점에 대해 임의의 정점 `v1`과 연결되어 있는 정점 `v2`를 연결 리스트의 형태로 저장

  - 연결리스트 사용 이유 : 임의의 정점에 연결되어 있는 정점이 몇개인지 알 수 없으므로 연결된 정점을 찾을 때 마다 추가하여 실제 정점의 개수만큼만 메모리를 사용한다.
  - 가중치가 없는 그래프 : 연결된 정점을 저장
  - 가중치가 있는 그래프 : 연결된 정점과 간선의 가중치를 함께 저장 → (node, weight)

- 연결 리스트에 저장된 정점이 곧 간선을 의미

- 구현

  ```swift
  let V = 5
  let edges = [[0, 1], [0, 2], [1, 2], [1, 3], [1, 4], [2, 4], [3, 4]]
  
  var adjacentList = [[Int]](repeating: [], count: V)
  for edge in edges {
    let node1 = edge[0]
    let node2 = edge[1]
    adjacentList[node1].append(node2)
    adjacentList[node2].append(node1)
  }
  
  ```





## 그래프의 탐색

> 임의의 한 정점에서 시작하여 연결된 모든 정점을 **1번씩만** 방문하는 것

### 깊이 우선 탐색(DFS, Depth First Search)

- 연결된 임의의 정점 중 하나를 선택하며 탐색해 나가는 방법
- 연결된 정점 중 아직 탐색하지 않은 정점 한 개를 선택하며 탐색해나가고, 더 이상 연결된 정점이 없거나 방문하지 않은 정점이 없다면 이전 정점으로 되돌아가서 탐색
- 탐색해 온 정점을 다시 돌아가야 하기 때문에 **Stack**을 사용하여 구현 → 메모리 stack 영역을 하용하는 함수 호출을 활용하여 재귀적으로(recursive) 구현가능
  - Stack의 top은 현재 정점을 의미
  - 다음 정점을 탐색할 때 push(recursive call)
  - 이전 정점으로 되돌아갈 때 pop(recursive return)
- Stack이 비어 있으면(재귀가 끝나면) 탐색 종료
- 인접 행렬보다 인접 리스트를 사용하는게 더 빠르고 좋다
  - 인접 행렬 : **O(V²)** → V개의 node에 대해 인접행렬을 V번 검사해야 함
  - 인접 리스트 : **O(V + E)** → V개의 node에 대해 각각의 차수 만큼만 탐색
- 장점
  - BFS에 비해 저장공간의 필요성이 적다. 백트랙킹을 해야하는 노드들만 저장하면 됨
  - 찾아야하는 노드가 깊은 단계에 있을수록, 그 노드가 좌측에 있을수록 BFS 보다 유리함
- 단점
  - 답이 아닌 경로가 매우 깊다면, 그 경로에 깊이 빠질 우려가 있음

#### 인접 행렬 사용

```swift
var checkVisits: [Bool] = .init(repeating: false, count: V)
// 정점의 개수만큼 방문 여부를 확인할 수 있는 배열 생성

func DFS(_ n: Int) {
  checkVisits[n] = true
  print(n)
  for i in 0..<adjacentMatrix.count {
    if adjacentMatrix[n][i] == true && checkVisits[i] == false {
      // 현재 node와 인접한 다른 node가 존재하고 아직 방문하지 않은 경우
      // 해당 node에 대해 DFS 수행
      
      DFS(i)
    }
  }
  
}
```

#### 인접 리스트 사용

```swift
var checkVisits = [Bool](repeating: false, count: V)
// 정점의 개수만큼 방문 여부를 확인할 수 있는 배열 생성

func DFS(_ n: Int) {
  checkVisits[n] = true
  
  for i in adjacentList[n] {
    if checkVisits[i] == false {
      // 인접 리스트에 방문하지 않은 node가 있다면
      // 해당 node에 대해 DFS 수행
      
      DFS(i)
    }
  }
}
```



### 너비 우선 탐색(BFS, Breadth First Search)

- 연결된 정점을 한번에 모두 방문하는 것
- 현재 node에서 탐색 가능한 node를 모두 queue에 넣고 head에 있는 node에 대해 BFS를 반복해서 수행
- **Queue에 push되는 순간 방문한 것으로 check해야함. 그렇지 않으면 node를 중복으로 방문하는 경우가 생기고, BFS가 아님**
- Queue가 비어있으면 종료
- 인접행렬보다 **인접리스트를 사용하는게 더 빠르고 좋다**
  - 인접 행렬 : **O(V²)** → V개의 node에 대해 인접행렬을 V번 검사해야함
  - 인접 리스트 : **O(V + E)** → V개의 node에 대해 각각 차수만큼만 탐색
- 장점
  - 너비를 우선으로 탐색하기 때문에 답이 되는 경로가 여러 개인 경우에도 최단경로임을 보장
  - 최단 경로가 존재한다면 어느 한 경로가 무한히 깊어진다 해도 최단 경로를 반드시 찾을 수 있다
  - 노드의 수가 적고 깊이가 얕은 해가 존재할 때 유리
- 단점
  - 재귀 호출을 사용하는 DFS 와는 달리 큐를 이용해 다음에 탐색할 노드들을 저장하기 때문에 노드의 수가 많을수록 필요없는 노드들까지 저장해야하기때문에 더 큰 저장공간이 필요함

#### 인접 행렬 사용

```swift
var checkVisits = [Bool](repeating: false, count: V)
// 정점의 개수만큼 방문 여부를 확인할 수 있는 배열 생성

func BFS(_ adjacentMatrix: [[Bool]]) {
  var queue = [0]
  checkVisits[0] = true

  while !queue.isEmpty {
    let currentNode = queue.removeFirst()
    // queue에서 pop하면서 해당 node 검사 준비
    
    for node in 0..<adjacentMatrix[currentNode].count {
      
      if adjacentMatrix[currentNode][node] == true && checkVisits[node] == false {
        // 현재 node와 인접한 다른 node가 있고 방문하지 않았다면
        // queue에 push 하고 방문 체크
        queue.append(node)
        checkVisits[node] = true
      }
    }
  }
}
```



#### 인접 리스트 사용

```swift
var checkVisits = [Bool](repeating: false, count: V)
// 정점의 개수만큼 방문 여부를 확인할 수 있는 배열 생성

func BFS(_ adjacentList: [[Int]]) {
  var queue = [0]
  checkVisits[0] = true

  while !queue.isEmpty {
    let currentNode = queue.removeFirst()
		// queue에서 pop하면서 해당 node 검사 준비
    
    for node in adjacentList[currentNode] {
      if checkVisits[node] == false {
        // 인접 리스트에 방문 하지않은 node가 있다면
        // queue에 push 하고 방문 체크
        queue.append(node)
        checkVisits[node] = true
      }
    }
  }
}

```

