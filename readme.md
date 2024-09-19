
 completed #days
 
## day 251 ⤵️⤵️
[problem link](https://www.geeksforgeeks.org/problems/parenthesis-checker2744/1)

# code 🚀💯
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

## day 252 ⤵️⤵️
[problem link](https://www.geeksforgeeks.org/problems/reverse-words-in-a-given-string5459/1)

# code 🚀✅
```
    string reverseWords(string str) {
        reverse(str.begin(),str.end());
        int i=0,j=0,n=str.size();
        while(j<n){
            if(str[j]=='.'){
                reverse(str.begin()+i,str.begin()+j);
                i=j+1;
            }
            j++;
        }
        reverse(str.begin()+i,str.end());
        return str;
    }
```
## day 253 🎈
[problem link](https://www.geeksforgeeks.org/problems/facing-the-sun2126/1)

# code 🧑‍💻🧑‍💻🚀
```
 int countBuildings(vector<int> &height) {
        stack<int>st;
        int n=height.size();
        for(int i=n-1;i>=0;i--){
            while(!st.empty() and height[i]>=height[st.top()]){
                st.pop();
            }
            st.push(i);
        }
        return st.size();
    }
```
