# Lists II: Indexing, Slicing, and Best Practices

**Date:** November 7, 2025  
**Course:** PY101 - Introduction to Python  
**Week:** 3, Lesson 05

## What You'll Learn

Lists store collections, but accessing the right data at the right time requires precise control. This lesson teaches you how to retrieve individual items using indices, extract ranges using slices, and modify list values safely. You'll learn the difference between list references and copies, understand positive and negative indexing, and master slicing patterns that you'll use throughout your programming career.

---

## Why Indexing and Slicing Matter

Data rarely comes in the exact format you need. You extract the first 10 search results, grab the last three sensor readings, split datasets into training and testing sets, or reverse sequences for processing. Every data operation depends on accessing specific items or ranges within collections.

Real applications constantly use these patterns: machine learning algorithms split data into batches, web apps display paginated results, audio processors analyze sliding windows of sound samples, and financial systems calculate rolling averages. Mastering indexing and slicing gives you precise control over data.

---

## Understanding List Indices

### Positive Indexing: Counting from the Start

Python lists use zero-based indexing. The first item sits at position 0, the second at position 1, and so on.

```python
# Access individual temperature readings
temps = [17, 22, 28, 13, 14]

print(f"First reading: {temps[0]}°C")
# Output: First reading: 17°C

print(f"Second reading: {temps[1]}°C")
# Output: Second reading: 22°C

print(f"Last position (index 4): {temps[4]}°C")
# Output: Last position (index 4): 14°C
```

**Key Point:** A list with 5 items has valid indices from 0 to 4. The length is 5, but the highest index is 4.

### Negative Indexing: Counting from the End

Negative indices count backward from the last item. This provides an easy way to access items from the end without calculating positions.

```python
# Access items from the end
temps = [17, 22, 28, 13, 14]

print(f"Last reading: {temps[-1]}°C")
# Output: Last reading: 14°C

print(f"Second to last: {temps[-2]}°C")
# Output: Second to last: 13°C

print(f"Third from end: {temps[-3]}°C")
# Output: Third from end: 28°C
```

### Visual Index Map

```python
temps = [17, 22, 28, 13, 14]
#         0   1   2   3   4    (positive indices)
#        -5  -4  -3  -2  -1    (negative indices)
```

Every item has two valid indices: one positive counting from the start, one negative counting from the end. Both `temps[0]` and `temps[-5]` return 17.

---

## List Mutability: Changing Values

Lists are mutable, meaning you can change their contents after creation. Use indexing to update specific positions.

```python
# Update specific temperature reading
temps = [17, 22, 28, 13, 14]
temps[2] = 100  # Change third item (index 2)

print(temps)
# Output: [17, 22, 100, 13, 14]
```

```python
# Update using negative index
scores = [85, 90, 78, 92]
scores[-1] = 95  # Change last score

print(scores)
# Output: [85, 90, 78, 95]
```

**Critical Distinction:** Assignment with brackets changes one item. Assignment without brackets replaces the entire list.

```python
values = [1, 2, 3]
values[0] = 99      # Changes first item: [99, 2, 3]

values = [4, 5, 6]  # Replaces entire list: [4, 5, 6]
```

---

## Slicing: Extracting Ranges

Slicing creates new lists by extracting ranges from existing lists. The syntax is `list[start:stop]` where start is included and stop is excluded.

### Basic Slicing

```python
# Extract ranges from temperature data
temps = [17, 22, 28, 13, 14]

# Get items at indices 1, 2, 3 (stops before 4)
middle_temps = temps[1:4]
print(middle_temps)
# Output: [22, 28, 13]

# Get first three items (indices 0, 1, 2)
first_three = temps[0:3]
print(first_three)
# Output: [17, 22, 28]
```

### Omitting Start or Stop

```python
temps = [17, 22, 28, 13, 14]

# Omit start: begins at index 0
from_start = temps[:3]
print(from_start)
# Output: [17, 22, 28]

# Omit stop: goes to the end
to_end = temps[2:]
print(to_end)
# Output: [28, 13, 14]

# Both omitted: copies entire list
full_copy = temps[:]
print(full_copy)
# Output: [17, 22, 28, 13, 14]
```

### Negative Indices in Slices

```python
temps = [17, 22, 28, 13, 14]

# Get last two items
last_two = temps[-2:]
print(last_two)
# Output: [13, 14]

# Get everything except last two
except_last_two = temps[:-2]
print(except_last_two)
# Output: [17, 22, 28]
```

---

## Stride: Skipping Items

The full slicing syntax is `list[start:stop:stride]`. Stride determines the step size between items.

### Every Other Item

