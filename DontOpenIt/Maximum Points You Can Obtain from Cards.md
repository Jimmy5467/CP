## 1423. Maximum Points You Can Obtain from Cards

There are several cards arranged in a row, and each card has an associated number of points. The points are given in the integer array cardPoints.

In one step, you can take one card from the beginning or from the end of the row. You have to take exactly k cards.

Your score is the sum of the points of the cards you have taken.

Given the integer array cardPoints and the integer k, return the maximum score you can obtain.

class Solution {
public:
    int maxScore(vector<int>& a, int k) {
        int n = a.size(), sum=a[0];
        int pre[n], re[n];
        pre[0]=a[0];
        for(int i=1; i<n; i++){
            pre[i] = a[i] + pre[i-1];
            sum+=a[i];
        }
        if(k==n)    return sum;
        int ans=0;
        for(int i=0; i<k; i++){
            int tm = sum - pre[n-k+i] + pre[i];
            ans = max(ans, tm);
        }
        ans = max(ans, sum - pre[n-k-1]);
        ans = max(ans, pre[k-1]);
        return ans;
    }
};
  
  
If dont understood or have any better solution, lets discuss it on [discussions](https://github.com/Jimmy5467/CP/discussions). 

Star it, if helped ⭐.
