## 630. Course Schedule III

There are n different online courses numbered from 1 to n. You are given an array courses where courses[i] = [durationi, lastDayi] indicate that the ith course should be taken continuously for durationi days and must be finished before or on lastDayi.

You will start on the 1st day and you cannot take two or more courses simultaneously.

Return the maximum number of courses that you can take.

```
bool compare(vector<int> &a, vector<int> &b)
{
    if(a[1]==b[1])
        return a[0]<b[0];
    
    return a[1]<b[1];
}
class Solution {
public:
    int scheduleCourse(vector<vector<int>>& courses) {
        sort(courses.begin(),courses.end(),compare);
        priority_queue<int> pq;  
        int last=0; 
        for(int i=0;i<courses.size();i++)
        {
            int duration = courses[i][0], deadline = courses[i][1];
            if(last+duration<=deadline)
            {
                pq.push(duration);
                last+=duration;
            }
            else
            {
                if(!pq.empty()&&duration<pq.top()&&(last-pq.top()+duration<=deadline))
                {
                    last+=(duration-pq.top());
                    pq.pop();
                    pq.push(duration);
                }
            }
        }
        
        return pq.size();
    }
};
```

If dont understood or have any better solution, lets discuss it on [discussions](https://github.com/Jimmy5467/CP/discussions). 

Star it, if helped ⭐.
