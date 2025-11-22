
# **Keeping comments that connect to pseudocode**

Date: Saturday, November 22, 2025

Course: CS101 – AAS in AI Software Engineering

Week: 2, Lesson 9

**Purpose**

Keep comments and code aligned so your implementation mirrors the plan. This makes debugging faster, reviews cleaner, and changes safer.

**Learning Objectives**

- Maintain a 1:1 mapping between pseudocode lines and implementation.
- Keep comments directly above the code they describe.
- Update comments when plans change (renumber, rename, relocate).
- Use small alignment checks to catch drift early.

**Prerequisites**

- Basic Python syntax: input, variables, integer division, dicts, print.
- Loops and conditionals familiarity (no function stubs in this lesson).

**Core Idea**

Write the plan first as pseudocode comments. Implement code directly beneath each comment. If the plan changes, comments move and renumber before code changes. The comment is the source of truth for intent; the code must match it exactly.

**Reference Pattern (worked example)**

```python
# 1. ask user for years of experience

years = int(input("years of experience:"))



# 2. compute seniority bucket

#   a. divide years by 5  (floor)

bucket = years // 5



# 3. handle negative input by showing 'invalid' and exit

if years < 0: print("invalid"); quit()



# 4. look up a message by bucket

messages = {0: "rookie", 1: "junior", 2: "mid", 3: "senior"}

msg = messages.get(bucket, "legend")



# 5. print the message

print(msg)



# 6. done
```

Alignment rules:

- Comment sits directly above the corresponding code.
- Names in comments and code match (messages vs message, bucket vs buckets).
- Nested steps are indented in the comment (e.g., “a.” under step 2) and reflected in code placement.

**Process**

**Step 1: Draft the plan as comments**

- Write each step as a comment, one per line, in order.
- Include nested substeps inline (e.g., “a.”).
- No code yet; run and confirm no output.

**Step 2: Implement line-by-line**

- Add exactly one code line beneath each comment.
- Run after each addition to validate behavior.
- Keep names consistent with the comment wording.

**Step 3: Alignment checks (micro-audits)**

- Comments and code remain vertically paired (no blank lines in between).
- Variable and dictionary names match comment intent precisely.
- Control flow matches step order (no code jumping ahead of comments).

**Step 4: Plan change discipline**

- Edit and renumber comments first.
- Move code under the updated comments.
- Re-run and re-check alignment before continuing.

**Common Mistakes and Fixes**

- Name drift: message vs messages, bucket vs buckets. Fix by standardizing names and grep-searching for mismatches.
- Misordered code: code placed under the wrong comment. Fix by cutting and moving code to match the comment’s position.
- Hidden logic: adding extra lines not reflected in comments. Fix by adding or updating the comment so intent stays explicit.
- Over-commenting or blank lines: breaks the visual pairing. Fix by keeping comments tight to code, no spacers.

**Drills**

**Drill A: Baseline alignment**

- Start from the reference pattern.
- Intentionally rename one variable in code (e.g., bucket → buckets).
- Locate and correct all related mismatches; re-run.

**Drill B: Plan change**

- Insert a new step after computing bucket:
  - Comment: “# 3. cap bucket at 3”
  - Code: ‎⁠bucket = min(bucket, 3)⁠
- Renumber downstream comments and ensure code order matches.

**Drill C: Mapping practice**

- Given this comment list, implement exactly one line under each:
  - “# 1. read username”
  - “# 2. normalize to lowercase”
  - “# 3. reject empty name and exit”
  - “# 4. lookup role by name”
  - “# 5. print role”
- Keep a single dictionary for lookup; match names across comments and code.

**Self-Check**

- Visual: Every comment is immediately followed by its code line with no blank line between.
- Semantic: Names and intent in comments match code behavior exactly.
- Execution: Running after each step yields the expected prompt/behavior; negative-path checks exit early as documented.
- Change-resilience: After inserting/deleting a step, both comments and code remain ordered and aligned.

**Notes for Your System**

- Capture each exercise in your Obsidian vault: title the note with the lesson name, include the final aligned code and a short “Plan Change Log” section listing what changed and why.