# Python Errors

**Date:** October 25, 2025  
**Course:** PY101 - Introduction to Python

## What Are Errors?

Errors (also called exceptions) are Python's way of telling you something went wrong. When Python encounters a problem it can't handle, it stops your program and displays an error message (a **traceback**) explaining what happened and where.

**The Good News:**  
Error messages aren't punishment. They're helpful clues that guide you directly to the problem. Learning to read them makes debugging much faster.

---

## Anatomy of an Error Message

When Python crashes, it shows you a **traceback** with three key pieces of information:

```python
Traceback (most recent call last):
  File "my_program.py", line 5, in <module>
    print(total)
NameError: name 'total' is not defined
```

**Breaking It Down:**

1. **"Traceback (most recent call last)"** - Python is showing you the path that led to the error
2. **File location and line number** - `File "my_program.py", line 5` tells you exactly where to look
3. **The problematic code** - `print(total)` shows the line that caused the crash
4. **Error type and description** - `NameError: name 'total' is not defined` explains what went wrong

**Reading Strategy:**  
Start from the bottom and work your way up. The last line tells you the error type and what went wrong. The line above shows the specific code that triggered it.

---

## Common Error Types

### 1. NameError

**When It Happens:** You try to use a variable, function, or name that Python doesn't recognize.

**Common Causes:**
- Typo in variable name
- Using a variable before defining it
- Variable defined inside a function (local scope)

```python
# Example 1: Variable never defined
print(my_name)
# NameError: name 'my_name' is not defined

# Example 2: Typo
greeting = "Hello"
print(greting)  # Typo: should be 'greeting'
# NameError: name 'greting' is not defined

# Example 3: Wrong order
print(age)
age = 25
# NameError: name 'age' is not defined
```

**How to Fix:**
- Check spelling carefully
- Make sure you define variables before using them
- Ensure the variable is in the right scope

---

### 2. SyntaxError

**When It Happens:** You wrote code that doesn't follow Python's grammar rules. Python can't even run the program because it doesn't understand what you're trying to say.

**Common Causes:**
- Missing colons (`:`) after `if`, `for`, `def`, etc.
- Unmatched parentheses, brackets, or quotes
- Using Python keywords incorrectly
- Incorrect indentation

```python
# Example 1: Missing colon
def greet()
    print("Hello")
# SyntaxError: invalid syntax

# Example 2: Unmatched quotes
message = "Hello world
# SyntaxError: EOL while scanning string literal

# Example 3: Missing closing parenthesis
result = (5 + 3
print(result)
# SyntaxError: unexpected EOF while parsing
```

**How to Fix:**
- Check for missing colons at the end of control structures
- Count your parentheses, brackets, and quotes (every opener needs a closer)
- Check indentation (use consistent spaces or tabs)
- Look at the line indicated in the error AND the line before it

**Pro Tip:** Syntax errors often point to the line AFTER the actual mistake. If line 5 shows a syntax error, check line 4 too.

---

### 3. TypeError

**When It Happens:** You try to perform an operation on a value of the wrong type.

**Common Causes:**
- Trying to add a string and a number
- Using the wrong type with an operator
- Passing wrong type to a function

```python
# Example 1: Can't add string and integer
age = 25
print("I am " + age + " years old")
# TypeError: can only concatenate str (not "int") to str

# Example 2: Can't multiply string by float
print("*" * 3.5)
# TypeError: can't multiply sequence by non-int of type 'float'

# Example 3: Wrong argument type
number = "42"
result = number + 10
# TypeError: can only concatenate str (not "int") to str
```

**How to Fix:**
- Convert types explicitly using `str()`, `int()`, or `float()`
- Check what type your variables are
- Use f-strings for string formatting instead of concatenation

```python
# Fix for Example 1
age = 25
print(f"I am {age} years old")  # f-string handles conversion
# Or: print("I am " + str(age) + " years old")

# Fix for Example 2
print("*" * int(3.5))  # Convert float to int
# Output: ***

# Fix for Example 3
number = "42"
result = int(number) + 10  # Convert string to integer
print(result)  # Output: 52
```

---

### 4. ZeroDivisionError

**When It Happens:** You try to divide a number by zero, which is mathematically undefined.

```python
# Direct division by zero
result = 10 / 0
# ZeroDivisionError: division by zero

# Division by variable that equals zero
denominator = 0
result = 100 / denominator
# ZeroDivisionError: division by zero
```

**How to Fix:**
- Check if the denominator is zero before dividing
- Use conditional logic to prevent division by zero

```python
# Safe division
numerator = 100
denominator = 0

if denominator != 0:
    result = numerator / denominator
    print(f"Result: {result}")
else:
    print("Error: Cannot divide by zero")

# Output: Error: Cannot divide by zero
```

---

### 5. IndentationError

**When It Happens:** Your code has inconsistent or incorrect indentation. Python uses indentation to understand code structure.

**Common Causes:**
- Mixing tabs and spaces
- Inconsistent number of spaces
- Missing indentation in function or loop bodies

```python
# Example 1: No indentation in function
def greet():
print("Hello")  # Should be indented
# IndentationError: expected an indented block

# Example 2: Inconsistent indentation
def calculate():
    x = 5
      y = 10  # Extra spaces
    return x + y
# IndentationError: unexpected indent

# Example 3: Mixing tabs and spaces (invisible problem)
def process():
    step1 = True    # 4 spaces
	step2 = False   # 1 tab (looks same but isn't)
# IndentationError: unindent does not match any outer indentation level
```

