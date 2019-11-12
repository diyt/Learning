# Learning

- Binary Search: [Template 3](https://aaronice.gitbooks.io/lintcode/content/knowledge/binary-search.html), Two termination conditions.  
- Two Pointers: [Triangle Count](https://www.lintcode.com/problem/triangle-count/description) - Remember to fix largest edge.  
- Partition Array:
  - [Template](https://www.lintcode.com/problem/partition-array/description)
  - [Quick Select](https://www.lintcode.com/problem/kth-largest-element/description)
  - [Sort 3 colors](https://www.lintcode.com/problem/sort-colors/my-submissions)
  - [Sort k colors](https://www.lintcode.com/problem/sort-colors-ii/description)  
- BSF Traversal:
  - When to use BFS:
    - 图的遍历 Traversal in Graph
      - 层级遍历 Level Order Traversal
      - 由点及面 Connected Component
      - 拓扑排序 Topological Sorting
    - 最短路径 Shortest Path in Simple Graph
      - 仅限简单图求最短路径. 即图中每条边长度都是1，或者边长都相等. For more complex problems, use Dijkstra, Floyd.
  - BSF in Binary Tree: 
    - [Binary Tree Level Order Traversal](https://www.lintcode.com/problem/binary-tree-level-order-traversal/). The algorithm that requires levels need one more for loop.
    - [Binary Tree Serialization/Deserialization](https://www.lintcode.com/problem/serialize-and-deserialize-binary-tree/description)
  - BSF in Graph: (May have cycles, need to record visited nodes)
    - [Word Ladder](https://www.lintcode.com/problem/word-ladder/description)
  - BSF in Matrix: 
    - [Number of Islands](https://www.lintcode.com/problem/number-of-islands/description)  
      Create a direction array to help traversing all directions. Can also be solved by [Union Find](https://www.lintcode.com/problem/graph-valid-tree/description).
      ``` 
      int[] deltaX = new int[]{1,0,0,-1};
      int[] deltaY = new int[]{0,1,-1,0};
      ```
