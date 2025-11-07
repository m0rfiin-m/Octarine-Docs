# Lists V: Ordering Lists - sorted() vs sort()

**Date:** November 8, 2025  
**Course:** PY101 - Introduction to Python  
**Week:** 3, Lesson 08

## What You'll Learn

Sorting transforms unorganized data into ordered sequences. This lesson teaches you the two ways to sort lists in Python: the `sorted()` function that creates new sorted lists, and the `.sort()` method that modifies lists in place. You'll learn when to use each approach, how to customize sorting with parameters, and understand why choosing the right sorting method matters for your program's efficiency.

---

## Why Sorting Matters

Programs constantly need ordered data. You sort search results by relevance, display leaderboards from highest to lowest scores, organize files alphabetically, or arrange timestamps chronologically. Every ranking, every ordered display, every priority queue depends on sorting.

Real applications use sorting everywhere: e-commerce sites order products by price, social media feeds rank posts by engagement, analytics dashboards display top performers, and recommendation systems prioritize suggestions. Sorting turns raw data into meaningful sequences that users can understand and navigate.

---

## The sorted() Function: Creating New Sorted Lists

The `sorted()` function takes a list and returns a new sorted list. The original list stays unchanged.

### Basic sorted() Usage

```python
# Sort test scores while preserving original order
grades = [88, 72, 91, 60, 85]

sorted_grades = sorted(grades)

print(f"Original grades: {grades}")
# Output: Original grades: [88, 72, 91, 60, 85]

print(f"Sorted grades: {sorted_grades}")
# Output: Sorted grades: [60, 72, 85, 88, 91]
```

**Key Behavior:** The `sorted()` function creates a brand new list. The original `grades` list remains in its original order.

### Sorting Strings Alphabetically

```python
# Sort city names alphabetically
cities = ["Austin", "Boston", "Dallas", "Miami", "Chicago"]

sorted_cities = sorted(cities)

print(f"Sorted cities: {sorted_cities}")
# Output: Sorted cities: ['Austin', 'Boston', 'Chicago', 'Dallas', 'Miami']
```

Strings sort in alphabetical order. Capital letters come before lowercase letters in Python's default sorting.

### When to Use sorted()

Use `sorted()` when you need both the original order and the sorted order, or when working with data you shouldn't modify.

```python
# Display top 3 scores while keeping original submission order
submissions = [78, 92, 65, 88, 95, 71]

# Keep original order for processing
print("Submission order:")
for i, score in enumerate(submissions, 1):
    print(f"  Submission {i}: {score}")

# Show top 3 without losing original order
top_scores = sorted(submissions, reverse=True)[:3]
print(f"\nTop 3 scores: {top_scores}")
# Output: Submission order:
# Output:   Submission 1: 78
# Output:   Submission 2: 92
# Output:   Submission 3: 65
# Output:   Submission 4: 88
# Output:   Submission 5: 95
# Output:   Submission 6: 71
# Output:
# Output: Top 3 scores: [95, 92, 88]
```

---

## The .sort() Method: Modifying Lists In Place

The `.sort()` method changes the original list directly. It sorts the list in place and returns `None`.

### Basic .sort() Usage

```python
# Sort prices and modify the original list
prices = [29.99, 15.50, 45.00, 8.99, 22.75]

prices.sort()  # Modifies prices directly

print(f"Sorted prices: {prices}")
# Output: Sorted prices: [8.99, 15.5, 22.75, 29.99, 45.0]
```

The original `prices` list now contains sorted values. You can't get the unsorted version back.

### Critical: .sort() Returns None

```python
# Common mistake: trying to capture sorted result
numbers = [5, 2, 8, 1, 9]

result = numbers.sort()  # This assigns None to result

print(f"Result: {result}")
# Output: Result: None

print(f"Numbers: {numbers}")
# Output: Numbers: [1, 2, 5, 8, 9]
```

The `.sort()` method modifies the list but returns `None`. Don't assign its result to a variable.

