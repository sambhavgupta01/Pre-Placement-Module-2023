class Solution {
public:
    int orangesRotting(vector<vector<int>>& grid) {
        int r=grid.size();
        int c=grid[0].size();
        
        int fresh=0;
        queue<pair<int,int>> q;
        
        for(int i=0;i<r;i++){
            for(int j=0;j<c;j++){
                if(grid[i][j]==1)
                    fresh++;
                else if(grid[i][j]==2)
                    q.push({i,j});
            }
        }
        
        vector<pair<int,int>> dir={{0,1},{1,0},{0,-1},{-1,0}};
        
        int time=0;
        
        while(!q.empty()){
            if(!fresh)
                return time;
            int s=q.size();
            time++;
            
            while(s--){
                int x=q.front().first;
                int y=q.front().second;
                q.pop();
                
                
                for(pair<int,int> d:dir){
                    int nx=x+d.first;
                    int ny=y+d.second;
                    
                    if(nx<0||nx>=r||ny<0||ny>=c)
                        continue;
                    
                    if(grid[nx][ny]==1){
                        grid[nx][ny]=2;
                        fresh--;
                        q.push({nx,ny});
                    }
                }
            }
        }
        
        if(fresh==0)
            return time;
        return -1;
    }
};