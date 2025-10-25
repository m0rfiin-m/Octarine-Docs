# Study Guide: Scope and Local Variables in Python

## Key Concepts

**Scope** refers to where a variable can be accessed in your code.

- **Local scope:** A variable defined inside a function. It can only be used inside that function.
- **Global scope:** A variable defined outside any function. It can be accessed anywhere in the file, including inside functions (unless "shadowed" by a local variable with the same name).

---

## Common Errors

- **Using a variable before it's defined:** Results in a `NameError`
- **Trying to use a local variable outside of its function:** Also results in a `NameError`

---

## Examples

### 1. Using an undefined variable

```python
def print_bill():
    print("The tax rate is", tax_rate)

print_bill()
tax_rate = 0.1  # Results in NameError: tax_rate is not defined
```

### 2. Local variable scope example

```python
def banner():
    line = "*" * 10
    return line

banner()
print(line)  # NameError: line is not defined
```

### 3. Global vs Local variable "shadowing"

```python
count = 10

def print_counts():
    count = 5  # Local variable with same name as global
    print("Inside:", count)

print_counts()  # Prints: Inside: 5
print("Outside:", count)  # Prints: Outside: 10
```

---

## How to Avoid Scope Issues

Always pass required values into functions using parameters rather than relying on global variables.

### Example

```python
def calc_total(base, tip_rate):
    print(base + tip_rate)

calc_total(100, 0.1)  # Correct usage
```

---

## Quick Quiz Questions

- A variable created inside a function is called a **local variable**
- To use outside data inside a function you should pass it as a **parameter**

---

## Summary Table

| Type   | Where Defined    | Where Usable                  | Example              |
|--------|------------------|-------------------------------|----------------------|
| Local  | Inside function  | Only inside that function     | `line` in `banner()` |
| Global | Outside function | Anywhere, unless shadowed     | `count` variable     |

---

## Tips

- If you get a `NameError`, check whether your variable is defined within the correct scope
- Use clear function parameters for better code clarity and fewer bugs
