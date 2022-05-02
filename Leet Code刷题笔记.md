# LeetCode 刷题记录

- [LeetCode 刷题记录](#leetcode-刷题记录)
  * [两数之和](#两数之和)
    + [暴力解法](#暴力解法)
    + [Hash Map](#hash-map)
  * [最小差值I](#最小差值i)
  * [删除数组中的重复项](#删除数组中的重复项)
    + [贪心算法](#贪心算法)
    + [双指针](#双指针)
  * [旋转数组](#旋转数组)
  * [存在重复元素](#存在重复元素)
  * [只出现一次的数字](#只出现一次的数字)

## 两数之和

给定一个整数数组nums和一个整数目标值target，请你在该数组中找出和为目标值target的那两个整数，并返回它们的数组下标。

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

因为不需要全部查询整个数组，因此只需要拿出数组的一部分进行查询即可，执行时间提高显著。

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

给你一个整数数组nums，和一个整数k。

在一个操作中，您可以选择```0 <= i < nums.length```的任何索引i。将nums[i]改为nums[i]+x，其中x是一个范围为[-k,k]的整数。对于每个索引i，最多只能应用一次此操作。

nums的分数是nums中最大和最小元素的差值。

在对nums中的每个索引最多应用一次上述操作后，返回nums的最低分数。

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

给你一个升序排列的数组nums，请你原地删除重复出现的元素，使每个元素只出现一次，返回删除后数组的新长度。元素的相对顺序应该保持一致。

由于在某些语言中不能改变数组的长度，所以必须将结果放在数组nums的第一部分。更规范地说，如果在删除重复项之后有k个元素，那么nums的前k个元素应该保存最终结果。

将最终结果插入nums的前k个位置后返回k。

不要使用额外的空间，你必须在原地修改输入数组并在使用O(1)额外空间的条件下完成。

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

## 旋转数组


给你一个数组，将数组中的元素向右轮转 k 个位置，其中 k 是非负数。

来源：力扣（LeetCode）
链接：https://leetcode-cn.com/leetbook/read/top-interview-questions-easy/x2skh7/

```python
def rotate(self, nums, k):
    k %= len(nums)
    items = nums[:-k]
    nums[:-k] = []
    nums.extend(items)
    return nums
```

## 存在重复元素

给你一个整数数组 nums 。如果任一值在数组中出现 至少两次 ，返回 true ；如果数组中每个元素互不相同，返回 false 。


来源：力扣（LeetCode）
链接：https://leetcode-cn.com/leetbook/read/top-interview-questions-easy/x248f5/

```python
def containsDuplicate(self, nums):
    hashmap = {}
    for i, e in enumerate(nums):
        if e in hashmap: return True
        hashmap[e] = i
    return False
```

## 只出现一次的数字

给定一个非空整数数组，除了某个元素只出现一次以外，其余每个元素均出现两次。找出那个只出现了一次的元素。

说明：

你的算法应该具有线性时间复杂度。 你可以不使用额外空间来实现吗？


来源：力扣 (LeetCode)
链接：https://leetcode-cn.com/leetbook/read/top-interview-questions-easy/x21ib6/

```python
def singleNumber(self, nums):
    ans = 0
    for i in nums: ans ^= i
    return ans
```














