# Lists I: Creating Lists

**Date:** November 6, 2025  
**Course:** PY101 - Introduction to Python  
**Week:** 3, Lesson 4

## What You'll Learn

Lists are Python's most versatile data structure for storing collections of related values. You'll learn why lists are essential, how to create them manually and automatically with `range()`, how to count items with `len()`, and how to modify list values through indexing. Understanding mutability and proper list syntax will prepare you for more advanced list operations in upcoming lessons.

---

## What Is a List (and Why Use It)?

A **list** lets you group related values into a single variable instead of managing multiple separate variables.

### The Problem with Separate Variables

```python
# Managing temperatures with separate variables
temp1 = 73
temp2 = 68
temp3 = 75
temp4 = 70

print(temp1, temp2, temp3, temp4)
# Output: 73 68 75 70
```

**Problems:**
- Need a new variable for each value
- Can't easily process all values together
- Adding more data requires creating more variables
- No way to know how many values you have

### The List Solution

```python
# Managing temperatures with a list
temps = [73, 68, 75, 70]
print(temps)
# Output: [73, 68, 75, 70]
```

**Benefits:**
- Single variable holds all values
- Easy to add or remove values
- Can process all items with loops
- Can check how many items with `len()`

**Why This Matters:** Lists make it possible to work with any amount of data using the same code.

---

## Creating Lists

Lists are created using square brackets `[]` with items separated by commas.

### List of Numbers

```python
temps = [73, 68, 75, 70]
scores = [100, 95, 87, 92]
ages = [25, 30, 28, 35, 22]
```

### List of Strings

```python
cities = ["Austin", "Boston", "Dallas", "Miami"]
names = ["Marco", "Alice", "Bob"]
```

### Mixed Types (Possible but Not Recommended)

```python
mixed = [42, "hello", 3.14, True]
# Valid Python, but usually not a good practice
```

**Best Practice:** Keep lists homogeneous (same type) for clarity and easier processing.

### Empty Lists

```python
empty = []
print(empty)
# Output: []

print(len(empty))
# Output: 0
```

---

## Counting Items with `len()`

Use the `len()` function to count how many items are in a list.

```python
temps = [73, 68, 75, 70]
print(len(temps))
# Output: 4

cities = ["Austin", "Boston", "Dallas"]
print(len(cities))
# Output: 3

empty = []
print(len(empty))
# Output: 0
```

### Common Mistake: Wrong Brackets

**Bad Code:**

```python
numbers = [2][4][6][8][10]
print(len(numbers))
# This creates nested indexing, not a list!
```

**Why This Fails:**  
Square brackets without commas create indexing operations, not a list.

**Fixed Code:**

```python
numbers = [2, 4, 6, 8, 10]
print(len(numbers))
# Output: 5
```

**Why This Works:**  
Items are separated by commas inside square brackets.

---

## Building Lists Automatically with `range()`

The `range()` function combined with `list()` creates lists of numbers automatically.

**Syntax:** `list(range(start, stop, step))`

### Basic Range

```python
# Numbers 1 through 5
numbers = list(range(1, 6))
print(numbers)
# Output: [1, 2, 3, 4, 5]
```

**Remember:** Stop value is NOT included (6 is excluded).

### Range with Step

```python
# Even numbers from 2 to 10
evens = list(range(2, 11, 2))
print(evens)
# Output: [2, 4, 6, 8, 10]

# Odd numbers from 1 to 10
odds = list(range(1, 11, 2))
print(odds)
# Output: [1, 3, 5, 7, 9]
```

### Range Starting at 0

```python
# Default start is 0
zeros = list(range(5))
print(zeros)
# Output: [0, 1, 2, 3, 4]
```

### Countdown with Negative Step

```python
# Count down from 10 to 1
countdown = list(range(10, 0, -1))
print(countdown)
# Output: [10, 9, 8, 7, 6, 5, 4, 3, 2, 1]
```

**Why This Matters:** Creating lists with `range()` is much faster than typing each number manually.

---

## Changing List Values (Mutability)

Lists are **mutable**, meaning you can change their values after creation.

### Accessing List Items

Use square brackets with an index (position):

```python
temps = [73, 68, 75, 70]

print(temps[0])  # 73 (first item)
print(temps[1])  # 68 (second item)
print(temps[3])  # 70 (fourth item)
```

