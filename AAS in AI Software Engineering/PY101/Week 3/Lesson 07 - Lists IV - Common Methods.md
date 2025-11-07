# Lists IV: Common Methods

**Date:** November 8, 2025  
**Course:** PY101 - Introduction to Python  
**Week:** 3, Lesson 07

## What You'll Learn

Lists become powerful when you can modify them during program execution. This lesson covers the essential methods that let you add, remove, and manipulate list items. You'll learn when to use each method and understand the key differences between similar operations.

---

## Why List Methods Matter

Programs rarely work with static data. You need to add items when users create new records, remove items when they delete things, and insert items at specific positions when organizing data. List methods give you precise control over how your data changes during runtime.

Think of a shopping cart: customers add items (`append`), remove items they don't want (`remove`), insert priority items at the front (`insert`), and empty the cart item by item (`pop`). Every interactive program needs these operations.

---

## Quick Review: Looping Through Lists

Before modifying lists, you need to access their items. The most common approach loops by value:

```python
# Calculate total from temperature readings
temps = [17, 22, 19, 25]
total = 0

for temp in temps:
    print(f"{temp}°C")
    total += temp

print(f"Total sum: {total}°C")
# Output: 17°C
# Output: 22°C
# Output: 19°C
# Output: 25°C
# Output: Total sum: 83°C
```

This pattern processes each value in sequence. Now let's learn how to change the list itself.

---

## Adding Items to Lists

### The `.append()` Method

The `append()` method adds one item to the end of a list. This is the most common way to build lists during program execution.

```python
# Build a shopping cart as user adds items
cart = []
cart.append("milk")
cart.append("eggs")
cart.append("bread")

print(cart)
# Output: ['milk', 'eggs', 'bread']

print(f"Cart has {len(cart)} items")
# Output: Cart has 3 items
```

**Key Point:** `append()` always adds to the end (tail) of the list and increases the list length by exactly 1.

### The `.insert()` Method

The `insert()` method adds an item at a specific position. All items from that position onward shift one spot to the right.

```python
# Prioritize urgent tasks at the start of a task list
tasks = ["groceries", "laundry", "emails"]
tasks.insert(0, "urgent meeting")

print(tasks)
# Output: ['urgent meeting', 'groceries', 'laundry', 'emails']
```

**Syntax:** `list.insert(index, value)` takes two arguments: the position (index) and the item to add.

```python
# Insert item in the middle of a list
scores = [85, 90, 95]
scores.insert(1, 88)  # Insert 88 at index 1

print(scores)
# Output: [85, 88, 90, 95]
```

**When to Use:** Use `insert()` when position matters. Use `append()` when you just need to add items in order.

### The `.extend()` Method

The `extend()` method adds all items from another iterable to the end of your list. The items get flattened into the existing list.

```python
# Combine multiple data sources
morning_temps = [17, 19, 22]
afternoon_temps = [25, 28, 26]

morning_temps.extend(afternoon_temps)

print(morning_temps)
# Output: [17, 19, 22, 25, 28, 26]

print(f"Total readings: {len(morning_temps)}")
# Output: Total readings: 6
```

**Critical Difference:** Compare `extend()` with `append()`:

```python
# extend() flattens the items
list1 = [1, 2, 3]
list1.extend([4, 5])
print(list1)
# Output: [1, 2, 3, 4, 5]

# append() adds the entire list as one nested item
list2 = [1, 2, 3]
list2.append([4, 5])
print(list2)
# Output: [1, 2, 3, [4, 5]]
```

Use `extend()` when you want to merge lists. Use `append()` when you want to add a list as a single nested element.

---

## Removing Items from Lists

Python provides two main methods for removing items, each with different behavior.

### The `.remove()` Method

The `remove()` method searches for a value and deletes the first match it finds.

```python
# Remove a specific item from inventory
inventory = ["apple", "banana", "apple", "orange"]
inventory.remove("apple")  # Removes only the first "apple"

print(inventory)
# Output: ['banana', 'apple', 'orange']
```

