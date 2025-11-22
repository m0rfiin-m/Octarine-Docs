
# PY101 Lesson Plan: Escape Room Master Plan Review

## Concept Overview

The Temple Escape project demonstrates fundamental programming concepts through an interactive puzzle game. The assignment requires building three sequential challenges where the temple sets parameters and the player must match them to progress. This review covers the complete implementation strategy, validation patterns, and structural decisions that make the program work.

## Core Requirements

The program must satisfy specific technical constraints. Every output message uses f-strings, even when no variable interpolation occurs. Input comes exclusively from `input()` calls with no hardcoded values for puzzles. The pseudocode must provide 3-4 levels of hierarchical detail matching the actual code flow. All three puzzles operate independently as separate functions with proper validation and error handling.

## Program Structure

The implementation follows a modular design with helper functions handling repetitive validation patterns. Three puzzle functions (`enter_code`, `choose_path`, `balance_weights`) each return boolean values indicating success or failure. The main driver `start_temple_escape` controls the flow by checking each puzzle's return value before advancing to the next challenge.

Named constants replace all magic numbers. `CODE_LEN` sets the gate code length at 4 digits. `PATHS` defines the tuple of valid path options as "left", "center", and "right". `MIN_W` and `MAX_W` establish weight boundaries at 0 and 999 respectively. These constants appear at the module level, making them accessible throughout the program and easy to modify for different difficulty levels.

## Helper Functions

`read_digits_exact` handles fixed-length numeric input. It accepts a prompt string and required length, returning an integer if the input matches exactly that many digits, otherwise returning None. The validation checks both length and character content using `len(raw)` and `raw.isdigit()`. This pattern eliminates code duplication across puzzles that need numeric codes.

`read_path` manages string input from a predefined set of options. It normalizes input to lowercase using `.lower()` and validates against the allowed tuple. The function returns the valid path string or None if the input doesn't match any allowed option. This handles the path selection puzzle where case-insensitive matching improves user experience.

`read_int_in_range` validates numeric input within inclusive bounds. It first checks if the raw input contains only digits, then converts to integer and verifies the value falls within the specified range. The `isdigit()` method automatically rejects negative numbers since strings containing minus signs fail the check. This function handles weight inputs where valid values span from 0 to 999.

## Validation Patterns

Input validation follows a consistent three-step pattern. First, obtain raw input and strip whitespace. Second, validate format and constraints specific to the expected input type. Third, return the validated value or None to signal failure. This approach keeps validation logic centralized in helper functions while puzzle functions focus on game logic.

The `isdigit()` method checks if all characters in a string are numeric digits. It returns False for empty strings, strings containing spaces, decimal points, or minus signs. This makes it suitable for validating positive integers but requires the string to contain only digit characters 0-9. For the gate code, this ensures players enter exactly four numeric digits without spaces or other characters.

String methods handle path validation. The `strip()` method removes leading and trailing whitespace from user input. The `lower()` method converts all characters to lowercase, allowing the program to accept "Left", "LEFT", or "left" as equivalent inputs. The membership test `raw in allowed` checks if the normalized input matches any element in the paths tuple.

## Puzzle Logic

The gate code puzzle demonstrates sequential validation. The temple first sets a secret code using the same validation that applies to the player's attempt. If either input fails validation, the puzzle returns False and prints an appropriate error message. When both inputs are valid, the function compares them numerically. An exact match prints success and returns True, while any mismatch prints failure with both the attempted and correct codes, then returns False.

The path choice puzzle follows identical structure with different validation. Both temple and player inputs go through `read_path`, which handles string normalization and membership checking. The comparison uses string equality rather than numeric equality. This puzzle demonstrates how the same validation pattern applies to different data types by swapping the helper function while keeping the overall logic structure unchanged.

The weight balance puzzle introduces multi-value validation. Three separate inputs (target, weight A, weight B) each use `read_int_in_range` with the same bounds. Any validation failure on any input causes the puzzle to return False immediately. When all three inputs succeed, the function computes the sum of weights A and B, then compares this total to the target. Success occurs only when the sum exactly equals the target value.