### When to Use .sort()

Use `.sort()` when you want to permanently reorder a list and don't need the original order.

```python
# Organize task list alphabetically for display
tasks = ["email team", "attend meeting", "write report", "review code"]

tasks.sort()

print("Organized task list:")
for i, task in enumerate(tasks, 1):
    print(f"{i}. {task}")
# Output: Organized task list:
# Output: 1. attend meeting
# Output: 2. email team
# Output: 3. review code
# Output: 4. write report
```

---

## Reverse Sorting

Both `sorted()` and `.sort()` support reverse sorting using the `reverse=True` parameter.

### Reverse with sorted()

```python
# Show highest to lowest scores
scores = [78, 92, 65, 88, 95, 71]

descending_scores = sorted(scores, reverse=True)

print(f"Scores (high to low): {descending_scores}")
# Output: Scores (high to low): [95, 92, 88, 78, 71, 65]

print(f"Original unchanged: {scores}")
# Output: Original unchanged: [78, 92, 65, 88, 95, 71]
```

### Reverse with .sort()

```python
# Sort products by price, most expensive first
prices = [19.99, 49.99, 9.99, 29.99, 39.99]

prices.sort(reverse=True)

print(f"Prices (high to low): {prices}")
# Output: Prices (high to low): [49.99, 39.99, 29.99, 19.99, 9.99]
```

---

## Custom Sorting with key Parameter

The `key` parameter lets you sort based on specific criteria instead of the default comparison.

### Sorting by Length

```python
# Sort words by their length
words = ["hi", "elephant", "cat", "panda", "dog"]

words.sort(key=len)

print(f"Sorted by length: {words}")
# Output: Sorted by length: ['hi', 'cat', 'dog', 'panda', 'elephant']
```

The `key=len` tells Python to sort based on each word's length, not alphabetically.

### Sorting by Absolute Value

```python
# Sort numbers by absolute value (distance from zero)
temperatures = [-5, 15, -20, 8, -12, 3]

sorted_temps = sorted(temperatures, key=abs)

print(f"Sorted by absolute value: {sorted_temps}")
# Output: Sorted by absolute value: [3, -5, 8, -12, 15, -20]
```

The `key=abs` parameter sorts based on the absolute value of each number.

### Sorting Strings Case-Insensitively

```python
# Sort names alphabetically, ignoring case
names = ["alice", "Bob", "Charlie", "diana"]

names.sort(key=str.lower)

print(f"Case-insensitive sort: {names}")
# Output: Case-insensitive sort: ['alice', 'Bob', 'Charlie', 'diana']
```

Without `key=str.lower`, capital letters sort before lowercase letters. This parameter normalizes comparison.

---

## Combining key and reverse

You can use both parameters together to sort by a custom criterion in descending order.

```python
# Sort names by length, longest first
names = ["Al", "Barbara", "Kent", "Christopher", "Jo"]

names.sort(key=len, reverse=True)

print(f"Longest to shortest: {names}")
# Output: Longest to shortest: ['Christopher', 'Barbara', 'Kent', 'Al', 'Jo']
```

```python
# Sort product codes by their numeric part, highest first
codes = ["ITEM-50", "ITEM-120", "ITEM-8", "ITEM-95"]

# Extract number from string for comparison
codes.sort(key=lambda x: int(x.split('-')[1]), reverse=True)

print(f"Sorted by number (high to low): {codes}")
# Output: Sorted by number (high to low): ['ITEM-120', 'ITEM-95', 'ITEM-50', 'ITEM-8']
```

---

## Stable Sorting

Python's sorting is stable. When items compare as equal, they maintain their original relative order.

```python
# Demonstrate stable sort with words of same length
words = ["bat", "cat", "dog", "ant", "pig", "rat"]

# Sort by length (multiple words have length 3)
words.sort(key=len)

print(f"Stable sort by length: {words}")
# Output: Stable sort by length: ['bat', 'cat', 'dog', 'ant', 'pig', 'rat']
```

