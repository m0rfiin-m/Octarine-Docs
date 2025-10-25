# Functions I: Why, Define, and Call

## Why Use Functions?

**Avoid repetition:** Instead of copying/pasting loads of similar code, put the logic in a function and just call it when needed.

**Keep code organized:** Functions separate tasks and make your code easier to understand and maintain.

**Reuse:** Write once, use many times.

### Example (Messy Copy-Paste)

```python
bill1 = 15.00
tip1 = bill1 * 0.18
total1 = bill1 + tip1
print("Total 1: $" + str(total1))

bill2 = 23.50
tip2 = bill2 * 0.18
total2 = bill2 + tip2
print("Total 2: $" + str(total2))
```

If you want to do this for 10 bills, you end up copying and changing lines over and over—messy and error-prone!

---

## How to Define a Function in Python

### Basic Structure

- Use `def` to start a function definition
- Give the function a name
- List any parameters in parentheses (these are like local variables for the function)
- The code inside runs when you call the function

### Simple Example

```python
def greet(name):
    print(f"hi, {name}!")
```

- `def` = define
- `greet` = function name
- `(name)` = parameter

---

## Calling a Function

```python
greet("Alex")
# Output: hi, Alex!
```

### Using a Variable

```python
friend = "Sam"
greet(friend)   # Output: hi, Sam!
```

---

## Multiple Parameters

```python
def calc_total(base, tip_percent):
    tip = base * tip_percent / 100
    total = base + tip
    print(f"total: ${total:.2f}")

calc_total(10, 15)   # Output: total: $11.50
```

`base` and `tip_percent` are parameters. You can pass any numbers you want (e.g. from variables or user input).

### With User Input

```python
def calc_total(base, tip_percent):
    tip = base * tip_percent / 100
    total = base + tip
    print(f"total: ${total:.2f}")

base = float(input("Enter the bill amount: "))
tip_percent = float(input("Enter the tip percent: "))
calc_total(base, tip_percent)
```

This version lets the user enter values dynamically!

---

## Step-by-Step Example

### 1. Define the function

```python
def show_greeting(name):
    print(f"Welcome, {name}!")
```

### 2. Use the function

```python
user_name = input("Your name: ")
show_greeting(user_name)   # Output: Welcome, Marco!
```

### 3. Practice Problem: Function for Area

**Word Problem:** Make a function to calculate area of a rectangle, given width and height.

**Step-by-Step:**
1. Define the function with two parameters
2. Multiply them to get area
3. Print result

```python
def rectangle_area(width, height):
    area = width * height
    print(f"Area is {area} square units.")

rectangle_area(5, 9)   # Output: Area is 45 square units.
```

**Try this with user input:**

```python
w = float(input("Width: "))
h = float(input("Height: "))
rectangle_area(w, h)
```

---

## What NOT to Do

### Don't put = in function names

```python
def greet=(name):     # WRONG! SyntaxError
    print(name)
```

### Don't use values instead of variable names in definitions

```python
def greet("Alex"):    # WRONG!
    print("hi, Alex!")
```

### Don't call a function by the wrong name

```python
greet("Sam")          # OK if you defined 'greet'
gret("Sam")           # NameError! (typo)
```

### Don't pass extra arguments than defined

```python
def greet(name):
    print(name)
greet("A", "B")   # TypeError: greet() takes 1 argument
```

### Don't try to use the function before defining it

```python
say_hi("B")       # NameError: name 'say_hi' is not defined
def say_hi(name):
    print("Hi " + name)
```

### Don't forget to call the function!

```python
def hi(name):
    print("Hi " + name)
# This does nothing unless you add: hi("Alex")
```

---

## More Function Practice Examples

### Example 1: Double a Number

```python
def double_num(x):
    return x * 2

print(double_num(7))   # Output: 14
```

### Example 2: Celsius to Fahrenheit Converter

```python
def c_to_f(c):
    f = c * 9 / 5 + 32
    return f

print(c_to_f(20))      # Output: 68.0
```

### Example 3: Grade Calculator

```python
def grade_percentage(points_earned, points_possible):
    percent = points_earned / points_possible * 100
    print(f"Grade: {percent:.1f}%")

grade_percentage(82, 100)   # Output: Grade: 82.0%
```

### Example 4: Pay Calculator (With Input)

```python
def weekly_pay(hours, wage):
    return hours * wage

h = float(input("Hours worked: "))
w = float(input("Hourly wage: "))
print("Pay:", weekly_pay(h, w))
```

---

## Key Points about Functions

- Functions help avoid repetition—write once, use everywhere
- Make sure to define before you call
- Pass parameters to make your functions flexible
- Always match the number of arguments to your definition
- Watch typos in names Python is strict!
- Functions make code readable and "modular"

**Practice tip:** Try making a function for common tasks in everyday problems like calculating tax, converting units, or greeting users.
