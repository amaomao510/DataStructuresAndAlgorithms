##### 题目：3Sum
Given an array nums of n integers, are there elements a, b, c in nums such that a + b + c = 0? Find all unique triplets in the array which gives the sum of zero.

Note:

The solution set must not contain duplicate triplets.

~~~
Given array nums = [-1, 0, 1, 2, -1, -4],

A solution set is:
[
  [-1, 0, 1],
  [-1, -1, 2]
]
~~~




思路：类似取2Sum；以一个数为起始值，寻找另外两个和为0-number的情况。
     需要额外考虑去重的情况.
     算法复杂度：0(n*n)

Solution:

~~~
class Solution {
    public List<List<Integer>> threeSum(int[] nums) {
        List<List<Integer>> res = new ArrayList<>();
        if(nums.length < 3)
            return res;
        Arrays.sort(nums);
        for(int i = 0; i < nums.length - 2; i++){
            if(i == 0 || (i > 0 && nums[i] != nums[i -1])){
                int lo = i + 1, hi = nums.length -1, sum = 0 - nums[i];
                while(lo < hi){
                    if(nums[lo] + nums[hi] == sum){
                        res.add(Arrays.asList(nums[i], nums[lo], nums[hi]));
                        while(lo < hi && nums[lo] == nums[lo + 1])
                            lo++;
                        while(lo < hi && nums[hi] == nums[hi - 1])
                            hi--;
                        lo++;
                        hi--;
                    }
                    else if(nums[lo] + nums[hi] < sum){
                        lo++;
                    }else
                        hi--;
                }
                
            }
        }
        return res;
    }
}
~~~