All words have the same length, so they stay in their original order. Stability preserves existing order when sort keys are identical.

### Practical Stability Example

```python
# Sort students by grade, preserving alphabetical order for ties
students = [
    ("Alice", 92),
    ("Bob", 85),
    ("Charlie", 92),
    ("Diana", 85),
    ("Eve", 92)
]

# First sort by name (alphabetically)
students.sort(key=lambda x: x[0])

# Then sort by grade (stable sort preserves alphabetical order for same grades)
students.sort(key=lambda x: x[1], reverse=True)

print("Students sorted by grade (alphabetical for ties):")
for name, grade in students:
    print(f"  {name}: {grade}")
# Output: Students sorted by grade (alphabetical for ties):
# Output:   Alice: 92
# Output:   Charlie: 92
# Output:   Eve: 92
# Output:   Bob: 85
# Output:   Diana: 85
```

Students with grade 92 maintain alphabetical order (Alice, Charlie, Eve) because sorting is stable.

---

## Comparison: sorted() vs .sort()

| Feature | `sorted(list)` | `list.sort()` |
|---------|----------------|---------------|
| Returns | New sorted list | `None` |
| Original list | Unchanged | Modified |
| Usage | `new = sorted(old)` | `old.sort()` |
| Performance | Creates new list (uses more memory) | Sorts in place (more efficient) |
| When to use | Need original order preserved | Don't need original order |

---

## Practical Examples

### E-commerce Product Sorting

```python
# Sort products by price for display options
products = [
    ("Laptop", 899.99),
    ("Mouse", 24.99),
    ("Keyboard", 79.99),
    ("Monitor", 299.99),
    ("Webcam", 59.99)
]

# Sort by price, low to high
by_price_low = sorted(products, key=lambda x: x[1])

print("Products by price (low to high):")
for name, price in by_price_low:
    print(f"  {name}: ${price:.2f}")

# Sort by price, high to low
by_price_high = sorted(products, key=lambda x: x[1], reverse=True)

print("\nProducts by price (high to low):")
for name, price in by_price_high:
    print(f"  {name}: ${price:.2f}")
# Output: Products by price (low to high):
# Output:   Mouse: $24.99
# Output:   Webcam: $59.99
# Output:   Keyboard: $79.99
# Output:   Monitor: $299.99
# Output:   Laptop: $899.99
# Output:
# Output: Products by price (high to low):
# Output:   Laptop: $899.99
# Output:   Monitor: $299.99
# Output:   Keyboard: $79.99
# Output:   Webcam: $59.99
# Output:   Mouse: $24.99
```

### Leaderboard Display

```python
# Display game scores from highest to lowest
player_scores = [
    ("Alice", 15200),
    ("Bob", 12800),
    ("Charlie", 18500),
    ("Diana", 16700),
    ("Eve", 14300)
]

# Sort by score, highest first
player_scores.sort(key=lambda x: x[1], reverse=True)

print("Game Leaderboard:")
for rank, (name, score) in enumerate(player_scores, 1):
    print(f"  {rank}. {name}: {score:,} points")
# Output: Game Leaderboard:
# Output:   1. Charlie: 18,500 points
# Output:   2. Diana: 16,700 points
# Output:   3. Alice: 15,200 points
# Output:   4. Eve: 14,300 points
# Output:   5. Bob: 12,800 points
```

### File Organization

```python
# Sort files by extension, then by name
files = [
    "report.pdf",
    "data.csv",
    "image.png",
    "analysis.pdf",
    "chart.png",
    "results.csv"
]

# Extract extension for sorting
def get_extension(filename):
    return filename.split('.')[-1]

# Sort by extension, then by name (stable sort)
files.sort()  # First sort alphabetically
files.sort(key=get_extension)  # Then group by extension (stable)

print("Files organized by extension:")
for file in files:
    print(f"  {file}")
# Output: Files organized by extension:
# Output:   data.csv
# Output:   results.csv
# Output:   analysis.pdf
# Output:   report.pdf
# Output:   chart.png
# Output:   image.png
```

