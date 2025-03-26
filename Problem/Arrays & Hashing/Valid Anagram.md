# Valid Anagram

## Description
Give two string ```s``` and ```t```, if they have are anagrams, return ```true```, otherwise return ```false```.
Anagram means string contain same characters with other one, although they are not in same order.
## Example
Example 1
```
Input: s = "racecar", t = "carrace"

Output: true
```
Example 2
```
Input: s = "jar", t = "jam"

Output: false
```
## Approach
1. Sort two string respectively, then compare them.
2. Calculate character's appear time in each string, compare them.
## Considerations
- ```s``` and ```t``` consist of lowercase English letters.
## Solution
#### language: CPP
1. Sort
```
class Solution {
public:
    bool isAnagram(string s, string t) {
        if(s.size()!=t.size()) return false;
        sort(s.begin(), s.end());
        sort(t.begin(), t.end());
        return s==t;
    }
};
```
2. Calculate character's appear time
```
class Solution {
public:
    bool isAnagram(string s, string t) {
        if(s.size()!=t.size()) return false;
        vector<int> record_s(26, 0), record_t(26, 0); // unordered_map is also feasible.
        for(int i=0; i<s.size(); i++){
            record_s[s[i]-'a']++;
            record_t[t[i]-'a']++;
        }
        return record_s==record_t;
    }
};
```
## Time Complexity
1. $O(nlogn+mlogm)$
2. $O(n+m)$
## Reference
- [What is Anagram](https://en.wikipedia.org/wiki/Anagram)