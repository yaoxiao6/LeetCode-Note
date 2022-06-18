# DP

- Max subarray --- [Kadane's Algorithm](https://en.wikipedia.org/wiki/Maximum_subarray_problem#Kadane's_algorith)

# Graph

- [Dijkstra's Algorithm](https://leetcode.com/problems/network-delay-time/solution/)

# 双指针
- 必定需要排序 `Arrays.sort(nums);`
- 如果需要“三个指针”，别乱套了，其中一个指针应该就是从前到后扫一遍，以它为定海神针去设计双指针 例题：3sum
- 去重的时候，要用"新的"和"看过的"比较，如果两个都是"新的"就会出事儿！有时候看过的在左边有时候在右边，要注意每一个都认真观察

# String 
- 如果涉及到大小的变化，很喜欢 从后往前 看
- 乾坤大挪移？我用双指针！