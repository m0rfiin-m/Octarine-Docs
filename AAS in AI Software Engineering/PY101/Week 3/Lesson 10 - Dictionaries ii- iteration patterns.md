
### 1. The 3 Main Iteration Methods

You learned three key methods to loop through different parts of a dictionary. We'll use your `menu` dictionary as the example:

```python
menu = {
    "Pizza": 8,
    "Sushi": 20,
    "Pho": 14
}
```

---

### 2. Looping Through Keys

Use the `.keys()` method to get just the keys (e.g., the dish names).

```python
# The .keys() method gives you all the keys
for dish in menu.keys():
    # You can then use the key in your loop
    print(dish.upper())

# --- Output ---
# PIZZA
# SUSHI
# PHO
```

---

### 3. Looping Through Values

Use the `.values()` method to get just the values (e.g., the prices). This is useful for calculations.

```python
# 1. Simply printing all values
for price in menu.values():
    print(price)

# --- Output ---
# 8
# 20
# 14

# 2. Calculating a total
total = 0
for price in menu.values():
    total += price  # Add each price to the total

print(total)

# --- Output ---
# 42
```

---

### 4. Looping Through Key-Value Pairs

Use the `.items()` method to get **both** the key and the value at the same time. This is the most common pattern.

- You must use **two loop variables** (e.g., `dish, price`) to "unpack" the pair.

```python
# Note the two variables: dish, price
for dish, price in menu.items():
    print(f"{dish}: ${price}")

# --- Output ---
# Pizza: $8
# Sushi: $20
# Pho: $14
```

---

### 5. Combining Loops with Conditionals

You can put an `if` statement *inside* your loop to do different things based on the data.

```python
# Using the .items() loop
for dish, price in menu.items():
    
    # Check a condition on the value
    if price > 10:
        print(f"{dish}: ${price} expensive")
    else:
        print(f"{dish}: ${price}")

# --- Output ---
# Pizza: $8
# Sushi: $20 expensive
# Pho: $14 expensive
```

### 🧠 Quick Review

- Want only keys? Use `.keys()`

- Want only values? Use `.values()`

- Want both? Use `.items()`