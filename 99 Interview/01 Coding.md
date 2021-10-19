# Array
* <a id="Leetcode0560" href="https://leetcode.com/problems/subarray-sum-equals-k/">[Leetcode 0560. Subarray Sum Equals K]</a> : <a href="https://github.com/lambda826/Algorithms/blob/master/src/coding/leetcode/_01_array/_0560_Subarray_Sum_Equals_K.java">**Solution**</a>
---
# String
* <a id="Leetcode0415" href="https://leetcode.com/problems/add-strings/">[Leetcode 0415. Add Strings]</a> : <a href="https://github.com/lambda826/Algorithms/blob/master/src/coding/leetcode/_02_string/_0415_Add_Strings.java">**Solution**</a>
* <a id="Leetcode0043" href="https://leetcode.com/problems/multiply-strings/">[Leetcode 0043. Multiply Strings]</a> : <a href="https://github.com/lambda826/Algorithms/blob/master/src/coding/leetcode/_02_string/_0043_Multiply_Strings.java">**Solution**</a>

## Palindrome
  * <a id="Leetcode0125" href="https://leetcode.com/problems/valid-palindrome/">[Leetcode 0125. Valid Palindrome]</a> : <a href="https://github.com/lambda826/Algorithms/blob/master/src/coding/leetcode/_02_string/palindrome/_0125_Valid_Palindrome.java">**Solution**</a>
    * Character.isLetterOrDigit
    * Character.toLowerCase
* <a id="Leetcode0680" href="https://leetcode.com/problems/valid-palindrome-ii/">[Leetcode 0680. Valid Palindrome II]</a> : <a href="https://github.com/lambda826/Algorithms/blob/master/src/coding/leetcode/_02_string/palindrome/_0680_Valid_Palindrome_II.java">**Solution**</a>
* <a id="Leetcode0516" href="https://leetcode.com/problems/longest-palindromic-subsequence/">[Leetcode 0516. Longest Palindromic Subsequence]</a> : <a href="https://github.com/lambda826/Algorithms/blob/master/src/coding/leetcode/_02_string/palindrome/_0516_Longest_Palindromic_Subsequence.java">**Solution**</a>
* <a id="Leetcode1216" href="https://leetcode.com/problems/valid-palindrome-iii/">[Leetcode 1216. Valid Palindrome III]</a> : <a href="https://github.com/lambda826/Algorithms/blob/master/src/coding/leetcode/_02_string/palindrome/_1216_Valid_Palindrome_III.java">**Solution**</a>
* <a id="Leetcode0005" href="https://leetcode.com/problems/longest-palindromic-substring/">[Leetcode 0005. Longest Palindromic Substring]</a> : <a href="https://github.com/lambda826/Algorithms/blob/master/src/coding/leetcode/_02_string/palindrome/_0005_Longest_Palindromic_Substring.java">**Solution**</a>

## Parentheses
* <a id="Leetcode0020" href="https://leetcode.com/problems/valid-parentheses/">[Leetcode 0020. Valid Parentheses]</a> : <a href="https://github.com/lambda826/Algorithms/blob/master/src/coding/leetcode/_02_string/parentheses/_0020_Valid_Parentheses.java">**Solution**</a>
* <a id="Leetcode0921" href="https://leetcode.com/problems/minimum-add-to-make-parentheses-valid/">[Leetcode 0921. Minimum Add to Make Parentheses Valid]</a> : <a href="https://github.com/lambda826/Algorithms/blob/master/src/coding/leetcode/_02_string/parentheses/_0921_Minimum_Add_to_Make_Parentheses_Valid.java">**Solution**</a>
* <a id="Leetcode1249" href="https://leetcode.com/problems/minimum-remove-to-make-valid-parentheses/">[Leetcode 1249. Minimum Remove to Make Valid Parentheses]</a> : <a href="https://github.com/lambda826/Algorithms/blob/master/src/coding/leetcode/_02_string/parentheses/_1249_Minimum_Remove_to_Make_Valid_Parentheses.java">**Solution**</a>
* <a id="Leetcode0032" href="https://leetcode.com/problems/longest-valid-parentheses/">[Leetcode 0032. Longest Valid Parentheses]</a> : <a href="https://github.com/lambda826/Algorithms/blob/master/src/coding/leetcode/_02_string/parentheses/_0032_Longest_Valid_Parentheses.java">**Solution**</a>
* <a id="Leetcode0301" href="https://leetcode.com/problems/remove-invalid-parentheses/">[Leetcode 0301. Remove Invalid Parentheses]</a> : <a href="https://github.com/lambda826/Algorithms/blob/master/src/coding/leetcode/_02_string/parentheses/_0301_Remove_Invalid_Parentheses.java">**Solution**</a>
---

