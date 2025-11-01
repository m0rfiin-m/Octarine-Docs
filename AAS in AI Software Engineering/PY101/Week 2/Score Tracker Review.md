# Score Tracker Review - PY101 Week 2

**Date:** October 30, 2025  
**Course:** PY101 - Introduction to Python  
**Week:** 2, Review Challenge

## What This Review Covers

This document tracks the evolution of a Score Tracker program through multiple attempts, showing what failed, what passed, and why. It includes the original requirements, all code versions with their critiques, and additional practice problems to strengthen understanding.

---

## Original Requirements

Build a score tracker program that:

✅ Asks for the names of two teams  
✅ Prompts for the maximum score needed to win (must be a positive integer)  
✅ Repeatedly asks the user for the current score of each team  
✅ The program continues until:
  - One team reaches or goes past the maximum score (they win automatically), OR
  - The user types "Game over" to stop the game manually  
✅ Scores entered should be non-negative integers (handle invalid entries by asking again)  
✅ Include at least one function and comments  
✅ Show scores after each round, and the winner at the end  
✅ Make sure your code runs without syntax or runtime errors

### Expected Output Example

```
Welcome to the Live Score Tracker!

Enter Team 1 name: Tigers
Enter Team 2 name: Sharks
Enter maximum score to win: 15

--- Game started! ---

Enter Tigers score: 5
Enter Sharks score: 3
Current Score | Tigers: 5 | Sharks: 3

Enter Tigers score: 12
Enter Sharks score: 10
Current Score | Tigers: 12 | Sharks: 10

Enter Tigers score: 15
Enter Sharks score: 11
Current Score | Tigers: 15 | Sharks: 11

########### FINAL SCORE ###########
Tigers: 15 | Sharks: 11
Winner: Tigers 🏆
##################################
```

---

## Attempt 1: FAILED ❌

### The Code

```python
"""
Live Score Tracker - PY101 Week 2 Review
Simple score tracker using only Week 2 concepts
"""

# Welcome message
print("Welcome to the Live Score Tracker!")
print()

# Get team names
team1_name = input("Enter Team 1 name: ")
team2_name = input("Enter Team 2 name: ")

# Get maximum score
max_score = int(input("Enter maximum score to win: "))

print()
print("--- Game started! ---")
print()

# Initialize scores
team1_score = 0
team2_score = 0

# Game loop
while True:
    # Get Team 1 score
    score_input = input(f"Enter {team1_name} score: ")
    
    # Check if user typed "game over"
    if score_input.lower() == "game over":
        break
    
    team1_score = int(score_input)
    
    # Get Team 2 score
    score_input = input(f"Enter {team2_name} score: ")
    
    # Check if user typed "game over"
    if score_input.lower() == "game over":
        break
    
    team2_score = int(score_input)
    
    # Display current scores
    print(f"Current Score | {team1_name}: {team1_score} | {team2_name}: {team2_score}")
    print()
    
    # Check if either team won
    if team1_score >= max_score or team2_score >= max_score:
        break

# Display final results
print()
print("#" * 11 + " FINAL SCORE " + "#" * 11)
print(f"{team1_name}: {team1_score} | {team2_name}: {team2_score}")

# Determine winner
if team1_score > team2_score:
    print(f"Winner: {team1_name} 🏆")
elif team2_score > team1_score:
    print(f"Winner: {team2_name} 🏆")
else:
    print("It's a tie! 🤝")

print("#" * 35)
```

### Critique

**Result:** FAILED ❌

**What Went Wrong:**

❌ **No function included** - Requirement stated "at least one function" but none were present. This triggered automatic failure.

❌ **No input validation** - Typing text where an integer is expected causes the program to crash with a ValueError.

❌ **Lack of comments** - Code would benefit from clearer separation of logic through functions and more comments.

**What Worked:**

✅ Main loop correctly updates and displays scores  
✅ Ends the game when a team reaches maximum score or user types "game over"

**Lesson Learned:** Always read requirements carefully. "At least one function" means you MUST include a function, not just might want to.

---

## Attempt 2: PASSED ✅ (with improvements needed)

### The Code

