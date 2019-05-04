
<details>
  <summary>List</summary>
  
  ## List
  **순서를 가지고 일렬로 나열한 데이터의 모임**
  - 배열로 구현하면 데이터의 삽입 삭제에서 무조건 O(N), 링크드 리스트는 O(1)
  - 배열에선 인덱스로 특정노드르 바로 가져올 수 있지만, 링크드리스트는 순차탐색을 해야한다.
  - 탐색 또는 정렬을 자주하면 **배열**로, 추가/삭제가 많으면 **연결리스트**로
  
  ### 배열로 구현
  - 삽입, 삭제시 불리: O(N)
  - 메모리 효율 불리: 사용하지않는 메모리도 계속 예약해놔야해서
  - 인덱스탐색, 정렬시 유리: 인덱스로 노드 불러오는것이 O(1)이라서 유리
  
  ### Linked List로 구현
  - 삽입, 삭제시 유리: O(1) (노드를 알고 있다면)
  - 메모리 효율 유리: 사용하는 메모리만 예약
  - 탐색시 순차탐색을 할 수 밖에 없는 특성(처음부터 차례로 검색해야한다는 것)
  - 그러나, Tree 자료구조를 구성하기 위한 기본이 되기 때문에, 가치가 있음.
 
</details>
  

<details>
  <summary>Stack</summary>
  
  ## Stack
  **Last In First Out의 자료구조. 데이터를 위로쌓듯이올리고, 뺄때 위에서 뺀다.**
  
  - 배열이든, 연결리스트든 간단하게 구현 가능
  - 운영체제에서는.... 프로세스를 구성하는 4개 요소중 한 부분.
    - 어떤함수든 호출되는 순간 그 함수를 위한 stack frame이 할당됨.
    - 해당 함수가 종료될때, stack frame을 다 걷어내고 그 아래에 return값을 반환해서 자신을 호출한 함수에게 return값 전달
    - 그래프 탐색알고리즘인 DFS 구현시, 잘 사용되는 자료구조.
</details>


<details>
  <summary>Hash</summary>
  
  ## Hash
  **key 로 data를 O(1)에 찾는 자료구조. 사실 배열이라고 보면 된다.**
  
  특정 값을 찾을때 데이터 고유의 index를 사용하므로 주로 O(1)  
  항상 O(1)이 아닌 이유는, Collision 때문
  특별한 알고리즘을 이용하여 저장할 데이터와 관련된 고유한 key를 잘 만들어내야 하는데 이것이 hash function 임
  그럼에도 불구하고 다른데이터가 같은 key값을 가질때 Collision 발생했다고 하며, 이때에는 주로 2가지 방법이 있다.
  1. Open Address 방식
  * collision 발생시, 다른 버킷을 linear한 방식 혹은 2차함수 이용하는 등의 방법으로 찾는다.
  2. Separate Chaining 방식
  * 해당 버킷에 Linked List로 연결하거나(데이터 수가 적을때 좋음)
  * 해당 버킷에 Tree를 연결해놓고, 해당 Tree에 추가하는 것.(데이터수가 많을 때 좋음)
</details>
  
  
<details>
  <summary>Queue</summary>
  
  ## Queue
  ** First Input First Out의 자료구조 **
  
  - Enque, Deque 연산으로 데이터를 넣거나 뺀다.
  - 배열로구현시 Deque하게되면 앞에가 비어서 땡겨주는 연산을 하느라 O(N)이 될수있는데, 이때문에 배열로 구현할땐 원형 큐로 구현 한다.
  - Linked List로 구현하면 간단하게 구현 가능
  
## Priority Queue
**Queue의 일종인데, Deque시 순서상관없이 가장 높은 우선순위를 가진 노드가 빠져 나온다는 점이 다르다.**
  
  - 배열 혹은 링크드리스트로 구현(잘안쓰임)
    - 데이터의 추가, 삭제시 항상 정렬이 되어있어야 하기때문에 최소 O(NlogN) 시간복잡도 든다.
    
  - **힙트리** 자료구조로 구현(잘쓰임)
    - Enque: O(log N) 
      - 추가할땐 가장 말단노드에 추가한후 위로 올라가면서 heapify 해나간다
    - Deque: O(log N) 
      - 루트노드를 빼고, 말단노드를 루트노드로 바꾼후, 아래로 내려가며 heapify 한다.
