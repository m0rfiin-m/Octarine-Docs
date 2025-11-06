# Study Guide: Indexing, Slicing, and List Best Practices

## List Creation and Basics

### Creating Lists
```python
temps = [17, 22, 28, 13, 14]
```

### Basic Operations
```python
print(temps)        # Shows entire list
print(len(temps))   # Returns 5
```

### ❌ Bad Code Example: Wrong Brackets
```python
temps = (17, 22, 28)  # This is a TUPLE, not a list!
```

**Why it matters:** Tuples use parentheses and are immutable. Lists use square brackets and can be changed.

---

## Indexing in Lists

### Positive Indexing (Left to Right, Zero-Based)
```python
temps[0]   # returns 17 (first item)
temps[1]   # returns 22 (second item)
temps[4]   # returns 14 (fifth item)
```

### Negative Indexing (Right to Left)
```python
temps[-1]  # returns 14 (last item)
temps[-2]  # returns 13 (second to last)
```

### Visualizing Indices
```python
temps = [17, 22, 28, 13, 14]
#         0   1   2   3   4    # Positive indices
#        -5  -4  -3  -2  -1    # Negative indices
```

---

## Mutability: Changing List Values

Lists are mutable, meaning you can update values after creation:

```python
temps[2] = 100
print(temps)  # Output: [17, 22, 100, 13, 14]
```

---

## Slicing Lists

### Basic Slicing: `[start:stop]`
Start is included, stop is excluded:

```python
temps[1:4]   # returns [22, 100, 13] (indices 1, 2, 3)
temps[0:3]   # returns [17, 22, 100] (first three values)
temps[-2:]   # returns [13, 14] (last two values)
temps[:3]    # returns [17, 22, 100] (omit start = begin at 0)
temps[2:]    # returns [100, 13, 14] (omit stop = go to end)
```

### Stride (Step Pattern)
```python
# Get every other temperature reading (useful for downsampling sensor data)
temps[::2]   # [17, 100, 14]

# Reverse a list (common in data processing pipelines)
temps[::-1]  # [14, 13, 100, 22, 17]

# Every third item starting from index 1
temps[1::3]  # [22, 13]
```

### Slicing Always Creates a New List
This is important for understanding memory and references:

```python
nums = [1, 2, 3, 4, 5]
sub = nums[1:4]     # Creates NEW list [2, 3, 4]
sub[0] = 99         # Changes sub, not nums
print(nums)         # [1, 2, 3, 4, 5] - unchanged
print(sub)          # [99, 3, 4] - modified
```

---

## Index Errors and Safe Access

### ❌ Bad Code Example (Can Crash)
```python
print(nums[99])  # IndexError: list index out of range
```

### ✅ Good Practice: Guard with Length Check
```python
idx = 3
if idx < len(nums):
    print(nums[idx])  # Only prints if idx is valid
```

### ✅ Better Practice: Try-Except (More Pythonic)
```python
try:
    print(nums[idx])
except IndexError:
    print("Index out of range")
```

**When to use which:**
- Use `if idx < len(nums)` when you're checking before accessing
- Use `try-except` when you're handling errors that might occur (asks forgiveness, not permission - the Python way)

---

## Safe Value Retrieval Function

Define a function to get the last item, or return "N/A" if the list is empty:

```python
def last_or_none(lst):
    if len(lst) > 0:
        return lst[-1]
    else:
        return "N/A"

print(last_or_none([2, 4, 8]))  # Output: 8
print(last_or_none([]))         # Output: N/A
```

### Alternative: More Pythonic Version
```python
def last_or_none(lst):
    return lst[-1] if lst else "N/A"

# Even shorter using the 'or' operator
def last_or_default(lst, default="N/A"):
    return lst[-1] if lst else default
```

---

## Critical Concept: List References vs Copies

This will bite you if you don't understand it:

```python
# ❌ Assignment creates references, not copies
original = [1, 2, 3]
reference = original      # Both point to SAME list in memory
reference[0] = 99
print(original)          # [99, 2, 3] - CHANGED! (unexpected)

# ✅ To actually copy a list:
original = [1, 2, 3]
copy = original[:]       # New list with same values
copy[0] = 99
print(original)          # [1, 2, 3] - unchanged (expected)

# ✅ Alternative copy methods:
copy2 = original.copy()
copy3 = list(original)
```

**Why this matters:** When you pass lists to functions, you're passing references. Changes inside the function affect the original list.

---

## Bad vs Good Code Patterns

| Scenario | ❌ Bad Code Example | ✅ Good Code Example |
|----------|---------------------|----------------------|
| Make a list | `temps = (1, 2, 3)` | `temps = [1, 2, 3]` |
| Out-of-range index | `print(nums[99])` | `if idx < len(nums): print(nums[idx])` |
| Change value by index | `temps = 5` (replaces whole list) | `temps[2] = 100` |
| Safe "last value" | `print(lst[-1])` (crashes if empty) | `last_or_none(lst)` |
| Get subset | `new_list = []`<br>`for i in range(3):`<br>`    new_list.append(nums[i])` | `new_list = nums[:3]` |
| Check if empty | `if len(lst) == 0:` | `if not lst:` |
| Copy a list | `new_lst = lst` (just references) | `new_lst = lst[:]` or `lst.copy()` |
| Get last 3 items | `lst[len(lst)-3:len(lst)]` | `lst[-3:]` |

---

## Real-World AI/Data Science Application

Pattern you'll use constantly in machine learning and data processing:

```python
# Processing batches of sensor data
sensor_readings = [17, 22, 28, 13, 14, 19, 25, 30, 15, 12]

# Split into training and test sets (common in ML)
train_data = sensor_readings[:7]   # First 70% (7 items)
test_data = sensor_readings[7:]    # Last 30% (3 items)

# Get sliding windows for time series analysis
window_size = 3
for i in range(len(sensor_readings) - window_size + 1):
    window = sensor_readings[i:i+window_size]
    print(f"Window {i}: {window}")
```

**Output:**
```
Window 0: [17, 22, 28]
Window 1: [22, 28, 13]
Window 2: [28, 13, 14]
...
```

This sliding window pattern is fundamental in:
- Time series forecasting
- Natural language processing (n-grams)
- Computer vision (image patches)
- Signal processing

---

## Practice Checklist

- [ ] Index with both positive and negative numbers
- [ ] Use slices to extract sublists
- [ ] Use stride steps (like `[::2]`) for patterns
- [ ] Always use guards or checks before accessing indices that might not exist
- [ ] Understand the difference between references and copies
- [ ] Write functions that safely handle empty lists
- [ ] Practice splitting data into training/test sets
- [ ] Implement sliding window patterns

---

## Key Takeaways

1. **Slicing creates new lists** - changes to slices don't affect the original
2. **Assignment creates references** - use `[:]` or `.copy()` to actually copy
3. **Check before you access** - guard against IndexError with length checks or try-except
4. **Negative indexing is powerful** - use `[-1]` for last item, `[-3:]` for last three
5. **Stride for patterns** - `[::2]` for every other, `[::-1]` to reverse
6. **These patterns are everywhere in AI** - train/test splits, sliding windows, data preprocessing

---

## Performance Note

**Slicing creates new lists in memory.** For small lists (hundreds of items), this is fine. For large datasets (millions of items), consider:
- Using NumPy arrays (more efficient slicing)
- Working with views instead of copies
- Processing data in chunks rather than loading everything

You'll learn more about this as you get into AI coursework, but keep it in mind when working with large amounts of data.
