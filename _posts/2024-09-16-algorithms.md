---
title: 代码随想录
tags: Algorithms
---

代码随想录的学习笔记。

<!--more-->

# 代码随想录

## 二分查找

注意事项：
- 前提:数组已经排序好了。
- 调用`size()`函数,函数的返回类型为`size_t`,可以定义一个`int`类型变量接收这个值,否则在比较时候可能会报错。
- 使用左闭右闭区间, `right = nums.size() -1;`
- `middle = ( left + right ) / 2`; 可能会导致溢出,因此可以使用等价代换。
- `middle = left + ( right - left ) / 2;`
- 最后没有查找到需要 `return -1`;

算法实现：
```cpp
int binary_search(vector<int> &nums, int target)
{
    int left = 0, right = nums.size() - 1;
    while(left <= right){
        int middle = left + (right - left) / 2;
        if(nums[middle] == target){
            return middle;
        }else if(nums[middle] > target){
            right = middle -1;
        }else if(nums[middle] < target){
            left = middle + 1;
        }
    }
    return -1;
}
```



## 移除元素

1. 暴力算法

算法思路：
- 当遇到`val`的时候,将后面所有的元素复制到前面来，并且覆盖当前元素。
- 后一个元素覆盖前一个元素。
- 注意边界条件，最后一个元素是` nums[size - 1]`,对应的赋值应该是`nums[size - 2] = nums[size - 1]`

算法实现：
```cpp
int removeElement(vector<int> &nums, int val)
{
    int size = nums.size();
    for (int i = 0; i < size; i++)
    {
        if (nums[i] == val)
        {
            for (int j = i; j < size - 1; j++)
            {
                nums[j] = nums[j + 1];
            }
            i--;
            size--;
        }
    }
    return size;
}
```



2. 快慢双指针

算法思路：
- 两个指针从头一起开始，使用`fast_index`遍历整个数组，如果没有遇到`val`，就向前走，如果遇到了`val`，那么`fast_index++`，`slow_index`原地等待，直到`fast_index`遇到不等于`val`的值，将fast_index的值赋值给`slow_index`，然后`slow_index++`。

算法实现：
```cpp
int removeElement(vector<int> &nums, int val)
{
    int fast_index = 0,slow_index = 0;
    int size = nums.size();
    for(;fast_index < size;fast_index++){
        if(nums[fast_index] != val){
            nums[slow_index++] = nums[fast_index];
        }
    }
    return slow_index;
}
```