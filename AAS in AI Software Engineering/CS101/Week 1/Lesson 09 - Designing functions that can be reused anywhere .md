
**Study Guide: Designing functions that can be reused anywhere**

**Core idea:** A reusable function does one job, takes inputs via parameters, and returns a result. Define it once, call it anywhere.

**Key concepts to lock in**

- **Definition vs. Call:** In the ‎⁠def⁠ line, you name parameters. In the call, you pass arguments. Example: ‎⁠def fahrenheit_to_celsius(f):⁠ vs. ‎⁠fahrenheit_to_celsius(77)⁠.
- **Return, don’t print:** Use ‎⁠return⁠ inside functions so you can reuse results. Print outside when needed.
- **Order matters:** Define the function before calling it.
- **Loops with functions:** Iterate a list, call the function per item, collect or print results.
- **Accumulator pattern:** Initialize ‎⁠total = 0⁠, update inside the loop with ‎⁠total += value⁠, then use/print after the loop.

**Canonical examples from the lesson**

```python
def fahrenheit_to_celsius(f):

    return (f - 32) * 5 / 9



temps = [32, 68, 77]

total = 0

for t in temps:

    c = fahrenheit_to_celsius(t)

    print(c)

    total += c

print(total)

def sum_odds(nums):

    total = 0

    for n in nums:

        if n % 2 == 1:

            total += n

    return total



print(sum_odds([1, 2, 3, 4, 5]))  
# answer is 9
```

**Pitfalls to avoid**

- Calling a function before it’s defined.
- Printing inside the function when you should return.
- Misplaced indentation (e.g., ‎⁠return⁠ inside the loop).
- Confusing parameter vs. argument.
- Writing duplicate loops instead of one loop that both computes and accumulates.

**Quick drills**

- Change ‎⁠temps⁠ and confirm your loop still works: ‎⁠[14, 41, 59, 86]⁠.
- Build a list of Celsius values: ‎⁠c_values = [fahrenheit_to_celsius(t) for t in temps]⁠; then ‎⁠sum(c_values)⁠.
- Add a simple check after accumulation: ‎⁠assert total &gt; 0⁠ right after printing total.
- Write ‎⁠average(nums)⁠ using ‎⁠sum(nums) / len(nums)⁠ and return the result.

**Obsidian notes (minimal)**

- Function = name + parameters → returns a value.
- Parameter (in def) vs. argument (in call).
- Accumulator pattern: init, update, use after loop.
- Reuse: pure function + return → testable, portable.