**Remember:** Indexing starts at 0, not 1.

### Modifying List Items

```python
numbers = [1, 2, 3, 4, 5]
numbers[0] = 99
print(numbers)
# Output: [99, 2, 3, 4, 5]
```

### Changing the Last Item

```python
evens = [2, 4, 6, 8, 10]
evens[4] = 42
print(evens)
# Output: [2, 4, 6, 8, 42]
```

**Using Negative Indexing:**

```python
evens = [2, 4, 6, 8, 10]
evens[-1] = 42  # Change last item
print(evens)
# Output: [2, 4, 6, 8, 42]
```

---

## Common Errors and Fixes

### Error: Using Parentheses Instead of Brackets

**Bad Code:**

```python
evens = [2, 4, 6, 8, 10]
evens(4) = 42
# TypeError: 'list' object is not callable
```

**Why This Fails:**  
Parentheses `()` are for function calls, not indexing. Lists use square brackets `[]`.

**Fixed Code:**

```python
evens = [2, 4, 6, 8, 10]
evens[4] = 42
print(evens)
# Output: [2, 4, 6, 8, 42]
```

**Why This Works:**  
Square brackets `[]` are the correct syntax for list indexing.

---

### Error: Wrong Variable Name

**Bad Code:**

```python
cities = ["Austin", "Boston", "Dallas"]
print(len(city))
# NameError: name 'city' is not defined
```

**Why This Fails:**  
The list is named `cities` (plural), but code uses `city` (singular).

**Fixed Code:**

```python
cities = ["Austin", "Boston", "Dallas"]
print(len(cities))
# Output: 3
```

**Why This Works:**  
Variable name matches the list name exactly.

---

### Error: Trying to Use String Methods on Lists

**Bad Code:**

```python
cities = ["Austin", "Boston", "Dallas"]
cities = cities.upper()
# AttributeError: 'list' object has no attribute 'upper'
```

**Why This Fails:**  
`.upper()` is a string method, not a list method. You can't uppercase an entire list.

**Fixed Code:**

```python
cities = ["Austin", "Boston", "Dallas"]
cities[0] = cities[0].upper()  # Uppercase first city
print(cities)
# Output: ['AUSTIN', 'Boston', 'Dallas']
```

**Why This Works:**  
Access the individual string in the list, then use `.upper()` on that string.

---

### Error: Creating List Without Commas

**Bad Code:**

```python
numbers = [2][4][6][8]
print(numbers)
# This tries to do nested indexing, not create a list
```

**Why This Fails:**  
Without commas, Python interprets this as multiple indexing operations.

**Fixed Code:**

```python
numbers = [2, 4, 6, 8]
print(numbers)
# Output: [2, 4, 6, 8]
```

**Why This Works:**  
Commas separate list items properly.

---

## Practice Challenge: City List

You have these separate variables:

```python
city1 = "Austin"
city2 = "Boston"
city3 = "Dallas"
city4 = "Miami"
city5 = "Seattle"
```

**Goals:**
1. Create a list called `cities` containing all five city names
2. Print the length of the list
3. Change the first city to uppercase

### Solution

```python
# Step 1: Create the list
cities = [city1, city2, city3, city4, city5]
print(cities)
# Output: ['Austin', 'Boston', 'Dallas', 'Miami', 'Seattle']

# Step 2: Print the length
print(len(cities))
# Output: 5

# Step 3: Change first city to uppercase
cities[0] = cities[0].upper()
print(cities)
# Output: ['AUSTIN', 'Boston', 'Dallas', 'Miami', 'Seattle']
```

### Alternative: Create List Directly

```python
cities = ["Austin", "Boston", "Dallas", "Miami", "Seattle"]
print(len(cities))
# Output: 5

cities[0] = cities[0].upper()
print(cities)
# Output: ['AUSTIN', 'Boston', 'Dallas', 'Miami', 'Seattle']
```

---

## Practice Exercises

**Exercise 1: Create a Score List**

Create a list of test scores: 85, 90, 78, 92, 88

<details>
<summary>Solution</summary>

```python
scores = [85, 90, 78, 92, 88]
print(scores)
# Output: [85, 90, 78, 92, 88]
```

**Explanation:** List items in square brackets, separated by commas.

