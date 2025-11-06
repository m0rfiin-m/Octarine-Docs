
# Lesson: Mastering List Iteration

Welcome to your personalized lesson for **Lists iii: mastering list iteration**—designed for beginners aiming for an AAS in AI Software Engineering. We'll learn, practice, and reinforce every technique needed to safely loop through lists in Python.

---

## 1. **Looping Through Lists (Direct Value Loop)**

To visit each item:

```python
temps = [17, 22, 19, 25]
for temp in temps:
    print(temp)
```

**Try it!** Can you print each number with "°C" afterwards?

- **Hint:** Join with a string: `print(str(temp) + "°C")` or f-string: `print(f"{temp} °C")`

## 2. **Summing Values During Iteration**

Want to total all values?

```python
total = 0
for temp in temps:
    print(str(temp) + "°C")
    total += temp  # short for total = total + temp
print(total)
```

- *Review:* Why does `print(total)` need to be outside the loop?

## 3. **Index-Based Looping**

Sometimes you need both the index and value:

```python
for i in range(len(temps)):
    value = temps[i]
    print(f"#{i} -> {value}")
```

- *Check:* What does `range(len(temps))` produce with 4 items?

## 4. **Guard Pattern: Select by Index**

To act only at a certain index:

```python
idx = 2  # choose which index
for i in range(len(temps)):
    value = temps[i]
    if i == idx:
        print(value)
```

- *Practice:* What prints with `idx = 2`?

## 5. **Even and Odd Checks**

Inside your loop, check if each value is even or odd:

```python
for temp in temps:
    print(str(temp) + "°C")
    if temp % 2 == 0:
        print("even")
    else:
        print("odd")
```

- *Review:* Why does `% 2 == 0` mean even?

## 6. **Membership Test: Find an Item Fast**

Use Python's `in` keyword:

```python
print(100 in temps)  # prints True if 100 is in the list, else False
```

- *Quiz:* What outputs for `[17, 22,[19][25]`?

## 7. **Sample Output Review**

Running all these together prints:

```plaintext
17°C
odd
22°C
even
19°C
odd
25°C
odd
False
83
19
```

Where:

- The temperatures and their parity
- `False` means 100 is **not** present in `temps`
- `83` is the sum
- `19` is the value at index 2 (using the guard pattern)

---

## Mini Summary

- **Value loop:** `for element in list:`
- **Index loop:** `for i in range(len(list)):`
- **Running total:** Add inside, print after.
- **Guard by index:** Use `if` inside loop.
- **Even/odd:** Use `% 2` check.
- **Membership:** `item in list`

---

**Next Steps:**
Would you like to practice modifying one of these patterns? For example:

- Print only odd-indexed values?
- Label temps "high" if above 20°C?

If you want deeper practice or have questions, just ask! You can also rate your comfort with these skills so we can target your next steps.