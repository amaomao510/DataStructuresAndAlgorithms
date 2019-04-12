##### 题目：Tow sum
Given an array of integers, return indices of the two numbers such that they add up to a specific target.

You may assume that each input would have exactly one solution, and you may not use the same element twice.



~~~
Example:

Given nums = [2, 7, 11, 15], target = 9,
Because nums[0] + nums[1] = 2 + 7 = 9,
return [0, 1].
~~~


Solution1:

~~~
class Solution {
    public int[] twoSum(int[] nums, int target) {
        int i,j;
        int length = nums.length;
        for(i = 0; i < length -1; i++){
            for(j = i+1; j < length; j++){
                if(nums[i] + nums[j] == target)
                    return new int[]{i, j};
            }
        }
        
       return new int[]{-1, -1};
    }
}
~~~


Solution2:
思路：通过hashMap来减少运行次数，空间复杂度会增加.

~~~
class Solution {
    public int[] twoSum(int[] nums, int target) {
       HashMap<Integer, Integer> maps = new HashMap();
       for(int i = 0; i < nums.length; i++){
           if(maps.containsKey(target - nums[i]) && maps.get(target- nums[i]) != i)
               return new int[]{maps.get(target- nums[i]), i};
	   //避免同样的值覆盖之前的Index，在比较之后在put当前的number.
           maps.put(nums[i], i);
       } 
        
        return new int[]{};
    }
}
~~~