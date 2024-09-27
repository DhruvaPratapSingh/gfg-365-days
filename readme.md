
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



## day 254☠️🎉

[problem link](https://www.geeksforgeeks.org/problems/clone-a-linked-list-with-next-and-random-pointer/1)


# code ➡️🤺

```
 Node *copyList(Node *head) {
        Node* temp=head;
        unordered_map<Node*,Node*>m;
        while(temp!=NULL){
            m[temp]=new Node(temp->data);
            temp=temp->next;
        }
        temp=head;
        while(temp!=NULL){
            m[temp]->next=m[temp->next];
            m[temp]->random=m[temp->random];
            temp=temp->next;
        }
        return m[head];
    }
```

## day 255 🚀🎉

[problem link](https://www.geeksforgeeks.org/problems/longest-prefix-suffix2527/1)

# code 🧑‍💻⤵️

```
 int lps(string str) {
        int n=str.size();
         vector<int>lps(n,0);
    int pref=0;
    int suf=1;
    while(suf<n){
        if(str[pref]==str[suf]){
            lps[suf]=pref+1;
            pref++;
            suf++;
        }
        else{
            if(pref==0){
                lps[suf]=0;
                suf++;
            }
            else{
                pref=lps[pref-1];
            }
        }
    }
    return lps[n-1];
    }
```


## day 256 
[problem link](https://www.geeksforgeeks.org/problems/longest-prefix-suffix2527/1)

# code 
```
 int lps(string str) {
        int n=str.size();
         vector<int>lps(n,0);
    int pref=0;
    int suf=1;
    while(suf<n){
        if(str[pref]==str[suf]){
            lps[suf]=pref+1;
            pref++;
            suf++;
        }
        else{
            if(pref==0){
                lps[suf]=0;
                suf++;
            }
            else{
                pref=lps[pref-1];
            }
        }
    }
    return lps[n-1];
    }
```


## day 257
[problem link](https://www.geeksforgeeks.org/problems/find-missing-and-repeating2512/1)

# code

```
sort(arr.begin(),arr.end());
      int mis=0,rep=0;
      for(int i=0;i<n-1;i++){
          if(arr[i]==arr[i+1]) rep=arr[i];
      }
      int a=1;
      for(int i=0;i<n;i++){
          if(arr[i]==a)a++;
      }
      return {rep,a};
    }
```

## day 258
[[problem link](https://www.geeksforgeeks.org/problems/check-if-linked-list-is-pallindrome/1)

# code

```
Node* rev(Node* head){
        Node* prev=NULL;
        Node* curr=head;
        while(curr!=NULL){
            Node* next=curr->next;
            curr->next=prev;
            prev=curr;
            curr=next;
        }
        return prev;
    }
    bool isPalindrome(Node *head) {
        Node* revlist=rev(head);
        Node* tem=head;
        Node* tem2=revlist;
        while(tem!=NULL){
            if(tem->data!=tem2->data)return 0;
            // cout<<tem->data<<" "<<tem2->data;
            tem=tem->next;
            tem2=tem2->next;
        }
        return 1;
    }
```
## day 259
[problem link](https://www.geeksforgeeks.org/problems/roof-top-1587115621/1)
```
int maxStep(vector<int>& arr) {
        int maxi=0,count=0;
        for(int i=1;i<arr.size();i++){
            count = arr[i-1]<arr[i] ? count+1:0;
            maxi=max(maxi,count);
        }
        return maxi;
    }
```

## day 260
[problem link](https://www.geeksforgeeks.org/problems/maximum-of-all-subarrays-of-size-k3101/1)
# code
# 1️⃣ sliding window gives tle
```
 vector<int> max_of_subarrays(int k, vector<int> &arr) {
          vector<int>ans;
        int i=0,j=0,n=arr.size();
        while(j<n){
            if(j-i+1<k){
                j++;
            }
             else if(j-i+1==k){
                 int val=*max_element(arr.begin()+i,arr.begin()+j+1);
                ans.push_back(val);
                i++;
                j++;
            }
        }
        return ans;
    }
```

# 2️⃣ deque method
```
vector<int> max_of_subarrays(int k, vector<int> &arr) {
          vector<int>ans;
        int i=0,j=0,n=arr.size();
        deque<int>dq;
        while(j<n){
            while(!dq.empty() and arr[j]>dq.back()){
                dq.pop_back();
            }
            dq.push_back(arr[j]);
             if(j-i+1==k){
                ans.push_back(dq.front());
                if(dq.front()==arr[i]){
                   dq.pop_front(); 
                }
                i++;
            }
                j++;
        }
        return ans;
    }
```
