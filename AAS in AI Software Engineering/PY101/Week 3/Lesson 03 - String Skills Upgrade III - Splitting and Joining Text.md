# String Skills Upgrade III: Splitting and Joining Text

**Date:** November 5, 2025  
**Course:** PY101 - Introduction to Python  
**Week:** 3, Lesson 3

## What You'll Learn

Splitting and joining are essential string operations for processing structured data like CSV files, user input, and text formatting. You'll learn how to use `.split()` to break strings into lists, `.strip()` to clean each piece, handle empty strings from consecutive separators, and use `.join()` to recombine cleaned data. These skills are fundamental for data processing and text manipulation.

---

## Splitting Strings with `.split()`

The `.split()` method divides a string into a list of substrings using a separator.

**Syntax:** `string.split(separator)`

### Basic Split Example

```python
text = "a,b,c"
parts = text.split(",")
print(parts)
# Output: ['a', 'b', 'c']
```

**What Happened:** The comma is removed, and the string is divided into three separate pieces.

### Split with Spaces

```python
sentence = "Python is awesome"
words = sentence.split(" ")
print(words)
# Output: ['Python', 'is', 'awesome']
```

### Split Without Arguments (Default)

When you don't specify a separator, `.split()` splits on any whitespace and removes empty strings:

```python
text = "Python   is    awesome"
words = text.split()
print(words)
# Output: ['Python', 'is', 'awesome']
```

**Why This Matters:** `.split()` with no argument is perfect for splitting sentences into words, handling any amount of whitespace automatically.

---

## Handling Extra Spaces

When your data has extra spaces around separators, they stay in the result:

```python
messy = " a , b , c "
parts = messy.split(",")
print(parts)
# Output: [' a ', ' b ', ' c ']
```

Notice the spaces around each letter? `.split()` only removes the separator, not surrounding whitespace.

### Solution: Combine `.split()` with `.strip()`

```python
messy = " a , b , c "
parts = messy.split(",")
clean = []

for item in parts:
    clean.append(item.strip())

print(clean)
# Output: ['a', 'b', 'c']
```

**How It Works:**
1. `.split(",")` divides at commas: `[' a ', ' b ', ' c ']`
2. Loop through each item
3. `.strip()` removes spaces from each piece
4. Append cleaned item to new list

---

## Extra Separators Create Empty Strings

When separators appear consecutively, `.split()` creates empty strings.

```python
colors = "red,blue,,green"
parts = colors.split(",")
print(parts)
# Output: ['red', 'blue', '', 'green']

print(len(parts))
# Output: 4
```

**Why This Happens:** The double comma `,,` means there's nothing between the separators, so `.split()` creates an empty string `''`.

### Visual Breakdown

```
"red,blue,,green"
     ↓    ↓↓
"red" "blue" "" "green"
```

The double comma produces an empty string in the list.

---

## Practical Example: Cleaning CSV Data

Let's clean a messy line of comma-separated data:

```python
data = " Dallas | Houston | Austin "
fields = data.split("|")
print(fields)
# Output: [' Dallas ', ' Houston ', ' Austin ']

# Clean up spaces
clean = []
for city in fields:
    clean.append(city.strip())

print(clean)
# Output: ['Dallas', 'Houston', 'Austin']
```

**Real-World Use:** CSV files, user input, and configuration files often have extra spaces that need cleaning.

---

## Joining Strings with `.join()`

The `.join()` method combines a list of strings into a single string using a separator.

**Syntax:** `separator.join(list_of_strings)`

**Important:** The separator goes BEFORE `.join()`, not inside it.

### Basic Join Example

```python
words = ['Dallas', 'Houston', 'Austin']
result = "; ".join(words)
print(result)
# Output: Dallas; Houston; Austin
```

### Different Separators

```python
words = ['Python', 'is', 'awesome']

# Join with spaces
print(" ".join(words))
# Output: Python is awesome

# Join with hyphens
print("-".join(words))
# Output: Python-is-awesome

# Join with nothing
print("".join(words))
# Output: Pythonisawesome
```

### Common Pattern: Split, Clean, Join

```python
# Messy CSV data
data = " eggs, milk, , bread , "

# Split on comma
parts = data.split(",")
# Output: [' eggs', ' milk', ' ', ' bread ', ' ']

# Clean each piece
clean = []
for item in parts:
    item = item.strip()
    if item:  # Only keep non-empty strings
        clean.append(item)
# Output: ['eggs', 'milk', 'bread']

# Join with semicolon
result = ";".join(clean)
print(result)
# Output: eggs;milk;bread
```

