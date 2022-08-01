그래프는 비선형 자료구조 중 하나이며 일렬로 나열(선형자료구조)하지 않고 순서와 관계가 복잡한 구조를 말한다.

## 그래프란?
> 객체의 일부 쌍(pair)들이 **연관되어**있는 객체 집합 구조를 말한다.
> 정점과 간선으로 이루어진 자료 구조

## 정점(vertex)과 간선(edge)`
어떠한 지점에서 다른 지점으로 어떠한 경로를 통해 이동한다고 했을 때, 그 지점을 `정점(vertex)` 이라고 하고, 그 경로는 `간선(edge)`이라고 한다.
정점으로 나가는 간선을 outdegree, 정점으로 들어오는 간선을 indegree라고 한다.

## 그래프 순회
그래프 순회란 그래프 탐색(Search)라과도 하며 그래프의 각 정점을 방문하는 과정을 말한다.
그래프의 각 정점을 방문하는 그래프 순회에는 크게 깊이 우선 탐색과 너비우선 탐색 2가지 알고리즘이 있다.

## 그래프의 표현
- 인접 행렬
  : 출발 노드를 키로, 도착 노드를 값으로 표현한다. 도착 노드는 여러 개가 될 수 있으므로 리스트 형태가 된다.
- 인접 리스트
    ```Python
  graph = {
  1 : [2,3,4],
  2 : [5],
  3 : [5],
  4 : [],
  5 : [6,7],
  6 : [],
  7 : [3],
  }
```

## DFS(깊이 우선 탐색)
 **:** **최대한 깊이 내려간 뒤, 더이상 깊이 갈 곳이 없을 경우 옆으로 이동**
루트 노드(혹은 다른 임의의 노드)에서 시작해서 다음 분기(branch)로 넘어가기 전에 
**해당 분기를 완벽하게 탐색**하는 방식
모든 노드를 방문하고자 하는 경우에 이 방법을 선택
![[Pasted image 20220801220631.png]]


#### **2. 너비 우선 탐색 (BFS, Breadth-First Search)**
**: 최대한 넓게 이동한 다음, 더 이상 갈 수 없을 때 아래로 이동**
주로 두 노드 사이의 **최단 경로**를 찾고 싶을 때
![[Pasted image 20220801220945.png]]

루트 노드(혹은 다른 임의의 노드)에서 시작해서 **인접한 노드를 먼저** **탐색**하는 방법으로, 
시작 정점으로부터 가까운 정점을 먼저 방문하고 멀리 떨어져 있는 정점을 나중에 방문하는 순회 방법

**[1] 처음 시작 노드 방문 (A)**
![](https://github.com/ChanhuiSeok/ChanhuiSeok.github.io/blob/master/assets/img/sample/algo27_2.PNG?raw=true)

---
**[2] A는 큐에서 삭제 및 방문 표시 후 A의 인접 노드들을 큐에 삽입**
![](https://github.com/ChanhuiSeok/ChanhuiSeok.github.io/blob/master/assets/img/sample/algo27_3.PNG?raw=true)

---

**[3] A의 인접노드들 중 가장 큐에 먼저 들어간 B를 큐에서 삭제 및 방문 표시, B의 인접 노드들을 큐에 삽입**
![](https://github.com/ChanhuiSeok/ChanhuiSeok.github.io/blob/master/assets/img/sample/algo27_4.PNG?raw=true)

---

**[4] C를 큐에서 삭제 및 방문 표시, C의 인접 노드를 큐에 넣으려 했으나 없으므로 skip**
![](https://github.com/ChanhuiSeok/ChanhuiSeok.github.io/blob/master/assets/img/sample/algo27_5.PNG?raw=true)

---

**[5] 마찬가지로 D도 큐에서 삭제 및 방문 표시, D의 인접 노드 G를 큐에 삽입**
![](https://github.com/ChanhuiSeok/ChanhuiSeok.github.io/blob/master/assets/img/sample/algo27_7.PNG?raw=true)

---

**[6] 큐에 남아있는 요소들을 차례대로 위와 같은 방법으로 방문 및 표시하면서 결과적으로 BFS 탐색 완료**(큐가 완전히 비게 될 때)
![](https://github.com/ChanhuiSeok/ChanhuiSeok.github.io/blob/master/assets/img/sample/algo27_8.PNG?raw=true)