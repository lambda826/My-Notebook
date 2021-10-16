# Merge Sort
## Top-down Merge Sort
> Process (Divide-and-Conquer paradigm):
>  - Divide the unsorted list into n sublists, each comprising 1 element (a list of 1 element is supposed sorted).
>  ![在这里插入图片描述](https://img-blog.csdnimg.cn/96989a3658de434da188f65ec0ff7305.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2hleXVueGlhbmc=,size_16,color_FFFFFF,t_70#pic_center)
>  - Repeatedly merge sublists to produce newly sorted sublists until there is only 1 sublist remaining. This will be the sorted list.
![在这里插入图片描述](https://img-blog.csdnimg.cn/daf08b0307994b90adfdcacaddc44d1c.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2hleXVueGlhbmc=,size_16,color_FFFFFF,t_70#pic_center)
>---
> Performance
> - **Stable**
> - Time Complexity
>   - Average: **O(n log n)**
>  - Space Complexity
>    - O(n)
> ---
> Note
> 
### Implementation
```java

```
---
## ​Bottom-Up Merge Sort
> Process:
> - The Bottom-Up merge sort approach uses iterative methodology.
> It starts with the “single-element” array, and combines two adjacent elements and also sorting the two at the same time.
> The combined-sorted arrays are again combined and sorted with each other until one single unit of sorted array is achieved.
>  ---
>![在这里插入图片描述](https://img-blog.csdnimg.cn/bf7376b583424760852bc4e2229af745.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2hleXVueGlhbmc=,size_16,color_FFFFFF,t_70#pic_center)
>![在这里插入图片描述](https://img-blog.csdnimg.cn/85f8c2b5b8ed46a4bfd4dad314640e61.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2hleXVueGlhbmc=,size_16,color_FFFFFF,t_70#pic_center)
![在这里插入图片描述](https://img-blog.csdnimg.cn/88a8bb5848a84c379285234368c5f67b.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2hleXVueGlhbmc=,size_16,color_FFFFFF,t_70#pic_center)
> 
>---
> Performance
> - **Stable/Unstable**
> - Time Complexity
>   - Average: **O(n log n)**
>  - Space Complexity
>    - O(n)
> ---
> Note
> 
### Implementation
```java

```
---

## Space Improvement
> Approach: (Euclidean Division)
>  * For integer types, merge sort can be made inplace using some mathematics trick of modulus and division. That means storing two elements value at one index and can be extracted using modulus and division. 
>    * First we have to find a value greater than all the elements of the array.
>    * Now we can store the original value as modulus and the second value as division.
>    * Suppose we want to store arr[i] and arr[j] both at index i(means in arr[i]).
>    * First we have to find a ‘maxval’ greater than both arr[i] and arr[j].
>    * Now we can store as arr[i] = arr[i] + arr[j]*maxval.
>    * Now arr[i]%maxval will give the original value of arr[i] and arr[i]/maxval will give the value of arr[j].
>    * So below is the implementation on merge sort.
>  ---
> Possible issues in Merging:
> 1. If current number is Integer.MAX then new encoded value which is usually greater than current element will cause integer **overflow** and data corruption (In python there is no limit to number size so this issue will not occur).
> 2. Doesn’t handle **negative numbers** (ie, when encoding a -ve number(current) with another -ve number(chosen smallest) the sign can’t be preserved since both numbers have -ve sign. Also absolute values must be used when computing dividend = divisor * quotient + remainder (divisor = maxele, quotient = smallest, remainder = original) and sign must be restored, still it might not work due to sign preservation issue.
> 3. Only applicable to **Unsigned integers**, like indexes which are usually non-negative.
> 4. AUX = O(n) in worst case, assuming in a language like python where there is no limit to word/integer size, when input array elements are almost at Integer.MAX, then encoded value will require possibly 2x bits space to represent new number, the 2x bit space on whole can become +1x array size, which is almost like creating an AUX array but in an indirect way.
> 5. mod and division operations are the **costliest**, hence reduces overall performance (upto some extent).

```java

```
<!--stackedit_data:
eyJoaXN0b3J5IjpbOTk2NzkyOTMwXX0=
-->