```python
# Get every second temperature reading
temps = [17, 22, 28, 13, 14, 19, 25, 30]

every_other = temps[::2]
print(every_other)
# Output: [17, 28, 14, 25]
```

**Use Case:** Downsampling sensor data to reduce storage or processing load.

### Reversing Lists

```python
# Reverse the list using negative stride
temps = [17, 22, 28, 13, 14]

reversed_temps = temps[::-1]
print(reversed_temps)
# Output: [14, 13, 28, 22, 17]
```

**Use Case:** Processing data in reverse chronological order or flipping sequences.

### Custom Stride Patterns

```python
# Every third item starting from index 1
temps = [10, 20, 30, 40, 50, 60, 70, 80, 90]

pattern = temps[1::3]
print(pattern)
# Output: [20, 50, 80]
```

---

## Critical Concept: Slices Create New Lists

Slicing always creates a new list in memory. Changes to the slice do not affect the original.

```python
# Demonstrate slice independence
original = [1, 2, 3, 4, 5]
slice_copy = original[1:4]  # Creates [2, 3, 4]

# Modify the slice
slice_copy[0] = 99

print(f"Original: {original}")
# Output: Original: [1, 2, 3, 4, 5]

print(f"Slice: {slice_copy}")
# Output: Slice: [99, 3, 4]
```

The original list remains unchanged because the slice created a new list.

---

## References vs Copies

Understanding the difference between references and copies prevents subtle bugs in your code.

### Assignment Creates References

```python
# Assignment points to the same list
original = [1, 2, 3]
reference = original  # Both names point to same list

# Modify through reference
reference[0] = 99

print(f"Original: {original}")
# Output: Original: [99, 2, 3]

print(f"Reference: {reference}")
# Output: Reference: [99, 2, 3]
```

Both `original` and `reference` point to the same list in memory. Changing one changes both.

### Creating Actual Copies

```python
# Three ways to copy a list
original = [1, 2, 3]

copy1 = original[:]         # Slice notation
copy2 = original.copy()     # Copy method
copy3 = list(original)      # List constructor

# Modify the copy
copy1[0] = 99

print(f"Original: {original}")
# Output: Original: [1, 2, 3]

print(f"Copy: {copy1}")
# Output: Copy: [99, 2, 3]
```

All three methods create independent copies. Changes to copies don't affect the original.

**Why This Matters:** When you pass lists to functions, you pass references. Functions can modify your original lists unless you explicitly copy them first.

---

## Safe Index Access

Accessing invalid indices crashes your program. Use defensive programming to prevent errors.

### The Problem: Index Out of Range

```python
# This crashes if index doesn't exist
numbers = [10, 20, 30]
print(numbers[99])
# Error: IndexError: list index out of range
```

### Solution 1: Guard with Length Check

```python
# Check bounds before accessing
numbers = [10, 20, 30]
index = 5

if index < len(numbers):
    print(numbers[index])
else:
    print("Index out of range")
# Output: Index out of range
```

### Solution 2: Try-Except Block

```python
# Handle the error if it occurs
numbers = [10, 20, 30]
index = 5

try:
    print(numbers[index])
except IndexError:
    print("Index out of range")
# Output: Index out of range
```

**When to Use Which:**
- Use length checks when you control the index and can prevent the error
- Use try-except when handling user input or external data where errors might occur

### Safe Access Function

```python
# Return default value if index is invalid
def safe_get(lst, index, default=None):
    """Get item at index, or return default if out of range."""
    if 0 <= index < len(lst):
        return lst[index]
    return default

numbers = [10, 20, 30]

print(safe_get(numbers, 1))      # Output: 20
print(safe_get(numbers, 99))     # Output: None
print(safe_get(numbers, 99, -1)) # Output: -1
```

---

## Practical Patterns

### Splitting Data for Machine Learning

```python
# Split dataset into training and testing sets
data = [12, 45, 67, 23, 89, 34, 56, 78, 90, 21]

# Use first 70% for training, last 30% for testing
split_point = int(len(data) * 0.7)

train_data = data[:split_point]
test_data = data[split_point:]

print(f"Training set ({len(train_data)} items): {train_data}")
# Output: Training set (7 items): [12, 45, 67, 23, 89, 34, 56]

print(f"Testing set ({len(test_data)} items): {test_data}")
# Output: Testing set (3 items): [78, 90, 21]
```

### Sliding Window Analysis

