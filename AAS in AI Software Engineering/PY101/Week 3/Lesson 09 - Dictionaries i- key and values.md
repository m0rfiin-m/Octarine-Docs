
### 1. Creating and Accessing Dictionaries

A dictionary is a collection of **key-value pairs**. You create one using curly braces `{}`.

- **Syntax:** Each pair is written as `key: value`, and pairs are separated by commas `,`.

- **Accessing a value:** You use square brackets `[]` with the key's name.

```python
# Creating a dictionary
student = {
    "name": "Marco",
    "city": "Dallas"
}

# Accessing and printing values
print(student["name"])  # Output: Marco
print(student["city"])  # Output: Dallas
```

---

### 2. Adding and Updating Dictionary Data

You use the same square bracket `[]` syntax to either add a new key-value pair or update an existing one.

- **To add:** If the key doesn't exist, Python adds it.

- **To update:** If the key *does* exist, Python updates its value.

```python
# Starting with our dictionary
student = {
    "name": "Marco",
    "city": "Dallas"
}

# Adding a new key "major"
student["major"] = "CS"

# Updating an existing key "age" (let's add it first)
student["age"] = 22
print(student)  # Output: {'name': 'Marco', 'city': 'Dallas', 'major': 'CS', 'age': 22}

# Now, update the age
student["age"] = 23
print(student)  # Output: {'name': 'Marco', 'city': 'Dallas', 'major': 'CS', 'age': 23}

# --- Example with the menu ---
menu = {
    "Pizza": 5,
    "Sushi": 20,
    "Pho": 14
}

# Updating the price of "Pizza"
menu["Pizza"] = 8
print(menu)     # Output: {'Pizza': 8, 'Sushi': 20, 'Pho': 14}
```

---

### 3. The Rule for Dictionary Keys (Immutability)

This is a very important rule in Python: **Dictionary keys must be an immutable type.**

- **Immutable** means "cannot be changed."

- **Valid Keys (Immutable):** Strings, numbers (integers), and tuples are allowed.

- **Invalid Keys (Mutable):** Lists and other dictionaries are *not* allowed.

Trying to use a list as a key will cause a `TypeError`.

```python
# This works (tuple key)
good = {
    (1, 2): "ok"
}
print(good)

# This fails (list key)
# bad = {
#    [1, 2]: "oops"
# }
# ^ This code produces: TypeError: unhashable type: 'list'
```

---

### 4. Bonus: Looping and Calculating

You can use methods to work with all the values in a dictionary.

- `menu.values()`: This gives you just the values (e.g., all the prices).

- `len(menu)`: This gives you the number of key-value pairs in the dictionary.

You can combine these to calculate the average price from your `menu` dictionary.

```python
menu = {
    "Pizza": 8,
    "Sushi": 20,
    "Pho": 14
}

total = 0
for price in menu.values():
    total += price  # Same as total = total + price

# Calculate the average
avg = total / len(menu)

print(total) # Output: 42
print(avg)  # Output: 14.0
```

This covers all the main points from your lesson. Let me know when you'd like to start the next lesson or practice this one again!