</details>
  
<details>
  <summary>Tree</summary>
  
  ## Tree  
  **싸이클이 없는 그래프. 루트노드가 정의되어 있음.**
- 이진트리(Binary Tree)
  - 이진트리 종류
    - full binary tree: 모든 노드의 자식은 0개나 2개
    - perfect binary tree: 모든 리프노드의 높이가 같다.
    - complete binary tree: 위에서 아래로, 왼쪽에서 오른쪽으로 빠짐없이 채워져있는 트리.
  - 이진트리 순회방법
    - in-order  : 왼,나,오 (스택 or 재귀로 구현)
    - pre-order : 나,왼,오 (스택 or 재귀로 구현)
    - post-order: 왼,오,나 (스택 or 재귀로 구현)
    - level-order: BFS처럼, 레벨순서로 방문함(큐로 구현)
  - 이진 탐색 트리(Binary Search Tree, BST)
    - 이진트리의 일종으로, 특정 규칙에 따라 노드의 위치가 결정되는데, 그 규칙은 "왼쪽자식노드<=부모노드<=오른쪽자식노드" 임
    - 탐색/삽입/삭제 모두 O(log N)
    - AVL트리등을 사용하여 tree가 skew되는상황을 막지않으면, 탐색에 O(N)이 소요될 수도 있다.
  - AVL-tree(균형 이진 탐색 트리1)
    - binary tree
    - 규칙: "모든 노드에서 오른쪽 트리와 왼쪽 트리의 height차이가 1 이하"
    - 삽입/삭제를 할 때마다 균형이 안맞는것을 맞추기위해 트리의 일부를 왼쪽 혹은 오른쪽으로 회전시켜야 함
    - 균형은 아래의 Red-black tree보다 훨씬 잘 잡히지만, 그렇기 때문에 Red-black tree보다 삽입과 제거가 느리고 탐색자체는 빠르다. 그래서 보통 자가 균형 이진 탐색 트리가 필요한경우, Red-black tree 사용한다.
  - Red-black tree(균형 이진 탐색 트리2)
    - 이상적인 상황이든, 최악의 상황이든 상관없이 탐색/삽입/삭제 모두 시간복잡도 O(log N)이다. ~~궁극의 트리~~
    
  - 힙(Heap)
    - full binary tree(위에서아래로, 왼쪽에서오른쪽으로 빈틈없음)
    - 규칙: "부모노드가 자식노드보다 항상 값이 크다"
    - priority queue만들때 사용하는 자료구조
  
  - B-tree
    - ![B-tree](https://upload.wikimedia.org/wikipedia/commons/thumb/6/65/B-tree.svg/600px-B-tree.svg.png)
    - 데이터베이스와, 파일 시스템에서 널리 사용되는 트리 자료구조
    - 모든 노드에 있는 값들은 정렬되어 있는 상태이며, 각노드마다 order를 나타내는 숫자인 m개의 자식을 가질 수 있다.
    - 이 B-tree를 B-tree of order m 이라고 한다.
    - B-tree는 노드의 접근시간이 노드에서의연산시간에 비해 훨씬 길 경우, 다른 구현 방식에 비해 상당한 이점을 가지고 있다(?)
</details>

<details>
  <summary>Graph</summary>
  
  ## Graph
  **Vertex와 Edge로 구성되어 있는 자료구조**
  1. 그래프 탐색 알고리즘
  * BFS
  * DFS
    
  2. MST(Minimum Spanning Tree) 알고리즘
  * 모든 Vertex를 연결하는 최소비용을 구하는 방법
  * prim 알고리즘
  * kruskal 알고리즘
    
  3. Shortest Path
  * 특정 노드에서 나머지노드의 최소길이를 구하는 방법
  * 다익스트라 알고리즘
</details>


