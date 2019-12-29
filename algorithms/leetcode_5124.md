# 5124[顺次数](https://leetcode-cn.com/problems/sequential-digits/)

## description

我们定义「顺次数」为：每一位上的数字都比前一位上的数字大 1 的整数。

请你返回由 [low, high] 范围内所有顺次数组成的 有序 列表（从小到大排序）。

示例 1：

```
输出：low = 100, high = 300
输出：[123,234]
```
示例 2：

```
输出：low = 1000, high = 13000
输出：[1234,2345,3456,4567,5678,6789,12345]
```

提示：

10 <= low <= high <= 10^9

## my solution

```c++
class Solution {
public:
    vector<int> sequentialDigits(int low, int high) {
        vector<int> result;
        int gap=0, base=0;
        int n = low;
        while (n) {
            base = (base%10+1) + base*10;
            gap = gap*10 + 1;
            n /= 10;
        }
        int cur = base;
        while (cur < low) {
            if (cur%10 == 9) {
                base = (base%10+1) + base*10;
                gap = gap*10 + 1;
                cur = base;
            } else {
                cur += gap;
            }
        }
        while (cur < high) {
            result.emplace_back(cur);
            if (cur%10 == 9) {
                base = (base%10+1) + base*10;
                gap = gap*10 + 1;
                cur = base;
            } else {
                cur += gap;
            }
        }
        return result;
    }
};
```

## time and space complexity

这个时间复杂度怎么分析呢？输入范围是固定的...

S(n) = O(1)
