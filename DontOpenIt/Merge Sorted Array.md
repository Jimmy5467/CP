## 88. Merge Sorted Array

You are given two integer arrays nums1 and nums2, sorted in non-decreasing order, and two integers m and n, representing the number of elements in nums1 and nums2 respectively.

Merge nums1 and nums2 into a single array sorted in non-decreasing order.

The final sorted array should not be returned by the function, but instead be stored inside the array nums1. To accommodate this, nums1 has a length of m + n, where the first m elements denote the elements that should be merged, and the last n elements are set to 0 and should be ignored. nums2 has a length of n.

```
class Solution {
public:
    void merge(vector<int>& n1, int m, vector<int>& n2, int n) {
        int p1=m-1,p2=n-1,len=n1.size()-1;
        while(p1 >= 0 && p2 >= 0){
            if(n1[p1]>n2[p2]){
                n1[len]=n1[p1];
                p1--;
                len--;
            }   
            else{
                n1[len]=n2[p2];
                p2--;
                len--;
            }
        }
        while(p2>=0){
            n1[len]=n2[p2];
            p2--;
            len--;
        }
    }
};
```

If dont understood or have any better solution, lets discuss it on [discussions](https://github.com/Jimmy5467/CP/discussions). 

Star it, if helped ⭐.
