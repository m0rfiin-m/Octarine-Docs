
# Breaking the problem 

Date: Wednesday, November 19, 2025
Course: CS101 – AAS in AI Software Engineering
Week: 2, Lesson 2
Lesson: Breaking the problem

---

## What You’ll Learn

- **Verb-first analysis:** Spot the verbs in a problem statement to reveal every action your code needs.
- **Task list drafting:** Create an unordered action list before sorting anything.
- **Sequencing & ordering:** Arrange actions into the actual order your code will run.
- **Imperative pseudocode:** Convert actions into clear, direct command steps.
- **Sanity-checking plans:** Review for missing steps, duplicates, or ambiguous commands.
- **Breaking complex tasks:** Split large steps (like “sum all positives”) into finer details, especially when using loops or decisions.

---

## Core Ideas

- **Always start with problem verbs.** They’re signals for each required action (e.g., read, print, sum, double).
- **List all tasks, unordered at first, to avoid missing anything.**
- **Refine by ordering:** Sort tasks by when they must happen in code.
- **Turn into commands:** Write each action as a direct instruction (“Read input,” “Print result”).
- **Use repetition and condition keywords (“for each,” “if”).** Loop and decision-making steps often need extra lines.
- **Sanity check:** Make sure you didn’t skip a step or repeat anything.

---

## Reference Snippet

**1. Original problem:**

> “Write a program that reads a number, doubles it, and prints the result.”

**Step-by-step breakdown:**

```python
# 1. Read input
# 2. Double the number
# 3. Print result
```

**Complex example:**
Sum all positive numbers in a list.

```python
# 1. Read input
# 2. For each number in the list:
#      a. If number is positive, add it to sum
# 3. Print result
```

---

## Common Pitfalls

- **Missing verbs:** Failing to catch all required actions, causing incomplete solutions.
- **Big tasks left unbroken:** Steps like “sum all” must be split into “loop” and “if” checks.
- **Order errors:** Running steps out of sequence—like printing before calculation.
- **Vague commands:** Using unclear lines rather than imperative steps.
- **Forgetting loop/if logic:** Not specifying repetition or decision actions for multi-item tasks.

---

## Quick Practice

1. **Underline all verbs** in:
   “Write a program that finds the largest number in a list, and prints its value.”

2. **Create an unordered action list** just from those verbs.

3. **Arrange them in order** as steps to be performed by your code.

4. **Write pseudocode:**

   - Make each step a command (“Find largest number,” “Print value”).

*Stretch:* For “print only positive numbers,” break steps into a loop and if decision.

---

## Why Breaking Down Problems Matters

- A clear sequence means fewer coding mistakes and less confusion later.
- Small, direct steps make each problem easier to code.
- Breaking down big tasks reveals subtle bugs **before** you code.
- Sets the foundation for professional problem-solving in AI and software engineering projects.

---

Let me know which lesson you need next, and I’ll create a guide in this style! If you want extra practice or examples for a specific topic, just ask.

[1](https://maestro.org/learn/688b5ab40508accc71b2ef49-4/688b5ab40508accc71b2e8bd-58/690c7c6cda10b5a4bdfc66fe)