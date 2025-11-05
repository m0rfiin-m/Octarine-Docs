# Lesson 01 - String Skills Upgrade I: Indexing and Slicing

**Week 3: Basic Data Structures** | Nov 03 - Nov 09  
**Topic:** String manipulation through indexing and slicing operations

---

## Learning Objectives

By the end of this lesson, you will:
- Understand how Python indexes string characters
- Access individual characters using positive and negative indices
- Extract substrings using slice notation
- Apply step values to control slicing patterns
- Build a function that extracts the middle third of a string

---

## Core Concepts

### 1. String Indexing Basics

Every character in a Python string has a position (index), starting from 0.

**Example: "PYTHON"**

| Letter | P | Y | T | H | O | N |
|--------|---|---|---|---|---|---|
| Index  | 0 | 1 | 2 | 3 | 4 | 5 |

**Accessing Characters:**
```python
text = "Marco"
print(text[0])  # M
print(text[2])  # r
print(text[4])  # o
```

**Key Point:** First character is at index 0, not 1.

---

### 2. Negative Indexing

Python lets you count backwards from the end using negative numbers.

**-1 = last character, -2 = second-to-last, etc.**

```python
word = "python"
print(word[-1])  # n (last)
print(word[-2])  # o (second-to-last)
print(word[-6])  # p (first character from the end)
```

**Practice:**
```python
city = "Dallas"
print(city[-2])  # a (second-to-last)
print(city[-1])  # s (last)
```

---

### 3. Slicing Strings

**Syntax:** `text[start:stop]`

**Critical Rule:** Start is included, stop is NOT included.

```python
phrase = "live code"
print(phrase[0:4])  # "live" (indices 0,1,2,3)
print(phrase[5:9])  # "code" (indices 5,6,7,8)
```

**Visual Breakdown:**
```
"live code"
 0123 56789
```

To get "ve c" (indices 2,3,4,5):
```python
print(phrase[2:6])  # "ve c"
```

**Why 6?** Because stop index is NOT included, so [2:6] gets indices 2,3,4,5.

---

### 4. Omitting Slice Bounds

**Start from beginning:** Leave start blank  
**Go to end:** Leave stop blank

```python
phrase = "hello world"

# From index 6 to end
print(phrase[6:])   # "world"

# From start to index 5 (not including 5)
print(phrase[:5])   # "hello"

# Entire string (both omitted)
print(phrase[:])    # "hello world"
```

---

### 5. Step in Slicing

**Syntax:** `text[start:stop:step]`

Step controls how you move through the string.

```python
secret = "abcdefg"

# Every 2nd character (step of 2)
print(secret[::2])   # "aceg"

# Every 3rd character
print(secret[::3])   # "adg"

# Reverse the string (step of -1)
print(secret[::-1])  # "gfedcba"
```

**Common Patterns:**
- `[::2]` - Every other character
- `[::3]` - Every third character
- `[::-1]` - Reverse the string
- `[1::2]` - Every other character starting at index 1

---

## Practical Application

### Mini-Challenge: Extract Middle Third

**Goal:** Write a function that returns the middle third of a string whose length is divisible by 3.

**Example:**
```python
middle_third("SpaceStation")  # Returns "eSta"
```

**Strategy:**
1. Get total length with `len()`
2. Calculate one-third with integer division `//`
3. Slice from 1/3 to 2/3

**Solution:**
```python
def middle_third(text):
    n = len(text)           # Total length
    third = n // 3          # One third
    return text[third:2*third]  # From 1/3 to 2/3

# Test it
result = middle_third("SpaceStation")
print(result)  # Output: eSta
```

**How it works for "SpaceStation" (12 characters):**
- `n = 12`
- `third = 12 // 3 = 4`
- Return `text[4:8]` which is "eSta"

---

## Key Takeaways

**Indexing:**
- `text[n]` - Get character at position n (starts at 0)
- `text[-n]` - Count backwards from end

**Slicing:**
- `text[start:stop]` - From start (included) to stop (excluded)
- `text[start:]` - From start to end
- `text[:stop]` - From beginning to stop
- `text[start:stop:step]` - With custom step

**Common Mistakes:**
- Forgetting stop is NOT included in slice
- Confusing negative indexing with reverse slicing
- Off-by-one errors when calculating indices

---

## Practice Exercises

**Exercise 1:** Extract first 3 characters
```python
word = "Python"
# Your code here
```

**Exercise 2:** Get last 4 characters
```python
word = "Programming"
# Your code here
```

**Exercise 3:** Reverse a string
```python
word = "Hello"
# Your code here
```

**Exercise 4:** Get every other character
```python
word = "abcdefgh"
# Your code here
```

**Solutions:**
```python
# 1. word[:3]  → "Pyt"
# 2. word[-4:] → "ming"
# 3. word[::-1] → "olleH"
# 4. word[::2] → "aceg"
```

---

## Related Concepts

**From Week 1:**
- Variables and assignment
- Data types (strings)
- Functions basics

**From Week 2:**
- For loops (can iterate over strings)
- Range function (similar indexing concept)

**Next Lesson:**
- String methods (`.lower()`, `.strip()`, etc.)

---

**Status:** ✅ Completed  
**Next:** Lesson 02 - String Skills Upgrade II: Common Methods
