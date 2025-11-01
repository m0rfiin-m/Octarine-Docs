# Lesson 4: Booleans and Comparisons - Equality vs Identity

**Course:** PY101 - Python Fundamentals  
**Week:** 2  
**Date:** October 29, 2025  
**Status:** 📚 In Progress

## Overview

This lesson covers boolean values, comparison operators, and the critical difference between equality (`==`) and identity (`is`) in Python. Understanding these concepts is essential for writing robust Python code and avoiding common bugs related to object references.

## Key Concepts

### Boolean Basics

Booleans are a data type with only two possible values: `True` or `False`. They result from comparison operations and logical expressions.

```python
# Basic boolean values
is_sunny = True
is_raining = False

# Booleans from comparisons
big = 10 > 3      # True
small = 2 > 5     # False
passed = 88 >= 70 # True

print(big, small, passed)  # Output: True False True
```

**Comparison Operators:**
```python
x = 5
y = 10

print(x == y)   # Equal to: False
print(x != y)   # Not equal to: True
print(x < y)    # Less than: True
print(x <= y)   # Less than or equal: True
print(x > y)    # Greater than: False
print(x >= y)   # Greater than or equal: False
```

**Logical Operators:**
```python
# and, or, not operators
has_license = True
has_car = False

can_drive = has_license and has_car  # False
can_travel = has_license or has_car  # True
needs_license = not has_license      # False
```

### Equality vs Identity: The Core Distinction

**Equality (`==`) - Value Comparison**  
Checks if two objects have the same value or content.

```python
# Equality examples
a = 5
b = 5
print(a == b)  # True - same values

list1 = [1, 2, 3]
list2 = [1, 2, 3]
print(list1 == list2)  # True - same contents
```

**Identity (`is`) - Object Comparison**  
Checks if two variables refer to the same object in memory.

```python
# Identity examples
a = [1, 2, 3]
b = [1, 2, 3]  # Different object, same content
c = a          # Same object (alias)

print(a == b)  # True  - same values
print(a is b)  # False - different objects
print(a is c)  # True  - same object
```

## Practical Examples

### String Comparison
```python
name1 = "marco"
name2 = "mar" + "co"

same_letters = name1 == name2  # True
same_object = name1 is name2   # Usually True (string interning)

print(same_letters, same_object)  # True True
```

### List Comparison
```python
nums = [1, 2, 1, 3]
first_two_equal = nums[0] == nums[2]  # True

if first_two_equal:
    print("first pair match")
else:
    print("no match")

# Identity check for list elements
print(nums[0] is nums[2])  # True (small integers cached)
```

## Advanced Concepts

### Object Identity and Memory

Python caches small integers (-5 to 256) and reuses them for performance:

```python
# Small integers are cached
x = 256
y = 256
print(x is y)  # True

# Large numbers might not be cached
x = 257
y = 257
print(x is y)  # May be False (implementation dependent)
```

### Mutable vs Immutable Objects

**Immutable objects** (strings, tuples, numbers):
```python
str1 = "hello"
str2 = "hello"
print(str1 is str2)  # Usually True (string interning)
```

**Mutable objects** (lists, dictionaries, sets):
```python
list1 = [1, 2, 3]
list2 = [1, 2, 3]
print(list1 is list2)  # Always False (different objects)

# Modifying mutable objects affects all references
original = [1, 2, 3]
alias = original
original.append(4)
print(alias)  # [1, 2, 3, 4] - both changed!
```

### When to Use `==` vs `is`

**Use `==` for:**
- Comparing values/content
- Most general comparisons
- Checking if data structures contain the same elements

```python
# Good uses of ==
user_input = input("Enter password: ")
if user_input == "secret123":
    print("Access granted")

scores = [85, 90, 88]
target = [85, 90, 88]
if scores == target:
    print("Scores match target")
```

**Use `is` for:**
- Checking against `None`
- Checking against boolean literals
- Performance-critical code (faster than `==`)
- Verifying object aliases

```python
# Good uses of is
def process_data(data=None):
    if data is None:
        data = []
    return data

flag = True
if flag is True:  # Better: if flag:
    print("Flag is set")

# Checking for same object
original_list = [1, 2, 3]
backup = original_list
if backup is original_list:
    print("backup points to original")
```

## Common Pitfalls

