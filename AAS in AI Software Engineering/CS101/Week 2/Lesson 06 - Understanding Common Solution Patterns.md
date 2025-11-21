
# Understanding Common Solution Patterns

Date: Thursday, November 20, 2025, 3 PM PST

Course: CS101 – AAS in AI Software Engineering

Week: 2, Lesson 6

## Lesson Overview

**Goal:** Learn how to use **dictionary lookups** and related solution patterns to simplify your code, reduce errors, and handle many decision paths efficiently—especially when replacing long `if`/`elif` chains.

---

## Why Use These Patterns?

- **Clarity:** Fewer lines, easier to read and maintain.

- **Speed:** Python finds answers instantly, even with many options.

- **Safety:** `.get()` prevents your code from crashing on missing keys.

- **Flexibility:** Easy to add, remove, or change behaviors.

---

## Key Patterns

## 1. Dictionary Lookup

**Definition:**
Use a dictionary to directly map inputs (keys) to outputs (values).

**Example Table:**

| light_color | action |
| --- | --- |
| "green" | "go" |
| "yellow" | "wait" |
| "red" | "stop" |

**In code:**

```python
actions = 
{ "green": "go", 
"yellow": "wait", 
"red": "stop" 
} 
color = "green" print(actions[color]) # Outputs: go
```

*Question:*
What would `print(actions["yellow"])` output?
*(Type your answer before peeking below.)*

---

## 2. Safe Lookup with `.get()`

**Definition:**
Use `.get(key, default)` to safely return a value or a fallback if the key is missing.

```python
color = "blue" 
print(actions.get(color, "unknown")) # Outputs: unknown
```

*Checkpoint:*
What happens if you use `actions["blue"]` instead?

- a) Prints "unknown"

- b) Gives a KeyError

- c) Prints nothing

---

## 3. Bucket Mapping (Grouping Inputs)

**When to Use:**
When values fall into groups (like grading by score).

```python
grade_map = 
{ 10: "A", 
9: "A", 
8: "B", 
7: "C", 
6: "D" 
} 
score = 82 
bucket = score // 10 
print(grade_map.get(bucket, "F")) # Outputs: B
```

*Think:*
What would print for `score = 63`?

- a) C

- b) D

- c) F

Try it and check!

---

## 4. Multi-Factor Lookup with Tuples

**When to Use:**
When decisions depend on more than one input.

```python
`warnings = { (0, "fast"): "brake NOW", 
(1, "fast"): "prepare to stop", 
(0, "slow"): "coast", 
(1, "slow"): "steady" 
} 
distance = 1 speed = "slow" 
print(warnings.get((distance, speed), "all clear")) # Outputs: steady`
```

*Practice:*
Change `speed` to `"med"` and see what prints.

---

## Mini-Review: Key Points

- **Dictionary lookup**: Cleanly replaces `if`/`elif` chains.

- `.get()`: Adds safe error handling.

- **Grouping (bucket mapping)**: Quick way to assign categories.

- **Tuple keys**: Lets you decide using more than one factor.

---

## Quick Practice

1. Turn a menu of food choices into a dictionary and look up what happens when the user types "pizza".

2. Write a short grade mapping using bucket logic for scores (try with 95 and 73).

3. Make a tuple-keyed dict for (day, weather) =&gt; activity.

---

## Mnemonic

**DIP:**
**D**ictionaries for **I**nstant **P**atterns—get answers fast!