**Key Characteristics:**
- Returns `None` (modifies the list in place)
- Searches by value, not by position
- Removes only the first match
- Raises `ValueError` if the value doesn't exist

```python
# Attempting to remove non-existent item causes error
numbers = [10, 20, 30]
numbers.remove(99)
# Error: ValueError: list.remove(x): x not in list
```

**Safe Removal Pattern:**

```python
# Check before removing to avoid errors
inventory = ["apple", "banana", "orange"]
item_to_remove = "grape"

if item_to_remove in inventory:
    inventory.remove(item_to_remove)
    print(f"Removed {item_to_remove}")
else:
    print(f"{item_to_remove} not found in inventory")
# Output: grape not found in inventory
```

### The `.pop()` Method

The `pop()` method removes an item by position and returns that item. This lets you capture the removed value for further use.

```python
# Process and remove the last item in a queue
queue = ["task1", "task2", "task3"]
completed_task = queue.pop()  # Removes and returns last item

print(f"Completed: {completed_task}")
# Output: Completed: task3

print(f"Remaining tasks: {queue}")
# Output: Remaining tasks: ['task1', 'task2']
```

**With Index Argument:**

```python
# Remove item at specific position
scores = [85, 90, 95, 100]
removed_score = scores.pop(1)  # Remove item at index 1

print(f"Removed: {removed_score}")
# Output: Removed: 90

print(f"Updated scores: {scores}")
# Output: Updated scores: [85, 95, 100]
```

**Key Difference from `remove()`:**

```python
# pop() removes by POSITION and RETURNS the item
values = [10, 20, 30, 40]
last_value = values.pop()  # Returns 40
print(last_value)
# Output: 40

# remove() removes by VALUE and RETURNS nothing
values = [10, 20, 30, 40]
result = values.remove(30)
print(result)
# Output: None
```

---

## Method Comparison Table

| Method | Purpose | What It Returns | How It Finds Items |
|--------|---------|----------------|-------------------|
| `.append(item)` | Adds one item to end | `None` | N/A |
| `.insert(index, value)` | Adds item at position | `None` | By index |
| `.extend(iterable)` | Adds all items from iterable | `None` | N/A |
| `.remove(value)` | Deletes first match | `None` | By value |
| `.pop(index)` | Deletes item at position | The removed item | By index |

---

## Practical Examples

### Building a Dynamic Playlist

```python
# User builds a music playlist
playlist = []

# Add songs as user selects them
playlist.append("Song A")
playlist.append("Song B")
playlist.append("Song C")

# User wants to prioritize a favorite song at the start
playlist.insert(0, "Favorite Song")

# User removes a song they don't want
playlist.remove("Song B")

# User plays and removes the last song
now_playing = playlist.pop()

print(f"Now playing: {now_playing}")
# Output: Now playing: Song C

print(f"Playlist: {playlist}")
# Output: Playlist: ['Favorite Song', 'Song A']
```

### Processing User Input

```python
# Collect user responses and process them
responses = []

# Simulate collecting three responses
responses.append("yes")
responses.append("no")
responses.append("yes")

# Count "yes" responses while removing them
yes_count = 0
while "yes" in responses:
    responses.remove("yes")
    yes_count += 1

print(f"Total 'yes' responses: {yes_count}")
# Output: Total 'yes' responses: 2

print(f"Remaining responses: {responses}")
# Output: Remaining responses: ['no']
```

### Merging Data from Multiple Sources

```python
# Combine temperature readings from different sensors
sensor_1_readings = [22, 23, 24]
sensor_2_readings = [25, 26, 27]
sensor_3_readings = [28, 29, 30]

# Combine all readings into one list
all_readings = []
all_readings.extend(sensor_1_readings)
all_readings.extend(sensor_2_readings)
all_readings.extend(sensor_3_readings)

print(f"All readings: {all_readings}")
# Output: All readings: [22, 23, 24, 25, 26, 27, 28, 29, 30]

print(f"Total readings: {len(all_readings)}")
# Output: Total readings: 9

# Calculate average
average = sum(all_readings) / len(all_readings)
print(f"Average temperature: {average:.1f}°C")
# Output: Average temperature: 25.5°C
```