## Control Flow

The main driver implements sequential gating through nested conditionals. If `enter_code()` returns True, execution proceeds to `choose_path()`. If that also returns True, execution reaches `balance_weights()`. Any False return at any stage terminates the puzzle sequence without proceeding to subsequent challenges. This creates a progressive difficulty curve where players must complete earlier puzzles before attempting later ones.

Python evaluates boolean expressions using short-circuit logic. In the statement `if enter_code():`, Python calls the function and checks its return value. If it returns False, Python skips the entire nested block without evaluating `choose_path()`. This behavior is exactly what the game needs since failed puzzles should prevent access to later challenges.

The program prints an end-of-attempt message regardless of how far the player progressed. This message appears after the conditional chain completes, whether that happens after the first puzzle failure or after completing all three. The unconditional message provides closure to the game session and prompts the player to restart for another attempt.

## F-String Usage

Every print statement must use f-string formatting even when no variables require interpolation. The syntax `print(f"Static text")` satisfies this requirement for messages without dynamic content. The assignment tests this rule strictly, checking that no print calls use plain strings like `print("Static text")`.

F-strings with variables use curly braces for interpolation. The expression `print(f"Gate opens. Code {attempt:0{CODE_LEN}d} accepted.")` demonstrates nested formatting where `CODE_LEN` determines padding width. The `:0Nd` format specification pads the integer with leading zeros to N digits, ensuring codes display as "0042" rather than "42".

Multiple variables in a single f-string work naturally. The statement `print(f"Not balanced: {a} + {b} = {total} (target {target}). Resetting...")` includes four different variables with clear separation through literal text. This produces readable output showing the player exactly what values were involved in the failed balance attempt.

## Type Hints

Function signatures include type annotations for parameters and return values. The syntax `def read_digits_exact(prompt: str, length: int) -> int | None:` specifies that the function accepts a string and an integer, returning either an integer or None. The pipe operator `|` creates a union type representing multiple possible return types.

The `None` type indicates the absence of a value, used here to signal validation failure. Functions that might fail validation return `int | None` rather than raising exceptions. This approach lets calling code check the return value with a simple `if result is None:` test, making error handling explicit and straightforward.

Collection types specify their contents using square brackets. The annotation `allowed: tuple[str, ...]` indicates a tuple containing an arbitrary number of string elements. The ellipsis `...` represents variable length rather than a fixed number of elements. This accurately describes the `PATHS` constant as a tuple of strings without specifying exactly three elements.

## Docstrings

Each function includes a docstring describing its purpose, parameters, and return value. The triple-quoted string appears immediately after the function definition and before any code. Python's documentation tools can extract these strings automatically to generate reference materials.

The docstring format follows a consistent structure. The first line provides a brief summary of what the function does. A blank line separates this from the detailed sections. The Parameters section lists each argument with its purpose. The Returns section describes what the function gives back to its caller. This structure helps readers quickly understand the function's interface without reading implementation details.

Docstrings use present tense and imperative mood. "Ask for a numeric string" rather than "This function asks" or "Will ask". The description focuses on what the function accomplishes from the caller's perspective rather than implementation mechanics. This matches professional Python documentation conventions seen in standard library documentation.

## Pseudocode Requirements

The pseudocode provides a hierarchical outline with 3-4 levels of detail. Level 1 represents the main driver function. Level 2 breaks down into major steps like the three puzzles. Level 3 details the operations within each puzzle. Level 4 specifies the individual validation checks and comparisons.

Numbering follows a consistent decimal system. Top-level steps use integers (1, 2, 3). Second-level steps add one decimal place (1.1, 1.2, 1.3). Third-level steps add another (1.2.1, 1.2.2). Fourth-level steps add a final place (1.2.1.1, 1.2.1.2). This numbering makes it easy to reference specific steps and shows hierarchical relationships clearly.

Each pseudocode line describes one concrete action or decision. "Validate length equals CODE_LEN" is more specific than "Check input". "Return None if invalid, convert to int if valid" clearly states both possible outcomes. The pseudocode should be detailed enough that someone could implement the program from it without seeing the actual code.

