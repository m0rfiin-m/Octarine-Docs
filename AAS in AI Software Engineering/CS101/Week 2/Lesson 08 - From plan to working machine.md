
# From Plan to Working Machine

Date: Thursday, November 20, 2025, 3 PM PST

Course: CS101 – AAS in AI Software Engineering

Week: 2, Lesson 8

## Lesson Overview

**Goal:**
Learn to transform a basic **pseudocode plan** into a functional Python program, by methodically translating each step and testing along the way.

---

## Why This Matters

- **Bridges planning and coding**: Trains you to turn ideas into software in small, reliable steps.

- **Reduces errors**: Step-by-step coding lets you catch mistakes early.

- **Boosts confidence**: Each successful line builds momentum.

---

## The Process: Step-by-Step Approach

## 1. Start with Pseudocode Comments

Write the plan as comments at the top of your code file:

```python
# Get the user’s age 
# Divide the age by 10 (floor division) 
# Lookup a warning based on the decade 
# Print the warning message
```

*Why?*

- Comments keep your steps clear and organized as you translate each one.

---

## 2. Translate Each Step One at a Time

**Step 1:**
Turn the first comment into code.

```python
age = int(input("Enter your age: "))
```

- Test this line: The program should ask for your age.

**Checkpoint:**
What will happen if you type a word instead of a number?

---

**Step 2:**
Directly below the next comment, add:

```python
decade = age // 10
```

- This divides age by 10 and drops any decimal.

**Practice:**
If you enter `34`, what does `decade` become?

---

**Step 3:**
Add a dictionary for possible warnings (map each decade to a message):

```python
warnings_map = { 
0: "Too young!", 
1: "Almost there.", 
2: "Getting started!", 
3: "Stay alert!", 
4: "Be wise!" 
}
```

Then, look up the warning:

```python
warning = warnings_map.get(decade, "No warning.")
```

---

**Step 4:**
Print the warning message:

```python
print(warning)
```

---

## 3. Match Code to Comments

Each code line goes right under its matching comment to keep things organized and error-free.

**Reflection:**
How did this help you catch typos (like variable name mismatches)?

---

## Common Errors & How to Fix

- **NameError:** Occurs if you mistype a variable name (e.g., `warning_map` vs `warnings_map`).
  *Solution:* Double-check spelling and match variable names exactly.

- **KeyError:** Happens if the decade isn’t in your dictionary and you use `[]` instead of `.get()`.
  *Solution:* Always use `.get()` with a default message.

---

## Review Checklist

- Did you code each step right after its comment?

- Did you test after every new code line?

- Are variable names consistent and spelled correctly?

- Are your dictionary keys set up for your use case?

---

## Mnemonic

**POPCORN:**
**P**seudocode
**O**rdered steps
**P**ython
**C**omments
**O**ne step at a time
**R**un and test
**N**ame check!