# LinkedList
---

# Hashing
---
# Sorting
## Quick Sort
## Merge Sort
* <a id="Leetcode0021" href="https://leetcode.com/problems/merge-two-sorted-lists/">[Leetcode 0021. Merge Two Sorted Lists]</a> : <a href="https://github.com/lambda826/Algorithms/blob/master/src/coding/leetcode/_04_sorting/mergeSort/_0021_Merge_Two_Sorted_Lists.java">**Solution**</a>
* <a id="Leetcode0023" href="https://leetcode.com/problems/merge-k-sorted-lists/">[Leetcode 0023. Merge k Sorted Lists]</a> : <a href="https://github.com/lambda826/Algorithms/blob/master/src/coding/leetcode/_04_sorting/mergeSort/_0023_Merge_k_Sorted_Lists.java">**Solution**</a>
* <a id="Leetcode0088" href="https://leetcode.com/problems/merge-sorted-array/">[Leetcode 0088. Merge Sorted Array]</a> : <a href="https://github.com/lambda826/Algorithms/blob/master/src/coding/leetcode/_04_sorting/mergeSort/_0088_Merge_Sorted_Array.java">**Solution**</a>

---
# Binary Search
---

# BFS
---
# BFS or DFS
<a id="Leetcode199" href="https://leetcode.com/problems/binary-tree-right-side-view/">[Leetcode 199].</a>  Binary Tree Right Side View
```java
    // BFS
    public List<Integer> rightSideView_BFS(TreeNode root) {
        List<Integer> list = new ArrayList<>();
        if (root != null) {
            ArrayDeque<TreeNode> queue = new ArrayDeque<>();
            queue.offer(root);
            while (!queue.isEmpty()) {
                list.add(queue.getLast().val);
                int size = queue.size();
                while (size-- > 0) {
                    enQueue(queue.poll(), queue);
                }
            }
        }
        return list;
    }
```
```java
    // DFS
    // First add right subtree and then left subtree
    // The first node to add for each level is the rightmost node
    // When the list.size() is less than height, it indicates the node is the rightmost one
    public List<Integer> rightSideView_DFS(TreeNode root) {
        List<Integer> list = new ArrayList<>();
        DFS(root, list, 1);
        return list;
    }

    private void DFS(TreeNode node, List<Integer> list, int height) {
        if (node != null) {
            if (list.size() < height) {
                list.add(node.val);
            }
            DFS(node.right, list, height + 1);
            DFS(node.left, list, height + 1);
        }
    }
```