## Testing Strategy

The test harness demonstrates input simulation without external dependencies. It patches Python's built-in `input()`function temporarily, replacing it with a lambda that pulls from an iterator. This lets tests provide predetermined inputs without requiring user interaction during test execution.

The `simulate` function accepts a callable and a list of inputs. It converts the input list to an iterator, saves the original `input`function, installs the replacement, calls the target function, and restores the original `input` before returning. The try-finally block ensures restoration happens even if the tested function raises an exception.

Adding a default value to the iterator prevents crashes when tested functions request more inputs than provided. The expression `next(it, "")` returns an empty string when the iterator exhausts rather than raising StopIteration. This makes tests more robust since missing test inputs produce validation failures rather than test harness crashes.

## Common Mistakes

Forgetting to use f-strings for static messages is the most frequent error. Every print statement must begin with `print(f"`even when the string contains no variables. The assignment specification explicitly requires this for all output messages regardless of content.

Using hardcoded puzzle values violates the "no hardcoding" rule. The temple must set its values via `input()` calls just like the player. Code like `secret = 1234` fails the requirement even if the logic otherwise works correctly. Both temple and player inputs must come from the user.

Insufficient pseudocode detail loses points on the documentation requirement. Single-level outlines like "Get input, validate input, check input" don't show enough structure. The pseudocode needs to break down into granular steps showing what validation means and how checking works in specific terms.

Validating only the player's input while accepting any temple input creates an inconsistency. If the temple sets an invalid secret code, the puzzle should fail just as it would for an invalid player attempt. Both inputs need identical validation since both must meet the same format requirements.

## Key Takeaways

Modular design through helper functions reduces code duplication and centralizes validation logic. When multiple parts of the program need similar validation, abstracting that into a shared helper makes the code more maintainable and consistent.

Boolean return values enable sequential control flow where success gates access to subsequent challenges. Functions that return True or False make conditional chains readable and explicit about their progression logic.

Consistent validation patterns across all inputs create predictable behavior. Whether validating codes, paths, or weights, the three-step pattern of getting input, checking constraints, and returning a value or None makes the program's behavior uniform and understandable.

Type hints and docstrings document the program's interface without cluttering implementation code. These annotations help readers understand what each function expects and provides without parsing through the actual logic.

The program demonstrates that complex interactive applications can be built from simple building blocks. Three puzzle functions, three helper functions, and one driver create an engaging game through careful composition of small, focused functions that each do one thing well.

## Complete Implementation

