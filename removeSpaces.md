# Given a string s, remove all the spaces from the string and return the modified string.

Examples:

Input: s = "g eeks for ge eks"
Output: "geeksforgeeks"

Explanation: All space characters are removed from the given string while preserving the order of the remaining characters, resulting in the final string "geeksforgeeks".

```java
class Solution {
    String removeSpaces(String s) {
        // code here
        String str="";
        for(int i=0;i<s.length();i++){
            if(s.charAt(i)==' '){
                continue;
            }
            else{
                str=str+s.charAt(i);
            }
        }
        return str;
        
    }
}
```
or we can write a simple 
```java
class Solution {
    String removeSpaces(String s) {
        return s.replace(" ", "");
    }
}
```
