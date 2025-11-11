
Here’s a structured study guide of the lesson, with all examples and work.

**Naming That Tells a Story**

This lesson trains you to rename variables and functions so the code explains itself. You practiced noun/verb naming, consistent replacements, function parameters, and the difference between list alias vs copy using slicing.

**Core idea**

Good names reduce guessing. Names should communicate meaning and intent so anyone can read your code without hunting for context.

Good naming = clear, no guessing needed.

**Quick Naming Rules**

	1. Use **snake_case** for variables and functions (max_temp_c).

	2. Use **nouns** for data (playlist, max_temp_c).

	3. Use **verbs** for actions (get_average, sort_playlist).

These three rules drive everything you practiced.

**Warm‑up: Clearer variables**

```python
Initial comparison:x = 7

max_temp_c = 7



“max_temp_c” wins because it tells what the value means.

```

**Micro‑Drill: Rename Everything Consistently**

```python
Original confusing code:a = [25, 32, 27]

b = []

for c in a:

    b.append((c * 9/5) + 32)



Your first pass (partial replacement):daily_score = [25,32,27]

average_score = []



for c in a:

    b.append((c*9/5) + 32)



Fixed with full, consistent replacements:daily_score = [25,32,27]

average_score = []



for c in daily_score:

    average_score.append((c*9/5) + 32)



Final loop variable renamed to tell its role:daily_score = [25,32,27]

average_score = []



for final_score in daily_score:

    average_score.append((final_score*9/5) + 32)

```

Why it’s good:

- **Data as nouns:** daily_score, average_score.
- **Loop variable tells the story:** final_score describes the item being processed.
- **Consistency:** updated names in every reference.

**Function Renaming: Verb‑First, Parameter Names That Signal Flexibility**

```python
Starting unclear function:def pl(d, fn):

    return sorted(d, key=fn)



Progressive renames:def sort_playlist(music, fn):

    return sorted(music, key=fn)



More specific parameter (sort by title only):def sort_playlist(music, title):

    return sorted(music, key=title)



Best flexible version using a generic key function:def sort_playlist(music, sort_key):

    return sorted(music, key=sort_key)



# Typo fix you applied (from “sprted” → “sorted”) and removal of duplicate definitions were part of the exercise’s cleanup.

```

Why it’s good:

- **Verb for action:** sort_playlist.
- **Flexible parameter:** sort_key works for title, artist, duration, etc.
- **Signals intent:** anyone reading it knows what it does.

**Copy vs Alias with Lists: Slicing Matters**

```python
Start:temps = [22, 24, 21]



Alias and copy:daily_temps = temps          # alias: same underlying list

daily_temps_copy = temps[:]  # copy: new list with same values



Proof:daily_temps[0] = 100

print(temps)

print(daily_temps_copy)



Observed output:[100, 24, 21]

[22, 24, 21]


```

What this proves:

Alias: daily_temps and temps point to the same data; changing one changes the other.

Copy: temps[:] creates a new list; changes don’t propagate.

**Final Edits You Made**

You reinforced the concept with a second pass and name corrections:

```python
temps = [22, 24,21]

daily_temps = temps

dail_temps_copy = temps[:]   # small typo retained from your work: "dail" instead of "daily"



daily_temps[0] = 100

print(temps)



get_avg = dail_temps_copy

calculate_average_temperature = get_avg
```

Note on naming:

- “get_avg” as a data variable isn’t ideal; for a function, a story‑telling upgrade would be **calculate_average_temperature**.
- Minor typo “dail_temps_copy” should be “daily_temps_copy” in future edits.

**Pitfalls Highlighted in the Lesson**

- **Quoting overshadowing concepts:** don’t let literal outputs or copied lines distract from naming clarity.
- **Reusing the same names:** causes confusion; always rename everywhere, not partially.
- **Future‑topic creep:** stick to allowed topics; avoid docstrings/comments in this lesson.
- **Alias vs copy confusion:** simple assignment is alias; slicing makes a copy.
- **Misuse of colons:** keep colons for correct Python syntax (function definitions, loops), not in variable names or assignment.

**Fast Reference: Bad → Better**

| Type |  | Bad |  | Better |  |
| --- | --- | --- | --- | --- | --- |
| Variable |  | a |  | daily_score |  |
| Variable |  | b |  | average_score |  |
| Loop item |  | c |  | final_score |  |
| Function |  | pl |  | sort_playlist |  |
| Parameter |  | fn |  | sort_key |  |
| Temperature value |  | x |  | max_temp_c |  |

**What You Should Retain**

- **Snake case.**
- **Nouns for data, verbs for actions.**
- **Rename everywhere, not partially.**
- **Use sorted with a meaningful key name (sort_key).**
- **Slicing ([:]) creates copies; plain assignment creates aliases.**

Keep these tight and you won’t fight your code later—the names will do the explaining for you.