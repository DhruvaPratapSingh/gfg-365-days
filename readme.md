![Computer-Science-Pictures-HD](https://github.com/user-attachments/assets/a0d37fc5-5902-4bb6-b014-9a5291dcd975)

 completed #days
 
## day 251
[problem link](https://www.geeksforgeeks.org/problems/parenthesis-checker2744/1)

# code
```
 bool ispar(string x)
    {
        stack<char>st;
        for(int i=0;i<x.size();i++){
            if(x[i]=='(' || x[i]=='{' || x[i]=='[')st.push(x[i]);
            else{
                if(!st.empty() and st.top()=='(' and x[i]==')')st.pop();
               else if(!st.empty() and st.top()=='{' and x[i]=='}')st.pop();
                else if(!st.empty() and st.top()=='[' and x[i]==']')st.pop();
               else return 0;
            }
        }
        return st.size()==0;
    }
```
