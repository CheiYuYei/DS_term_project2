#include<iostream>
using namespace std;

int main()
{
  int m;
  int n;
  int Battery;
  cin >> m >> n >> Battery;
  char floor[m][n]={} ;

  int robot_m[100],robot_n[100];
  int Battery_now = Battery;
  for(int i=0;i<m;i++)
  {
      for(int j=0;j<n;j++)
      {
          cin >> floor[i][j];
          if (floor[i][j]=='R'){
            robot_m[0] = i;
            robot_n[0] = j;
          }
      }
  }
  bool finish = false;
  bool stop=false;
  int step=0;
  int been_found[m][n];
  int been_visit[m][n];
  int print_step=0;
  int print_m[300],print_n[300];
  print_m[0]=robot_m[0];
  print_n[0]=robot_n[0];
  for(int i=0;i<m;i++)
  {
      for(int j=0;j<n;j++)
      {
          been_found[i][j] = 0;
          been_visit[i][j] = 0;
      }
  }
  bool Backward[300];
  if(robot_m[0]==0 || robot_n[0]==0 || robot_m[0]==m-1 || robot_n[0]==n-1){
  while(!finish)
  {
      {
      if(robot_n[step]==0)
      {
          {
              been_found[robot_m[step]][robot_n[step]+1]=1;
              been_visit[robot_m[step]][robot_n[step]+1]=1;
              robot_m[step+1]=robot_m[step];
              robot_n[step+1]=robot_n[step]+1;
              int n=0;
              if(floor[robot_m[step+1]][robot_n[step+1]+1]=='0'){
                n=n+1;
              }
              if(floor[robot_m[step+1]+1][robot_n[step+1]]=='0'){
                n=n+1;
              }
              if(floor[robot_m[step+1]-1][robot_n[step+1]]=='0'){
                n=n+1;
              }
              if(n==1)
                Backward[step+1]=true;
              else Backward[step+1]=false;
              Battery_now=Battery_now-1;
              print_step=print_step+1;
              print_m[print_step]=robot_m[step+1];
              print_n[print_step]=robot_n[step+1];
              step=step+1;
              continue;
          }
      }
      else if(robot_m[step]==0)
      {
          //if(floor[robot_m[step]+1][robot_n[step]]=='0')
          {
              been_found[robot_m[step]+1][robot_n[step]]=1;
              been_visit[robot_m[step]+1][robot_n[step]]=1;
              robot_m[step+1]=robot_m[step]+1;
              robot_n[step+1]=robot_n[step];
              int n=0;
              if(floor[robot_m[step+1]][robot_n[step+1]+1]=='0'){
                n=n+1;
              }
              if(floor[robot_m[step+1]+1][robot_n[step+1]]=='0'){
                n=n+1;
              }
              if(floor[robot_m[step+1]][robot_n[step+1]-1]=='0'){
                n=n+1;
              }
              if(n==1)
                Backward[step+1]=true;
              else Backward[step+1]=false;
              Battery_now=Battery_now-1;
              print_step=print_step+1;
              print_m[print_step]=robot_m[step+1];
              print_n[print_step]=robot_n[step+1];
              step=step+1;
              continue;
          }
      }
      else if(robot_n[step]==n-1)
      {
          {
              been_found[robot_m[step]][robot_n[step]-1]=1;
              been_visit[robot_m[step]][robot_n[step]-1]=1;
              robot_m[step+1]=robot_m[step];
              robot_n[step+1]=robot_n[step]-1;
              int n=0;
              if(floor[robot_m[step+1]+1][robot_n[step+1]]=='0'){
                n=n+1;
              }
              if(floor[robot_m[step+1]-1][robot_n[step+1]]=='0'){
                n=n+1;
              }
              if(floor[robot_m[step+1]][robot_n[step+1]-1]=='0'){
                n=n+1;
              }
              if(n==1)
                Backward[step+1]=true;
              else Backward[step+1]=false;
              Battery_now=Battery_now-1;
              print_step=print_step+1;
              print_m[print_step]=robot_m[step+1];
              print_n[print_step]=robot_n[step+1];
              step=step+1;
              continue;
          }
      }
      else if(robot_m[step]==m-1)
      {
          {
              been_found[robot_m[step]-1][robot_n[step]]=1;
              been_visit[robot_m[step]-1][robot_n[step]]=1;
              robot_m[step+1]=robot_m[step]-1;
              robot_n[step+1]=robot_n[step];
              int n=0;
              if(floor[robot_m[step+1]][robot_n[step+1]+1]=='0'){
                n=n+1;
              }
              if(floor[robot_m[step+1]-1][robot_n[step+1]]=='0'){
                n=n+1;
              }
              if(floor[robot_m[step+1]][robot_n[step+1]-1]=='0'){
                n=n+1;
              }
              if(n==1)
                Backward[step+1]=true;
              else Backward[step+1]=false;
              Battery_now=Battery_now-1;
              print_step=print_step+1;
              print_m[print_step]=robot_m[step+1];
              print_n[print_step]=robot_n[step+1];
              step=step+1;
              continue;
          }
      }
      else
      {
          if(floor[robot_m[step]-1][robot_n[step]]=='0')
          {
              if(been_found[robot_m[step]-1][robot_n[step]]==0){
                    been_found[robot_m[step]-1][robot_n[step]]=1;
                    been_visit[robot_m[step]-1][robot_n[step]]=1;
                    robot_m[step+1]=robot_m[step]-1;
                    robot_n[step+1]=robot_n[step];
                    int n=0,m=0;
                    if(floor[robot_m[step+1]][robot_n[step+1]+1]=='0'){
                            n=n+1;
                            m=m+1;
                    }
                    if(floor[robot_m[step+1]-1][robot_n[step+1]]=='0'){
                            n=n+1;
                            m=m+1;
                    }
                    if(floor[robot_m[step+1]][robot_n[step+1]-1]=='0'){
                            n=n+1;
                            m=m+1;
                    }
                    if(floor[robot_m[step+1]+1][robot_n[step+1]]=='0'){
                            n=n+1;
                            m=m+1;
                    }
                    if(floor[robot_m[step+1]+1][robot_n[step+1]+1]=='0'){
                            n=n+1;
                    }
                    if(floor[robot_m[step+1]-1][robot_n[step+1]+1]=='0'){
                            n=n+1;
                    }
                    if(floor[robot_m[step+1]-1][robot_n[step+1]-1]=='0'){
                            n=n+1;
                    }
                    if(floor[robot_m[step+1]+1][robot_n[step+1]-1]=='0'){
                            n=n+1;
                    }
                    if(n<=4 && m>1 && Backward[step]==true)
                    {
                        Backward[step+1]=true;
                    }
                    else{
                            if(m>=3)
                            Backward[step+1]=false;
                            else if(n>3)
                                Backward[step+1]=true;
                            else Backward[step+1]=false;
                    }
                    Battery_now=Battery_now-1;
                    print_step=print_step+1;
                    print_m[print_step]=robot_m[step+1];
                    print_n[print_step]=robot_n[step+1];
                    step=step+1;
                    continue;
              }
          }
          if(floor[robot_m[step]+1][robot_n[step]]=='0')
          {
              if(been_found[robot_m[step]+1][robot_n[step]]==0){
                    been_found[robot_m[step]+1][robot_n[step]]=1;
                    been_visit[robot_m[step]+1][robot_n[step]]=1;
                    robot_m[step+1]=robot_m[step]+1;
                    robot_n[step+1]=robot_n[step];
                    int n=0,m=0;
                    if(floor[robot_m[step+1]][robot_n[step+1]+1]=='0'){
                            n=n+1;
                            m=m+1;
                    }
                    if(floor[robot_m[step+1]-1][robot_n[step+1]]=='0'){
                            n=n+1;
                            m=m+1;
                    }
                    if(floor[robot_m[step+1]][robot_n[step+1]-1]=='0'){
                            n=n+1;
                            m=m+1;
                    }
                    if(floor[robot_m[step+1]+1][robot_n[step+1]]=='0'){
                            n=n+1;
                            m=m+1;
                    }
                    if(floor[robot_m[step+1]+1][robot_n[step+1]+1]=='0'){
                            n=n+1;
                    }
                    if(floor[robot_m[step+1]-1][robot_n[step+1]+1]=='0'){
                            n=n+1;
                    }
                    if(floor[robot_m[step+1]-1][robot_n[step+1]-1]=='0'){
                            n=n+1;
                    }
                    if(floor[robot_m[step+1]+1][robot_n[step+1]-1]=='0'){
                            n=n+1;
                    }
                    if(n<=4 && m>1 && Backward[step]==true)
                    {
                        Backward[step+1]=true;
                    }
                    else{
                            if(m>=3)
                            Backward[step+1]=false;
                            else if(n>3)
                                Backward[step+1]=true;
                            else Backward[step+1]=false;
                    }
                    Battery_now=Battery_now-1;
                    print_step=print_step+1;
                    print_m[print_step]=robot_m[step+1];
                    print_n[print_step]=robot_n[step+1];
                    step=step+1;
                    continue;
              }
          }
          if(floor[robot_m[step]][robot_n[step]-1]=='0')
          {
              if(been_found[robot_m[step]][robot_n[step]-1]==0){
                    been_found[robot_m[step]][robot_n[step]-1]=1;
                    been_visit[robot_m[step]][robot_n[step]-1]=1;
                    robot_m[step+1]=robot_m[step];
                    robot_n[step+1]=robot_n[step]-1;
                    int n=0,m=0;
                    if(floor[robot_m[step+1]][robot_n[step+1]+1]=='0'){
                            n=n+1;
                            m=m+1;
                    }
                    if(floor[robot_m[step+1]-1][robot_n[step+1]]=='0'){
                            n=n+1;
                            m=m+1;
                    }
                    if(floor[robot_m[step+1]][robot_n[step+1]-1]=='0'){
                            n=n+1;
                            m=m+1;
                    }
                    if(floor[robot_m[step+1]+1][robot_n[step+1]]=='0'){
                            n=n+1;
                            m=m+1;
                    }
                    if(floor[robot_m[step+1]+1][robot_n[step+1]+1]=='0'){
                            n=n+1;
                    }
                    if(floor[robot_m[step+1]-1][robot_n[step+1]+1]=='0'){
                            n=n+1;
                    }
                    if(floor[robot_m[step+1]-1][robot_n[step+1]-1]=='0'){
                            n=n+1;
                    }
                    if(floor[robot_m[step+1]+1][robot_n[step+1]-1]=='0'){
                            n=n+1;
                    }
                    if(n<=4 && m>1 && Backward[step]==true)
                    {
                        Backward[step+1]=true;
                    }
                    else{
                            if(m>=3)
                            Backward[step+1]=false;
                            else if(n>3)
                                Backward[step+1]=true;
                            else Backward[step+1]=false;
                    }
                    Battery_now=Battery_now-1;
                    print_step=print_step+1;
                    print_m[print_step]=robot_m[step+1];
                    print_n[print_step]=robot_n[step+1];
                    step=step+1;
                    continue;
              }
          }
          if(floor[robot_m[step]][robot_n[step]+1]=='0')
          {
              if(been_found[robot_m[step]][robot_n[step]+1]==0){
                    been_found[robot_m[step]][robot_n[step]+1]=1;
                    been_visit[robot_m[step]][robot_n[step]+1]=1;
                    robot_m[step+1]=robot_m[step];
                    robot_n[step+1]=robot_n[step]+1;
                    int n=0,m=0;
                    if(floor[robot_m[step+1]][robot_n[step+1]+1]=='0'){
                            n=n+1;
                            m=m+1;
                    }
                    if(floor[robot_m[step+1]-1][robot_n[step+1]]=='0'){
                            n=n+1;
                            m=m+1;
                    }
                    if(floor[robot_m[step+1]][robot_n[step+1]-1]=='0'){
                            n=n+1;
                            m=m+1;
                    }
                    if(floor[robot_m[step+1]+1][robot_n[step+1]]=='0'){
                            n=n+1;
                            m=m+1;
                    }
                    if(floor[robot_m[step+1]+1][robot_n[step+1]+1]=='0'){
                            n=n+1;
                    }
                    if(floor[robot_m[step+1]-1][robot_n[step+1]+1]=='0'){
                            n=n+1;
                    }
                    if(floor[robot_m[step+1]-1][robot_n[step+1]-1]=='0'){
                            n=n+1;
                    }
                    if(floor[robot_m[step+1]+1][robot_n[step+1]-1]=='0'){
                            n=n+1;
                    }
                    if(n<=4 && m>1 && Backward[step]==true)
                    {
                        Backward[step+1]=true;
                    }
                    else{
                            if(m>=3)
                            Backward[step+1]=false;
                            else if(n>3)
                                Backward[step+1]=true;
                            else Backward[step+1]=false;
                    }
                    Battery_now=Battery_now-1;
                    print_step=print_step+1;
                    print_m[print_step]=robot_m[step+1];
                    print_n[print_step]=robot_n[step+1];
                    step=step+1;
                    continue;
              }
          }

          print_step=print_step+1;
          step=step-1;
          print_n[print_step]=robot_n[step];
          print_m[print_step]=robot_m[step];
          Battery_now=Battery_now-1;
      }
      }
      else if(Battery_now<=Battery/2)
      {
          if(!stop){
          if(Backward[step]==true)
          {
              been_found[robot_m[step]][robot_n[step]]=0;
          }
          else if(Backward[step]==false && Backward[step-1]==true)
          {
                    int n=0;
                    if(floor[robot_m[step]][robot_n[step]+1]=='0'){
                            n=n+1;
                    }
                    if(floor[robot_m[step]-1][robot_n[step]]=='0'){
                            n=n+1;
                    }
                    if(floor[robot_m[step]][robot_n[step]-1]=='0'){
                            n=n+1;
                    }
                    if(floor[robot_m[step]+1][robot_n[step]]=='0'){
                            n=n+1;
                    }
                    if(n<=4 && n>1)
                        been_found[robot_m[step]][robot_n[step]]=0;
                    else{
                            been_found[robot_m[step]][robot_n[step]]=1;
                            floor[robot_m[step]][robot_n[step]]='1';
                    }
          }
          else
          {
              been_found[robot_m[step]][robot_n[step]]=1;
              floor[robot_m[step]][robot_n[step]]='1';
          }}
          else been_found[robot_m[step]][robot_n[step]]=1;
          if(step==0)
          {
              Battery_now=Battery;
          }
          else
          {
              print_step=print_step+1;
              step=step-1;
              print_n[print_step]=robot_n[step];
              print_m[print_step]=robot_m[step];
              Battery_now=Battery_now-1;
          }
      }

      bool been=false;
      for(int i=0;i<m;i++)
      {
          for(int j=0;j<n;j++)
          {
              if(been_visit[i][j]==0 && floor[i][j]=='0')
              {
                  i=m;j=n;
                  been=false;
              }
              else
                been=true;
          }
      }


      if(step==0 && been)
        break;
      else finish=false;
  }
  }

  cout << print_step << endl;
  for(int k=0;k<=print_step;k++)
  {
      cout << print_m[k] << " " << print_n[k] << endl;
  }

}
