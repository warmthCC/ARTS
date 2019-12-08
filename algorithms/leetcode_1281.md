# 1281 [使结果不超过阈值的最小除数](https://leetcode-cn.com/problems/find-the-smallest-divisor-given-a-threshold/)

## description

给你一个整数数组 nums 和一个正整数 threshold  ，你需要选择一个正整数作为除数，然后将数组里每个数都除以它，并对除法结果求和。

请你找出能够使上述结果小于等于阈值 threshold 的除数中 最小 的那个。

每个数除以除数后都向上取整，比方说 7/3 = 3 ， 10/2 = 5 。

题目保证一定有解。

示例 1：

```
输入：nums = [1,2,5,9], threshold = 6
输出：5
解释：如果除数为 1 ，我们可以得到和为 17 （1+2+5+9）。
如果除数为 4 ，我们可以得到和为 7 (1+1+2+3) 。如果除数为 5 ，和为 5 (1+1+1+2)。
```

示例 2：

```
输入：nums = [2,3,5,7,11], threshold = 11
输出：3
```

示例 3：

```
输入：nums = [19], threshold = 5
输出：4
``` 

提示：

1 <= nums.length <= 5 * 10^4

1 <= nums[i] <= 10^6

nums.length <= threshold <= 10^6

## my solution

二分查找
为了找到满足条件的正整数N，先确定N的上下限。

根据题目有：

![](1281_1.png)

所以N的上下限为

![](1281_2.png)

```c++
class Solution {
public:
    int smallestDivisor(vector<int>& nums, int threshold) {
        // binary search
        int lo = 0, hi = 0;
        for (auto n : nums) {
            lo += n/threshold;
            hi = max(hi, n);
        }
        lo = max(1,lo);
        while (lo < hi) {
            int mid = lo + ((hi-lo) >> 1);
            int curres = 0;
            for (auto n:nums) {
                curres += divided(n,mid);
            }
            if (curres <= threshold) {
                hi = mid;
            } else {
                lo = mid+1;
            }
        }
        return lo;
    }

    int divided (int n, int div) {
        int result = n/div;
        if (div * result < n) {
            ++result;
        }
        return result;
    }
};
```

## time and space complexity

T(N) = O(max(N,log(max(nums)-max(1,lo))))

S(N) = O(1)