---

## Common Errors and Fixes

### Error 1: Trying to Capture .sort() Result

**Bad Code:**

```python
# Attempting to assign sorted list from .sort()
numbers = [5, 2, 8, 1, 9]
sorted_numbers = numbers.sort()

print(f"Sorted: {sorted_numbers}")
# Output: Sorted: None
```

**Why This Fails:**  
The `.sort()` method returns `None`, not the sorted list. It modifies in place.

**Fixed Code:**

```python
# Use sorted() to get a new sorted list
numbers = [5, 2, 8, 1, 9]
sorted_numbers = sorted(numbers)

print(f"Sorted: {sorted_numbers}")
# Output: Sorted: [1, 2, 5, 8, 9]

print(f"Original: {numbers}")
# Output: Original: [5, 2, 8, 1, 9]
```

**Why This Works:**  
The `sorted()` function returns the new sorted list while leaving the original unchanged.

### Error 2: Expecting Original List After .sort()

**Bad Code:**

```python
# Thinking .sort() preserves original
data = [45, 12, 89, 23, 67]
data.sort()

# Trying to use original order - but it's gone!
print(f"Original data: {data}")
# Output: Original data: [12, 23, 45, 67, 89]
```

**Why This Fails:**  
The `.sort()` method permanently modifies the list. The original order is lost.

**Fixed Code:**

```python
# Keep original by using sorted()
data = [45, 12, 89, 23, 67]
sorted_data = sorted(data)

print(f"Original data: {data}")
# Output: Original data: [45, 12, 89, 23, 67]

print(f"Sorted data: {sorted_data}")
# Output: Sorted data: [12, 23, 45, 67, 89]
```

**Why This Works:**  
The `sorted()` function creates a new list, preserving the original.

### Error 3: Incorrect reverse Syntax

**Bad Code:**

```python
# Using wrong position for reverse parameter
numbers = [5, 2, 8, 1, 9]
numbers.sort(True)  # Wrong: reverse must be named parameter
# Error: sort() takes at most 2 positional arguments (1 given)
```

**Why This Fails:**  
The `reverse` parameter must be specified by name, not as a positional argument.

**Fixed Code:**

```python
# Use reverse as named parameter
numbers = [5, 2, 8, 1, 9]
numbers.sort(reverse=True)

print(f"Descending: {numbers}")
# Output: Descending: [9, 8, 5, 2, 1]
```

**Why This Works:**  
Using `reverse=True` explicitly names the parameter, which is required for optional sorting parameters.

### Error 4: Sorting Mixed Types

**Bad Code:**

```python
# Attempting to sort numbers and strings together
mixed = [5, "hello", 3, "world", 1]
mixed.sort()
# Error: TypeError: '<' not supported between instances of 'str' and 'int'
```

**Why This Fails:**  
Python can't compare strings to numbers for sorting. Lists must contain comparable types.

**Fixed Code:**

```python
# Convert all items to strings for comparison
mixed = [5, "hello", 3, "world", 1]
mixed_strings = sorted(mixed, key=str)

print(f"Sorted as strings: {mixed_strings}")
# Output: Sorted as strings: [1, 3, 5, 'hello', 'world']
```

**Why This Works:**  
Using `key=str` converts all items to strings before comparison, making them comparable.

---

## Practice Exercises

**Exercise 1: Sort and Preserve**

Given `temperatures = [22, 18, 25, 19, 30, 16]`, create a sorted version while keeping the original order intact. Print both lists.

<details>
<summary>Solution</summary>

```python
# Use sorted() to create new list without modifying original
temperatures = [22, 18, 25, 19, 30, 16]

sorted_temps = sorted(temperatures)

print(f"Original: {temperatures}")
# Output: Original: [22, 18, 25, 19, 30, 16]

print(f"Sorted: {sorted_temps}")
# Output: Sorted: [16, 18, 19, 22, 25, 30]
```