```python
# temple_escape.py

"""
1. Start Temple Escape (main driver)
   1.1 Print welcome and instructions
   1.2 Gate Code (enter_code)
       1.2.1 Temple sets secret 4-digit code
             1.2.1.1 Prompt for CODE_LEN digit code
             1.2.1.2 Validate length equals CODE_LEN
             1.2.1.3 Validate all characters are digits
             1.2.1.4 Return None if invalid, convert to int if valid
       1.2.2 Player attempts 4-digit code
             1.2.2.1 Prompt for CODE_LEN digit attempt
             1.2.2.2 Validate length equals CODE_LEN
             1.2.2.3 Validate all characters are digits
             1.2.2.4 Return None if invalid, convert to int if valid
       1.2.3 Compare attempt to secret
             1.2.3.1 If match, print success message and return True
             1.2.3.2 If no match, print failure message and return False
   1.3 Path Choice (choose_path) if 1.2 success
       1.3.1 Temple sets correct path
             1.3.1.1 Prompt for path from PATHS options
             1.3.1.2 Normalize input to lowercase
             1.3.1.3 Validate path is in allowed set
             1.3.1.4 Return None if invalid, return path if valid
       1.3.2 Player chooses path
             1.3.2.1 Prompt for path from PATHS options
             1.3.2.2 Normalize input to lowercase
             1.3.2.3 Validate path is in allowed set
             1.3.2.4 Return None if invalid, return path if valid
       1.3.3 Compare player choice to correct path
             1.3.3.1 If match, print success message and return True
             1.3.3.2 If no match, print failure message and return False
   1.4 Weight Balance (balance_weights) if 1.3 success
       1.4.1 Temple sets target weight
             1.4.1.1 Prompt for target in range MIN_W to MAX_W
             1.4.1.2 Validate input contains only digits
             1.4.1.3 Convert to int and validate in range
             1.4.1.4 Return None if invalid, return int if valid
       1.4.2 Player sets weight A
             1.4.2.1 Prompt for weight A in range MIN_W to MAX_W
             1.4.2.2 Validate input contains only digits
             1.4.2.3 Convert to int and validate in range
             1.4.2.4 Return None if invalid, return int if valid
       1.4.3 Player sets weight B
             1.4.3.1 Prompt for weight B in range MIN_W to MAX_W
             1.4.3.2 Validate input contains only digits
             1.4.3.3 Convert to int and validate in range
             1.4.3.4 Return None if invalid, return int if valid
       1.4.4 Calculate sum and compare to target
             1.4.4.1 Compute total as A + B
             1.4.4.2 If total equals target, print success and return True
             1.4.4.3 If total not equal, print failure and return False
   1.5 Print end-of-attempt message
"""

# Named constants (replace magic numbers)
CODE_LEN: int = 4
PATHS: tuple[str, ...] = ("left", "center", "right")
MIN_W: int = 0
MAX_W: int = 999

# Helpers

def read_digits_exact(prompt: str, length: int) -> int | None:
    """
    Ask for a numeric string of exact length; return int or None.

    Parameters:
        prompt: text shown to the user
        length: required exact digit count

    Returns:
        int if valid input of exact length, else None
    """
    raw = input(prompt).strip()
    if len(raw) != length or not raw.isdigit():
        print(f"Input must be exactly {length} digits.")
        return None
    return int(raw)

def read_path(prompt: str, allowed: tuple[str, ...] = PATHS) -> str | None:
    """
    Ask for a path word from the allowed set; return normalized string or None.

    Parameters:
        prompt: text shown to the user
        allowed: valid options (default PATHS)

    Returns:
        the chosen path in lowercase if valid, else None
    """
    raw = input(prompt).strip().lower()
    if raw not in allowed:
        print(f"Path must be one of: {', '.join(allowed)}.")
        return None
    return raw

def read_int_in_range(prompt: str, lo: int, hi: int) -> int | None:
    """
    Ask for an integer within [lo, hi]; return int or None.

    Parameters:
        prompt: text shown to the user
        lo: inclusive lower bound
        hi: inclusive upper bound

    Returns:
        int within [lo, hi] if valid, else None
    """
    raw = input(prompt).strip()
    if not raw.isdigit():
        print(f"Please enter digits only (range {lo}–{hi}).")
        return None
    val = int(raw)
    if not (lo <= val <= hi):
        print(f"Value must be between {lo} and {hi}.")
        return None
    return val

# Puzzle 1

def enter_code() -> bool:
    """
    Gate Code: temple sets secret; player attempts; success on exact match.

    Returns:
        True if attempt equals secret, else False
    """
    # [1.2.1] temple sets secret code
    secret = read_digits_exact(f"Temple sets the secret {CODE_LEN}-digit code: ", CODE_LEN)
    if secret is None:
        print(f"Gate remains locked. Resetting...")
        return False

    # [1.2.2] player attempt
    attempt = read_digits_exact(f"Enter your {CODE_LEN}-digit attempt: ", CODE_LEN)
    if attempt is None:
        print(f"Invalid attempt format. Resetting...")
        return False

    # [1.2.3] check
    if attempt == secret:
        print(f"Gate opens. Code {attempt:0{CODE_LEN}d} accepted.")
        return True
    print(f"Wrong code {attempt:0{CODE_LEN}d}. Resetting...")
    return False

# Puzzle 2

def choose_path() -> bool:
    """
    Path Choice: temple sets correct path; player chooses; success on match.

    Returns:
        True if player choice equals temple's correct path, else False
    """
    # [1.3.1] temple picks correct path
    correct = read_path(f"Temple sets the correct path ({', '.join(PATHS)}): ")
    if correct is None:
        print(f"Invalid correct path. Resetting...")
        return False

    # [1.3.2] player choice
    choice = read_path(f"Choose your path ({', '.join(PATHS)}): ")
    if choice is None:
        print(f"Invalid choice. Resetting...")
        return False

    # [1.3.3] check
    if choice == correct:
        print(f"Path '{choice}' is safe. Proceed.")
        return True
    print(f"Path '{choice}' is a trap. Resetting...")
    return False

# Puzzle 3

def balance_weights() -> bool:
    """
    Weight Balance: target equals A + B.

    Returns:
        True if A + B equals target, else False
    """
    # [1.4.1] temple sets target
    target = read_int_in_range(f"Temple sets the target weight ({MIN_W}–{MAX_W}): ", MIN_W, MAX_W)
    if target is None:
        print(f"Invalid target. Resetting...")
        return False

    # [1.4.2] player sets weight A
    a = read_int_in_range(f"Place object A ({MIN_W}–{MAX_W}): ", MIN_W, MAX_W)
    if a is None:
        print(f"Invalid A. Resetting...")
        return False

    # [1.4.3] player sets weight B
    b = read_int_in_range(f"Place object B ({MIN_W}–{MAX_W}): ", MIN_W, MAX_W)
    if b is None:
        print(f"Invalid B. Resetting...")
        return False

    # [1.4.4] check
    total = a + b
    if total == target:
        print(f"Balanced. {a} + {b} = {total} equals target {target}.")
        return True
    print(f"Not balanced: {a} + {b} = {total} (target {target}). Resetting...")
    return False

# Driver

def start_temple_escape():
    """Main game flow controlling the temple puzzles."""
    # [1.1] intro
    print(f"\nWelcome to the Ancient Temple of Code.")
    print(f"Solve all three puzzles to escape.\n")

    # flow
    if enter_code():
        if choose_path():
            balance_weights()

    # [1.5] end
    print(f"\nEnd of attempt. Restart the temple to try again.")

# Optional: simple test harness (no external libs)
# Run by executing: python temple_escape.py test
def _run_tests():
    """
    Very small harness that simulates inputs by patching built-in input().
    Prints PASS/FAIL for a few cases.
    """
    import builtins

    def simulate(func, inputs):
        it = iter(inputs)
        original_input = builtins.input
        builtins.input = lambda prompt='': next(it, "")
        try:
            return func()
        finally:
            builtins.input = original_input

    print(f"Running tests...")
    # Puzzle 1: success
    ok = simulate(enter_code, ["1234", "1234"])
    print(f"enter_code success: {'PASS' if ok else 'FAIL'}")
    # Puzzle 1: fail
    ok = simulate(enter_code, ["1234", "0000"])
    print(f"enter_code fail: {'PASS' if not ok else 'FAIL'}")
    # Puzzle 2: success
    ok = simulate(choose_path, ["left", "left"])
    print(f"choose_path success: {'PASS' if ok else 'FAIL'}")
    # Puzzle 3: success
    ok = simulate(balance_weights, ["10", "7", "3"])
    print(f"balance_weights success: {'PASS' if ok else 'FAIL'}")

# Start
if __name__ == "__main__":
    import sys
    if len(sys.argv) > 1 and sys.argv[1] == "test":
        _run_tests()
    else:
        start_temple_escape()
```

## Usage Examples

To run the game normally:

```python
python temple_escape.py
```

To run the test suite:

```python
python temple_escape.py test
```

Sample game session:

```python
Welcome to the Ancient Temple of Code.
Solve all three puzzles to escape.

Temple sets the secret 4-digit code: 1234
Enter your 4-digit attempt: 1234
Gate opens. Code 1234 accepted.
Temple sets the correct path (left, center, right): center
Choose your path (left, center, right): center
Path 'center' is safe. Proceed.
Temple sets the target weight (0–999): 100
Place object A (0–999): 60
Place object B (0–999): 40
Balanced. 60 + 40 = 100 equals target 100.

End of attempt. Restart the temple to try again.
```