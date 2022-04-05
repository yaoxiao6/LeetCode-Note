# 解题思路
- 无序先 sort
- 能用 List 别用 Array
- Null 情况先解决，每次缩短之后，时刻注意 index out of range
- 非线性情况，用 Tabulation 柱状图算法 转化成 linear 的情况
- hashset 可以自动处理重复的情况
- 当我有两个 Array / List 需要 iterate 的时候，尝试 two pointer 

# 基本语言 Syntax
- `?` --- `variable x = (expression) ? value if true : value if false`， 比如 `int a = (nums[i] % 2 == 0) ? b+1 :  b-1;`
- `List<int[]>` 转 `int[][]`: `output.toArray(new int[output.size()][2])`
- List <--> Array
   ```
   List<Integer> sourceList = Arrays.asList(0, 1, 2, 3, 4, 5);
   Integer[] targetArray = sourceList.toArray(new Integer[0]);
   ```
- 找 array 的 max min 
   ```
   import java.util.Arrays;
   import java.util.Collections;

   int min = Collections.min(Arrays.asList(num));
   int max = Collections.max(Arrays.asList(num));
   ```
- 用 List 创建一个 Set: `Set<String> mySet = new HashSet(myList);` 
- `int globalMax = Integer.MIN_VALUE`, `int globalMin = Integer.MAX_VALUE`

# 数据结构
## HashMap
- HashMap 重复 `put()` 同一个 key，会保留最后一个put的数字，相当于 `set()`
- HashMap `get()` 一个不存在的值会返回 null，不会报错，但是如果你去使用这个null可就要 NullPointerExceptions 了
- 无则放0，有则加一，HashMap 这么写最短
```
Map<Integer, Integer> tabPos = new HashMap<>();
for(int i: nums){
   tabPos.putIfAbsent(i, 0);
   tabPos.computeIfPresent(i, (key, value) -> value + 1);
}
```
- [`putIfAbsent()` 和 `computeIfAbsent()` 区别](https://stackoverflow.com/questions/48183999/what-is-the-difference-between-putifabsent-and-computeifabsent-in-java-8-map)

## Queue
- 如何 new 一个 queue --- `Queue<String> layer = new LinkedList<>();`
- `offer("hello");`
- `String a = poll();`
- `.contains()`
- `.isEmpty()`

# 算法

## Two Pointer
- 处理 two pointer 异步 tracer 的时候，考虑使用 
```
int a = (l1 == null) ? 0 : l1.value; 
int b = (l2 == null) ? 0 : l2.value;
``` 
典型例题： 2

## Dynamic Programming 
- 下面这种 $O(m*n)$ 可以用这个 dp 解决： "随身携带目前找到的 minimum， 并且和当前值比较大小，从而找到最大的 difference" 典型例题: 122
```
for(int i = 0; i<nums.length; i++){
   for(int j = i; j<nums.length; j++){
       // some code; 
   }
}
``` 
- 写 dp 的时候，常问自己一个问题：“我加上下一个之后，对于我要求的答案会有什么改变，对于我要求的答案的 complement 又有什么改变”，典型例题：918
- dp 先写出数学表达式再处理代码
- 想出 dp 的关键在于，关注“策略”是什么，怎样可以做到最大
- dp 先想办法暴力遍历所有情况，然后合并那些“A基于B”的情况，一般用来counting，典型例题：139
- 状态机思维：先明确有几种可能的状态，再找到状态之间是如何转换的，然后根据状态之间转换写出关系式，最终使用代码实现它，一般用在find max，典型例题：309 

## DFS
- preorder = top down --- we care "top" first, then we go down
- postorder = bottom up --- we trace to the post first, after dealing with that, we go up. 因为是先处理 bottom，再考虑向上传什么，所以是相当于先探路，考虑两边那边好走，再做选择，然后把目前node最好的选择结果向上传递
- DFS 需要recurrence，而且 return 的值很可能是 local max 和题目要求的 global max 不一样，所以建议分开写，也就是 dfs 专门写个method，然后让 global max 在其中比较，最后返回的是 global max
- 写recurrence，先无脑 base case，然后再管是 top-down 还是 bottom-up，以此决定先 do-something 还是先 call 自己。

## [Bitwise operator](https://www.geeksforgeeks.org/bitwise-operators-in-java/)
| 符号 | 名字       |
| ---- | ---------- |
| `&`  | and        |
| `|`  | or         |
| `^`  | xor        |
| `~`  | complement |
| `<<` |            |
| `>>` |            |