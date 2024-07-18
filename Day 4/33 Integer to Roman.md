# Approach 1
<!-- Describe your approach to solving the problem. -->

# Complexity
- Time complexity: O(1)
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity: O(1)
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```
class Solution {
public:
    string intToRoman(int num){
        string romans[]={"M", "CM", "D", "CD", "C", "XC", "L", "XL", "X", "IX", "V", "IV", "I"};
        int nums[]={1000, 900, 500, 400, 100, 90, 50, 40, 10, 9, 5, 4, 1};
        string ans = "";
        for(int i=0;i<13;i++){
            while(num>=nums[i]){
                num-=nums[i];
                ans+=romans[i];
            }
        }
        return ans;
    }
};
```

# Approach
<!-- Describe your approach to solving the problem. -->

# Complexity
- Time complexity: O(1)
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity: O(1)
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```
class Solution {
public:
    string intToRoman(int num) {
        string ones[]={"","I","II","III","IV","V","VI","VII","VIII","IX"};
        string tens[]={"","X","XX","XXX","XL","L","LX","LXX","LXXX","XC"};
        string hrns[]={"","C","CC","CCC","CD","D","DC","DCC","DCCC","CM"};
        string ths[]={"","M","MM","MMM"};
        
        return ths[num/1000] + hrns[(num%1000)/100] + tens[(num%100)/10] + ones[num%10];
    }
};
```