**How to Fix:**
- Use 4 spaces for each indentation level (Python standard)
- Configure your editor to convert tabs to spaces
- Be consistent throughout your entire file
- Use a code editor that shows whitespace characters

---

### 6. ValueError

**When It Happens:** You give a function the right type of data, but the value itself is invalid or inappropriate.

```python
# Example 1: Converting invalid string to integer
age = int("twenty")
# ValueError: invalid literal for int() with base 10: 'twenty'

# Example 2: Invalid value for math operation
import math
result = math.sqrt(-1)  # Can't take square root of negative number
# ValueError: math domain error
```

**How to Fix:**
- Validate user input before converting
- Check if values are in acceptable ranges
- Use try-except blocks to handle invalid conversions

```python
# Safe conversion with validation
user_input = "twenty"

if user_input.isdigit():
    age = int(user_input)
    print(f"Age: {age}")
else:
    print("Please enter a valid number")

# Output: Please enter a valid number
```

---

## Error Prevention Strategies

### 1. Test as You Go

Don't write 100 lines of code and then run it. Test small sections frequently.

```python
# Bad approach: Write everything first
def complex_function():
    # 50 lines of code here
    return result

# Good approach: Test incrementally
def complex_function():
    step1 = calculate_first_part()
    print("Step 1 result:", step1)  # Test this first
    
    step2 = calculate_second_part(step1)
    print("Step 2 result:", step2)  # Then test this
    
    return finalize(step2)
```

### 2. Read Error Messages Carefully

Don't just glance at the error. Read the entire message.

```python
# Error message breakdown:
Traceback (most recent call last):
  File "calculator.py", line 15, in <module>  # Where you were
    result = divide(10, 0)                     # What you called
  File "calculator.py", line 8, in divide     # Where error occurred
    return a / b                               # The problematic line
ZeroDivisionError: division by zero           # What went wrong
```

**Reading Order:**
1. Bottom line: What type of error?
2. Middle lines: Which function/line caused it?
3. Top lines: How did we get there?

### 3. Use Print Statements for Debugging

When you can't figure out the error, add print statements to see what's happening.

```python
def calculate_discount(price, discount_rate):
    print("Input price:", price)              # Check input
    print("Input discount_rate:", discount_rate)
    
    discount = price * discount_rate
    print("Calculated discount:", discount)   # Check calculation
    
    final_price = price - discount
    print("Final price:", final_price)        # Check result
    
    return final_price
```

### 4. Comment Out Code to Isolate Problems

If you have multiple errors, comment out sections to find which part is causing trouble.

```python
def buggy_function():
    step1 = working_code()
    
    # step2 = possibly_broken_code()  # Comment this out
    # step3 = also_suspicious()        # And this
    
    return step1

# Run this. Does it work? If yes, the bug is in the commented section.
# Uncomment one line at a time to find the exact problem.
```

---

## Practice: Error Identification

For each example, identify the error type and explain how to fix it:

### Exercise 1
```python
name = "Marco
print(name)
```

<details>
<summary>Click to see answer</summary>

**Error Type:** SyntaxError  
**Problem:** Missing closing quote on line 1  
**Fix:** `name = "Marco"`

</details>

### Exercise 2
```python
def calculate_total(price):
total = price * 1.2
return total
```

<details>
<summary>Click to see answer</summary>

**Error Type:** IndentationError  
**Problem:** Function body isn't indented  
**Fix:**
```python
def calculate_total(price):
    total = price * 1.2
    return total
```

</details>

### Exercise 3
```python
age = "25"
years_to_retirement = 65 - age
```

<details>
<summary>Click to see answer</summary>

**Error Type:** TypeError  
**Problem:** Can't subtract string from integer  
**Fix:** `years_to_retirement = 65 - int(age)`

</details>

### Exercise 4
```python
total = 100
average = total / count
```

<details>
<summary>Click to see answer</summary>

**Error Type:** NameError  
**Problem:** Variable `count` is never defined  
**Fix:** Define `count` before using it: `count = 5`

</details>

---

## Error Summary Table

| Error Type | When It Happens | Common Fix |
|------------|-----------------|------------|
| **NameError** | Using undefined variable | Check spelling, define variable first |
| **SyntaxError** | Invalid Python grammar | Check colons, quotes, parentheses |
| **TypeError** | Wrong type for operation | Convert types with `str()`, `int()`, `float()` |
| **ZeroDivisionError** | Dividing by zero | Check denominator before dividing |
| **IndentationError** | Inconsistent indentation | Use 4 spaces consistently |
| **ValueError** | Invalid value for type | Validate input before converting |

---

## Key Takeaways

✅ **Errors are helpful** - They tell you exactly what's wrong and where  
✅ **Read from bottom up** - Start with the error type, then trace back  
✅ **Test frequently** - Don't write too much code before running it  
✅ **Look at the line before** - Syntax errors often point to the next line  
✅ **Use print statements** - They reveal what's happening inside your code  
✅ **Common errors have patterns** - Learn to recognize and fix them quickly

**Remember:** Every programmer encounters errors constantly. Getting good at reading and fixing them is a crucial skill. Errors aren't failures, they're learning opportunities.

---

**Last Updated:** October 25, 2025