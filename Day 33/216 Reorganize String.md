# Approach
<!-- Describe your approach to solving the problem. -->

# Complexity
- Time complexity: O(n)
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity: O(1)
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```
class Solution {
public:
    string reorganizeString(string s) {
        int array[26]={0};
        for(int i=0;i<s.size();i++){
            array[s[i]-'a']++;
        }
        char mostOccurChar;
        int maxOccurance=INT_MIN;
        for(int i=0;i<26;i++){
            if(array[i]>maxOccurance){
                maxOccurance = array[i];
                mostOccurChar = i+'a';
            }
        }
        int i=0;
        while(i<s.size() && maxOccurance>0){
            s[i] = mostOccurChar;
            maxOccurance--;
            i+=2;
        }
        if(maxOccurance != 0)
            return "";
        
        array[mostOccurChar-'a'] = 0;

        for(int j=0;j<26;j++){
            while(array[j]>0){
                if(i>=s.size())
                    i=1;
                s[i] = j+ 'a';
                i+=2;
                array[j]--;
            }
        }
        return s;
    }
};
```
