
# **Building code incrementally**

Date: Saturday, November 22, 2025

Course: CS101 – AAS in AI Software Engineering

Week: 2, Lesson 11

**Purpose**

Ship small, working slices. Start with placeholders, swap in real logic step by step, keeping structure and comments aligned.

**Mastery outcomes**

- Use hardcoded returns/prints to validate flow.
- Replace stubs one line at a time (input → math → lookup → output).
- Keep definitions above usage to avoid NameError.
- Maintain name/order consistency across comments, functions, and calls.

**Scope envelope**

- Functions, returns, print, dicts, floor division.
- No test tables or dry runs.

**Phase 1: Skeleton with stubs**

```python
# read years

def read_year():

    pass



# bucket years

def bucket_years(years):

    pass



# show message

def show_message(msg):

    pass



# main

# years = read_year()

# show_message(bucket_years(years))
```

Goal: structure compiles; no output expected.

**Phase 2: Wire with placeholders**

```python
def read_year():

    return 2024  # placeholder



def bucket_years(years):

    return "rookie"  # placeholder



def show_message(msg):

    print(msg)



# demo

show_message(bucket_years(read_year()))


```

Goal: prove the flow without real input/logic.

**Phase 3: Swap in real input and math**

```python
def read_year():

    return int(input("years: "))



messages = {0: "rookie", 1: "novice", 2: "intermediate", 3: "experienced", 4: "veteran"}



def bucket_years(years):

    bucket = years // 5

    return messages.get(bucket, "legend")



def show_message(msg):

    print(msg)



years = read_year()

show_message(bucket_years(years))
```

Rules:

- Define functions/dicts before usage.
- Replace one line at a time; run after each change.

**Guard rail (optional**)def guard_negative(years):

if years &lt; 0:

print("invalid")

raise SystemExit

Call this right after reading input, before bucketing:years = read_year()

guard_negative(years)

show_message(bucket_years(years))

**Common mistakes → fixes**

- NameError: move definitions (functions/dicts) above usage.
- Printing a function object: use parentheses, e.g., print(bucket_years()).
- None output: add explicit return value.
- Indentation: function body indented one level; no mixed tabs/spaces.
- Comment drift: update comments first when plans change; keep 1:1 alignment.

**Drills (copy‑ready)**

```python
Baseline alignment:def read_year():

    return 2024



def bucket_years(years):

    return "rookie"



def show_message(msg):

    print(msg)



show_message(bucket_years(read_year()))



Real input:def read_year():

    return int(input("years: "))



print(read_year())



Bucket logic:messages = {0: "rookie", 1: "novice", 2: "intermediate", 3: "experienced", 4: "veteran"}



def bucket_years(years):

    bucket = years // 5

    return messages.get(bucket, "legend")



print(bucket_years(11))



Full pipeline:messages = {0: "rookie", 1: "novice", 2: "intermediate", 3: "experienced", 4: "veteran"}



def read_year():

    return int(input("years: "))



def bucket_years(years):

    bucket = years // 5

    return messages.get(bucket, "legend")



def show_message(msg):

    print(msg)



years = read_year()

show_message(bucket_years(years))
```

**Self‑check**

- Definitions above usage; main calls at the bottom.
- Every change is small; program runs after each edit.
- Comments map directly to code; names match exactly.
- Placeholders replaced cleanly without breaking flow.