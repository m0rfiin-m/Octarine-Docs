# String Skills Upgrade I: Indexing and Slicing

**Date:** November 3, 2025  
**Course:** PY101 - Introduction to Python  
**Week:** 3, Lesson 1

## What You'll Learn

String indexing and slicing are fundamental skills for text manipulation in Python. You'll learn how to access individual characters using positive and negative indices, extract substrings with slice notation, and apply step values to control patterns. By the end, you'll build a function that extracts the middle third of any string divisible by 3.

---

## Letter Positioning: Indexing

Every character in a Python string has a **position (index)**, starting from 0 on the left.

### Understanding String Indices

For the word `"PYTHON"`:

| **Letter** | **P** | **Y** | **T** | **H** | **O** | **N** |
|------------|-------|-------|-------|-------|-------|-------|
| **Index**  | 0     | 1     | 2     | 3     | 4     | 5     |

To access a specific letter, use square brackets: `text[index]`

```python
name = "Marco"
print(name[0])  # M (first character)
print(name[2])  # r (third character)
print(name[4])  # o (fifth character)
```

**Why This Matters:** Indexing from 0 is a convention in most programming languages. The first position is index 0, not 1.

---

## Negative Indexing

Python allows **negative indices** to access characters from the end of a string.

`-1` is the last character, `-2` the second-to-last, and so on.

```python
word = "python"
print(word[-1])   # n (last character)
print(word[-2])   # o (second-to-last)
print(word[-6])   # p (first character, counting backwards)
```

### Practice Example

Print the second-to-last letter of `"Dallas"`:

```python
city = "Dallas"
print(city[-2])
# Output: a
```

**Why This Matters:** Negative indexing is useful when you need to access the end of a string without knowing its exact length.

---

## Slicing Strings

**Slicing** lets you extract a substring (chunk of text) using the syntax: `text[start:stop]`

**Critical Rule:** The start index is included, but the stop index is NOT included.

### Basic Slicing Example

```python
phrase = "live code"
print(phrase[0:4])   # live (indices 0,1,2,3)
print(phrase[5:9])   # code (indices 5,6,7,8)
```

### Visual Breakdown

```
"live code"
 0123 56789
```

To grab `"ve c"` from `"live code"` (positions 2,3,4,5):

```python
print(phrase[2:6])
# Output: ve c
```

**Why 6?** Because the stop index is NOT included, so `[2:6]` gives you indices 2, 3, 4, 5.

---

## Omitting Bounds in Slices

You can leave the **start** blank to begin at index 0, or leave the **stop** blank to go to the end.

```python
phrase = "hello world"

# From index 6 to end
print(phrase[6:])
# Output: world

# From start to index 5 (not including 5)
print(phrase[:5])
# Output: hello

# Entire string (both omitted)
print(phrase[:])
# Output: hello world
```

**Common Pattern:** Use `[:5]` for "first 5 characters" and `[-5:]` for "last 5 characters"

---

## Step in Slicing

The full slice syntax is: `text[start:stop:step]`

**Step** controls how you move through the string (default is 1).

### Stepping Through Characters

```python
secret = "abcdefg"

# Every 2nd character (step of 2)
print(secret[::2])
# Output: aceg

# Every 3rd character
print(secret[::3])
# Output: adg

# To reverse a string (step of -1)
print(secret[::-1])
# Output: gfedcba
```

### Common Step Patterns

- `[::2]` - Every other character
- `[::3]` - Every third character
- `[::-1]` - Reverse the entire string
- `[1::2]` - Every other character starting at index 1

---

## Mini-Challenge: Writing `middle_third(text)`

**Goal:** Write a function that returns the middle third of a string whose length is divisible by 3.

**Example:**

```python
result = middle_third("SpaceStation")
print(result)
# Output: eSta
```

### Strategy

1. Use `len(text)` to get the total length
2. Use integer division (`//`) to calculate one-third
3. Use slicing with calculated indices for the middle third

