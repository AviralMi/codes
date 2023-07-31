class Solution {
public:
    string makeFancyString(string s) {
        string r="";
        int c=1;
        for(int i=0;i<s.size();i++){
            if(s[i]==s[i+1])    c++;
            else    c=1;
            if(c>=3)  continue;           
            r+=s[i];
        }
        return r;   
    }
};
