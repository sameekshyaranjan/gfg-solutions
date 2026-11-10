## 01. Longest Subarray with Sum K

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/longest-sub-array-with-sum-k0809/1)

### Problem Description

**Task:** Given an array arr[] containing integers and an integer k, your task is to find the length of the longest subarray where the sum of its elements is equal to the given value k. If there is no subarray with sum equal to k, return 0.Examples:Input: arr[] = [10, 5, 2, 7, 1, -10], k = 15

#### Examples

##### Example 1

- **Output:**
```text
0
```
- **Explanation:** No subarray with sum = 5 is present in arr[].

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(n)
- **Expected Auxiliary Space Complexity:** O(n)

### Accepted Solutions (1)

#### Solution 1 (C++)

- **Submitted:** 2026-11-10 19:21:24
- **Status:** Correct
- **Marks:** 4

```cpp
class Solution {
  public:
    int longestSubarray(vector<int>& arr, int k) {
        int n=arr.size();
        int maxlen=0;
        long long sum=0;
        
        map<long long, int> presummap;
        
        for(int i=0;i<n;i++){
            sum=sum+arr[i];
            if(sum==k){
                maxlen=max(maxlen,i+1);
            }
            
            long long rem=sum-k;
            if(presummap.find(rem)!=presummap.end()){
                maxlen=max(maxlen,i-presummap[rem]);
            }
            
            if(presummap.find(sum)==presummap.end()){
                presummap[sum]=i;
            }
        }
        return maxlen;
        
    }
};
```

*Generated on: 11/10/2026, 7:28:08 PM*