```python
"""
Live Score Tracker - PY101 Week 2 Review
Simple score tracker using only Week 2 concepts
"""

def display_final_score(team1_name, team1_score, team2_name, team2_score):
    """
    Display the final score and winner at the end of the game.
    """
    # Print final score header
    print()
    print("#" * 11 + " FINAL SCORE " + "#" * 11)
    print(f"{team1_name}: {team1_score} | {team2_name}: {team2_score}")
    
    # Determine and display winner
    if team1_score > team2_score:
        print(f"Winner: {team1_name} 🏆")
    elif team2_score > team1_score:
        print(f"Winner: {team2_name} 🏆")
    else:
        print("It's a tie! 🤝")
    
    # Print bottom border
    print("#" * 35)


# Welcome message
print("Welcome to the Live Score Tracker!")
print()

# Get team names
team1_name = input("Enter Team 1 name: ")
team2_name = input("Enter Team 2 name: ")

# Get maximum score with validation
while True:
    max_score_input = input("Enter maximum score to win: ")
    # Check if input is a valid positive number
    if max_score_input.isdigit():
        max_score = int(max_score_input)
        if max_score > 0:
            break
        else:
            print("Score must be greater than 0. Try again.")
    else:
        print("Please enter a valid number.")

print()
print("--- Game started! ---")
print()

# Initialize scores
team1_score = 0
team2_score = 0

# Game loop - continues until team wins or user ends game
while True:
    # Get Team 1 score with validation
    while True:
        score_input = input(f"Enter {team1_name} score: ")
        
        # Check if user wants to end game
        if score_input.lower() == "game over":
            team1_score = 0
            team2_score = 0
            display_final_score(team1_name, team1_score, team2_name, team2_score)
            exit()
        
        # Validate input is a number
        if score_input.isdigit():
            team1_score = int(score_input)
            break
        else:
            print("Please enter a valid number or 'Game over' to end.")
    
    # Get Team 2 score with validation
    while True:
        score_input = input(f"Enter {team2_name} score: ")
        
        # Check if user wants to end game
        if score_input.lower() == "game over":
            display_final_score(team1_name, team1_score, team2_name, team2_score)
            exit()
        
        # Validate input is a number
        if score_input.isdigit():
            team2_score = int(score_input)
            break
        else:
            print("Please enter a valid number or 'Game over' to end.")
    
    # Display current scores after each round
    print(f"Current Score | {team1_name}: {team1_score} | {team2_name}: {team2_score}")
    print()
    
    # Check if either team reached the maximum score
    if team1_score >= max_score or team2_score >= max_score:
        break

# Display final results using the function
display_final_score(team1_name, team1_score, team2_name, team2_score)
```

### Critique

**Result:** PASSED ✅ (but with areas for improvement)

**What Worked:**

✅ Validates user input for maximum score and each score update  
✅ Loop ends correctly when a team reaches the target or user types "Game over"  
✅ Uses a clear helper function to print the final scoreboard  
✅ Code is readable with comments and good variable names

**What Needs Improvement:**

⚠️ **Inconsistent behavior with "Game over"** - Typing "Game over" during the first team's score input resets both scores to zero instead of keeping the last valid scores

⚠️ **Inconsistent score clearing** - Clears scores in one early exit path but not in the other

⚠️ **Validation loop issue** - For invalid maximum-score entries, responds but doesn't re-prompt immediately; a tighter loop would help

**Lesson Learned:** Consistency matters. If you handle one case a certain way, handle all similar cases the same way.

---

## Attempt 3: PASSED ✅ (Best Version)

### The Code

