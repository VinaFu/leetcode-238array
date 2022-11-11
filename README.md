# leetcode-238array

思路可以，做法画的时间太长，属于暴力解题了。
这个题目就是左右分开：所谓左右分开：

1.  brute force：runtime error

    class Solution:
      def productExceptSelf(self, nums: List[int]) -> List[int]:
          res = []
          for i in range(len(nums)):
              # remove the item on index
              new = nums[:i] + nums[i+1:]   //左右分开
              # product of new list
              import numpy as np
              arr = np.array(new)
              x = np.prod(arr)
              res.append(x)
          return res
          
          
2. 高级做法：左右的乘积能不能不用每次都跑一遍？

          1   2   |3|   4
  前乘积   1   2   |6|   24
  后乘积  24  24   |12|   4
         
  例如：选中了3，那么它以前乘积为：2； 它后面的乘积为4.那么前后相乘即可。
       这样每次找一个数就可以了。
       
  难点：后乘积，倒序开乘。倒序的操作哦
         
