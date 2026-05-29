
# Array with All Palindromes

## Problem Statement
Given an array `arr[]` of positive integers, check whether all elements in the array are palindrome numbers or not.

A number is called a palindrome if it reads the same forward and backward.

Return:
- `true` → if all elements are palindrome
- `false` → otherwise

---

# Example 1

### Input
```text
arr[] = [111, 222, 333, 444, 555]
````

### Output

```text
true
```

### Explanation

All numbers remain the same when reversed:

* 111 → 111
* 222 → 222
* 333 → 333
* 444 → 444
* 555 → 555

So the answer is `true`.

---

# Example 2

### Input

```text
arr[] = [121, 131, 20]
```

### Output

```text
false
```

### Explanation

* 121 → palindrome
* 131 → palindrome
* 20 → reversed becomes 02

Since `20` is not a palindrome, the answer is `false`.

---

# Approach

1. Traverse each element in the array.
2. Reverse the number.
3. Compare the reversed number with the original number.
4. If any number is not palindrome, return `false`.
5. If all are palindrome, return `true`.

---

# Time Complexity

* **O(n × d)**
* `n` = size of array
* `d` = number of digits

# Auxiliary Space

* **O(1)**

---

# Java Solution

```java
class Solution {

    // Function to check palindrome number
    boolean isPalindrome(int num) {
        int original = num;
        int reverse = 0;

        while (num > 0) {
            int digit = num % 10;
            reverse = reverse * 10 + digit;
            num /= 10;
        }

        return original == reverse;
    }

    // Function to check all array elements
    public boolean PalinArray(int[] arr) {

        for (int num : arr) {
            if (!isPalindrome(num)) {
                return false;
            }
        }

        return true;
    }
}
```

---

# Dry Run

### Input

```text
arr[] = [121, 131, 20]
```

### Checking 121

```text
Reverse = 121
Palindrome ✔
```

### Checking 131

```text
Reverse = 131
Palindrome ✔
```

### Checking 20

```text
Reverse = 2
Not Palindrome ✘
```

### Final Output

```text
false
```

---

```
```
