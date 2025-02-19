# Leetcode-1415

# C++

class Solution {
public:
    void func(int n,vector<string>&v,string s,int a)
    {
        if(s.length()==n)
        {
            v.push_back(s);
            return;
        }
        for(int i=0;i<3;i++)
        {
          if(a==-1||a!=i)
          {
            int b=a;
            a=i;
            s+=char(i+97);
            func(n,v,s,a);
            a=b;
            s.pop_back();
          }
        }
        return;
    }
    string getHappyString(int n, int k) {
        vector<string>v;
        string s="";
        int  a=-1;
        func(n,v,s,a);
        if(v.size()<k)return "";
        return v[k-1];
    }
};

# Python

class Solution:
    def func(self, n, v, s, a):
        if len(s) == n:
            v.append(s)
            return
        
        for i in range(3):
            if a == -1 or a != i:
                b = a
                a = i
                s += chr(i + 97)
                self.func(n, v, s, a)
                a = b
                s = s[:-1]

    def getHappyString(self, n: int, k: int) -> str:
        v = []
        s = ""
        a = -1
        self.func(n, v, s, a)
        return "" if len(v) < k else v[k - 1]

# Java

import java.util.*;

class Solution {
    public void func(int n, List<String> v, StringBuilder s, int a) {
        if (s.length() == n) {
            v.add(s.toString());
            return;
        }
        for (int i = 0; i < 3; i++) {
            if (a == -1 || a != i) {
                int b = a;
                a = i;
                s.append((char) (i + 97));
                func(n, v, s, a);
                a = b;
                s.deleteCharAt(s.length() - 1);
            }
        }
    }

    public String getHappyString(int n, int k) {
        List<String> v = new ArrayList<>();
        StringBuilder s = new StringBuilder();
        int a = -1;
        func(n, v, s, a);
        return v.size() < k ? "" : v.get(k - 1);
    }

    public static void main(String[] args) {
        Solution sol = new Solution();
        System.out.println(sol.getHappyString(3, 9)); // Example test case
    }
}