```python
"""
Live Score Tracker - PY101 Week 2 Review
Simple score tracker using only Week 2 concepts
"""

def display_final_score(team1_name, team1_score, team2_name, team2_score):
    """
    Display the final score and winner at the end of the game.
    """
    # Print final score header
    print()
    print("###########" + " FINAL SCORE " + "###########")
    print(f"{team1_name}: {team1_score} | {team2_name}: {team2_score}")
    
    # Determine and display winner
    if team1_score > team2_score:
        print(f"Winner: {team1_name} 🏆")
    elif team2_score > team1_score:
        print(f"Winner: {team2_name} 🏆")
    else:
        print("It's a tie! 🤝")
    
    # Print bottom border
    print("##################################")


# Welcome message
print("Welcome to the Live Score Tracker!")
print()

# Get team names
team1_name = input("Enter Team 1 name: ")
team2_name = input("Enter Team 2 name: ")

# Get maximum score with validation
max_score = 0
while max_score <= 0:
    max_score_input = input("Enter maximum score to win: ")
    # Check if input is a valid positive number
    if max_score_input.isdigit():
        max_score = int(max_score_input)
        if max_score <= 0:
            print("Score must be greater than 0. Try again.")
    else:
        print("Please enter a valid number.")

print()
print("--- Game started! ---")
print()

# Initialize scores
team1_score = 0
team2_score = 0

# Game loop - continues until team wins or user ends game
game_over = False
while not game_over:
    # Get Team 1 score with validation
    valid_input = False
    while not valid_input:
        score_input = input(f"Enter {team1_name} score: ")
        
        # Check if user wants to end game
        if score_input.lower() == "game over":
            game_over = True
            valid_input = True
        # Validate input is a number
        elif score_input.isdigit():
            team1_score = int(score_input)
            valid_input = True
        else:
            print("Please enter a valid number or 'Game over' to end.")
    
    # If game over, exit the main loop
    if game_over:
        break
    
    # Check if Team 1 already won - don't ask for Team 2 score
    if team1_score >= max_score:
        game_over = True
        # Display current scores
        print(f"Current Score | {team1_name}: {team1_score} | {team2_name}: {team2_score}")
        print()
        break
    
    # Get Team 2 score with validation
    valid_input = False
    while not valid_input:
        score_input = input(f"Enter {team2_name} score: ")
        
        # Check if user wants to end game
        if score_input.lower() == "game over":
            game_over = True
            valid_input = True
        # Validate input is a number
        elif score_input.isdigit():
            team2_score = int(score_input)
            valid_input = True
        else:
            print("Please enter a valid number or 'Game over' to end.")
    
    # If game over, exit the main loop
    if game_over:
        break
    
    # Display current scores after each round
    print(f"Current Score | {team1_name}: {team1_score} | {team2_name}: {team2_score}")
    print()
    
    # Check if either team reached the maximum score
    if team1_score >= max_score or team2_score >= max_score:
        game_over = True

# Display final results using the function
display_final_score(team1_name, team1_score, team2_name, team2_score)
```

### Critique

**Result:** PASSED ✅ (Best Version)

**What Worked:**

✅ Clean, readable code with helpful comments  
✅ Correct validation for positive maximum score and non-negative score updates  
✅ Loop ends properly when a team reaches the limit or user types "Game over"  
✅ Clear final output with winner or tie announcement  
✅ Keeps last valid scores when "Game over" is typed  
✅ Consistent behavior across all exit paths  
✅ Tighter validation loop for maximum score

**Minor Improvements Noted:**

⚠️ Max-score check happens after Team 1's score is entered (fixed version checks immediately)  
⚠️ Header width matches sample exactly

**Lesson Learned:** Early exit conditions save unnecessary prompts. Check win conditions as soon as possible.

---

## Key Concepts Used (Week 2)

### Lesson 1-2: Control Flow and If/Else
- Decision making with if/elif/else
- Proper indentation
- Multiple conditional branches

### Lesson 3: Logical Operators
- `not game_over` in while loop condition
- Combining conditions with `or` in win check

### Lesson 4: Booleans and Comparisons
- `>=` for win condition
- `>` and `<` for winner determination
- `==` for string comparison ("game over")

### Lesson 5: String Membership
- `.lower()` method for case-insensitive input
- `.isdigit()` method for validation

### Lesson 6: Elif Statements
- Multiple conditions for winner determination
- Validation logic with elif chains

### Lesson 9: While Loops
- Main game loop with `while not game_over`
- Validation loops with `while not valid_input`
- Tighter validation with `while max_score <= 0`

### Lesson 10: Break and Continue
- `break` to exit loops when game ends
- `break` when win condition is met

### Lesson 11: Counters and Totals
- Score tracking (totals)
- Boolean flags (`game_over`, `valid_input`) act as counters

---

## Common Mistakes to Avoid

### 1. Forgetting Required Elements

❌ **Wrong:**
```python
# No function at all
print("Score:", score)
```

✅ **Right:**
```python
def display_score(score):
    """Display the score."""
    print("Score:", score)
```

**Why:** Requirements explicitly state "include at least one function."

### 2. No Input Validation

❌ **Wrong:**
```python
score = int(input("Enter score: "))
# Crashes if user enters "hello"
```

✅ **Right:**
```python
while True:
    score_input = input("Enter score: ")
    if score_input.isdigit():
        score = int(score_input)
        break
    else:
        print("Please enter a valid number.")
```

**Why:** Users make mistakes. Always validate input.

### 3. Inconsistent Behavior

❌ **Wrong:**
```python
# Path 1: Clears scores
if condition1:
    score1 = 0
    score2 = 0

# Path 2: Keeps scores
if condition2:
    pass  # Doesn't clear
```