---

## Common Errors and Fixes

### Error 1: Using `remove()` with Non-Existent Values

**Bad Code:**

```python
# Attempting to remove item that doesn't exist
cart = ["milk", "eggs", "bread"]
cart.remove("butter")
# Error: ValueError: list.remove(x): x not in list
```

**Why This Fails:**  
The `remove()` method raises an error when the value isn't found in the list.

**Fixed Code:**

```python
# Check if item exists before removing
cart = ["milk", "eggs", "bread"]
item = "butter"

if item in cart:
    cart.remove(item)
    print(f"Removed {item}")
else:
    print(f"{item} not in cart")
# Output: butter not in cart
```

**Why This Works:**  
Checking membership with `in` prevents the error by confirming the item exists before attempting removal.

### Error 2: Confusing `append()` with `extend()`

**Bad Code:**

```python
# Trying to add multiple items with append
scores = [85, 90]
scores.append(95, 100)  # Wrong syntax
# Error: TypeError: append() takes exactly one argument (2 given)
```

**Why This Fails:**  
The `append()` method accepts only one argument. It adds that single item to the list.

**Fixed Code:**

```python
# Use extend() to add multiple items
scores = [85, 90]
new_scores = [95, 100]
scores.extend(new_scores)

print(scores)
# Output: [85, 90, 95, 100]
```

**Why This Works:**  
The `extend()` method iterates over the provided iterable and adds each item individually.

### Error 3: Expecting `remove()` to Return the Item

**Bad Code:**

```python
# Trying to capture the removed item
inventory = ["apple", "banana", "orange"]
removed_item = inventory.remove("banana")

print(f"Removed: {removed_item}")
# Output: Removed: None
```

**Why This Fails:**  
The `remove()` method returns `None`. It doesn't return the item it removed.

**Fixed Code:**

```python
# Use pop() when you need the removed item
inventory = ["apple", "banana", "orange"]
index_to_remove = inventory.index("banana")
removed_item = inventory.pop(index_to_remove)

print(f"Removed: {removed_item}")
# Output: Removed: banana

print(f"Updated inventory: {inventory}")
# Output: Updated inventory: ['apple', 'orange']
```

**Why This Works:**  
The `pop()` method removes the item at the specified index and returns it.

### Error 4: Using `pop()` on Empty Lists

**Bad Code:**

```python
# Trying to pop from empty list
tasks = []
completed = tasks.pop()
# Error: IndexError: pop from empty list
```

**Why This Fails:**  
You can't remove an item from an empty list.

**Fixed Code:**

```python
# Check if list has items before popping
tasks = []

if tasks:
    completed = tasks.pop()
    print(f"Completed: {completed}")
else:
    print("No tasks to complete")
# Output: No tasks to complete
```

**Why This Works:**  
Checking if the list is truthy (non-empty) prevents the error.

---

## Practice Exercises

**Exercise 1: Build a Task Manager**

Create a program that manages a to-do list. Start with an empty list. Add three tasks using `append()`. Insert a high-priority task at the beginning. Remove the second task. Print the final list.

<details>
<summary>Solution</summary>

```python
# Task management system
tasks = []

# Add initial tasks
tasks.append("Buy groceries")
tasks.append("Clean house")
tasks.append("Pay bills")

# Add urgent task at the start
tasks.insert(0, "Emergency dentist appointment")

# Remove second task (index 1)
tasks.pop(1)

print("Final task list:")
for i, task in enumerate(tasks, 1):
    print(f"{i}. {task}")
# Output: Final task list:
# Output: 1. Emergency dentist appointment
# Output: 2. Clean house
# Output: 3. Pay bills
```

**Explanation:** This solution demonstrates `append()` for adding items, `insert()` for prioritizing, and `pop()` for removing by position. The `enumerate()` function provides numbered output.

</details>

**Exercise 2: Merge Student Grade Lists**