---
# DFS or Backtracking
---
## Combination
### 1D
* <a id="Leetcode0322" href="https://leetcode.com/problems/coin-change/">[Leetcode 0322. Coin Change]</a> : <a href="https://github.com/lambda826/Algorithms/blob/master/src/coding/leetcode/_07_dfs_backtracking/combination/_1d/_0322_Coin_Change.java">**Solution**</a>
* <a id="Leetcode0518" href="https://leetcode.com/problems/coin-change-2/">[Leetcode 0518. Coin Change 2]</a> : <a href="https://github.com/lambda826/Algorithms/blob/master/src/coding/leetcode/_07_dfs_backtracking/combination/_1d/_0518_Coin_Change_2.java">**Solution**</a>
* <a id="Leetcode0039" href="https://leetcode.com/problems/combination-sum/">[Leetcode 0039. Combination Sum]</a> : <a href="https://github.com/lambda826/Algorithms/blob/master/src/coding/leetcode/_07_dfs_backtracking/combination/_1d/_0039_Combination_Sum.java">**Solution**</a>
* <a id="Leetcode0040" href="https://leetcode.com/problems/combination-sum-ii/">[Leetcode 0040. Combination Sum II]</a> : <a href="https://github.com/lambda826/Algorithms/blob/master/src/coding/leetcode/_07_dfs_backtracking/combination/_1d/_0040_Combination_Sum_II.java">**Solution**</a>
* <a id="Leetcode0377" href="https://leetcode.com/problems/combination-sum-iv/">[Leetcode 0377. Combination Sum IV]</a> : <a href="https://github.com/lambda826/Algorithms/blob/master/src/coding/leetcode/_07_dfs_backtracking/combination/_1d/_0377_Combination_Sum_IV.java">**Solution**</a>
* <a id="Leetcode0216" href="https://leetcode.com/problems/combination-sum-iii//">[Leetcode 0216. Combination Sum III]</a> : <a href="https://github.com/lambda826/Algorithms/blob/master/src/coding/leetcode/_07_dfs_backtracking/combination/_1d/_0216_Combination_Sum_III.java">**Solution**</a>
* <a id="Leetcode0241" href="https://leetcode.com/problems/different-ways-to-add-parentheses/">[Leetcode 0241. Different Ways to Add Parentheses]</a> : <a href="https://github.com/lambda826/Algorithms/blob/master/src/coding/leetcode/_07_dfs_backtracking/combination/_1d/_0241_Different_Ways_to_Add_Parentheses.java">**Solution**</a>

### 2D
## Permutation

<a id="Leetcode1947" href="https://leetcode.com/problems/maximum-compatibility-score-sum/">[Leetcode 1947].</a>  Maximum Compatibility Score Sum
```java
    ////////////////////////////////////////////////////////////////////////////////////////////////////////////////////
    ////////////////////////////////////////////////////////////////////////////////////////////////////////////////////
    // Brute force is to calculate all (student X mentor) combination.
    // The visited/duplicated calculate can be memorized.
    //
    // Takeaways :
    //      XOR ⊕ operation to check digits equality.
    //  	Use mask to record visited record.
    //  	Arrays::fill API.
    public int maxCompatibilitySum(int[][] students, int[][] mentors) {
        // The number of digits needed of the array equals to the number of the mentor combination
        // memo[mask] indicates the max sum of the rest mentor combination with visited one
        // We don't need a 2-d array to record student index because each layer the digit 1 increases by 1, which uniquely indicates the index of student.
        int[] memo = new int[1 << mentors.length];
        // Initialized to be -1 because the score of student * mentor can be zero
        Arrays.fill(memo, -1);
        return dfs(students, mentors, 0, memo, 0);
    }

    // student indicates the depth of the dfs tree
    // mentor indicates the branch factor of the dfs tree
    private int dfs(int[][] students, int[][] mentors, int studentIndex, int[] memo, int visitedMentorMask) {
        if (studentIndex == students.length) {
            return 0;
        }

        if (memo[visitedMentorMask] != -1) {
            return memo[visitedMentorMask];
        }

        for (int mentorIndex = 0; mentorIndex < mentors.length; ++mentorIndex) {
            // 1 << mentorIndex means which mentor it is
            if ((visitedMentorMask & (1 << mentorIndex)) == 0) {
                memo[visitedMentorMask] = Math.max(memo[visitedMentorMask],
                                                   score(students[studentIndex], mentors[mentorIndex])
                                                   + dfs(students, mentors, studentIndex + 1, memo, (visitedMentorMask | (1 << mentorIndex))));
            }
        }
        return memo[visitedMentorMask];
    }

    private int score(int[] a, int[] b) {
        int sum = 0;
        for (int i = 0; i < a.length; ++i) {
            sum += (a[i] ^ b[i] ^ 1);
        }
        return sum;
    }
```
---
# Dynamic Programming
<a id="Leetcode1143" href="https://leetcode.com/problems/longest-common-subsequence/">[Leetcode 1143].</a> Longest Common Subsequence
```java
    public int longestCommonSubsequence(String text1, String text2) {
        int[][] dp = new int[text1.length() + 1][text2.length() + 1];
        for (int i = 0; i < text1.length(); ++i) {
            for (int j = 0; j < text2.length(); ++j) {
                if (text1.charAt(i) == text2.charAt(j)) {
                    dp[i + 1][j + 1] = dp[i][j] + 1;
                } else {
                    dp[i + 1][j + 1] = Math.max(dp[i][j + 1], dp[i + 1][j]);
                }
            }
        }
        return dp[text1.length()][text2.length()];
    }
```
---
# Greedy
---

