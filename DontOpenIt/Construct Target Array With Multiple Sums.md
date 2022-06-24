## 1354. Construct Target Array With Multiple Sums

You are given an array target of n integers. From a starting array arr consisting of n 1's, you may perform the following procedure :

let x be the sum of all elements currently in your array.
choose index i, such that 0 <= i < n and set the value of arr at index i to x.
You may repeat this procedure as many times as needed.
Return true if it is possible to construct the target array from arr, otherwise, return false.

```
class Solution {
public:
    bool isPossible(vector<int>& target) {
        priority_queue<int> pq;
        long long sum = 0;
        for(auto num : target){
            pq.push(num);
            sum+=num;
        }
        while(pq.top() != 1){
            sum -= pq.top();
            if(sum == 0 || sum >= pq.top()) return false;
            int old = pq.top()%sum;
            if(sum != 1 && old == 0) return false;
            pq.pop();
            pq.push(old);
            sum += (old);
        }
        return true;
    }
};
```

If dont understood or have any better solution, lets discuss it on [discussions](https://github.com/Jimmy5467/CP/discussions). 

Star it, if helped ⭐.