### Sample Solution

```python
def middle_third(text):
    n = len(text)              # Get total length
    third = n // 3             # Calculate one-third
    return text[third:2*third] # Slice from 1/3 to 2/3

# Test it
result = middle_third("SpaceStation")
print(result)
# Output: eSta
```

### How It Works

For `"SpaceStation"` (12 characters):
- `n = 12`
- `third = 12 // 3 = 4`
- Return `text[4:8]` which gives indices 4,5,6,7
- Characters at those positions: `"eSta"`

**Checklist:**
- ✅ Uses `len()` to get string length
- ✅ Uses slicing to extract substring
- ✅ Works when length is a multiple of 3
- ✅ Returns the middle third correctly

---

## Common Errors and Fixes

### Error: IndexError

**Bad Code:**

```python
word = "cat"
print(word[5])
# IndexError: string index out of range
```

**Why This Fails:**  
The string "cat" only has indices 0, 1, 2. Index 5 doesn't exist.

**Fixed Code:**

```python
word = "cat"
print(word[2])
# Output: t
```

**Why This Works:**  
Index 2 is the last valid index for a 3-character string.

---

### Error: Off-by-One in Slicing

**Bad Code:**

```python
text = "Python"
# Trying to get first 3 characters
print(text[0:2])
# Output: Py (only 2 characters!)
```

**Why This Fails:**  
The stop index is NOT included, so `[0:2]` only gives indices 0 and 1.

**Fixed Code:**

```python
text = "Python"
print(text[0:3])
# Output: Pyt
```

**Why This Works:**  
`[0:3]` includes indices 0, 1, 2, giving you 3 characters.

---

## Practice Exercises

**Exercise 1: Extract First Three**

Extract the first 3 characters from `"Python"`:

<details>
<summary>Solution</summary>

```python
word = "Python"
print(word[:3])
# Output: Pyt
```

**Explanation:** Omit the start (defaults to 0), use 3 as stop.

</details>

**Exercise 2: Get Last Four**

Get the last 4 characters from `"Programming"`:

<details>
<summary>Solution</summary>

```python
word = "Programming"
print(word[-4:])
# Output: ming
```

**Explanation:** Start at -4 (fourth from end), go to the end.

</details>

**Exercise 3: Reverse a String**

Reverse the string `"Hello"`:

<details>
<summary>Solution</summary>

```python
word = "Hello"
print(word[::-1])
# Output: olleH
```

**Explanation:** Use step of -1 to reverse.

</details>

**Exercise 4: Every Other Character**

Get every other character from `"abcdefgh"`:

<details>
<summary>Solution</summary>

```python
word = "abcdefgh"
print(word[::2])
# Output: aceg
```

**Explanation:** Use step of 2 to skip every other character.

</details>

**Exercise 5: Middle Characters**

Extract characters at indices 2, 3, 4 from `"gaming"`:

<details>
<summary>Solution</summary>

```python
word = "gaming"
print(word[2:5])
# Output: min
```

**Explanation:** Start at 2, stop at 5 (not included), giving indices 2,3,4.

</details>

---

## Key Takeaways

✅ **Indexing starts at 0** - First character is `text[0]`, not `text[1]`  
✅ **Negative indices count backwards** - `text[-1]` is the last character  
✅ **Slicing syntax is [start:stop]** - Stop index is NOT included in result  
✅ **Omit bounds for convenience** - `[:5]` for first 5, `[5:]` for index 5 onward  
✅ **Use step for patterns** - `[::2]` for every other, `[::-1]` to reverse  
✅ **Stop is exclusive** - `[0:3]` gives 3 characters (indices 0,1,2)  
✅ **Calculate indices with len()** - Use `len(text)` and `//` for dynamic slicing

**Remember:** When slicing, the stop index is your "up to but not including" boundary. Think of it as marking where the slice ends, not what it includes.

---

**Last Updated:** November 3, 2025