✅ **Right:**
```python
# Both paths keep scores OR both clear scores
if condition1:
    pass  # Keep scores

if condition2:
    pass  # Keep scores
```

**Why:** Consistency makes code predictable and easier to debug.

### 4. Asking for Unnecessary Input

❌ **Wrong:**
```python
team1_score = int(input("Team 1: "))
if team1_score >= max_score:
    # Team 1 already won
    team2_score = int(input("Team 2: "))  # Why ask?
```

✅ **Right:**
```python
team1_score = int(input("Team 1: "))
if team1_score >= max_score:
    # Team 1 already won, don't ask for Team 2
    break
```

**Why:** Once the game is decided, stop asking for input.

### 5. Weak Validation Loops

❌ **Wrong:**
```python
while True:
    max_score_input = input("Enter max score: ")
    if max_score_input.isdigit():
        max_score = int(max_score_input)
        if max_score > 0:
            break
        # Prints error but loops again
```

✅ **Right:**
```python
max_score = 0
while max_score <= 0:
    max_score_input = input("Enter max score: ")
    if max_score_input.isdigit():
        max_score = int(max_score_input)
        if max_score <= 0:
            print("Must be positive.")
    else:
        print("Please enter a number.")
```

**Why:** Tighter condition (`while max_score <= 0`) makes the loop purpose clearer.

---

## Practice Problems

### Problem 1: Simple Counter

**Goal:** Track how many rounds were played.

**Requirements:**
- Initialize a counter before the loop
- Increment it each round
- Display total rounds at the end

<details>
<summary>Solution</summary>

```python
# Add to the game code:

# Before game loop
round_count = 0

# Inside game loop (after displaying scores)
round_count += 1

# After game ends
print(f"Total rounds played: {round_count}")
```
</details>

### Problem 2: Total Points Scored

**Goal:** Calculate total points scored by both teams.

**Requirements:**
- Initialize a total before the loop
- Add both team scores each round
- Display total at the end

<details>
<summary>Solution</summary>

```python
# Add to the game code:

# Before game loop
total_points = 0

# Inside game loop (after getting both scores)
total_points += team1_score + team2_score

# After game ends
print(f"Total points scored: {total_points}")
```
</details>

### Problem 3: Average Score Per Round

**Goal:** Calculate and display average score per round.

**Requirements:**
- Use both counter and total
- Calculate average (avoid division by zero)
- Display with one decimal place

<details>
<summary>Solution</summary>

```python
# Combine Problems 1 and 2, then add:

# After game ends
if round_count > 0:
    average = total_points / round_count
    print(f"Average per round: {average:.1f}")
else:
    print("No rounds played")
```
</details>

### Problem 4: Winning Margin

**Goal:** Display how many points the winner won by.

**Requirements:**
- Calculate difference between scores
- Only show if there's a winner (not a tie)
- Display in final results

<details>
<summary>Solution</summary>

```python
# Add to display_final_score function:

def display_final_score(team1_name, team1_score, team2_name, team2_score):
    print()
    print("###########" + " FINAL SCORE " + "###########")
    print(f"{team1_name}: {team1_score} | {team2_name}: {team2_score}")
    
    if team1_score > team2_score:
        print(f"Winner: {team1_name} 🏆")
        margin = team1_score - team2_score
        print(f"Winning margin: {margin} points")
    elif team2_score > team1_score:
        print(f"Winner: {team2_name} 🏆")
        margin = team2_score - team1_score
        print(f"Winning margin: {margin} points")
    else:
        print("It's a tie! 🤝")
    
    print("##################################")
```
</details>

### Problem 5: Lead Changes

**Goal:** Track how many times the lead changed during the game.

**Requirements:**
- Initialize counter before loop
- Compare previous leader to current leader
- Increment when leader changes
- Display total lead changes

<details>
<summary>Solution</summary>

```python
# Add to the game code:

# Before game loop
lead_changes = 0
previous_leader = ""

# After displaying scores each round
# Determine current leader
if team1_score > team2_score:
    current_leader = team1_name
elif team2_score > team1_score:
    current_leader = team2_name
else:
    current_leader = "Tie"

# Check if leader changed
if previous_leader != "" and previous_leader != current_leader:
    lead_changes += 1

# Update previous leader
previous_leader = current_leader

# After game ends
print(f"Lead changes: {lead_changes}")
```
</details>

### Problem 6: Score Validation with Range

**Goal:** Only accept scores within a reasonable range (0-100).

