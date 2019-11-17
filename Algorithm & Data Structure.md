# Algorithm and Data Structure

- Binary Search: [Template 3](https://aaronice.gitbooks.io/lintcode/content/knowledge/binary-search.html), Two termination conditions.  
- Two Pointers: [Triangle Count](https://www.lintcode.com/problem/triangle-count/description) - Remember to fix largest edge.  
- Partition Array:
  - [Template](https://www.lintcode.com/problem/partition-array/description)
  - [Quick Select](https://www.lintcode.com/problem/kth-largest-element/description)
  - [Sort 3 colors](https://www.lintcode.com/problem/sort-colors/my-submissions)
  - [Sort k colors](https://www.lintcode.com/problem/sort-colors-ii/description)  
- BFS Traversal:
  - When to use BFS:
    - 图的遍历 Traversal in Graph
      - 层级遍历 Level Order Traversal
      - 由点及面 Connected Component
      - 拓扑排序 Topological Sorting
    - 最短路径 Shortest Path in Simple Graph
      - 仅限简单图求最短路径. 即图中每条边长度都是1，或者边长都相等. For more complex problems, use Dijkstra, Floyd.
  - BFS in Binary Tree: 
    - [Binary Tree Level Order Traversal](https://www.lintcode.com/problem/binary-tree-level-order-traversal/). The algorithm that requires levels need one more for loop.
    - [Binary Tree Serialization/Deserialization](https://www.lintcode.com/problem/serialize-and-deserialize-binary-tree/description)
  - BFS in Graph: (May have cycles, need to record visited nodes)
    - [Word Ladder](https://www.lintcode.com/problem/word-ladder/description)
  - BFS in Matrix: 
    - [Number of Islands](https://www.lintcode.com/problem/number-of-islands/description)  
      Create a direction array to help traversing all directions. Can also be solved by [Union Find](https://www.lintcode.com/problem/graph-valid-tree/description).
      ``` 
      int[] deltaX = new int[]{1,0,0,-1};
      int[] deltaY = new int[]{0,1,-1,0};
      ```
- [Topological Sort](https://www.lintcode.com/problem/topological-sorting/description)
  - [BFS solution(preferred, won't cause infinite loop)](https://www.geeksforgeeks.org/topological-sorting-indegree-based-solution/): Calculate **indegree** for each node, keep pushing nodes with indegree 0 to a queue. Poll nodes from queue and add to result.
  - [DFS solution(will cause infinite loop when there's a cycle)](https://www.geeksforgeeks.org/topological-sorting/): Create a **visited map and stack**. Recursively calling dfsHelper function to unvisited nodes. Push nodes to stack in the end of dfsHelper function so that all children are already in the stack when push the node to stack. Popping nodes from stack and add to result.
- DFS Traversal
  - DFS in Trees
    - Calculate values, max, min, avg...: [Lowest Common Ancestor](https://www.lintcode.com/problem/lowest-common-ancestor/description) - Use ResultType to pass values between recursions
    - Transformation: [Flatten Binary Tree to Linked List](https://www.lintcode.com/problem/flatten-binary-tree-to-linked-list/) - Use a global variable to track the last visited node.
    - Binary Search Tree(BST)
      - BST inorder traversal: [use stack](https://www.lintcode.com/problem/binary-search-tree-iterator/description), [use global variable "lastNode"](https://www.lintcode.com/problem/validate-binary-search-tree/my-submissions)
      - [Find the closest k elements to target in BST](https://www.lintcode.com/problem/closest-binary-search-tree-value-ii/description): BST inorder traversal + Binary Search
  - DFS for Combination and subsets: Use recursion
    - When to use: 1. When need to find **ALL** solutions. 2. Doesn't require order. 3. O(2^n)
    - Three key parts when using DFS: **Definition, Breakdown, Exit**
    - Classic problems:
      - [Subsets(distinct numbers)](https://www.lintcode.com/problem/subsets/description): nextIndex = index + 1
      - [Subsets II(with duplicates numbers)](https://www.lintcode.com/problem/subsets-ii/description): nextIndex = index + 1, Add additional check to avoid counting same number twice
      - [Combination Sum(one number can be used multiple times)](https://www.lintcode.com/problem/combination-sum/description): nextIndex = index
      - [Combination Sum II(one number can only be used once)](https://www.lintcode.com/problem/combination-sum-ii/description): nextIndex = index + 1
  - DFS Complexity: https://www.jiuzhang.com/qa/2994/
      
