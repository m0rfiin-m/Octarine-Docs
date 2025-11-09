
### 1. Assignment (Aliasing) vs. Copying

This is the most important concept from the lesson.

- **Assignment (**`=`**):** When you use the equal sign (`=`), you are **not** making a copy. You are creating an "alias," or a second name, that points to the **exact same object** in memory.

- **Copying:** This creates a brand new, independent object with the same values as the original.

---

### 2. The "Side Effect" of Aliasing

When you have an alias, changing one variable will also change the other, because they are both names for the same object.

**List Example:**

```python
# 1. Create original list
temps = [10, 20, 30]

# 2. Create an alias (NOT a copy)
alias = temps

# 3. Modify the alias
alias[0] = 99

# 4. The original list is also changed!
print(temps)  # Output: [99, 20, 30]
```

**Dictionary Example:**

```python
# 1. Create original dictionary
menu = {"Pizza": 12, "Pho": 8}

# 2. Create an alias
menu_alias = menu

# 3. Modify the alias
menu_alias["Pizza"] = 99

# 4. The original dictionary is also changed!
print(menu)   # Output: {'Pizza': 99, 'Pho': 8}
```

---

### 3. Checking Identity (`is`) vs. Equality (`==`)

- `==` **(Equality):** Checks if the **values** are the same.

- `is` **(Identity):** Checks if two variables are the **exact same object** in memory.

Python

```plaintext
temps = [10, 20, 30]
alias = temps         # Same object
copy = temps.copy()   # Different object, same values

print(temps == copy)   # Output: True (values are equal)
print(temps is copy)   # Output: False (they are different objects)

print(temps == alias)  # Output: True (values are equal)
print(temps is alias)  # Output: True (they are the same object)
```

---

### 4. How to Make a Real, Independent Copy

To avoid changing your original data, you must make a copy.

#### For Lists:

You learned three ways. All of them create a new, independent list.

1. `.copy()` **method:** `copy1 = temps.copy()`

2. **Slicing** `[:]`**:** `copy2 = temps[:]`

3. `list()` **constructor:** `copy3 = list(temps)`

**Example:**

Python

```plaintext
temps = [10, 20, 30]
copy1 = temps.copy()
copy1[0] = 42

print(temps)  # Output: [10, 20, 30] (The original is safe!)
print(copy1) # Output: [42, 20, 30]
```

#### For Dictionaries:

You learned two ways. Both create a new, independent dictionary.

1. `dict()` **constructor:** `menu_copy = dict(menu)`

2. `.copy()` **method:** `menu_copy = menu.copy()`

**Example:**

Python

```plaintext
menu = {"Pizza": 12, "Pho": 8}
menu_copy = dict(menu)
menu_copy["Pho"] = 5

print(menu)       # Output: {'Pizza': 12, 'Pho': 8} (The original is safe!)
print(menu_copy)  # Output: {'Pizza': 12, 'Pho': 5}
```

This concept of "copy vs. alias" is one of the most common things that trips up new Python programmers, so it's great that you've mastered it!