### Pitfall 1: Using `is` with Values
```python
# WRONG - Don't do this
x = 1000
if x is 1000:  # Unreliable!
    print("x is 1000")

# CORRECT
if x == 1000:
    print("x equals 1000")
```

### Pitfall 2: Modifying Aliased Objects
```python
# DANGEROUS
original = [1, 2, 3]
copy = original  # This is an alias, not a copy!
copy.append(4)
print(original)  # [1, 2, 3, 4] - Oops!

# SAFE - Create actual copies
original = [1, 2, 3]
copy = original.copy()  # or list(original) or original[:]
copy.append(4)
print(original)  # [1, 2, 3] - Safe!
```

### Pitfall 3: Comparing Different Types
```python
# These comparisons work but might be unexpected
print(False == 0)    # True
print(True == 1)     # True
print(False is 0)    # False
print(True is 1)     # False

# Be explicit about types when needed
user_input = "0"
if user_input == "0":  # String comparison
    print("String zero")
if int(user_input) == 0:  # Numeric comparison
    print("Numeric zero")
```

## Practice Exercises

### Exercise 1: Student Grade Checker
```python
def check_grades(student_grades, passing_grades):
    """
    Compare if student achieved passing grades
    """
    # Check if they have same content
    same_grades = student_grades == passing_grades
    
    # Check if they're the same object
    same_object = student_grades is passing_grades
    
    return same_grades, same_object

# Test it
my_grades = [85, 90, 78]
required = [85, 90, 78]
reference = my_grades  # alias

print(check_grades(my_grades, required))   # (True, False)
print(check_grades(my_grades, reference))  # (True, True)
```

### Exercise 2: Configuration Validator
```python
def validate_config(config, default_config):
    """
    Validate configuration against defaults
    """
    for key, default_value in default_config.items():
        if key not in config:
            print(f"Missing key: {key}")
            continue
            
        user_value = config[key]
        
        # Check value equality
        if user_value == default_value:
            print(f"✓ {key}: matches default")
        else:
            print(f"✗ {key}: {user_value} != {default_value}")
            
        # Check if user accidentally used same object
        if user_value is default_value:
            print(f"⚠️  {key}: using same object reference!")

# Test it
defaults = {
    'debug': False,
    'max_users': 100,
    'features': ['auth', 'api']
}

user_config = {
    'debug': False,
    'max_users': 200,
    'features': defaults['features']  # Oops! Same reference
}

validate_config(user_config, defaults)
```

## Memory and Performance

### When Python Reuses Objects
- Small integers (-5 to 256) are cached
- Single character strings are often cached
- Empty tuples and frozensets are singletons
- `None`, `True`, `False` are singletons

### Performance Comparison
```python
import time

large_list = list(range(1000000))
same_list = large_list

# Timing == comparison
start = time.time()
for _ in range(1000):
    result = large_list == same_list
end = time.time()
print(f"== comparison: {end - start:.4f} seconds")

# Timing is comparison
start = time.time()
for _ in range(1000):
    result = large_list is same_list
end = time.time()
print(f"is comparison: {end - start:.4f} seconds")
```

## Summary

**Key Takeaways:**
- Booleans are a fundamental data type with values `True` or `False`
- `==` compares values/content (equality)
- `is` compares object identity in memory
- Use `==` for most value comparisons
- Use `is` primarily for `None`, boolean literals, and identity checks
- Mutable objects create new instances even with identical content
- Python caches small integers and short strings for performance
- Always use `.copy()` for independent copies of mutable objects

## Next Steps

1. Learn about `__eq__` and `__hash__` methods for custom classes
2. Study deep vs shallow copying with the `copy` module
3. Understand memory management and garbage collection
4. Explore advanced boolean logic and short-circuit evaluation
5. Practice with complex nested data structures

## Related Notes

- [[Week 2/Lesson 3 - Data Types and Variables]]
- [[Week 3/Lesson 1 - Control Flow]]

## Resources

- [Maestro Lesson: Booleans and Equality vs Identity](https://maestro.org/learn/688b5ab40508accc71b2ef49-4/688b5ab40508accc71b2e87a-56/68f5356d52288d89898846de)
- Python Official Documentation: Truth Value Testing
- Real Python: Comparing Python Objects

---

**Last Updated:** October 29, 2025