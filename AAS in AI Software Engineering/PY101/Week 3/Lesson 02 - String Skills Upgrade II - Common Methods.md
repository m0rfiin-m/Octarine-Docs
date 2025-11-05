# String Skills Upgrade II: Common Methods

**Date:** November 4, 2025  
**Course:** PY101 - Introduction to Python  
**Week:** 3, Lesson 2

## What You'll Learn

Python provides powerful built-in methods for cleaning, searching, and transforming strings. You'll master essential methods like `.strip()`, `.lower()`, `.find()`, and `.replace()`, plus learn how to chain them together for efficient text processing. These skills are fundamental for handling user input, processing data, and building real applications.

---

## Raw Strings and Output

Before cleaning or modifying a string, you need to see exactly what you're working with.

```python
raw = '   PyThOn 3.12!!!   '
print(raw)
# Output:    PyThOn 3.12!!!   
```

**Why This Matters:** The `print()` function shows spaces, newlines, and special characters exactly as they appear in the string. This helps you identify what needs to be cleaned.

---

## The `.strip()` Method

Removes **whitespace** (spaces, tabs, newlines) from both ends of a string.

### Basic Strip Usage

```python
messy = '   Dallas   '
clean = messy.strip()
print(clean)
# Output: Dallas
```

**Important:** `.strip()` only removes from the **ends**, not from the middle.

```python
text = '   hello   world   '
print(text.strip())
# Output: hello   world
# (middle spaces remain)
```

### Strip with Arguments

You can specify which characters to remove:

```python
text = "!!!hello!!!"
clean = text.strip('!')
print(clean)
# Output: hello
```

### Common Use Case: Clean User Input

```python
name = input("Enter your name: ").strip()
# If user types "  Marco  " with extra spaces
# name will be "Marco" after strip
```

**Why This Matters:** Users often accidentally add spaces when typing. `.strip()` ensures clean data.

---

## The `.lower()` Method

Converts all characters in a string to lowercase.

**Critical Point:** `.lower()` returns a NEW string. It doesn't change the original.

```python
name = "MaRCo"
lowercase = name.lower()

print(lowercase)   # marco
print(name)        # MaRCo (original unchanged)
```

### Case-Insensitive Comparisons

```python
user_input = "YES"
if user_input.lower() == "yes":
    print("User confirmed")
# Output: User confirmed
```

### Related Methods

```python
text = "hello world"

print(text.upper())       # HELLO WORLD
print(text.title())       # Hello World
print(text.capitalize())  # Hello world
```

**Why This Matters:** Case-insensitive checks prevent bugs. "YES", "yes", and "Yes" should all be treated the same.

---

## The `in` Keyword

Checks if a substring exists within a string. Returns `True` or `False`.

```python
print("rock" in "python rocks")
# Output: True

print("java" in "python rocks")
# Output: False
```

### Case Sensitivity

```python
print("Rock" in "python rocks")
# Output: False (capital R doesn't match)

# Solution: convert to lowercase first
print("Rock".lower() in "python rocks")
# Output: True
```

### Common Pattern: Error Detection

```python
message = "Error: file not found"

if "error" in message.lower():
    print("There's an error!")
# Output: There's an error!
```

**Why This Matters:** The `in` keyword is faster and simpler than `.find()` when you only need to check if something exists.

---

## The `.find()` Method

Returns the **starting index** where a substring first appears, or `-1` if not found.

```python
phrase = "live code"
pos = phrase.find("ve")
print(pos)
# Output: 2

pos = phrase.find("python")
print(pos)
# Output: -1 (not found)
```

### Visual Example

```
"live code"
 01234567
 
"ve" starts at index 2
```

### When to Use `.find()` vs `in`

**Use `in` when:** You only need to know if something exists  
**Use `.find()` when:** You need the position

