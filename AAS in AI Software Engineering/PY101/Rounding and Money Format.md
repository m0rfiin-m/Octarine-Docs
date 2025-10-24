
## 1. Floating-Point Precision
- Computers sometimes store decimals imperfectly.  
  ```python
  print(2.99 - 1)
  # Output: 1.9900000000000002
  ```
- This is normal for floating-point arithmetic.

---

## 2. The `round()` Function
**Syntax:**  
```python
round(value, decimals)
```

**Purpose:**  
Rounds a number to a set number of decimal places.

**Examples:**  
```python
print(round(2.99 - 1, 2))   # 1.99
print(round(6.1836, 2))     # 6.18
```

**Notes:**  
- The second argument is optional (default is 0).
- `round()` returns a **float**:
  ```python
  print(type(round(7/3, 2)))  # <class 'float'>
  ```

---

## 3. Rounding in Money Calculations
Rounding is key for currency since prices usually have two decimal places.  
```python
tax_amount = 8.333333
print(round(tax_amount, 2))  # 8.33
```

---

## 4. Displaying Money with `f-strings`
**Syntax:**  
```python
f"{variable:.2f}"
```

**Purpose:**  
Formats a number to two decimals for display (like money).

**Example:**  
```python
price = 19.5
print(f"${price:.2f}")  # $19.50
```

**Comparison:**  
```python
print(price)             # 19.5 (raw value)
print(round(price, 2))   # 19.5 (rounded)
print(f"${price:.2f}")   # $19.50 (formatted)
```

---

## 5. Combined Example: Café Check
```python
base = 4.5
tip = 0.8125
total = base + tip

print("raw total:", total)
print("rounded:", round(total, 2))
print(f"bill: ${total:.2f}")
```

**Output:**  
```
raw total: 5.3125
rounded: 5.31
bill: $5.31
```

---

## 6. Quick Review
| Expression | Result | Explanation |
|-------------|---------|-------------|
| `round(3.14159, 3)` | `3.142` | Rounded to 3 decimals |
| `f"{7/3:.2f}"` | `2.33` | Display 2 decimals, formatted |

---

## 7. Summary Rules
- Use `round(x, 2)` to clean numeric precision.  
- Use `f"${x:.2f}"` to print currency.  
- `round()` changes the value; formatting only changes how it’s displayed.  
- `round()` always returns a **float**, even if the result looks like an integer.
