## 26.删除排序数组中的重复项

**题目描述：** 

> 给定一个排序数组，你需要在 原地 删除重复出现的元素，使得每个元素只出现一次，返回移除后数组的新长度。
>
> 不要使用额外的数组空间，你必须在 原地 修改输入数组 并在使用 O(1) 额外空间的条件下完成。



**示例 1:**

``` 
给定数组 nums = [1,1,2], 

函数应该返回新的长度 2, 并且原数组 nums 的前两个元素被修改为 1, 2。 

你不需要考虑数组中超出新长度后面的元素。
```



**示例 2:**

```
给定 nums = [0,0,1,1,1,2,2,3,3,4],

函数应该返回新的长度 5, 并且原数组 nums 的前五个元素被修改为 0, 1, 2, 3, 4。

你不需要考虑数组中超出新长度后面的元素。
```





**解法一：**

- 解题思路

  - 已知条件：给定的是一个排序数组、并要求删除重复的元素、返回数组新长度、而且不能使用额外的数组空间（意味着必须在元素组中进行删除）
  - 思路：先遍历数组，将数组前后项进行对比，假如相同则删除数组后项

- 代码

  ``` javascript
  /**
   * @param {number[]} nums
   * @return {number}
   */
  var removeDuplicates = function(nums) {
      for (var i = 0 ; i < nums.length ; i++) {
          var j = i + 1;
          while(nums[i] === nums[j]) {
              nums.splice(j, 1);
          }
      }
      return nums.length
  };
  ```

- 测试结果

  ![](./result.png)
  
- 算法分析

  - 时间复杂度: `O(n)`
  - 空间复杂度: `O(1)`
  -  逻辑复杂度: `O(n)`



**解法二（借鉴而来）**

- 解题思路

  - 已知条件新增：按照实例一的说法， `[1,1,2] => [1,2,2]` 这样输出也是可以的，所以不需要删除数组元素
  - 思路：遍历数组，将数组数据进行比较，记录重复的长度，将前面的元素更改，并用`数组总长度 - 重复的长度`返回去重的数组长度即可

- 代码

  ``` javascript
  /**
   * @param {number[]} nums
   * @return {number}
   */
  var removeDuplicates = function(nums) {
  	var repeatCount = 0;
    var len = nums.length;
    for (let i = 1; i < len; i++) {
      if (nums[i] === nums[i - 1]) {
        repeatCount++;
      } else {
        nums[i - repeatCount] = nums[i];
      }
    }
    return len - repeatCount;
  };
  ```

- 测试结果

  ![](./result1.png)
  
- 算法分析

  - 时间复杂度: `O(n)`
  - 空间复杂度: `O(1)`
  -  逻辑复杂度: `O(n)`



**总结：**

> 此题做题时，没审好题，下次刷题需谨慎审题