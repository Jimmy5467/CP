## 1710. Maximum Units on a Truck

You are assigned to put some amount of boxes onto one truck. You are given a 2D array boxTypes, where boxTypes[i] = [numberOfBoxesi, numberOfUnitsPerBoxi]:

numberOfBoxesi is the number of boxes of type i.
numberOfUnitsPerBoxi is the number of units in each box of the type i.
You are also given an integer truckSize, which is the maximum number of boxes that can be put on the truck. You can choose any boxes to put on the truck as long as the number of boxes does not exceed truckSize.

Return the maximum total number of units that can be put on the truck.

```
class Solution {
public:
    int maximumUnits(vector<vector<int>>& boxTypes, int truckSize) {
        sort(boxTypes.begin(), boxTypes.end(),
          [] (const vector<int> &a, const vector<int> &b)
          {
              return a[1] > b[1];
          });
        int i=0,ans=0;
        while(truckSize>0 && i<boxTypes.size()){
            truckSize -= boxTypes[i][0];
            ans += boxTypes[i][0] * boxTypes[i][1];
            i++;
        }
        if(truckSize<0){
            i--;
            ans += truckSize*boxTypes[i][1];
        }
        return ans;
    }
};
```

If dont understood or have any better solution, lets discuss it on [discussions](https://github.com/Jimmy5467/CP/discussions). 

Star it, if helped ⭐.
