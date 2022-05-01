# LeetCode 刷题记录

[toc]

## 两数之和

给定一个整数数组 nums 和一个整数目标值 target，请你在该数组中找出 和为目标值 target  的那 两个 整数，并返回它们的数组下标。

你可以假设每种输入只会对应一个答案。但是，数组中同一个元素在答案里不能重复出现。

你可以按任意顺序返回答案。

来源：力扣（LeetCode）
链接：https://leetcode-cn.com/problems/two-sum

### 暴力解法

```python
def twoSum(nums, target):
	for i in range(len(nums)):
		t = target - nums[i]
		for j in range(i+1, len(nums)):
			if t == nums[j]: return [i, j]
```

执行用时1468ms。

```Python
def twoSum(nums, target):
    lens = len(nums)
    for i in range(1, lens):
        t = target - nums[i]
        s = nums[:i]
        if t in s: return [s.index(t), i]
```

执行用时348ms。

### Hash Map

使用哈希表加速查询时间。

```python
def twoSum(self, nums, target):
    hashmap = {}
    for i, num in enumerate(nums):
        t = target - num
        if t in hashmap: return [hashmap[t], i]
        else: hashmap[num] = i
```

执行用时20ms。

## 最小差值I

给你一个整数数组 $nums$，和一个整数 $k$ 。

在一个操作中，您可以选择$ 0 <= i < nums.length$ 的任何索引$ i$ 。将 $nums[i]$ 改为 $nums[i] + x $，其中$ x $是一个范围为$ [-k, k] $的整数。对于每个索引 $i $，最多 只能 应用 一次 此操作。

$nums $的 分数 是$ nums$ 中最大和最小元素的差值。 

在对  nums 中的每个索引最多应用一次上述操作后，返回 $nums$ 的最低 分数 。

来源：力扣（LeetCode）
链接：https://leetcode-cn.com/problems/smallest-range-i

```python
def smallestRangeI(nums, k):
    maxe = max(nums)
    mine = min(nums)

    ans = maxe - mine - 2*k
    
    if ans > 0: return ans
    else: return 0
```

## 删除数组中的重复项

给你一个 升序排列 的数组 $nums$ ，请你 原地 删除重复出现的元素，使每个元素 只出现一次 ，返回删除后数组的新长度。元素的 相对顺序 应该保持 一致 。

由于在某些语言中不能改变数组的长度，所以必须将结果放在数组$nums$的第一部分。更规范地说，如果在删除重复项之后有 $k$ 个元素，那么$ nums $的前$ k $个元素应该保存最终结果。

将最终结果插入$ nums $的前 $k $个位置后返回$ k$ 。

不要使用额外的空间，你必须在 原地 修改输入数组 并在使用 O(1) 额外空间的条件下完成。

链接：https://leetcode-cn.com/leetbook/read/top-interview-questions-easy/x2gy9m/
来源：力扣（LeetCode）

### 贪心算法

```python
def removeDuplicates(nums):
    lens = len(nums)
    for i in range(lens-1, 0, -1):
        if nums[i] == nums[i-1]: 
            lens -= 1
            del nums[i]
    return lens
```

执行时间24ms。

### 双指针