```python
email = "marco@example.com"
at_pos = email.find("@")

if at_pos != -1:
    username = email[:at_pos]
    domain = email[at_pos+1:]
    print(f"Username: {username}")
    print(f"Domain: {domain}")
# Output:
# Username: marco
# Domain: example.com
```

**Why This Matters:** Finding positions lets you split strings, extract parts, or validate format.

---

## The `.replace()` Method

Replaces **all occurrences** of a substring with another substring.

### Basic Replace

```python
msg = "spam spam bacon spam"
fixed = msg.replace("spam", "eggs")
print(fixed)
# Output: eggs eggs bacon eggs
```

### Deleting Characters

To delete characters, replace them with an empty string:

```python
messy = "hello!!!"
clean = messy.replace("!", "")
print(clean)
# Output: hello
```

### Multiple Replacements

```python
date = "2025-11-05"
formatted = date.replace("-", "/")
print(formatted)
# Output: 2025/11/05
```

### Practical Example: Sanitizing Input

```python
password = input("Enter password: ")
# Remove spaces user might have accidentally added
password = password.replace(" ", "")
```

**Why This Matters:** `.replace()` is essential for data cleaning, formatting, and sanitizing user input.

---

## Chaining Methods

You can apply multiple methods in sequence by chaining them together.

### Basic Chaining Example

```python
clean_word = "   HeLLo!!!   "
clean = clean_word.strip().lower().replace("!", "")
print(clean)
# Output: hello
```

### How It Works (Step-by-Step)

1. `clean_word.strip()` → `"HeLLo!!!"` (removed spaces)
2. `.lower()` → `"hello!!!"` (made lowercase)
3. `.replace("!", "")` → `"hello"` (removed exclamation marks)

### As a Reusable Function

```python
def clean_word(word):
    return word.strip().lower().replace('!', '')

print(clean_word("   HeLLo!!!   "))
# Output: hello

print(clean_word(" PYTHON!!! "))
# Output: python

print(clean_word("  WhAt!?  "))
# Output: what!?
# (Note: only ! is removed, not ?)
```

### Order Matters

```python
# Efficient: strip first (less to process)
"   HELLO   ".strip().lower()
# "HELLO" → "hello"

# Also works, but processes more characters
"   HELLO   ".lower().strip()
# "   hello   " → "hello"
```

**Best Practice:** Apply `.strip()` first to reduce the string size before other operations.

---

## Common Patterns and Use Cases

### Pattern 1: Validate Yes/No Input

```python
response = input("Continue? (yes/no): ")
if response.strip().lower() in ["yes", "y"]:
    print("Continuing...")
elif response.strip().lower() in ["no", "n"]:
    print("Stopping...")
else:
    print("Invalid response")
```

### Pattern 2: Clean and Standardize Data

```python
def clean_email(email):
    # Remove spaces, convert to lowercase
    return email.strip().lower()

emails = ["  Marco@Example.COM  ", "test@SITE.com  "]
cleaned = [clean_email(email) for email in emails]
print(cleaned)
# Output: ['marco@example.com', 'test@site.com']
```

### Pattern 3: Remove Multiple Characters

```python
def remove_punctuation(text):
    text = text.replace("!", "")
    text = text.replace("?", "")
    text = text.replace(".", "")
    return text

clean = remove_punctuation("Hello!!! How are you?")
print(clean)
# Output: Hello How are you
```

---

## Common Errors and Fixes

### Error: Forgetting Methods Return New Strings

**Bad Code:**

```python
word = "HELLO"
word.lower()
print(word)
# Output: HELLO (unchanged!)
```

**Why This Fails:**  
`.lower()` doesn't change the original string. It returns a new one.

**Fixed Code:**

```python
word = "HELLO"
word = word.lower()  # Assign the result back
print(word)
# Output: hello
```

**Why This Works:**  
You must assign the result back to the variable (or use it directly).

---

### Error: Using `.find()` Wrong in Conditionals

**Bad Code:**

