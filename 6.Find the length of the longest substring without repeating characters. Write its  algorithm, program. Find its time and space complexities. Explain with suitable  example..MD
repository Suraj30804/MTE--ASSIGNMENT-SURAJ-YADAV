
# 🔡 Longest Substring Without Repeating Characters

## ✅ Problem Statement

Given a string, find the **length of the longest substring** without repeating characters.

---

## 🧠 Algorithm (Sliding Window + HashSet)

1. Use two pointers `start` and `end` to represent the window.
2. Use a **HashSet** to store characters in the current window.
3. Move `end` forward:
   - If `s[end]` is **not in the set**, add it and update the max length.
   - If it **is** in the set, remove `s[start]` and move `start` forward.
4. Repeat until `end` reaches the end of the string.

---

## 💻 Java Program

```java
import java.util.HashSet;

public class LongestUniqueSubstring {

    public static int lengthOfLongestSubstring(String s) {
        HashSet<Character> set = new HashSet<>();
        int start = 0, maxLength = 0;

        for (int end = 0; end < s.length(); end++) {
            char currentChar = s.charAt(end);

            // If char is already in the set, shrink the window from the left
            while (set.contains(currentChar)) {
                set.remove(s.charAt(start));
                start++;
            }

            set.add(currentChar);
            maxLength = Math.max(maxLength, end - start + 1);
        }

        return maxLength;
    }

    public static void main(String[] args) {
        String s = "abcabcbb";
        int result = lengthOfLongestSubstring(s);
        System.out.println("Length of longest substring without repeating characters: " + result);
    }
}
```

---

## 📌 Example

### Input:
```
s = "abcabcbb"
```

### Step-by-step:
- Start with empty set.
- Traverse: `a → ab → abc` (length 3)
- Repeat found: remove `a`, continue with `bca`, `cab`, etc.
- Longest unique substring = `"abc"` → ✅ Length = 3

### ✅ Output:
```
3
```

---

## ⏱️ Time & Space Complexity

| Operation         | Complexity |
|-------------------|------------|
| Time              | O(n)       |
| Space             | O(k)       |

Where `n` = length of string, `k` = size of character set (e.g., 26 for lowercase letters).

---

## 📚 Summary

This is a classic application of the **Sliding Window technique** with a **HashSet** to track uniqueness efficiently. It's useful in real-time input scanning, text editors, and more.