**Requirements:**
- Modify validation to check range
- Give appropriate error messages
- Still allow "game over"

<details>
<summary>Solution</summary>

```python
# Modify score input validation:

valid_input = False
while not valid_input:
    score_input = input(f"Enter {team_name} score: ")
    
    if score_input.lower() == "game over":
        game_over = True
        valid_input = True
    elif score_input.isdigit():
        score = int(score_input)
        if 0 <= score <= 100:
            valid_input = True
        else:
            print("Score must be between 0 and 100.")
    else:
        print("Please enter a valid number or 'Game over' to end.")
```
</details>

### Problem 7: Close Game Indicator

**Goal:** Tell user if the game was close (within 5 points).

**Requirements:**
- Calculate point difference
- Display message if difference ≤ 5
- Show in final results

<details>
<summary>Solution</summary>

```python
# Add to display_final_score function after winner:

if team1_score != team2_score:
    difference = abs(team1_score - team2_score)
    if difference <= 5:
        print("What a close game!")
```
</details>

### Problem 8: Comeback Tracker

**Goal:** Track if a team came from behind to win.

**Requirements:**
- Track who was leading after first round
- Compare first leader to final winner
- Display comeback message if different

<details>
<summary>Solution</summary>

```python
# Add to the game code:

# Before game loop
first_leader = ""

# After first round scores (add round counter first)
if round_count == 1:
    if team1_score > team2_score:
        first_leader = team1_name
    elif team2_score > team1_score:
        first_leader = team2_name

# In display_final_score function:
def display_final_score(team1_name, team1_score, team2_name, team2_score, first_leader):
    # ... existing code ...
    
    if team1_score > team2_score:
        print(f"Winner: {team1_name} 🏆")
        if first_leader != "" and first_leader != team1_name:
            print("Amazing comeback victory!")
    elif team2_score > team1_score:
        print(f"Winner: {team2_name} 🏆")
        if first_leader != "" and first_leader != team2_name:
            print("Amazing comeback victory!")
```
</details>

---

## Study Tips

### 1. Break Down the Requirements

Before writing any code:
- List each requirement
- Identify which Week 2 concept solves it
- Write pseudocode first

### 2. Test Input Validation

Always test with bad input:
- Type letters where numbers expected
- Type negative numbers
- Type "game over" at different points
- Type nothing (just press Enter)

### 3. Trace Your Logic

Walk through your code manually:
- What happens if Team 1 enters 15 and wins immediately?
- What happens if user types "game over" right away?
- What happens with a tie score?

### 4. Read Error Messages Carefully

Common errors and what they mean:
- `NameError`: Variable not defined (forgot to initialize?)
- `ValueError`: Can't convert string to int (need validation?)
- `IndentationError`: Incorrect spacing (check your indents)

### 5. Use Comments as Planning

Write comments first, code second:
```python
# Get team names

# Get max score with validation

# Game loop
    # Get Team 1 score
    # Check win condition
    # Get Team 2 score
    # Display scores
    
# Display final results
```

---

## Final Checklist

Before submitting any code review:

**Requirements:**
- [ ] At least one function included
- [ ] Input validation for all user inputs
- [ ] Comments explaining major sections
- [ ] Code runs without errors
- [ ] Handles "game over" correctly
- [ ] Shows scores after each round
- [ ] Displays final winner

**Quality:**
- [ ] Consistent behavior (no score resets)
- [ ] Efficient (no unnecessary prompts)
- [ ] Readable variable names
- [ ] Proper indentation
- [ ] Follows Week 2 concepts only

**Testing:**
- [ ] Tested with valid inputs
- [ ] Tested with invalid inputs
- [ ] Tested "game over" at different points
- [ ] Tested immediate win (first score = max)
- [ ] Tested tie game

---

## Key Takeaways

✅ **Always include required elements** - If it says "at least one function," you MUST have a function

✅ **Validate all user input** - Use `.isdigit()` to check before converting to int

✅ **Be consistent** - Handle similar situations the same way

✅ **Check win conditions early** - Don't ask for unnecessary input

✅ **Test thoroughly** - Try to break your own code before submitting

✅ **Use only concepts learned** - Don't use try/except or other advanced features not covered in Week 2

✅ **Read critiques carefully** - Each critique teaches you something specific to improve

**Remember:** Word problems are just requirements written in sentences. Break them down into bullet points, identify the concepts needed, and tackle each piece one at a time. You've got this!

---

**Last Updated:** October 30, 2025
