# Two Sum

## Description
Give an integer array ```nums``` and integer ```target```, return indices of two numbers they add up to ```target```.
## Example
Example 1
```
Input: 
nums = [3,4,5,6], target = 7

Output: [0,1]
```
Example 2
```
Input: nums = [4,5,6], target = 10

Output: [0,2]
```
Example 3
```
Input: nums = [5,5], target = 10

Output: [0,1]
```
## Approach
1. Brute force
    two for loop, check if ```nums[i]+nums[j]==target```.
2. Hash Map
    Record last appear index of every number, and check if ```map[target-nums[i]]``` exist, make sure map result doesn't equal to ```i```;
## Considerations
- 
## Solution
#### language: CPP
1. Brute Force
```
class Solution {
public:
    vector<int> twoSum(vector<int>& nums, int target) {
        for(int i=0; i<nums.size()-1; i++){
            for(int j=i+1; j<nums.size(); j++){
                if(nums[i]+nums[j]==target) return {i,  j};
            }
        }
        return {};
    }
};
```
2. Hash Map
```
class Solution {
public:
    vector<int> twoSum(vector<int>& nums, int target) {
        unordered_map<int, int> map;
        for(int i=0; i<nums.size(); i++){
            map[nums[i]] = i;
        }
        for(int i=0; i<nums.size()-1; i++){
            int diff = target-nums[i];
            if(map.count(diff) && map[diff]!=i){
                return {i, map[diff]};
            }
        }
        return {};
    }
};
```
## Time Complexity
1. $O(n^2)$
2. $O(n)$
## Reference
- 