</details>

**Exercise 2: Count Items**

How many items are in `[11, 22, 33]`?

<details>
<summary>Solution</summary>

```python
numbers = [11, 22, 33]
print(len(numbers))
# Output: 3
```

**Explanation:** Use `len()` function to count list items.

</details>

**Exercise 3: Create Range List**

Create a list of numbers from 1 to 10 using `range()`:

<details>
<summary>Solution</summary>

```python
numbers = list(range(1, 11))
print(numbers)
# Output: [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
```

**Explanation:** `range(1, 11)` goes up to but not including 11.

</details>

**Exercise 4: Change Third Item**

Change the third item in `temps = [73, 68, 75, 70]` to 100:

<details>
<summary>Solution</summary>

```python
temps = [73, 68, 75, 70]
temps[2] = 100  # Third item is at index 2
print(temps)
# Output: [73, 68, 100, 70]
```

**Explanation:** Third item is at index 2 (counting starts at 0).

</details>

**Exercise 5: Create Multiples of 5**

Create a list of multiples of 5 from 5 to 50:

<details>
<summary>Solution</summary>

```python
multiples = list(range(5, 51, 5))
print(multiples)
# Output: [5, 10, 15, 20, 25, 30, 35, 40, 45, 50]
```

**Explanation:** Start at 5, stop at 51 (not included), step by 5.

</details>

**Exercise 6: Change First to Zero**

Change the first item in `evens = [2, 4, 6, 8, 10]` to 0:

<details>
<summary>Solution</summary>

```python
evens = [2, 4, 6, 8, 10]
evens[0] = 0
print(evens)
# Output: [0, 4, 6, 8, 10]
```

**Explanation:** First item is at index 0.

</details>

---

## Common Mistakes Reference Table

| Mistake | Why It's Wrong | Correction |
|---------|---------------|------------|
| `evens(4) = 42` | Uses `()` instead of `[]` | `evens[4] = 42` |
| `print(len(city))` | Wrong variable name | `print(len(cities))` |
| `cities = cities.upper()` | `.upper()` not valid for lists | `cities[0] = cities[0].upper()` |
| `[2][4][6]` | Missing commas | `[2, 4, 6]` |
| `temps[5]` on 4-item list | Index out of range | Use valid index (0-3) |
| Misspelled variable names | Causes NameError | Double-check spelling |

---

## Lists vs Individual Variables

### With Individual Variables

```python
score1 = 85
score2 = 90
score3 = 78

# To add another score, need new variable
score4 = 92

# Hard to process all scores
average = (score1 + score2 + score3 + score4) / 4
```

### With a List

```python
scores = [85, 90, 78, 92]

# Easy to add more scores
scores.append(88)

# Easy to process all scores
average = sum(scores) / len(scores)
```

**Key Advantage:** Lists scale to any number of items without changing your code.

---

## Quick Self-Check Questions

**Question 1:** What does `len([11, 22, 33])` return?
<details>
<summary>Answer</summary>
3 (three items in the list)
</details>

**Question 2:** How do you change the third item in `temps` to 100?
<details>
<summary>Answer</summary>
`temps[2] = 100` (third item is at index 2)
</details>

**Question 3:** What would `evens[0] = 0` do to `evens = [2, 4, 6, 8, 10]`?
<details>
<summary>Answer</summary>
Changes first item to 0, resulting in `[0, 4, 6, 8, 10]`
</details>

**Question 4:** What's wrong with `list(range(1, 5, 0))`?
<details>
<summary>Answer</summary>
Step cannot be 0 (causes ValueError)
</details>

---

## Key Takeaways

✅ **Lists group related values in one variable** - Use square brackets `[]` with commas  
✅ **`len()` counts list items** - Returns the number of elements  
✅ **Indexing starts at 0** - First item is `list[0]`, not `list[1]`  
✅ **Lists are mutable** - You can change values after creation  
✅ **Use `list(range())` for number sequences** - Creates lists automatically  
✅ **Square brackets for indexing** - NEVER use parentheses like `list(0)`  
✅ **String methods work on individual items** - Access item first, then apply method

**Remember:** Lists are one of Python's most powerful features. They let you manage any amount of data with the same code, making your programs flexible and scalable.

---

**Last Updated:** November 6, 2025
