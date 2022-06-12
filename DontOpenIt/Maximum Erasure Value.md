## 1695. Maximum Erasure Value

You are given an array of positive integers nums and want to erase a subarray containing unique elements. The score you get by erasing the subarray is equal to the sum of its elements.

Return the maximum score you can get by erasing exactly one subarray.

An array b is called to be a subarray of a if it forms a contiguous subsequence of a, that is, if it is equal to a[l],a[l+1],...,a[r] for some (l,r).

```
class Solution {
public:
    int maximumUniqueSubarray(vector<int>& nums) {
        // vector<int> front,back;
        // int sum_front=0, sum_back=0, n=nums.size();
        // std::vector<int>::iterator it;
        // //front calculation
        // for(int i=0;i<n;i++){
        //     it = std::find (front.begin(), front.end(), nums[i]);
        //     if(it==front.end()){
        //         sum_front+=nums[i];
        //         front.push_back(nums[i]);
        //     }
        //     else
        //         break;
        // }
        // for(int i=0;i<n;i++){
        //     it = std::find (back.begin(), back.end(), nums[n-i-1]);
        //     if(it==back.end()){
        //         sum_back+=nums[n-i-1];
        //         back.push_back(nums[n-i-1]);
        //     }
        //     else
        //         break;
        // } 
        // return sum_front>sum_back?sum_front:sum_back;
        
        int l = 0;
        int r = 0;
		int best = 0;
        int score = 0;
        vector<int> vals(10001, 0);
		
        while(r < nums.size()){
            if(vals[nums[r]] == 0){
                vals[nums[r]]++;
                score += nums[r];
                best = max(best, score);
                r++;
            }
            else{
                score -= nums[l];
                vals[nums[l]]--;
                l++;
            }
        }
        return best;
    }
};
```


If dont understood or have any better solution, lets discuss it on [discussions](https://github.com/Jimmy5467/CP/discussions). 

Star it, if helped ⭐.