```python
# Analyze data in overlapping windows
sensor_data = [17, 22, 28, 13, 14, 19, 25]
window_size = 3

print("Sliding windows:")
for i in range(len(sensor_data) - window_size + 1):
    window = sensor_data[i:i + window_size]
    average = sum(window) / len(window)
    print(f"Window {i}: {window} - Average: {average:.1f}")
# Output: Sliding windows:
# Output: Window 0: [17, 22, 28] - Average: 22.3
# Output: Window 1: [22, 28, 13] - Average: 21.0
# Output: Window 2: [28, 13, 14] - Average: 18.3
# Output: Window 3: [13, 14, 19] - Average: 15.3
# Output: Window 4: [14, 19, 25] - Average: 19.3
```

**Applications:** Time series forecasting, signal processing, natural language processing (n-grams).

### Pagination

```python
# Display results in pages
results = list(range(1, 51))  # 50 items
page_size = 10
page_number = 2  # Zero-based: 0 is first page

start = page_number * page_size
end = start + page_size
page_items = results[start:end]

print(f"Page {page_number + 1} (items {start + 1}-{end}):")
print(page_items)
# Output: Page 3 (items 21-30):
# Output: [21, 22, 23, 24, 25, 26, 27, 28, 29, 30]
```

---

## Common Errors and Fixes

### Error 1: Accessing Invalid Index

**Bad Code:**

```python
# Crashes when index doesn't exist
scores = [85, 90, 78]
print(scores[10])
# Error: IndexError: list index out of range
```

**Why This Fails:**  
The list has only 3 items (indices 0-2). Index 10 doesn't exist.

**Fixed Code:**

```python
# Check bounds before accessing
scores = [85, 90, 78]
index = 10

if index < len(scores):
    print(scores[index])
else:
    print(f"Index {index} out of range (max: {len(scores) - 1})")
# Output: Index 10 out of range (max: 2)
```

**Why This Works:**  
Checking `index < len(scores)` ensures the index is valid before access.

### Error 2: Confusing Assignment with Modification

**Bad Code:**

```python
# This replaces the entire list, not one item
values = [1, 2, 3, 4, 5]
values = 99  # Wrong: now values is just the number 99

print(values[0])
# Error: TypeError: 'int' object is not subscriptable
```

**Why This Fails:**  
Assignment without brackets replaces the list variable with a single number.

**Fixed Code:**

```python
# Modify one item using bracket notation
values = [1, 2, 3, 4, 5]
values[0] = 99  # Correct: changes first item

print(values)
# Output: [99, 2, 3, 4, 5]
```

**Why This Works:**  
Using brackets `values[0]` targets a specific position for modification.

### Error 3: Modifying Reference When Copy Intended

**Bad Code:**

```python
# Thinking this creates a copy
original = [1, 2, 3]
modified = original  # This creates a reference, not a copy

modified[0] = 99

print(f"Original: {original}")
# Output: Original: [99, 2, 3]  (Unexpected change!)
```

**Why This Fails:**  
Simple assignment creates a reference to the same list. Both names point to identical data.

**Fixed Code:**

```python
# Create an actual copy
original = [1, 2, 3]
modified = original[:]  # or original.copy()

modified[0] = 99

print(f"Original: {original}")
# Output: Original: [1, 2, 3]

print(f"Modified: {modified}")
# Output: Modified: [99, 2, 3]
```

**Why This Works:**  
Slicing `[:]` or the `.copy()` method creates an independent list.

### Error 4: Off-by-One in Slice Ranges

**Bad Code:**

```python
# Trying to get first 3 items but using wrong stop index
numbers = [10, 20, 30, 40, 50]
first_three = numbers[0:2]  # Wrong: only gets 2 items

print(first_three)
# Output: [10, 20]  (Missing 30!)
```

**Why This Fails:**  
Slice stop index is exclusive. `[0:2]` includes indices 0 and 1, stopping before 2.

**Fixed Code:**

```python
# Stop index should be one past the last item you want
numbers = [10, 20, 30, 40, 50]
first_three = numbers[0:3]  # Correct: includes indices 0, 1, 2

print(first_three)
# Output: [10, 20, 30]
```

**Why This Works:**  
Using stop index 3 includes everything from 0 up to (but not including) 3.

---

## Practice Exercises

**Exercise 1: Access and Modify**

Create a list `temps = [18, 22, 19, 25, 21]`. Print the first temperature, the last temperature, and the middle temperature (index 2). Then change the middle temperature to 30 and print the updated list.

<details>
<summary>Solution</summary>

```python
# Access specific positions and modify
temps = [18, 22, 19, 25, 21]

print(f"First: {temps[0]}°C")
# Output: First: 18°C

print(f"Last: {temps[-1]}°C")
# Output: Last: 21°C

print(f"Middle: {temps[2]}°C")
# Output: Middle: 19°C

# Modify middle value
temps[2] = 30

print(f"Updated: {temps}")
# Output: Updated: [18, 22, 30, 25, 21]
```

