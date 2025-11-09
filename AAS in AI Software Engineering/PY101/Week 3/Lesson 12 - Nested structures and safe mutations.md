
This lesson focused on two critical skills: how to work with data *inside* other data (like a list inside a list) and how to do so *safely* to avoid bugs.

### 1. Accessing Nested Data

To get data from a nested structure, you "chain" the accessors (the `[]` brackets) from the outside in.

- **List of Lists:** You use multiple numeric indices.

  ```python
  temps_by_day = [
      [70, 72, 68],  # Index 0 (Monday)
      [75, 71, 69],  # Index 1 (Tuesday)
      [73, 70, 67]   # Index 2 (Wednesday)
  ]
  
  # Get Tuesday's first temp (75)
  # temps_by_day[1] -> [75, 71, 69]
  # temps_by_day[1][0] -> 75
  print(temps_by_day[1][0])
  
  ```

- **Dictionary of Dictionaries:** You use multiple keys.

  ```python
  menu = {
      "Pizza": {"price": 12, "sold": 30},
      "Pho":   {"price": 8, "sold": 25}
  }
  
  # Get Pho's "sold" value (25)
  # menu["Pho"] -> {"price": 8, "sold": 25}
  # menu["Pho"]["sold"] -> 25
  print(menu["Pho"]["sold"])
  
  ```

---

### 2. Mutating Nested Data

"Mutating" just means "changing." You use the same chain of `[]` brackets to assign a new value.

- **List:** `temps_by_day[1][0] = 80` (Changes Tuesday's first temp to 80)

- **Dictionary:** `menu["Pho"]["sold"] = 26` (Changes Pho's "sold" count to 26)

---

### 3. The Alias "Trap" (The Most Important Concept)

When you assign a nested item to a new variable, you are **not** making a copy. You are making an **alias** (another name) for the *exact same object* in memory.

**This means changing the alias will change the original structure.**

```python
# --- List Example ---
temps_by_day = [[70, 72, 68], [80, 71, 69]]

# Create an ALIAS for Monday's list
first_day = temps_by_day[0]

# Modify the alias
first_day[2] = 99  # Change the last temp to 99

# The ORIGINAL list is also changed!
print(temps_by_day)
# Output: [[70, 72, 99], [80, 71, 69]]

# --- Dictionary Example ---
pho_stats = menu["Pho"]
pho_stats["price"] = 9  # Change the price on the alias

# The ORIGINAL dictionary is also changed!
print(menu)
# Output: {'Pizza': {...}, 'Pho': {'price': 9, 'sold': 26}, ...}
```

The operator `is` checks for this. `first_day is temps_by_day[0]` would return `True`, because they are the same object.

---

### 4. How to Make a Safe, Independent Copy

To modify data without changing the original, you must make an explicit copy. For a nested list, you can use slicing `[:]`.

```python
temps_by_day = [[70, 72, 99], [80, 71, 69]]

# Create a COPY of Monday's list using [:]
monday_copy = temps_by_day[0][:]

# Modify the copy
monday_copy[0] = -100

# The original is UNCHANGED
print(temps_by_day)
# Output: [[70, 72, 99], [80, 71, 69]]

# The copy IS changed
print(monday_copy)
# Output: [-100, 72, 99]
```

> **Why this matters:** This concept of "alias vs. copy" is one of the most common sources of bugs in programming. You'll use it in data analysis, web development, and game design, any time you're working with complex data and don't want to accidentally change your original source.

---

### 5. Safe Reading from Dictionaries (The `.get()` Method)

Trying to access a key that doesn't exist with `[]` will crash your program with a `KeyError`.

```python
# This will CRASH
# print(menu["Tacos"])
```

To read safely, you have two options with the `.get()` method:

1. `.get(key)`**:**

   - Returns the value if the key exists.

   - Returns `None` (a special "nothing" value) if the key is missing. **It does not crash.**

   ```python
   print(menu.get("Tacos"))
   # Output: None
   
   ```

2. `.get(key, default_value)`**:**

   - Returns the value if the key exists.

   - Returns the `default_value` you provide if the key is missing.

   ```python
   # Get stats for "Tacos", or a default dictionary if it's not there
   tacos = menu.get("Tacos", {"price": 3, "sold": 0})
   
   print(tacos)
   # Output: {'price': 3, 'sold': 0}
   
   ```

You can then use this to safely add a new item to your dictionary:

```python
# 1. Safely get the item (or its default)
tacos = menu.get("Tacos", {"price": 3, "sold": 0})

# 2. Add it to the menu
menu["Tacos"] = tacos

print(menu)
# Output: {'Pizza': ..., 'Pho': ..., 'Burger': ..., 'Tacos': {'price': 3, 'sold': 0}}
```

This covers all the key concepts from that lesson. Would you like a mini-challenge to practice safe copying and `.get()`?