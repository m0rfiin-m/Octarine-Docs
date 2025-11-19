
# Study Guide: **Hierarchy in Pseudocode**

Let’s break down how to use hierarchy—**numbering, indentation, and sub-numbering**—in pseudocode, so you can write organized, readable plans for any programming problem.

---

## **What Is Hierarchy in Pseudocode?**

Hierarchy is the way we show which steps "contain" or depend on other steps, using indentation and sub-numbering.

**Why use it?**

- Clarifies what depends on what.
- Makes logic easier to follow, especially for conditions ("if... else…") or loops ("for each…").
- Prevents missing steps or confusion.

---

## **Key Rules for Hierarchy**

### 1. **Top-Level Steps:**

Use **numbers** (1, 2, 3…) for the main actions.

- Example:

  ```plaintext
  # 1. Start the machine
  # 2. Run diagnostics
  # 3. Print summary
  ```

### 2. **Sub-Steps/Children:**

Indent under the parent step and use **letters** (a, b, c…).

- Example:

  ```plaintext
  # 2. Run diagnostics
  #   a. Check memory
  #   b. Check battery
  ```

### 3. **Third-Level (Very Rare):**

Indent further and use **roman numerals** (i, ii, iii…).

- Example:

  ```plaintext
  #   b. Check battery
  #     i. If battery low
  #     ii. Warn user
  ```

### 4. **Indentation:**

- Use **2–4 spaces** for each new layer.
- **Keep it consistent**!

---

## **Example: Hierarchy in Pseudocode**

#### **Problem:** Add positive numbers in a list and show the total.

Plain steps (flat):

- Set sum to 0
- For each number
- If number is positive
- Add it to sum
- Print sum

**Structured hierarchy:**

```python
# 1. Set sum to 0
# 2. For each number
#   a. If number is positive
#     i. Add it to sum
# 3. Print sum
```

> **Notice:**
>
> - Step 2 is a parent ("For each number")
> - a/i are indented children under it ("If…", "Add…")

---

## **Hierarchy in a Branching Process**

#### **ATM Withdrawal Example:**

```python
# 1. Insert card
#   a. Enter PIN
# 2. Enter amount to withdraw
#   a. If balance is enough
#     i. Choose bill combination
#     ii. Withdraw cash
#   b. Else
#     i. Show error message
```

Try to "teach this back":

- Why do “Enter PIN” or “Show error message” get indented?
- What signal does “a”/“b”/“i” send to a reader?

---

## **Quick Review & Mnemonic**

A mnemonic to remember:

> **"N-L-R"** — **Numbers** for main steps, **Letters** for children, **Roman numerals** if you need one more level.

### **Mini-Recap Questions**

1. Why do we use numbers for top-level steps?
2. What's the purpose of indentation in pseudocode?
3. Which sub-step symbol comes after letters if you need another layer?

Take a minute and answer these! If you get stuck, ask for hints.

---

## **Your Turn: Practice**

Write steps for making a PB&J sandwich using hierarchy:

- List 3 main steps.
- Add at least one branching decision (e.g., “if allergic to peanuts…”).

Start with:

```python
# 1. ...
```

---

If you let me know your preferred template or grade level, I can tailor this guide or practice rounds even more! Would you like another practical example, a quiz, or walk through your answer together?

[1](https://maestro.org/learn/688b5ab40508accc71b2ef49-4/688b5ab40508accc71b2e8bd-58/690c7c6cda10b5a4bdfc66ff)