**Explanation:** Positive index `[0]` gets the first item, negative index `[-1]` gets the last, and `[2]` accesses the middle. Bracket notation with assignment modifies the specific position.

</details>

**Exercise 2: Extract Ranges**

Given `numbers = [5, 10, 15, 20, 25, 30, 35, 40]`, extract and print: (a) the first 3 numbers, (b) the last 3 numbers, (c) numbers from index 2 to 5.

<details>
<summary>Solution</summary>

```python
# Extract different ranges using slices
numbers = [5, 10, 15, 20, 25, 30, 35, 40]

# First 3 items
first_three = numbers[:3]
print(f"First 3: {first_three}")
# Output: First 3: [5, 10, 15]

# Last 3 items
last_three = numbers[-3:]
print(f"Last 3: {last_three}")
# Output: Last 3: [30, 35, 40]

# Items from index 2 to 5 (exclusive of 5)
middle_range = numbers[2:5]
print(f"Index 2-5: {middle_range}")
# Output: Index 2-5: [15, 20, 25]
```

**Explanation:** Omitting start `[:3]` begins at index 0. Negative index `-3:` starts three from the end. Range `[2:5]` includes indices 2, 3, 4 but stops before 5.

</details>

**Exercise 3: Reverse and Skip**

Given `values = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]`, create a reversed version and a version with every other item starting from the first.

<details>
<summary>Solution</summary>

```python
# Use stride patterns for reversal and skipping
values = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]

# Reverse entire list
reversed_values = values[::-1]
print(f"Reversed: {reversed_values}")
# Output: Reversed: [10, 9, 8, 7, 6, 5, 4, 3, 2, 1]

# Every other item (even indices: 0, 2, 4, ...)
every_other = values[::2]
print(f"Every other: {every_other}")
# Output: Every other: [1, 3, 5, 7, 9]
```

**Explanation:** Negative stride `[::-1]` reverses by stepping backward. Stride `[::2]` skips every other item by stepping forward by 2.

</details>

**Exercise 4: Safe Copy**

Create a list `original = [100, 200, 300]`. Make a copy, modify the copy's first element to 999, and print both lists to prove they're independent.

<details>
<summary>Solution</summary>

```python
# Demonstrate proper list copying
original = [100, 200, 300]

# Create independent copy
copy = original[:]

# Modify the copy
copy[0] = 999

print(f"Original: {original}")
# Output: Original: [100, 200, 300]

print(f"Copy: {copy}")
# Output: Copy: [999, 200, 300]
```

**Explanation:** Using `[:]` creates a new list with the same values. Modifying `copy` doesn't affect `original` because they're separate lists in memory.

</details>

**Exercise 5: Train-Test Split**

Given `data = [23, 45, 12, 67, 89, 34, 56, 78, 90, 21]`, split it into training (first 70%) and testing (last 30%) sets. Print both sets and their lengths.

<details>
<summary>Solution</summary>

```python
# Split data for machine learning workflow
data = [23, 45, 12, 67, 89, 34, 56, 78, 90, 21]

# Calculate split point (70% of data)
split_index = int(len(data) * 0.7)

# Split into train and test sets
train_set = data[:split_index]
test_set = data[split_index:]

print(f"Training ({len(train_set)} items): {train_set}")
# Output: Training (7 items): [23, 45, 12, 67, 89, 34, 56]

print(f"Testing ({len(test_set)} items): {test_set}")
# Output: Testing (3 items): [78, 90, 21]
```

**Explanation:** Calculating `split_index` as 70% of length gives the boundary between sets. Slice `[:split_index]` gets training data, `[split_index:]` gets testing data. This pattern is fundamental in machine learning.

</details>

---

## Key Takeaways

✅ **Zero-based indexing starts at 0** - First item is `[0]`, not `[1]`; list of 5 has indices 0-4  
✅ **Negative indices count from end** - Use `[-1]` for last item, `[-2]` for second to last  
✅ **Slices create new lists** - `list[start:stop]` makes a copy; changes don't affect original  
✅ **Stop index is exclusive** - `[0:3]` includes indices 0, 1, 2 but stops before 3  
✅ **Assignment creates references** - Use `[:]` or `.copy()` to make actual copies  
✅ **Stride controls step size** - `[::2]` for every other, `[::-1]` to reverse  
✅ **Guard against index errors** - Check `index < len(list)` or use try-except blocks

**Remember:** Slicing is inclusive at the start, exclusive at the stop. Think of slice indices as positions between items, not the items themselves.

---

**Last Updated:** November 6, 2025