# Tree
---
## LCA (Lowest Common Ancestor)
* <a id="Leetcode0236" href="https://leetcode.com/problems/lowest-common-ancestor-of-a-binary-tree/">[Leetcode 0236. Lowest Common Ancestor of a Binary Tree]</a> : <a href="https://github.com/lambda826/Algorithms/blob/master/src/coding/leetcode/_10_tree/lowest_common_ancesstor/_0236_Lowest_Common_Ancestor_of_a_Binary_Tree.java">**Solution**</a>
* <a id="Leetcode1644" href="https://leetcode.com/problems/lowest-common-ancestor-of-a-binary-tree-ii/">[Leetcode 1644. Lowest Common Ancestor of a Binary Tree II]</a> : <a href="https://github.com/lambda826/Algorithms/blob/master/src/coding/leetcode/_10_tree/lowest_common_ancesstor/_1644_Lowest_Common_Ancestor_of_a_Binary_Tree_II.java">**Solution**</a>
* <a id="Leetcode1676" href="https://leetcode.com/problems/lowest-common-ancestor-of-a-binary-tree-iv/">[Leetcode 1676. Lowest Common Ancestor of a Binary Tree IV]</a> : <a href="https://github.com/lambda826/Algorithms/blob/master/src/coding/leetcode/_10_tree/lowest_common_ancesstor/_1676_Lowest_Common_Ancestor_of_a_Binary_Tree_IV.java">**Solution**</a>
* <a id="Leetcode1123" href="https://leetcode.com/problems/lowest-common-ancestor-of-deepest-leaves/">[Leetcode 1123. Lowest Common Ancestor of Deepest Leaves]</a> : <a href="https://github.com/lambda826/Algorithms/blob/master/src/coding/leetcode/_10_tree/lowest_common_ancesstor/_1123_Lowest_Common_Ancestor_of_Deepest_Leaves.java">**Solution**</a>
* <a id="Leetcode0235" href="https://leetcode.com/problems/lowest-common-ancestor-of-a-binary-search-tree/">[Leetcode 0235. Lowest Common Ancestor of a Binary Search Tree]</a> : <a href="https://github.com/lambda826/Algorithms/blob/master/src/coding/leetcode/_10_tree/lowest_common_ancesstor/_0235_Lowest_Common_Ancestor_of_a_Binary_Search_Tree.java">**Solution**</a>
* <a id="Leetcode1650" href="https://leetcode.com/problems/lowest-common-ancestor-of-a-binary-tree-iii/">[Leetcode 1650. Lowest Common Ancestor of a Binary Tree III]</a> : <a href="https://github.com/lambda826/Algorithms/blob/master/src/coding/leetcode/_10_tree/lowest_common_ancesstor/_1650_Lowest_Common_Ancestor_of_a_Binary_Tree_III.java">**Solution**</a>

## Serialization & Deserialization
* <a id="Leetcode0297" href="https://leetcode.com/problems/serialize-and-deserialize-binary-tree/">[Leetcode 0297. Serialize and Deserialize Binary Tree]</a> : <a href="https://github.com/lambda826/Algorithms/blob/master/src/coding/leetcode/_10_tree/serialization/_0297_Serialize_and_Deserialize_Binary_Tree.java">**Solution**</a>
* <a id="Leetcode0449" href="https://leetcode.com/problems/serialize-and-deserialize-bst/">[Leetcode 0449. Serialize and Deserialize BST]</a> : <a href="https://github.com/lambda826/Algorithms/blob/master/src/coding/leetcode/_10_tree/serialization/_0449_Serialize_and_Deserialize_BST.java">**Solution**</a>
* <a id="Leetcode0428" href="master → origin/master">[Leetcode 0428. Serialize and Deserialize N-ary Tree]</a> : <a href="https://github.com/lambda826/Algorithms/blob/master/src/coding/leetcode/_10_tree/serialization/_0428_Serialize_and_Deserialize_N_ary_Tree.java">**Solution**</a>

