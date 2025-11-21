
# Reviewing the Plan

Date: Thursday, November 20, 2025, 3 PM PST

Course: CS101 – AAS in AI Software Engineering

Week: 2, Lesson 7

## Lesson Overview

**Goal:**
Practice reviewing step-by-step plans, fixing logical gaps, correcting numbering, and cleaning up overlaps—before you start coding.

---

## Why “Reviewing the Plan” Matters

- **Prevents bugs:** Find missing or redundant steps early.

- **Saves time:** Changes on paper are faster than fixing broken code.

- **Boosts clarity:** Clean, well-ordered logic is easier for you (and others) to understand.

---

## Key Skills

## 1. Spotting Gaps (Missing Steps)

- **Before coding:** Read each step. Is anything critical left out?

- **Practice:** "ATM Withdraw" usually needs a **balance check** before dispensing cash.

**Example Fix:**

```python
# 1. read card 
# 2. enter PIN 
# 3. check balance 
# <---- Insert the missing step! 
# 4. dispense cash
```

*Checkpoint:* What does checking balance help prevent?

---

## 2. Fixing Numbering

- Steps should be **sequential** (1, 2, 3, ...).

- Insert new actions and update step numbers.

*Practice Prompt:*
Insert “check balance” after “enter PIN” and renumber.

---

## 3. Avoiding Logical Overlaps

- **Overlaps:** When two conditions cover some of the same situations, later ones might be ignored.

**Example Problem:**

```python
if distance == "close" and speed == "fast": warn high 
elif distance == "close": warn high # <---- overlapped, never reached if speed is "fast"
```

*Solution:*
Write separate, unique rules for each scenario using multiple factors:

```python
if distance == "close" and speed == "fast": warn high 
elif distance == "close" and speed == "slow": warn low
```

---

## 4. Practice with Dictionary Mapping

Transform unique decisions into key-value pairs:

```python
warning_map = 
{ ("close", "fast"): "high", 
("close", "slow"): "low" 
} 
print(warning_map.get(("close", "fast"), "all clear")) 
print(warning_map.get(("far", "slow"), "all clear"))
```

*Checkpoint:*
What happens when the key isn’t found in `warning_map`?

---

## Quick Checklist Before Coding

- Are all important actions present?

- Is the numbering clear and sequential?

- Are decisions or steps unique (no hidden overlaps)?

- Can any logic be mapped using a dictionary for clarity?

---

## Fast Mnemonic

**GONE:**
**G**aps, **O**rder, **N**o overlaps, **E**xtra check for dictionary use.

---

## Practice Time

- Fix numbering on a small plan.

- Find and add missing safety checks.

- Rewrite overlapped logic with unique conditions.

- Map rules as key/value pairs in a dict.