**Why This Matters:** This pattern transforms messy data into clean, standardized format.

---

## Checking for Values with `in`

After splitting, you can check if specific values exist in the list:

```python
cities = ['Dallas', 'Houston', 'Austin']

print("Austin" in cities)
# Output: True

print("San Antonio" in cities)
# Output: False
```

### Case-Sensitive Checking

```python
cities = ['Dallas', 'Houston', 'Austin']

print("austin" in cities)
# Output: False (lowercase doesn't match)

# Solution: convert to lowercase first
cities_lower = [city.lower() for city in cities]
print("austin" in cities_lower)
# Output: True
```

---

## Common Errors and Fixes

### Error: Using `.len()` as a Method

**Bad Code:**

```python
text = "red,blue,green"
print(text.len())
# AttributeError: 'str' object has no attribute 'len'
```

**Why This Fails:**  
`len()` is a function, not a method. It goes on the outside, not after a dot.

**Fixed Code:**

```python
text = "red,blue,green"
parts = text.split(",")
print(len(parts))
# Output: 3
```

**Why This Works:**  
`len()` is called as a function with the list as an argument.

---

### Error: Variable Name Inconsistency

**Bad Code:**

```python
fields = " a , b , c ".split(",")
clean = []
for item in fields:
    cleaned.append(item.strip())  # Using 'cleaned' instead of 'clean'
# NameError: name 'cleaned' is not defined
```

**Why This Fails:**  
The list is named `clean`, but we're trying to append to `cleaned`.

**Fixed Code:**

```python
fields = " a , b , c ".split(",")
clean = []
for item in fields:
    clean.append(item.strip())  # Consistent naming
print(clean)
# Output: ['a', 'b', 'c']
```

**Why This Works:**  
Variable name is consistent throughout.

---

### Error: Typo in Variable Names

**Bad Code:**

```python
words = ['Hello', 'World']
snetence = " ".join(words)  # Typo: 'snetence' instead of 'sentence'
print(sentence)
# NameError: name 'sentence' is not defined
```

**Why This Fails:**  
Variable is created as `snetence` but referenced as `sentence`.

**Fixed Code:**

```python
words = ['Hello', 'World']
sentence = " ".join(words)
print(sentence)
# Output: Hello World
```

**Why This Works:**  
Spelling is correct and consistent.

---

### Error: Incorrect Function Syntax

**Bad Code:**

```python
def csv_clean(line)
    parts = line.split(",")
    return parts
# SyntaxError: invalid syntax
```

**Why This Fails:**  
Missing colon `:` after function definition.

**Fixed Code:**

```python
def csv_clean(line):
    parts = line.split(",")
    clean = []
    for item in parts:
        item = item.strip()
        if item:  # Remove empty strings
            clean.append(item)
    return ";".join(clean)

print(csv_clean(' eggs, milk, , bread , '))
# Output: eggs;milk;bread
```

**Why This Works:**  
Proper syntax with colon, correct indentation, and complete logic.

---

## Building a CSV Cleaner Function

Let's build a complete function that handles all aspects of cleaning CSV data:

```python
def csv_clean(line):
    """Clean a CSV line: split, strip, remove empties, rejoin."""
    # Split on comma
    parts = line.split(",")
    
    # Clean each part
    clean = []
    for item in parts:
        item = item.strip()  # Remove spaces
        if item:             # Only keep non-empty
            clean.append(item)
    
    # Join with semicolon
    return ";".join(clean)

# Test it
result = csv_clean(' eggs, milk, , bread , ')
print(result)
# Output: eggs;milk;bread

result = csv_clean('a,  b  ,,  c  ')
print(result)
# Output: a;b;c
```

### How This Function Works

**Step 1: Split**
```python
' eggs, milk, , bread , '.split(",")
# [' eggs', ' milk', ' ', ' bread ', ' ']
```

**Step 2: Strip and Filter**
```python
for item in parts:
    item = item.strip()  # Remove spaces
    if item:             # Skip empty strings
        clean.append(item)
# clean = ['eggs', 'milk', 'bread']
```

**Step 3: Join**
```python
";".join(clean)
# 'eggs;milk;bread'
```

---

## Practice Exercises

**Exercise 1: Split a Sentence**

