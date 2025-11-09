
### 1. The Goal: From Raw Text to Structured Data

This lesson was all about turning a messy block of text into a clean, usable **list of dictionaries**.

- **From This (Raw Text):**

  ```python
  Alice|Paris|29
  Bob|London|32
  
  ```

- **To This (List of Dicts):**

  Python

  ```python
  [
    {'name': 'Alice', 'city': 'Paris', 'age': '29'},
    {'name': 'Bob', 'city': 'London', 'age': '32'}
  ]
  
  ```

---

### 2. The Main Parsing Pattern

This is the most important part of the lesson. You learned a 4-step pattern to process multi-line data.

Python

```python
data = """Alice|Paris|29
Bob|London|32
Eve|Berlin|28"""

# 1. Initialize an empty list to store your results
people = []

# 2. Get a list of all lines
lines = data.splitlines()

# 3. Loop through each line
for line in lines:
    # 4. Inside the loop:
    
    # a. Split the line into its parts
    parts = line.split("|")
    
    # b. Map the parts to a new dictionary
    person = {
        "name": parts[0],
        "city": parts[1],
        "age": parts[2]
    }
    
    # c. Add the new dictionary to your main list
    people.append(person)

# The final result
print(people)
```

---

### 3. Key Functions and Concepts

#### `.splitlines()`

This function is built for multi-line strings (those created with `"""..."""`). It splits the string once for each new line, giving you a clean list of strings.

Python

```python
data = """Line one
Line two"""

print(data.splitlines())
# Output: ['Line one', 'Line two']
```

#### `.split(delimiter)`

You used this *inside* the loop. It takes a single line string and splits it into a list of smaller strings based on a "delimiter" (in your case, the `|` pipe character).

```python
line = "Alice|Paris|29"

print(line.split("|"))
# Output: ['Alice', 'Paris', '29']
```

#### Values are Copied, Not Linked

When you create a dictionary, Python copies the values over. It does **not** create a live link to the original `parts` list.

Python

```python
parts = ["Alice", "Paris", "29"]

# 1. The values are COPIED into the dictionary
person = {"name": parts[0], "city": parts[1], "age": parts[2]}

# 2. Changing 'parts' later...
parts[0] = "Marco"

# 3. ...does NOT affect the 'person' dictionary
print(person)
# Output: {'name': 'Alice', 'city': 'Paris', 'age': '29'}
```

---

The operator `is` checks for this. `first_day is temps_by_day[0]` would return `True`, because they are the same object.

### 4. Safe Access: `[]` vs. `.get()`

This was a critical review of a previous concept. When you have messy data, you need to access it safely.

- `dict["key"]` **(Bracket Access):**

  - **Pro:** It's fast and direct.

  - **Con:** It will **CRASH** your program with a `KeyError` if the key (e.g., "salary") doesn't exist.

- `dict.get("key")` **(The** `.get()` **Method):**

  - **Pro:** It is **SAFE**.

  - If the key exists, it returns the value (just like `[]`).

  - If the key does **not** exist, it returns `None` and your program continues running.

Python

```python
my_dict = {"food": "tacos"}

# --- Safe Access ---
print(my_dict.get("food"))    # Output: tacos
print(my_dict.get("drink"))   # Output: None (No crash!)

# --- Unsafe Access ---
print(my_dict["food"])    # Output: tacos
# print(my_dict["drink"])   # This line would CRASH with KeyError
```

This whole pattern loop, split, map to dict, append is one of the most common and powerful tasks in programming.