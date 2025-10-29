

# **Booleans and Comparisons: Equality vs Identity**

**Date:** October 24, 2025

**Course:** PY101 - Introduction to Python

**Week:** 1, Lesson 08

## **What You’ll Learn**

You will learn how Python evaluates truth values using booleans, how to compare objects using equality (==) versus identity (is), and how these comparisons affect your code’s behavior. This lesson helps you avoid common logical mistakes and understand how Python handles memory and object references.

---

## **Understanding Booleans**

Booleans are a core data type that represent truth values: **True** or **False**. They often result from comparison or logical operations.

### **Basic Boolean Examples**

```plaintext
# Boolean values
is_sunny = True
is_raining = False

# Comparisons produce boolean results
big = 10 > 3      # True
small = 2 > 5     # False
passed = 88 >= 70 # True

print(big, small, passed)
# Output: True False True
```

**Why This Matters:**

Booleans control program flow. They determine which actions a program takes, such as validating input or checking game conditions.

---

## **Comparison Operators**

Comparison operators compare values and return a boolean result.

```plaintext
x = 5
y = 10

print(x == y)   # Equal to: False
print(x != y)   # Not equal to: True
print(x < y)    # Less than: True
print(x <= y)   # Less than or equal: True
print(x > y)    # Greater than: False
print(x >= y)   # Greater than or equal: False
```

✅ Use comparison operators when testing conditions or validating data.

---

## **Logical Operators**

Logical operators combine boolean expressions.

```plaintext
has_license = True
has_car = False

can_drive = has_license and has_car  # False
can_travel = has_license or has_car  # True
needs_license = not has_license      # False
```

**Key Idea:**

- and returns True only if both expressions are True

- or returns True if at least one expression is True

- not inverts a boolean value

---

## **Equality vs Identity**

Python provides two main ways to compare objects: **equality (==)** and **identity (is)**.

### **Equality (**

### **==**

### **)**

Checks if two objects have the same **value**.

```plaintext
a = 5
b = 5
print(a == b)
# Output: True

list1 = [1]
list2 = [1]
print(list1 == list2)
# Output: True
```

**Meaning:**

Equality looks at whether the contents are the same.

---

### **Identity (**

### **is**

### **)**

Checks if two variables refer to the **same object** in memory.

```plaintext
a = [1]
b = [1]
c = a

print(a == b)
# Output: True
print(a is b)
# Output: False
print(a is c)
# Output: True
```

**Key Difference:**

== compares **values**, while is compares **object identity**.

---

## **Common Examples**

### **String Comparison**

```plaintext
name1 = "marco"
name2 = "mar" + "co"

print(name1 == name2)
# Output: True
print(name1 is name2)
# Output: True (string interning)
```

### **Integer Caching**

```plaintext
x = 256
y = 256
print(x is y)
# Output: True

x = 257
y = 257
print(x is y)
# Output: False
```

**Why This Happens:**

Python caches small integers (-5 to 256) for performance.

---

## **Mutable vs Immutable Objects**

Mutable objects (like lists) always occupy different memory locations even if they contain the same values.

```plaintext
list1 = [1]
list2 = [1]
print(list1 is list2)
# Output: False

original = [1]
alias = original
original.append(4)
print(alias)
# Output: [1, 4]
```

**Explanation:**

alias points to the same object as original, so changing one affects both.

---

## **Common Errors and Fixes**

### **Error Example: Using**

### **is**

### **for Value Comparison**

**Bad Code:**

```plaintext
x = 1000
if x is 1000:
    print("x is 1000")
# No output
```

**Why This Fails:**

is compares identity, and large integers are not cached.

**Fixed Code:**

```plaintext
if x == 1000:
    print("x equals 1000")
# Output: x equals 1000
```

---

### **Error Example: Aliasing Mutable Objects**

**Bad Code:**

```plaintext
numbers = [1]
copy = numbers
copy.append(2)
print(numbers)
# Output: [1, 2]
```

**Why This Fails:**

copy refers to the same list as numbers.

**Fixed Code:**

```plaintext
numbers = [1]
copy = numbers.copy()
copy.append(2)
print(numbers)
# Output: [1]
```

---

## **Practice Exercises**

**Exercise 1: Compare Lists**

Write a function that checks if two lists are equal in value and identity.

```plaintext
<details>
<summary>Solution</summary>
```

```plaintext
def compare_lists(a, b):
    print("Equal:", a == b)
    print("Same object:", a is b)

list1 = [1, 2, 3]
list2 = [1, 2, 3]
list3 = list1

compare_lists(list1, list2)
compare_lists(list1, list3)
# Output:
# Equal: True
# Same object: False
# Equal: True
# Same object: True
```

```plaintext
</details>
```

---

**Exercise 2: Grade Comparison**

Compare whether two students earned the same grades or share the same object reference.

```plaintext
<details>
<summary>Solution</summary>
```

```plaintext
grades_a = [90, 85, 100]
grades_b = [90, 85, 100]
grades_c = grades_a

print(grades_a == grades_b)  # True
print(grades_a is grades_b)  # False
print(grades_a is grades_c)  # True
```

```plaintext
</details>
```

---

**Exercise 3: Check for None**

Write a function that safely handles None using identity.

```plaintext
<details>
<summary>Solution</summary>
```

```plaintext
def process_data(data=None):
    if data is None:
        data = []
    data.append("processed")
    return data

print(process_data())
# Output: ['processed']
```

```plaintext
</details>
```

---

## **Key Takeaways**

✅ **Booleans** represent True or False values

✅ **== compares values**, not memory locations

✅ **is checks identity**, meaning object references

✅ **Immutable types** can share memory (strings, numbers)

✅ **Mutable types** always create new memory objects

✅ **Use is only for None, True, and False checks**

✅ **Avoid is when comparing numbers or strings**

**Remember:**

Use == for comparing contents and is for checking if two variables point to the same object.

---

**Last Updated:** October 29, 2025