## Post-order

<a id="Leetcode124" href="https://leetcode.com/problems/binary-tree-maximum-path-sum/">[Leetcode 124].</a> Binary Tree Maximum Path Sum

```java
    // Post-order
    public int maxPathSum(TreeNode root) {
        int[] max = { root.val };
        postOrder(root, max);
        return max[0];
    }

    private int postOrder(TreeNode node, int[] max) {
        if (node != null) {
            int left = Math.max(0, postOrder(node.left, max));
            int right = Math.max(0, postOrder(node.right, max));
            int val = node.val + Math.max(left, right);
            max[0] = Math.max(max[0], node.val + left + right);
            return val;
        } else {
            return 0;
        }
    }
```



## Trie
---
# Graph
## BFS or DFS
<a id="Leetcode785" href="https://leetcode.com/problems/is-graph-bipartite/">[Leetcode 785. Is Graph Bipartite?]</a>
```java
    // 1. Use an array to denote the color of each node;
    // 2. When enqueue the neighbour nodes, color them to the opposite color of current node;
    // 2.1. If any neighbour cannot be colored, return false;
    public static class Solution_BFS {

        public boolean isBipartite(int[][] graph) {
            Queue<Integer> queue = new ArrayDeque<>();
            int[] color = new int[graph.length];
            for (int i = 0; i < graph.length; ++i) {
                if (color[i] == 0) {
                    queue.offer(i);
                    color[i] = 1;
                    while (!queue.isEmpty()) {
                        int curr = queue.poll();
                        for (int nei : graph[curr]) {
                            if (color[nei] == 0) {
                                queue.offer(nei);
                                color[nei] = -color[curr];
                            } else if (color[nei] == color[curr]) {
                                return false;
                            }
                        }
                    }
                }
            }
            return true;
        }
    }
```
```java
    // Similar idea with BFS approach
    // 1. Use an array to denote the color of each node;
    // 2. Color every neighbour to the opposite color of current node.
    public class Solution_DFS {

        public boolean isBipartite(int[][] graph) {
            int[] color = new int[graph.length];
            for (int i = 0; i < graph.length; ++i) {
                if (color[i] == 0 && !DFS(graph, color, i, 1)) {
                    return false;
                }
            }
            return true;
        }

        private boolean DFS(int[][] graph, int[] color, int n, int c) {
            color[n] = c;
            for (int nei : graph[n]) {
                if (color[n] == color[nei]) {
                    return false;
                }
                if (color[nei] == 0 && !DFS(graph, color, nei, -color[n])) {
                    return false;
                }
            }
            return true;
        }
    }
```

## Topological Sorting
<a id="Leetcode207" href="https://leetcode.com/problems/course-schedule/">[Leetcode 207].</a> Course Schedule
**Topological sorting - DFS Approach**
```java
    // Topological sorting - DFS Approach: find a cycle in a graph.
    //      0. Build Graph using Adjacent List representation;
    //      1. For each node, visit if it is not visited;
    //      2. Update the visit status of the current node to be 1 (in the frontier);
    //          2.1 Recursively visit each neighbour (for loop) of the current node;
    //          2.2 Update the visit status of the current node to be 2 (finished visit);
    //
    // Takeaways:
    //      1. Adjacent List (List<Integer>[] adjacentList = new List[numberOfNodes]) to represent a DAG;
    //      2. Use an int[] array to indicate the status of the node:
    //          visited[i] == 0 means node i is unvisited;
    //          visited[i] == 1 means node i is in frontier;
    //          visited[i] == 2 means node i is visited;
    public boolean canFinish_DFS(int numCourses, int[][] prerequisites) {
        List<Integer>[] adjacentList = buildGraph(numCourses, prerequisites);
        int[] visited = new int[numCourses];
        for (int i = 0; i < numCourses; ++i) {
            if (visited[i] == 0) {
                if (containsCycle(adjacentList, i, visited)) {
                    return false;
                }
            }
        }
        return true;
    }

    private boolean containsCycle(List<Integer>[] adjacentList, int current, int[] visited) {
        if (visited[current] == 0) {
            visited[current] = 1; // Current node is in frontier
            if (adjacentList[current] != null) {
                for (int next : adjacentList[current]) {
                    // If the next node is already in the frontier
                    if (visited[next] == 1 || containsCycle(adjacentList, next, visited)) {
                        return true;
                    }
                }
            }
            visited[current] = 2; // Current node is visited
        }
        return false;
    }

    private List<Integer>[] buildGraph(int numCourses, int[][] prerequisites) {
        // Build graph as Adjacent List representation given edges
        List<Integer>[] adjacentList = new List[numCourses];
        for (int[] prerequisite : prerequisites) {
            // Initialize an ArrayList if it's first time visit the node
            if (adjacentList[prerequisite[1]] == null) {
                adjacentList[prerequisite[1]] = new ArrayList<>();
            }
            adjacentList[prerequisite[1]].add(prerequisite[0]); // Add the neighbour into neighbour list
        }
        return adjacentList;
    }
```