Split `"Python is amazing"` into a list of words:

<details>
<summary>Solution</summary>

```python
sentence = "Python is amazing"
words = sentence.split()
print(words)
# Output: ['Python', 'is', 'amazing']
```

**Explanation:** `.split()` with no argument splits on whitespace.

</details>

**Exercise 2: Clean and Split**

Split `" red , blue , green "` on commas and remove spaces:

<details>
<summary>Solution</summary>

```python
text = " red , blue , green "
parts = text.split(",")
clean = []
for color in parts:
    clean.append(color.strip())
print(clean)
# Output: ['red', 'blue', 'green']
```

**Explanation:** Split first, then strip each piece.

</details>

**Exercise 3: Join with Hyphens**

Join `['2025', '11', '05']` with hyphens:

<details>
<summary>Solution</summary>

```python
parts = ['2025', '11', '05']
date = "-".join(parts)
print(date)
# Output: 2025-11-05
```

**Explanation:** Separator goes before `.join()`.

</details>

**Exercise 4: Count Words**

Count how many words are in `"The quick brown fox"`:

<details>
<summary>Solution</summary>

```python
sentence = "The quick brown fox"
words = sentence.split()
print(len(words))
# Output: 4
```

**Explanation:** Split into words, then count with `len()`.

</details>

**Exercise 5: Remove Empty Strings**

Split `"a,,b,,c"` and remove empty strings:

<details>
<summary>Solution</summary>

```python
text = "a,,b,,c"
parts = text.split(",")
clean = []
for item in parts:
    if item:  # Skip empty strings
        clean.append(item)
print(clean)
# Output: ['a', 'b', 'c']
```

**Explanation:** Use `if item:` to filter out empty strings.

</details>

**Exercise 6: Build URL Path**

Join `['users', 'marco', 'profile']` with slashes:

<details>
<summary>Solution</summary>

```python
parts = ['users', 'marco', 'profile']
path = "/".join(parts)
print(f"/{path}")
# Output: /users/marco/profile
```

**Explanation:** Join with `/`, then add leading slash.

</details>

---

## Split vs Join Comparison

| Operation | Method | Input | Output |
|-----------|--------|-------|--------|
| Split | `text.split(",")` | `"a,b,c"` | `['a', 'b', 'c']` |
| Join | `",".join(list)` | `['a', 'b', 'c']` | `"a,b,c"` |
| Split | `text.split()` | `"a b c"` | `['a', 'b', 'c']` |
| Join | `" ".join(list)` | `['a', 'b', 'c']` | `"a b c"` |

**Key Difference:**
- `.split()` - string → list
- `.join()` - list → string

---

## Real-World Applications

### Use Case 1: Processing CSV Files

```python
def process_csv_line(line):
    """Process a single CSV line."""
    fields = line.split(",")
    cleaned = [field.strip() for field in fields if field.strip()]
    return cleaned

data = "John, 25, , Engineer"
result = process_csv_line(data)
print(result)
# Output: ['John', '25', 'Engineer']
```

### Use Case 2: Building File Paths

```python
def build_path(parts):
    """Build a file path from parts."""
    return "/".join(parts)

path_parts = ['home', 'marco', 'documents', 'report.pdf']
full_path = build_path(path_parts)
print(full_path)
# Output: home/marco/documents/report.pdf
```

### Use Case 3: Formatting Output

```python
def format_list(items, separator=", "):
    """Format a list as readable text."""
    return separator.join(items)

cities = ['Dallas', 'Houston', 'Austin']
print(format_list(cities))
# Output: Dallas, Houston, Austin

print(format_list(cities, " | "))
# Output: Dallas | Houston | Austin
```

---

## Key Takeaways

✅ **`.split(separator)` divides strings into lists** - Use specific separator or default whitespace  
✅ **Consecutive separators create empty strings** - `"a,,b"` splits to `['a', '', 'b']`  
✅ **`.strip()` cleans individual pieces** - Remove spaces after splitting  
✅ **`.join(list)` combines lists into strings** - Separator goes BEFORE .join()  
✅ **Filter empty strings with `if item:`** - Keeps only non-empty values  
✅ **`in` keyword checks list membership** - Returns True/False for existence  
✅ **Careful naming prevents bugs** - Use consistent variable names throughout

**Remember:** Split takes you from string to list, join takes you from list to string. Always clean (strip) between splitting and joining for best results.

---

**Last Updated:** November 5, 2025
