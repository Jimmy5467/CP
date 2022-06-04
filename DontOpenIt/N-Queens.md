## 51. N-Queens
The n-queens puzzle is the problem of placing n queens on an n x n chessboard such that no two queens attack each other.

Given an integer n, return all distinct solutions to the n-queens puzzle. You may return the answer in any order.

Each solution contains a distinct board configuration of the n-queens' placement, where 'Q' and '.' both indicate a queen and an empty space, respectively.

```
class Solution {
    vector<vector<string>> ans;
public:
    bool isSafe(vector<string> &board, int row, int col){
        for(int i = 0; i<board.size(); ++i){
            if(board[i][col] == 'Q'){return false;}
        }
        int x = row; int y = col;
		
        while(x>=0 && y>=0){
            if(board[x][y] == 'Q'){return false;}
            --x;  --y; 
        }
        
        while(row>=0 && col<board.size()){
            if(board[row][col] == 'Q'){return false;}
            --row; ++col;
        }
        
        return true;
    }
    
    void placeQueen(vector<string> &board, int row){
        if(row == board.size()){
            ans.push_back(board);
            return;
        }
        
        for(int col = 0; col<board.size() ; ++col){
            if(isSafe(board, row, col)){
                board[row][col] = 'Q';
                placeQueen(board, row+1);
                board[row][col] = '.';
            }   
        }
    }
    
    
    vector<vector<string>> solveNQueens(int n) {            
            vector<string> board(n, string(n, '.'));
            placeQueen(board, 0); 
            return ans;
    }
};
```


If dont understood or have any better solution, lets discuss it on [discussions](https://github.com/Jimmy5467/CP/discussions). 

Star it, if helped ⭐.
