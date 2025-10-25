# Functions III: return vs print and Early Return

## Why This Lesson Matters

Understanding return and print is key for writing useful and reusable functions in Python.

Knowing when a function ends helps you avoid bugs and control how your code flows.

---

## Step 1: What Does print Do?

`print()` sends output to the console for the user to see.

It does NOT give data back to the part of your program that called the function.

### Example

```python
def shout(msg):
    print("inside:", msg)   # Prints to console
    return msg.upper()
    print("never printed!") # This line is ignored

res = shout("hi")
print("result:", res)
```

**What prints?**

- `inside: hi` (from inside the function)
- `result: HI` (from outside, after the function call)

The "never printed!" line is skipped (see Early Return below).

---

## Step 2: What Does return Do?

`return` sends a value back to the place the function was called.

After Python sees a `return`, it stops the function right away.

### Example

```python
def greet(name):
    print("hello,", name)
    return "Hello, " + name + "!"
    print("Won't see this")

result = greet("Marco")
print("Final:", result)
```

**What prints?**

- `hello, Marco` (from the function)
- `Final: Hello, Marco!` (from the returned value)

"Won't see this" does NOT print, because it's after return.

**Key:** After return, nothing else in the function runs.

---

## Step 3: Using return for Results vs. print for Output

Only return lets you store or use the value later!

### Wrong (using print inside the function)

```python
def add(a, b):
    total = a + b
    print(total)

answer = add(4, 6)  # This prints "10", but answer is None!
print("answer is", answer)  # Output: answer is None
```

### Right (using return inside the function)

```python
def add(a, b):
    total = a + b
    return total

answer = add(4, 6)
print("answer is", answer)  # Output: answer is 10
```

---

## Step 4: Early Return (What Happens When You Use return Early?)

The moment Python hits a `return`, it leaves the function, even if there's more code after.

Anything after return in the same function won't run.

### Example

```python
def timer_demo(seconds):
    print("start")
    return
    print("done:", seconds, "s")  # never runs

timer_demo(5)
```

**Output:** Only `start` is printed.

---

## Step 5: print vs return in Border/Banner Project

Consider this banner example:

### Good version

```python
def build_border(symbol, length):
    line = symbol * length
    print("preview:", line)
    return line

top = build_border("#", 12)
bottom = build_border("#", 12)
banner = top + "\nPython rocks!\n" + bottom
print(banner)
```

You get both "preview" lines and then the complete banner.

### If you use only print and not return

```python
def build_border(symbol, length):
    line = symbol * length
    print("preview:", line)
    print(line)  # No return!

top = build_border("#", 12)
bottom = build_border("#", 12)
banner = top + "\nPython rocks!\n" + bottom  # This causes an error!
print(banner)
```

Now `top` and `bottom` are `None` (because the function returns nothing).

You'll get an error when trying to combine None with strings.

---

## Step 6: Common Errors and What NOT To Do

- Forgetting return when you need a value makes your variable None
- Putting code after return: That code will NEVER run
- Using print instead of return: Only use print for display, not for keeping or combining results
- Forgetting the colon (`:`) at the end of a function header results in a SyntaxError
- Wrong indentation for return causes IndentationError

---

## Practice Problems

### Problem 1: Debug the Return

```python
def subtract(a, b):
    return a - b
    print("Done!")  # Never runs

print(subtract(10, 4))  # Output: 6
```

### Problem 2: Difference Between Print and Return

```python
def triple(x):
    print(x * 3)

result = triple(5)
print(result)  # Output: 15, then None
```

**Change to:**

```python
def triple(x):
    return x * 3

result = triple(5)
print(result)  # Output: 15
```

### Problem 3: Banner Maker (return version)

```python
def banner_line(symbol, length):
    return symbol * length

line = banner_line("-", 18)
print(line)
print("Hello, World!")
print(line)
```

---

## Fill-In Summary

- A function header must end with `:`
- If a function has three parameters, you must supply three arguments
- Use `return` when you need to send a result back
- Use `print` when you want to show output, not save or reuse it

**Tip:** Whenever you want to use a value later (in a variable, calculation, or to build a bigger result), always use return. If you just want to show the user something, use print.