```python
text = "hello world"
if text.find("world"):
    print("Found")
# Output: (nothing printed!)
```

**Why This Fails:**  
`.find("world")` returns 6 (the index), but the condition checks if 6 is truthy. This works by accident if index is not 0, but fails when the substring is at position 0.

**Fixed Code:**

```python
text = "hello world"
if text.find("world") != -1:
    print("Found")
# Output: Found

# Or better yet, use in:
if "world" in text:
    print("Found")
# Output: Found
```

**Why This Works:**  
Check if `.find()` returns `-1` (not found) or use `in` keyword for existence checks.

---

## Practice Exercises

**Exercise 1: Clean User Input**

Write a function that cleans a username by removing spaces and converting to lowercase:

<details>
<summary>Solution</summary>

```python
def clean_username(username):
    return username.strip().lower()

print(clean_username("  MaRCo  "))
# Output: marco
```

**Explanation:** `.strip()` removes spaces from ends, `.lower()` converts to lowercase.

</details>

**Exercise 2: Remove Punctuation**

Remove all exclamation marks and question marks from `"  Hello!!! How are you?  "`:

<details>
<summary>Solution</summary>

```python
text = "  Hello!!! How are you?  "
clean = text.strip().replace("!", "").replace("?", "")
print(clean)
# Output: Hello How are you
```

**Explanation:** Chain `.replace()` calls to remove different characters.

</details>

**Exercise 3: Extract Domain from Email**

Extract the domain from `"user@example.com"`:

<details>
<summary>Solution</summary>

```python
email = "user@example.com"
at_pos = email.find("@")
domain = email[at_pos+1:]
print(domain)
# Output: example.com
```

**Explanation:** Find the @ position, then slice from after it to the end.

</details>

**Exercise 4: Case-Insensitive Search**

Check if "error" appears in `"ERROR: File not found"` (case-insensitive):

<details>
<summary>Solution</summary>

```python
message = "ERROR: File not found"
if "error" in message.lower():
    print("Error detected")
# Output: Error detected
```

**Explanation:** Convert to lowercase before checking with `in`.

</details>

**Exercise 5: Standardize Phone Number**

Replace all dashes in `"555-123-4567"` with dots:

<details>
<summary>Solution</summary>

```python
phone = "555-123-4567"
formatted = phone.replace("-", ".")
print(formatted)
# Output: 555.123.4567
```

**Explanation:** `.replace()` replaces all occurrences.

</details>

---

## Method Reference Table

| Method | Purpose | Example | Result |
|--------|---------|---------|--------|
| `.strip()` | Remove whitespace from ends | `"  hi  ".strip()` | `"hi"` |
| `.lower()` | Convert to lowercase | `"HI".lower()` | `"hi"` |
| `.upper()` | Convert to uppercase | `"hi".upper()` | `"HI"` |
| `.title()` | Capitalize each word | `"hi there".title()` | `"Hi There"` |
| `in` | Check if substring exists | `"a" in "cat"` | `True` |
| `.find()` | Get index of substring | `"cat".find("a")` | `1` |
| `.replace()` | Replace substring | `"hi".replace("i","o")` | `"ho"` |

---

## Key Takeaways

✅ **`.strip()` removes whitespace from ends** - Use it to clean user input  
✅ **`.lower()` returns a new string** - Must assign result back to variable  
✅ **`in` checks existence** - Returns True/False, simpler than `.find()`  
✅ **`.find()` returns position** - Returns -1 if not found, use when you need index  
✅ **`.replace()` changes all occurrences** - Replace with "" to delete characters  
✅ **Chaining methods is powerful** - `.strip().lower().replace()` in one line  
✅ **Order matters in chains** - `.strip()` first is usually most efficient

**Remember:** String methods don't modify the original string. They return a new string with the changes applied. Always assign the result back if you want to keep it.

---

**Last Updated:** November 4, 2025