**Topological sorting - BFS Approach**
```java
    // Topological sorting - BFS Approach: find a cycle in a graph.
    //      0. Build Graph using Adjacent List representation and In-Degree Array for each node;
    //      1. Enqueue all nodes with zero In-Degree value;
    //      2. BFS
    //          2.1 Add current visiting node into order list;
    //          2.2 Update In-Degrees of each neighbour of current visiting node;
    //          2.3 Enqueue the neighbour if the updated In-Degree becomes zero;
    //      3. Check the size of the order list;
    public boolean canFinish(int numCourses, int[][] prerequisites) {
        // Build Graph using Adjacent List with given edges
        List<Integer>[] adjacentList = new List[numCourses];
        int[] inDegrees = new int[numCourses];
        for (int[] prerequisite : prerequisites) {
            if (adjacentList[prerequisite[1]] == null) {
                adjacentList[prerequisite[1]] = new ArrayList<>();
            }
            adjacentList[prerequisite[1]].add(prerequisite[0]);
            inDegrees[prerequisite[0]]++; // Build inDegree array
        }

        // Enqueue nodes with zero inDegree
        Queue<Integer> zeroInDegreeQueue = new ArrayDeque<>();
        for (int i = 0; i < inDegrees.length; ++i) {
            if (inDegrees[i] == 0) {
                zeroInDegreeQueue.offer(i);
            }
        }

        // BFS
        List<Integer> order = new ArrayList<>();
        while (!zeroInDegreeQueue.isEmpty()) {
            int curr = zeroInDegreeQueue.poll();
            order.add(curr);
            if (adjacentList[curr] != null) {
                for (int next : adjacentList[curr]) {
                    // -1 inDegree for each neighbour of current node
                    // Enqueue if inDegree of the neighbour is zero
                    if (--inDegrees[next] == 0) {
                        zeroInDegreeQueue.offer(next);
                    }
                }
            }
        }
        return order.size() == numCourses;
    }
```

<a id="Leetcode210" href="https://leetcode.com/problems/course-schedule-ii/">[Leetcode 210].</a> Course Schedule II
**Topological sorting - DFS Approach**
```java
    // Topological sorting - DFS Approach
    //      0. Build Graph using Adjacent List representation;
    //      1. For each node, visit if it is not visited;
    //      2. Update the visit status of the current node to be 1 (in the frontier);
    //          2.1 Recursively visit each neighbour (for loop) of the current node;
    //          2.2 Update the visit status of the current node to be 2 (finished visit);
    //          2.3 Update order list;
    public int[] findOrder(int numCourses, int[][] prerequisites) {
        List<Integer>[] adjacentList = buildGraph(numCourses, prerequisites);
        int[] visited = new int[numCourses];
        int[] order = new int[numCourses];
        int[] index = { order.length - 1 };
        for (int i = 0; i < numCourses; ++i) {
            if (visited[i] == 0) {
                if (containsCycle(adjacentList, i, visited, order, index)) {
                    return new int[0];
                }
            }
        }
        return order;
    }

    private boolean containsCycle(List<Integer>[] adjacentList, int current, int[] visited, int[] order, int[] index) {
        if (visited[current] == 0) {
            visited[current] = 1; // Current node is in frontier
            if (adjacentList[current] != null) {
                for (int next : adjacentList[current]) {
                    // If the next node is already in the frontier
                    if (visited[next] == 1 || containsCycle(adjacentList, next, visited, order, index)) {
                        return true;
                    }
                }
            }
            visited[current] = 2; // Current node is visited
            order[index[0]--] = current; // Add current node into the order list after completing visiting the current node
        }
        return false;
    }

    private List<Integer>[] buildGraph(int numCourses, int[][] prerequisites) {
        // Build graph as Adjacent List representation given edges
        List<Integer>[] adjacentList = new List[numCourses];
        for (int[] prerequisite : prerequisites) {
            // Initialize an ArrayList if it's first time visit the node
            if (adjacentList[prerequisite[1]] == null) {
                adjacentList[prerequisite[1]] = new ArrayList<>();
            }
            adjacentList[prerequisite[1]].add(prerequisite[0]); // Add the neighbour into neighbour list
        }
        return adjacentList;
    }
```

