## 1074. Number of Submatrices That Sum to Target

Given a matrix and a target, return the number of non-empty submatrices that sum to target.

A submatrix x1, y1, x2, y2 is the set of all cells matrix[x][y] with x1 <= x <= x2 and y1 <= y <= y2.

Two submatrices (x1, y1, x2, y2) and (x1', y1', x2', y2') are different if they have some coordinate that is different: for example, if x1 != x1'.

 ```
 class Solution {
public:
    int numSubmatrixSumTarget(vector<vector<int>>& matrix, int target) {
        int m = matrix.size(),n = matrix[0].size(), count = 0;
        
        for (int i = 0; i < m; i++){      
            vector<int> CumulativeColumns = matrix[i]; 
            for (int j = i; j < m; j++){
                unordered_map<int,int> sumCount;         
                int totalSum = 0;
                
                for (int k = 0; k < n; k++){
                    totalSum += CumulativeColumns[k];        
                    if (totalSum == target) count++;        
                    if (sumCount.count(totalSum-target)) count += sumCount[totalSum-target];
                    sumCount[totalSum]++;                          
                    if (j < m - 1) CumulativeColumns[k] += matrix[j+1][k];   
                }
            }
        }
        return count;
    }
};
 ```
 

If dont understood or have any better solution, lets discuss it on [discussions](https://github.com/Jimmy5467/CP/discussions). 

Star it, if helped ⭐.
