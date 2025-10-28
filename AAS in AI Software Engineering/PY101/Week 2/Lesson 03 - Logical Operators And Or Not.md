# Logical Operators: And, Or, Not

**Date:** October 28, 2025  
**Course:** PY101 - Introduction to Python  
**Week:** 2, Lesson 3  
**Lesson Link:** [Maestro Lesson](https://maestro.org/learn/688b5ab40508accc71b2ef49-4/688b5ab40508accc71b2e87a-56/68f5356d52288d89898846dd)

## What You'll Learn

This lesson covers logical operators in Python that let you combine multiple conditions. You'll learn how `and`, `or`, and `not` work, understand short-circuiting behavior, and practice combining conditions for complex decision-making.

---

## The Three Logical Operators

Python provides three logical operators to combine or modify boolean expressions.

### `and` Operator

Both conditions must be True for the result to be True.

```python
temp = 55
weather = "rain"

print(temp < 60 and weather == "rain")
# Output: True
```

**Truth Table for `and`:**

| Left Side | Right Side | Result |
|-----------|------------|--------|
| True | True | True |
| True | False | False |
| False | True | False |
| False | False | False |

**Key Point:** If either side is False, the entire expression is False.

### `or` Operator

Only one condition needs to be True for the result to be True.

```python
temp = 65
weather = "sun"

print(temp < 60 or weather == "sun")
# Output: True
```

**Truth Table for `or`:**

| Left Side | Right Side | Result |
|-----------|------------|--------|
| True | True | True |
| True | False | True |
| False | True | True |
| False | False | False |

**Key Point:** If either side is True, the entire expression is True.

### `not` Operator

Flips the boolean value (True becomes False, False becomes True).

```python
door_open = True
print(not door_open)
# Output: False

door_open = False
print(not door_open)
# Output: True
```

**Truth Table for `not`:**

| Original | Result |
|----------|--------|
| True | False |
| False | True |

**Key Point:** `not` inverts whatever comes after it.

---

## Building Complex Conditions

### Simple Comparison

Start with a basic comparison that returns True or False.

```python
temp = 55
print(temp < 60)
# Output: True
```

### Combining with `and`

Check if multiple conditions are all True.

```python
temp = 55
weather = "rain"

print(temp < 60 and weather == "rain")
# Output: True
```

**How It Works:**
1. `temp < 60` evaluates to `True` (55 < 60)
2. `weather == "rain"` evaluates to `True`
3. `True and True` results in `True`

**Try Different Values:**

```python
# Case 1: Both conditions True
temp = 55
weather = "rain"
print(temp < 60 and weather == "rain")  # True

# Case 2: First True, second False
temp = 55
weather = "sun"
print(temp < 60 and weather == "rain")  # False

# Case 3: First False, second True
temp = 65
weather = "rain"
print(temp < 60 and weather == "rain")  # False

# Case 4: Both False
temp = 65
weather = "sun"
print(temp < 60 and weather == "rain")  # False
```

### Combining with `or`

Check if at least one condition is True.

```python
temp = 65
weather = "sun"

print(temp < 60 or weather == "sun")
# Output: True
```

**How It Works:**
1. `temp < 60` evaluates to `False` (65 is not < 60)
2. `weather == "sun"` evaluates to `True`
3. `False or True` results in `True`

**Try Different Values:**

```python
# Case 1: Both conditions True
temp = 55
weather = "sun"
print(temp < 60 or weather == "sun")  # True

# Case 2: First True, second False
temp = 55
weather = "rain"
print(temp < 60 or weather == "sun")  # True

# Case 3: First False, second True
temp = 65
weather = "sun"
print(temp < 60 or weather == "sun")  # True

# Case 4: Both False
temp = 65
weather = "rain"
print(temp < 60 or weather == "sun")  # False
```

---

## Using `not` to Invert Logic

### Flipping Simple Booleans

```python
door_open = True
print(not door_open)
# Output: False

door_open = False
print(not door_open)
# Output: True
```

### Flipping Comparisons

```python
age = 25
print(not age < 18)
# Output: True (because age < 18 is False, and not False is True)
```

### Flipping Complex Conditions

Always use parentheses when applying `not` to a complex expression.

```python
temp = 55
weather = "rain"

# Without not
print(temp < 60 and weather == "rain")
# Output: True

# With not (using parentheses)
print(not (temp < 60 and weather == "rain"))
# Output: False
```

**Why Parentheses Matter:**

```python
# Wrong - unclear precedence
print(not temp < 60 and weather == "rain")

# Correct - explicit grouping
print(not (temp < 60 and weather == "rain"))
```

---

## Combining Multiple Operators

You can chain logical operators to create sophisticated conditions.

### `and` with Multiple Conditions

```python
age = 25
has_license = True
has_insurance = True

print(age >= 18 and has_license and has_insurance)
# Output: True
```

All conditions must be True for the result to be True.

### `or` with Multiple Conditions

```python
payment_method = "credit"

print(payment_method == "cash" or payment_method == "credit" or payment_method == "debit")
# Output: True
```

Only one condition needs to be True for the result to be True.

### Mixing `and` and `or`

```python
age = 16
has_parent_permission = True

# Teen with permission OR adult (18+)
print((age >= 13 and has_parent_permission) or age >= 18)
# Output: True
```

**Use Parentheses:** When mixing operators, parentheses make your logic explicit and prevent errors.

---

## Short-Circuiting

Python optimizes logical operations by stopping evaluation as soon as the result is known.

### How Short-Circuiting Works

**With `and`:**
- If the left side is False, Python doesn't check the right side
- The result is already known to be False

**With `or`:**
- If the left side is True, Python doesn't check the right side
- The result is already known to be True

### Demonstrating Short-Circuiting

```python
def right():
    print("right side evaluated")
    return True

# False and X - right side never runs
print(False and right())
# Output: False
# (Notice "right side evaluated" never prints)

# True or X - right side never runs
print(True or right())
# Output: True
# (Notice "right side evaluated" never prints)
```

### When Short-Circuiting Matters

```python
def check_database():
    print("Checking database...")
    return True

# Only check database if user is logged in
is_logged_in = False

if is_logged_in and check_database():
    print("Access granted")
else:
    print("Login required")

# Output: Login required
# (Notice "Checking database..." never prints)
```

**Why This Is Useful:** Avoid expensive operations (like database queries) when they're unnecessary.

---

## Practical Examples

### Example 1: Age and Permission Check

```python
age = 16
has_parent_permission = True

if age >= 18 or (age >= 13 and has_parent_permission):
    print("Can create account")
else:
    print("Cannot create account")
# Output: Can create account
```

### Example 2: Weather Decision

```python
temp = 70
is_raining = False
is_sunny = True

if temp > 65 and not is_raining and is_sunny:
    print("Perfect day for a picnic!")
else:
    print("Maybe stay inside")
# Output: Perfect day for a picnic!
```

### Example 3: Login Validation

```python
username = "player1"
password = "secret123"
is_verified = True

if username == "player1" and password == "secret123" and is_verified:
    print("Login successful")
else:
    print("Login failed")
# Output: Login successful
```

### Example 4: Discount Eligibility

```python
is_student = True
is_senior = False
is_veteran = False

if is_student or is_senior or is_veteran:
    print("Eligible for discount")
else:
    print("Regular pricing")
# Output: Eligible for discount
```

---

## Loop with Multiple Conditions

Combine loops with logical operators for powerful filtering.

### Pattern: Filter Based on Multiple Criteria

```python
nums = [4, 7, 8, 11, 12]

for number in nums:
    if number < 10 and number % 2 == 0:
        print("small even")
    else:
        print("skip")
```

**Output:**
```
small even
skip
small even
skip
skip
```

**How It Works:**
1. Loop checks each number
2. Condition: number must be less than 10 AND even
3. Only 4 and 8 meet both criteria

### More Examples

**Example 1: Temperature Alerts**

```python
temperatures = [45, 72, 95, 58, 102]

for temp in temperatures:
    if temp < 50 or temp > 100:
        print(f"{temp}°F: ALERT")
    else:
        print(f"{temp}°F: Normal")
```

**Output:**
```
45°F: ALERT
72°F: Normal
95°F: Normal
58°F: Normal
102°F: ALERT
```

**Example 2: Grade Classification**

```python
scores = [95, 72, 88, 45, 91]

for score in scores:
    if score >= 90 and score <= 100:
        print(f"{score}: A")
    elif score >= 80 and score < 90:
        print(f"{score}: B")
    else:
        print(f"{score}: Other")
```

**Output:**
```
95: A
72: Other
88: B
45: Other
91: A
```

---

## Common Pitfalls

### Pitfall 1: Forgetting Parentheses with `not`

```python
temp = 55
weather = "rain"

# Wrong - ambiguous
print(not temp < 60 and weather == "rain")

# Correct - clear intent
print(not (temp < 60 and weather == "rain"))
```

### Pitfall 2: Confusing `and` with `or`

```python
age = 16

# Wrong - no one can satisfy both conditions
if age < 18 and age >= 18:
    print("This never happens")

# Correct - checking a range
if age >= 13 and age < 18:
    print("Teenager")
```

### Pitfall 3: Redundant Comparisons

```python
# Inefficient
if x == True:
    print("x is true")

# Better
if x:
    print("x is true")

# Inefficient
if x == False:
    print("x is false")

# Better
if not x:
    print("x is false")
```

### Pitfall 4: Wrong Order with Mixed Operators

```python
# Ambiguous - what happens first?
result = True or False and False

# Clear with parentheses
result = True or (False and False)  # True
result = (True or False) and False  # False
```

**Tip:** When in doubt, use parentheses to make your logic explicit.

---

## Practice Exercises

### Exercise 1: Complete the Conditions

Fill in the logical operators to make each line print True.

```python
x = False
print(not x ___ x)  # Should print True

a = 8
b = 3
print(a < 10 ___ not b < 2)  # Should print True

rain = False
sunny = True
print(not rain ___ sunny)  # Should print True
```

<details>
<summary>Solution</summary>

```python
x = False
print(not x or x)  # True (not False = True, True or False = True)

a = 8
b = 3
print(a < 10 and not b < 2)  # True (8 < 10 = True, not 3 < 2 = True, True and True = True)

rain = False
sunny = True
print(not rain and sunny)  # True (not False = True, True and True = True)
```
</details>

### Exercise 2: Access Control

Write a condition that grants access if the user is an admin OR (is a member AND has paid).

<details>
<summary>Solution</summary>

```python
is_admin = False
is_member = True
has_paid = True

if is_admin or (is_member and has_paid):
    print("Access granted")
else:
    print("Access denied")
# Output: Access granted
```
</details>

### Exercise 3: Number Filter

Write a loop that prints "match" for numbers that are either positive OR even (or both).

<details>
<summary>Solution</summary>

```python
numbers = [4, -7, 0, 11, -2]

for num in numbers:
    if num > 0 or num % 2 == 0:
        print(f"{num}: match")
    else:
        print(f"{num}: no match")
```

**Output:**
```
4: match (positive AND even)
-7: no match (negative AND odd)
0: match (even)
11: match (positive)
-2: match (even)
```
</details>

### Exercise 4: Predict the Output

What will this code print?

```python
def expensive_check():
    print("Running expensive check")
    return True

x = False
result = x and expensive_check()
print(result)
```

<details>
<summary>Answer</summary>

**Output:**
```
False
```

**Explanation:**
- `x` is False
- Because of short-circuiting with `and`, Python doesn't call `expensive_check()`
- "Running expensive check" never prints
- Result is False
</details>

---

## Real-World Applications

### User Authentication

```python
username = "admin"
password = "secure123"
two_factor_code = "456789"

if username == "admin" and password == "secure123" and two_factor_code == "456789":
    print("Access granted")
else:
    print("Authentication failed")
```

### E-commerce Cart

```python
cart_total = 45
has_coupon = True
is_member = True

if (cart_total > 50 or has_coupon) and is_member:
    print("Free shipping!")
else:
    print("Standard shipping applies")
```

### Game Logic

```python
health = 20
has_shield = False
level = 5

if health > 0 and (has_shield or level > 3):
    print("Player survives attack")
else:
    print("Player defeated")
```

### Form Validation

```python
email_provided = True
email_valid = True
terms_accepted = False

if email_provided and email_valid and terms_accepted:
    print("Registration complete")
else:
    print("Please complete all required fields")
```

---

## Key Takeaways

✅ **`and` requires all conditions True** - One False makes everything False  
✅ **`or` requires at least one True** - One True makes everything True  
✅ **`not` flips boolean values** - True becomes False, False becomes True  
✅ **Use parentheses for clarity** - Especially with `not` and mixed operators  
✅ **Short-circuiting saves time** - Python stops evaluating when result is known  
✅ **Combine operators for complex logic** - Build sophisticated decision trees  
✅ **Test all cases** - Verify your logic with different input combinations

**Remember:** Logical operators let you express complex decision-making in code. Master these fundamentals because they're the building blocks for everything from user authentication to game AI. The key is thinking through all possible combinations of True and False values.

---

**Last Updated:** October 28, 2025