**Topological sorting - BFS Approach**
```java
    // Topological sorting - BFS Approach: find a cycle in a graph.
    //      0. Build Graph using Adjacent List representation and In-Degree Array for each node;
    //      1. Enqueue all nodes with zero In-Degree value;
    //      2. BFS
    //          2.1 Add current visiting node into order list;
    //          2.2 Update In-Degrees of each neighbour of current visiting node;
    //          2.3 Enqueue the neighbour if the updated In-Degree becomes zero;
    //      3. Check the size of the order list;
    public int[] findOrder_Topological(int numCourses, int[][] prerequisites) {
        // Build Graph using Adjacent List with given edges
        List<Integer>[] adjacentList = new List[numCourses];
        int[] inDegrees = new int[numCourses];
        for (int[] prerequisite : prerequisites) {
            if (adjacentList[prerequisite[1]] == null) {
                adjacentList[prerequisite[1]] = new ArrayList<>();
            }
            adjacentList[prerequisite[1]].add(prerequisite[0]);
            inDegrees[prerequisite[0]]++; // Build inDegree array
        }

        // Enqueue nodes with zero inDegree
        Queue<Integer> zeroInDegreeQueue = new ArrayDeque<>();
        for (int i = 0; i < inDegrees.length; ++i) {
            if (inDegrees[i] == 0) {
                zeroInDegreeQueue.offer(i);
            }
        }

        // BFS
        int index = 0;
        int[] order = new int[numCourses];
        while (!zeroInDegreeQueue.isEmpty()) {
            int curr = zeroInDegreeQueue.poll();
            order[index++] = curr;
            if (adjacentList[curr] != null) {
                for (int next : adjacentList[curr]) {
                    // -1 inDegree for each neighbour of current node
                    // Enqueue if inDegree of the neighbour is zero
                    if (--inDegrees[next] == 0) {
                        zeroInDegreeQueue.offer(next);
                    }
                }
            }
        }
        return index == order.length ? order : new int[0];
    }
```