**Explanation:** The `sorted()` function returns a new sorted list while the original remains unchanged. Use this when you need both orderings.

</details>

**Exercise 2: Sort Names by Length**

Sort the list `names = ["Alexander", "Jo", "Christopher", "Sam", "Elizabeth"]` by length from shortest to longest.

<details>
<summary>Solution</summary>

```python
# Sort by string length using key parameter
names = ["Alexander", "Jo", "Christopher", "Sam", "Elizabeth"]

names.sort(key=len)

print(f"Sorted by length: {names}")
# Output: Sorted by length: ['Jo', 'Sam', 'Alexander', 'Elizabeth', 'Christopher']
```

**Explanation:** The `key=len` parameter tells Python to sort based on each string's length rather than alphabetically.

</details>

**Exercise 3: Reverse Numeric Sort**

Sort `scores = [78, 92, 65, 88, 95, 71]` from highest to lowest and modify the original list.

<details>
<summary>Solution</summary>

```python
# Sort in place, descending order
scores = [78, 92, 65, 88, 95, 71]

scores.sort(reverse=True)

print(f"Scores (high to low): {scores}")
# Output: Scores (high to low): [95, 92, 88, 78, 71, 65]
```

**Explanation:** Using `.sort(reverse=True)` modifies the list in place, sorting from highest to lowest.

</details>

**Exercise 4: Sort Tuples by Second Element**

Given `students = [("Alice", 85), ("Bob", 92), ("Charlie", 78), ("Diana", 95)]`, sort by grade from highest to lowest.

<details>
<summary>Solution</summary>

```python
# Sort tuples by second element (grade)
students = [("Alice", 85), ("Bob", 92), ("Charlie", 78), ("Diana", 95)]

students.sort(key=lambda x: x[1], reverse=True)

print("Students by grade (high to low):")
for name, grade in students:
    print(f"  {name}: {grade}")
# Output: Students by grade (high to low):
# Output:   Diana: 95
# Output:   Bob: 92
# Output:   Alice: 85
# Output:   Charlie: 78
```

**Explanation:** The lambda function `lambda x: x[1]` extracts the second element (grade) from each tuple for comparison. Combined with `reverse=True`, this sorts from highest grade to lowest.

</details>

**Exercise 5: Two-Level Sort**

Sort `words = ["apple", "pie", "cat", "elephant", "dog", "at"]` first by length (shortest first), then alphabetically for words of the same length.

<details>
<summary>Solution</summary>

```python
# Two-level sort using stable sort property
words = ["apple", "pie", "cat", "elephant", "dog", "at"]

# First sort alphabetically
words.sort()

# Then sort by length (stable sort preserves alphabetical order for ties)
words.sort(key=len)

print(f"Sorted by length, then alphabetically: {words}")
# Output: Sorted by length, then alphabetically: ['at', 'cat', 'dog', 'pie', 'apple', 'elephant']
```

**Explanation:** Python's stable sort preserves the alphabetical ordering when words have the same length. Sorting alphabetically first, then by length achieves the two-level sort.

</details>

---

## Key Takeaways

✅ **`sorted()` creates new lists** - Returns sorted copy, original list unchanged  
✅ **`.sort()` modifies in place** - Changes original list, returns `None`  
✅ **Use `reverse=True` for descending order** - Works with both `sorted()` and `.sort()`  
✅ **`key` parameter customizes comparison** - Sort by length, absolute value, or any function  
✅ **Combine `key` and `reverse`** - Sort by custom criteria in descending order  
✅ **Sorting is stable** - Equal items maintain their original relative order  
✅ **Choose based on need** - Use `sorted()` to preserve original, `.sort()` for efficiency

**Remember:** `sorted()` gives you a new list, `.sort()` changes the list you have. Choose based on whether you need the original order or not.

---

**Last Updated:** November 6, 2025
