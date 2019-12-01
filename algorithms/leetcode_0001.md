# 0001 [Two Sum](https://leetcode-cn.com/problems/two-sum/)

## description

Given an array of integers, return indices of the two numbers such that they add up to a specific target.

You may assume that each input would have exactly one solution, and you may not use the same element twice.

Example:

```
Given nums = [2, 7, 11, 15], target = 9,

Because nums[0] + nums[1] = 2 + 7 = 9,
return [0, 1].
```

## my solution

```c++
class Solution {
public:
    vector<int> twoSum(vector<int>& nums, int target) {
        unordered_map<int, int> m;
        vector<int> result;
        for (int i=0; i<nums.size(); ++i) {
            if (m.count(target-nums[i])!=0) {
                result.push_back(m[target-nums[i]]);
                result.push_back(i);
                break;
            }
            m[nums[i]] = i;
        }
        return result;
    }
};
```

## time and space complexity

T(n) = O(n)

S(n) = O(n)
