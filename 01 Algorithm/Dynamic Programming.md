## Dynamic Programming
### ~~Introduction~~
### Examples
#### ~~Rod Cutting~~
#### ~~Matrix-Chain Multiplication~~
#### Longest Common Subsequence (LCS)
**1. Problem statement**
> **Longest Common Subsequence (LCS):**
> * We are given two sequences X = { x~1~, x~2~, ... , x~m~ } and Y = { y~1~, y~2~, ... , y~n~ } and wish to find a maximum length common subsequence of X and Y.
>  ---
> **Note:**
> * A **subsequence** of a given sequence is just the given sequence with zero or more elements left out.
>   * Formally, given a sequence X = { x~1~, x~2~, ... , x~m~ }, another sequence Z = { z~1~, z~2~, ..., z~k~ }  is a subsequence of X if there exists a strictly increasing sequence { i~1~, i~2~, ... , i~k~ } of indices of X such that for all j = 1, 2, ..., k, we have x~ij~. 
>   * For example, Z = { B, C, D, B } is a subsequence of X = { A, B, C, B, D, A, B } with corresponding index sequence { 2, 3, 5, 7 }.
> * Given two sequences X and Y, we say that a sequence Z is a **common subsequence** of X and Y if Z is a subsequence of both X and Y. 
>   * For example, if X = { A, B, C, B, D, A, B } and Y  { B, D, C, A, B, A }, the sequence { B, C, A } is a common subsequence of both X and Y. The sequence { B, C, A } is not a longest common subsequence (LCS) of X and Y, however, since it has length 3 and the sequence { B, C, B, A }, which is also common to both X and Y, has length 4. The sequence { B, C, B, A } is an LCS of X and Y , as is the sequence { B, D, A, B }, since X and Y have no common subsequence of length 5 or greater.

**2. Analysis**
> **Step 1: Characterizing a longest common subsequence**
> * Optimal substructure of an LCS
>      LetX = { x~1~, x~2~, ... , x~m~ } and Y = { y~1~, y~2~, ... , y~n~ } be sequences, and let Z = { z~1~, z~2~, ... , z~k~ } be any LCS of X and Y.
>      1. If x~m~ = y~n~, then z~k~ = x~m~ = y~n~ and Z~k-1~ is an LCS of X~m-1~ and Y~n-1~.
>      2. If x~m~ ≠ y~n~, then z~k~ ≠ x~m~ implies that Z is an LCS of X~m-1~ and Y .
>      3. If x~m~ ≠ y~n~, then z~k~ ≠ y~n~ implies that Z is an LCS of X and Y~n-1~.
> ---
> **Step 2: A recursive solution**
> * If x~m~ = y~n~, we must find an LCS of X~m-1~ and Y~n-1~. Appending x~m~ = y~n~ to this LCS yields an LCS of X and Y.
> * If x~m~ ≠ y~n~, then we must solve **two** **subproblems**: finding an LCS of **X~m-1~ and Y** and finding an LCS of **X and Y~n-1~**. Whichever of these two LCSs is longer is an LCS of X and Y
> * To find an LCS of X and Y , we may need to find the LCSs of **X and Y~n-1~** and of **X~m-1~ and Y**. But each of these subproblems has the subsubproblem of finding an LCS of X~m-1~ and Y~n-1~.
![LCS recursive formulation](https://img-blog.csdnimg.cn/7723568e7ec94a71953ebec6e6d25008.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2hleXVueGlhbmc=,size_16,color_FFFFFF,t_70#pic_center)

**3. Java Solution**
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
#### Optimal binary search trees
<!--stackedit_data:
eyJoaXN0b3J5IjpbMjc3MjU5Mjg3XX0=
-->