<a id="Leetcode310" href="https://leetcode.com/problems/minimum-height-trees/">[Leetcode 310].</a> Minimum Height Trees
**Topological variation - BFS Approach**
```java
    // Topological variation - BFS Approach.
    //      0. Build Graph and inDegree Array;
    //      1. Enqueue terminal nodes who have only one neighbor (exact 1 inDegree);
    //      2. BFS
    //          2.1 Level traverse to remove the terminal nodes from the queue;
    //          2.2 Update inDegree neighbour of current node and enqueue if it becomes a terminal node;
    //          2.3 Break while loop once we reach the point when the queue has less than 3 nodes;
    //
    // Takeaways:
    //      1. If the graph is an undirected graph, then node i is a terminal node when inDegree[i] == 1.
    //      2. Arrays.fill(arr, new ArrayList<>()); will create only one copy of the ArrayList for all entries.
    public List<Integer> findMinHeightTrees(int n, int[][] edges) {
        // Edge case
        if (n == 1) {
            return new ArrayList<>() {{
                add(0);
            }};
        }

        List<Integer>[] adjacentList = new List[n];
        for (int i = 0; i < n; ++i) {
            adjacentList[i] = new ArrayList<>();
        }
        // Build Graph using Adjacent List given edges
        // Build InDegree array given edges
        int[] inDegrees = new int[n];
        for (int[] edge : edges) {
            adjacentList[edge[0]].add(edge[1]);
            adjacentList[edge[1]].add(edge[0]);
            inDegrees[edge[0]]++;
            inDegrees[edge[1]]++;
        }

        Queue<Integer> queue = new ArrayDeque<>();
        // Enqueue terminal nodes, terminal nodes have exact 1 for inDegree
        for (int i = 0; i < n; ++i) {
            if (inDegrees[i] == 1) {
                queue.offer(i);
            }
        }

        int remain = n; // Use to track the number of nodes left
        while (remain > 2) {
            int size = queue.size(); // Level traversal to dequeue all terminal nodes
            while (size-- > 0) {
                --remain;
                int curr = queue.poll();
                for (int neighbour : adjacentList[curr]) {
                    // Update inDegree neighbour of current node and enqueue if it becomes a terminal node
                    if (--inDegrees[neighbour] == 1) {
                        queue.offer(neighbour);
                    }
                }
            }
        }
        return new ArrayList<>(queue);
    }
```
---
# Union-Find
---
# Stack

---
# Monotonic Stack
<a id="Leetcode1130" href="https://leetcode.com/problems/minimum-cost-tree-from-leaf-values/">[Leetcode 1130].</a> Minimum Cost Tree From Leaf Values
```java
    // Given { a, b, c }
    // If a < b, b < c, then sum = ab + bc;
    // If a > b, b > c, then sum = ab + bc;
    //
    // If a < b, b > c, then sum = ab + bc regardless of a > c or a < c;
    // If a > b, b < c, a < c, then sum = ab + ac;
    // If a > b, b < c, a > c, then sum = bc + ac;
    //
    // Observe from above,
    // we always want to multiply the smallest number with the smaller number beside the smallest number.
    // In order to achieve that, we use a monotonic stack to store a decreasing array;
    // Whenever there is a valley point, we pop the number and multiply the smaller number beside it.
    public int mctFromLeafValues(int[] arr) {
        int sum = 0;
        Deque<Integer> queue = new ArrayDeque<>();
        queue.offerLast(Integer.MAX_VALUE);
        for (int i = 0; i < arr.length; ++i) {
            if (arr[i] < queue.peekLast()) {
                queue.offerLast(arr[i]);
            } else {
                while (arr[i] > queue.peekLast()) {
                    int peek = queue.pollLast();
                    sum += peek * Math.min(queue.peekLast(), arr[i]);
                }
                queue.offerLast(arr[i]);
            }
        }
        while (queue.size() > 2) {
            sum += queue.pollLast() * queue.peekLast();
        }
        return sum;
    }
```

# Recursion
<a id="Leetcode21" href="https://leetcode.com/problems/merge-two-sorted-lists/">[Leetcode 21].</a>  Merge Two Sorted Lists
```java
    public ListNode mergeTwoLists_Recursion(ListNode l1, ListNode l2) {
        if (l1 == null) {
            return l2;
        } else if (l2 == null) {
            return l1;
        } else if (l1.val < l2.val) {
            l1.next = mergeTwoLists_Recursion(l1.next, l2);
            return l1;
        } else {
            l2.next = mergeTwoLists_Recursion(l1, l2.next);
            return l2;
        }
    }
```
```java
    public ListNode mergeTwoLists(ListNode l1, ListNode l2) {
        ListNode res = new ListNode(0);
        ListNode curr = res;
        while (l1 != null && l2 != null) {
            if (l1.val < l2.val) {
                curr.next = l1;
                l1 = l1.next;
            } else {
                curr.next = l2;
                l2 = l2.next;
            }
            curr = curr.next;
        }
        if (l1 == null) {
            curr.next = l2;
        } else {
            curr.next = l1;
        }
        return res.next;
    }
```
# Math

​
<!--stackedit_data:
eyJoaXN0b3J5IjpbMjA0NjE3Mzc2MV19
-->