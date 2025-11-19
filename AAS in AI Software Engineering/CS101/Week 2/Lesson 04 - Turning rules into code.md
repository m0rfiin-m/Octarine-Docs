
# Turning Rules Into Code

**Date:** Wednesday, November 19, 2025, 2 PM PST
**Course:** CS101 – AAS in AI Software Engineering
**Week:** 2, Lesson 4

---

## 1. Lesson Big Idea

This lesson teaches you to **translate written rules into step-by-step code**.
Each rule becomes a small, clear action you write out one-by-one in Python. Typically, each rule or row in a decision table becomes its own `if`, `elif`, or `else` in your code.

---

## 2. Maestro’s 3-Step Checklist for Turning Rules Into Code

1. **Extract Action Verbs**

   - Pull out each rule's key action and write it as a short command.

2. **Check for Granularity**

   - Break up any action that's too large — each step should be concise and clear.

3. **Map Each Line, In Order, to Code**

   - Turn your action list directly into Python, using the same order. Use `if`, `elif`, `else` for decision-making.

---

## 3. Worked Example

**Rules:**

- Double the input.

- If the result is over 100, set it to 100.

**Pseudocode Plan:**

```python
#SET input_value TO 60 
#SET result TO input_value TIMES 2 
#IF result IS GREATER THAN 100 THEN     
#SET result TO 100 END IF PRINT result 
```

**Python Code:**

```python
input_value = 60 
result = input_value * 2 
if result > 100:     
     result = 100 print(result) 
```

*Result is 100, since 60 × 2 = 120, but the rule "caps" it at 100.*

---

## 4. Practice Activity: Weather Rules

**Rules:**

- If it’s raining, wear a raincoat.

- If it’s cold (below 15°C), wear a sweater.

- If it’s not raining and not cold, wear a t-shirt.

**Skeleton Python Code:**

```plaintext
python
```

`is_raining = True   # or False temperature = 10    # degrees Celsius  if is_raining:     print("Wear a raincoat") elif temperature < 15:     print("Wear a sweater") else:     print("Wear a t-shirt") `

*Change* `is_raining` *and* `temperature` *values to test all possible outcomes.*

---

## 5. Quiz Yourself

- What are the three Maestro checklist steps for turning rules into code?

- Why does each row in a decision table usually become its own `if`/`elif` in code?

---

## 6. Key Study Tips

- Go one rule at a time; don’t combine steps.

- Use clear variable names.

- Always test your logic with sample inputs.

- Each decision branch (`if`, `elif`, `else`) does one distinct action.

**Mnemonic:**
 **A.G.M.** – Action, Granularity, Map

---

If you want more examples or a practice challenge in your preferred Maestro format, let me know and I’ll tailor it further! Ready for the next lesson or quiz?

1. <https://maestro.org/learn/688b5ab40508accc71b2ef49-4/688b5ab40508accc71b2e8bd-58/690c7c6cda10b5a4bdfc6700>