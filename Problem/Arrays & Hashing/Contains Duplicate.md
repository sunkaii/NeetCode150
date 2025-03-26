# Contains Duplicate

## Description
Give an integer array ```nums```, if any values in ```nums``` appear more than once, return ```true```, otherwise return ```false```
## Example
Example 1
```
Input: nums = [1, 2, 3, 3]

Output: true
```
Example 2
```
Input: nums = [1, 2, 3, 4]

Output: false
```
## Approach
1. Brute Force
    Two for loop, traverse all elements.(TLE in LeetCode but Accepted in NeetCode)
2. Sort
    Sort ```nums``` in the beginning, so we can use only one for loop.
3. Hash Set
    One for loop, put element into set.
## Considerations
- $1$ <= nums.length <= $10^5$
## Solution
#### language: CPP
1. Brute Force
```
class Solution {
public:
    bool hasDuplicate(vector<int>& nums) {
        for(int i=0; i<nums.size(); i++){
            for(int j=i+1; j<nums.size(); j++){
                if(nums[i]==nums[j]) return true;
            }
        }
        return false;
    }
};
```
2. Sort
```
class Solution {
public:
    bool hasDuplicate(vector<int>& nums) {
        sort(nums.begin(), nums.end());
        for (int i=1; i<nums.size(); i++) {
            if(nums[i]==nums[i-1]) return true;
        }
        return false;
    }
};
```
3. Hash Set
```
class Solution {
public:
    bool hasDuplicate(vector<int>& nums) {
        unordered_set<int> set;
        for(int i=0; i<nums.size(); i++){
            if(set.count(nums[i])) return true;
            set.insert(nums[i]);
        }
        return false;
    }
};
```
## Time Complexity
1. $O(n^2)$
2. $O(nlogn)$
3. $O(n)$
## Reference
- 