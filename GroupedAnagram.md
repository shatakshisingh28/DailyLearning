# Group Anagrams (HashMap + Sorting)

## Problem Statement

Given an array of strings, group all anagrams together.

Two words are **anagrams** if they contain the same characters with the same frequency.

### Example

**Input**

```text
["eat", "tea", "tan", "ate", "nat", "bat"]
```

**Output**

```text
[
 [eat, tea, ate],
 [tan, nat],
 [bat]
]
```

---

# Approach

The idea is to use a **HashMap**.

* Sort each word.
* Use the sorted word as the key.
* Store all original words having the same sorted key in one list.

Example:

```text
eat → aet
tea → aet
ate → aet

tan → ant
nat → ant

bat → abt
```

HashMap after processing:

```text
aet -> [eat, tea, ate]
ant -> [tan, nat]
abt -> [bat]
```

Finally, return all the values of the HashMap.

---

# Code Explanation

## Step 1: Create a HashMap

```java
HashMap<String, List<String>> map = new HashMap<>();
```

* **Key:** Sorted word
* **Value:** List of original words

Example:

```text
aet -> [eat, tea]
```

---

## Step 2: Traverse every word

```java
for(String word : strs)
```

This loop processes one word at a time.

---

## Step 3: Convert the word into a character array

```java
char[] arr = word.toCharArray();
```

Example:

```text
eat

↓

['e','a','t']
```

---

## Step 4: Sort the characters

```java
Arrays.sort(arr);
```

Example:

```text
['e','a','t']

↓

['a','e','t']
```

Now every anagram has the same sorted form.

---

## Step 5: Convert it back into a String

```java
String key = new String(arr);
```

Example:

```text
['a','e','t']

↓

"aet"
```

This becomes the HashMap key.

---

## Step 6: Check if the key exists

```java
if(!map.containsKey(key)){
    map.put(key,new ArrayList<>());
}
```

If the key is not present, create a new list.

Example:

```text
aet -> []
```

---

## Step 7: Add the original word

```java
map.get(key).add(word);
```

Example:

```text
aet -> [eat]

Next:

tea

↓

aet -> [eat, tea]

Next:

ate

↓

aet -> [eat, tea, ate]
```

---

## Step 8: Return the answer

```java
return new ArrayList<>(map.values());
```

`map.values()` contains all grouped anagrams.

Example:

```text
[
[eat, tea, ate],
[tan, nat],
[bat]
]
```

---

# Main Method Explanation

## Read the number of strings

```java
int n = sc.nextInt();
```

Example:

```text
6
```

---

## Create the array

```java
String[] strs = new String[n];
```

Creates an array to store the input strings.

---

## Read the input strings

```java
for(int i = 0; i < n; i++){
    strs[i] = sc.next();
}
```

Example Input:

```text
eat
tea
tan
ate
nat
bat
```

---

## Call the function

```java
List<List<String>> result = groupAnagrams(strs);
```

The function groups all anagrams together.

---

## Print the result

```java
for(List<String> group : result){
    System.out.println(group);
}
```

Output:

```text
[eat, tea, ate]
[tan, nat]
[bat]
```

---

# Dry Run

Input:

```text
eat tea tan ate nat bat
```

| Word | Sorted Key | HashMap               |
| ---- | ---------- | --------------------- |
| eat  | aet        | aet → [eat]           |
| tea  | aet        | aet → [eat, tea]      |
| tan  | ant        | ant → [tan]           |
| ate  | aet        | aet → [eat, tea, ate] |
| nat  | ant        | ant → [tan, nat]      |
| bat  | abt        | abt → [bat]           |

Final Output:

```text
[
[eat, tea, ate],
[tan, nat],
[bat]
]
```

---

# Time Complexity

Sorting one word of length **K** takes:

```text
O(K log K)
```

For **N** words:

```text
O(N × K log K)
```

---

# Space Complexity

The HashMap stores all the strings.

```text
O(N × K)
```

---

# Key Takeaway

* Sort each word.
* Use the sorted word as the HashMap key.
* Words with the same sorted key are anagrams.
* Store them in the same list.
* Return all the lists from the HashMap.

**One-line Summary:**

> **Sort every word and use the sorted word as the key in a HashMap. All words with the same sorted key are grouped together as anagrams.**
