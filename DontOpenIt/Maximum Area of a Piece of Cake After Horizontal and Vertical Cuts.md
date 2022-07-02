## 1465. Maximum Area of a Piece of Cake After Horizontal and Vertical Cuts

You are given a rectangular cake of size h x w and two arrays of integers horizontalCuts and verticalCuts where:

horizontalCuts[i] is the distance from the top of the rectangular cake to the ith horizontal cut and similarly, and
verticalCuts[j] is the distance from the left of the rectangular cake to the jth vertical cut.
Return the maximum area of a piece of cake after you cut at each horizontal and vertical position provided in the arrays horizontalCuts and verticalCuts. Since the answer can be a large number, return this modulo 109 + 7.

```
class Solution {
public:
    int maxArea(int h, int w, vector<int>& horizontalCuts, vector<int>& verticalCuts) {
        horizontalCuts.insert(horizontalCuts.begin(), 0);  
        horizontalCuts.push_back(h);        
        verticalCuts.insert(verticalCuts.begin(), 0);
        verticalCuts.push_back(w);
        sort(verticalCuts.begin(),verticalCuts.end());
        sort(horizontalCuts.begin(),horizontalCuts.end());
        int maxh=0, maxv=0;
        for(int i=1;i<horizontalCuts.size();i++){
            // cout<<horizontalCuts[i];
            int temp = abs(horizontalCuts[i-1]-horizontalCuts[i]);
            maxh = maxh<temp? temp :maxh;
        }
        // cout<<endl;
        for(int i=1;i<verticalCuts.size();i++){
            int temp = abs(verticalCuts[i-1]-verticalCuts[i]);
            maxv = maxv<temp? temp :maxv;
        }
        // cout<<maxh<<" "<<maxv;
        return (1LL*maxh*maxv) % 1000000007;
    }
};
```

If dont understood or have any better solution, lets discuss it on [discussions](https://github.com/Jimmy5467/CP/discussions). 

Star it, if helped ⭐.
