# 🔁 Palindrome Permutation using HashSet (Java)
# 📌 Problem

Given a string s, check whether its characters can be rearranged to form a palindrome.

## 💡 Approach (Using HashSet)
Add character if it appears first time

Remove character if it appears again

At the end:

If set.size() <= 1 → ✅ palindrome possible

Else → ❌ not possible

## 👉 Why this works?
Because:

Characters with even frequency cancel out

Only odd frequency characters remain in set
## ✅ Java Code
```java

class Solution {
    boolean canFormPalindrome(String s) {
        HashSet<Character> set = new HashSet<>();
        
        for (char c : s.toCharArray()) {
            if (set.contains(c)) {
                set.remove(c);
            } else {
                set.add(c);
            }
        }
        
        return set.size() <= 1;
    }
}
```
## ⚡ Complexity
Time Complexity: O(n)

Space Complexity: O(1)