You have two lists: `class_a_grades = [85, 90, 78]` and `class_b_grades = [92, 88, 95]`. Combine them into one list called `all_grades` using `extend()`. Calculate and print the average grade.

<details>
<summary>Solution</summary>

```python
# Combine grades from multiple classes
class_a_grades = [85, 90, 78]
class_b_grades = [92, 88, 95]

# Merge all grades into one list
all_grades = []
all_grades.extend(class_a_grades)
all_grades.extend(class_b_grades)

# Calculate average
total = sum(all_grades)
count = len(all_grades)
average = total / count

print(f"All grades: {all_grades}")
# Output: All grades: [85, 90, 78, 92, 88, 95]

print(f"Average grade: {average:.1f}")
# Output: Average grade: 88.0
```

**Explanation:** The `extend()` method combines both lists into one. Using `sum()` and `len()` calculates the average efficiently.

</details>

**Exercise 3: Remove Duplicates Safely**

Given the list `numbers = [5, 10, 5, 20, 5, 30]`, remove all instances of the number `5` using a loop. Print the final list.

<details>
<summary>Solution</summary>

```python
# Remove all instances of a specific value
numbers = [5, 10, 5, 20, 5, 30]
value_to_remove = 5

# Remove all occurrences
while value_to_remove in numbers:
    numbers.remove(value_to_remove)

print(f"After removing {value_to_remove}: {numbers}")
# Output: After removing 5: [10, 20, 30]
```

**Explanation:** The `while` loop continues removing the value until it's no longer in the list. The `in` operator checks for membership before each removal.

</details>

**Exercise 4: Shopping Cart Operations**

Create a shopping cart starting with `["apple", "banana", "milk"]`. Add "bread" to the cart. Remove "banana". Add "eggs" at the beginning of the cart. Print the final cart and its length.

<details>
<summary>Solution</summary>

```python
# Shopping cart management
cart = ["apple", "banana", "milk"]

# Add bread to the end
cart.append("bread")

# Remove banana
cart.remove("banana")

# Add eggs as priority item at start
cart.insert(0, "eggs")

print(f"Shopping cart: {cart}")
# Output: Shopping cart: ['eggs', 'apple', 'milk', 'bread']

print(f"Total items: {len(cart)}")
# Output: Total items: 4
```

**Explanation:** This exercise combines `append()`, `remove()`, and `insert()` to demonstrate common cart operations. Each method modifies the list in place.

</details>

**Exercise 5: Process Queue with Pop**

You have a queue `queue = ["first", "second", "third", "fourth"]`. Process (remove and print) each item in order using `pop(0)` until the queue is empty.

<details>
<summary>Solution</summary>

```python
# Process items in a queue
queue = ["first", "second", "third", "fourth"]

# Process each item until queue is empty
while queue:
    current = queue.pop(0)  # Remove from front
    print(f"Processing: {current}")

print("Queue is empty")
# Output: Processing: first
# Output: Processing: second
# Output: Processing: third
# Output: Processing: fourth
# Output: Queue is empty
```

**Explanation:** Using `pop(0)` removes items from the front of the list, maintaining queue order (FIFO - First In, First Out). The `while queue:` loop continues until the list is empty.

</details>

---

## Key Takeaways

✅ **`append()` adds items to the end** - Use this for building lists incrementally during program execution  
✅ **`insert()` adds items at specific positions** - Use when placement matters, shifts items to the right  
✅ **`extend()` merges entire iterables** - Flattens items into existing list, different from `append()` which nests  
✅ **`remove()` deletes by value** - Removes first match only, returns `None`, raises error if not found  
✅ **`pop()` deletes by position and returns item** - Default removes last item, useful when you need the removed value  
✅ **Always check before removing** - Use `in` operator to avoid `ValueError` with `remove()`  
✅ **All methods modify in place** - Original list changes, no new list created

**Remember:** Use `append()` and `pop()` for stack operations (adding/removing from end), use `insert()` and `pop(0)` for queue operations (adding to end/removing from start).

---

**Last Updated:** November 6, 2025
