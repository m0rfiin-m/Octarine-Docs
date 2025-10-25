# Functions II: Inside the Function

**Date:** October 25, 2025  
**Course:** PY101 - Introduction to Python  
**Week:** 1, Lesson 11

## What Happens Inside a Function?

- The code inside a function runs every time you call it
- You can use parameters, variables, calculations, and even call other functions from inside

---

## Step 1: Parameters Are Local!

Parameters (like `symbol` and `length`) exist only inside the function. If you try to use them outside, you'll get a `NameError`.

### Example

```python
def repeat_line(symbol, count):
    line = symbol * count
    print(line)

repeat_line("=", 5)  # Output: =====

# print(line)  # ERROR! 'line' only exists inside the function
```

---

## Step 2: Calculations Inside Functions

Functions can do calculations using their parameters and create local variables for intermediate results.

### Example

```python
def rectangle_area(width, height):
    area = width * height
    print(f"Area is {area}")

rectangle_area(6, 4)  # Output: Area is 24
```

---

## Step 3: Returning Results

Use `return` to send a result back to where the function was called. You can assign this returned value to a variable.

### Example

```python
def double_num(x):
    result = x * 2
    return result

answer = double_num(5)
print(answer)  # Output: 10
```

---

## Step 4: Mixing Prints and Returns

You can print info and then return the result (but don't confuse them!). Return is for data, print is for showing output.

### Example

```python
def fancy_line(symbol, length):
    print(f"line built: {symbol * length}")
    return symbol * length

top = fancy_line("-", 8)  # Output: line built: --------
print(top)  # Output: --------
```

---

## Practice Problems

### Problem 1: Make a Box

**Task:** Define a function that prints a box using a symbol, given width and height.

```python
def draw_box(symbol, width, height):
    for i in range(height):
        print(symbol * width)

draw_box("#", 5, 3)
```

**Output:**

```
#####
#####
#####
```

### Problem 2: Adding Numbers

**Task:** Define a function that takes two numbers, adds them, and returns the sum.

```python
def add_nums(a, b):
    total = a + b
    return total

result = add_nums(4, 7)
print(result)  # Output: 11
```

### Problem 3: Personalized Line Builder

**Task:** Get the symbol and length from user input, build and print two lines as a border.

```python
def build_line(symbol, length):
    print(f"Making line: {symbol*length}")
    return symbol * length

s = input("Symbol? ")
l = int(input("Length? "))

top = build_line(s, l)
print(top)

bottom = build_line(s, l)
print(bottom)
```

---

## What NOT to Do Inside a Function

- Don't use parameters outside the function
- Don't forget to return if you want a value
- Don't mix up local and global variables carelessly
- Don't use print to "return" a result you'll need later (printing shows info, returning gives you data)

---

## Key Takeaways

- **Parameters are local:** Only inside the function!
- **Calculations and logic happen inside:** Use parameters and create local variables
- **Return sends a value out:** Assign returned value to a variable if needed
- **Don't confuse print/output with return/data**
- **Keep your code modular:** Functions are best when focused and re-usable
