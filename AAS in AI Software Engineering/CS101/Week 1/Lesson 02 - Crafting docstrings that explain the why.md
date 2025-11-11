
**Crafting docstrings that explain the why**

Docstrings describe what a function does, why it exists, how to use it, and what it returns. They live directly under the def line in triple quotes and are visible via help(func) or func.**doc**.

**Why docstrings matter**

- They remove ambiguity: you don’t need to read code internals to understand purpose.
- They standardize communication for future you and other devs.
- They guide tools (help, IDEs, docs generators).

**Format to memorize**

- One-sentence summary (start with a verb).
- Blank line.
- Details: parameters and return value(s).

Example template:

```python
def my_function(param):
    """
    One-sentence summary.

    Args:
        param: What it represents.

    Returns:
        What is returned and in what form.
    """
    # function body
```

**Example 1: Why docstrings help**

Starting function (confusing without context):

```python
def runit(x):

return x * 2 - 1

```

Problem: No clue what x should be, what the intent is, or why this exists. A docstring would clarify input expectations and purpose.

**Example 2: Clean a word (complete docstring)**

Final version from the lesson:

```python
def clean_word(word):

"""

Remove leading/trailing spaces, make lowercase, and strip out exclamation marks.

Args:

word: The string to clean.

Returns:

A new string with no exclamation marks, no spaces at the ends, and all lowercase.

"""

return word.strip().lower().replace("!", "")
```

Key points:

- Verb-first summary.
- Clear parameter description.
- Return value explained in plain language (not just a formula or method list).

**Example 3: Fahrenheit → Celsius (your iterations and fixes)**

Initial prompt:

```python
def convert_f_to_c(temp_f):

return (temp_f - 32) * 5/9

Your first attempt (issues: mismatched param, unclear return, wrong return code):def convert_f_to_c(temp_f):

"""

Convert fahrenheit to celcius

Args:

celcius: new temp

Return:

(temp_f -32) * 5/9

"""

return temp_f

Improved version (still needed polish):def convert_f_to_c(temp_f):

"""

Convert fahrenheit to celcius

Args:

temp_f: new temp

Return:

converted temps

"""

return (temp_f -32) * 5/9

```

Final polished docstring (corrected grammar and format):

```python
def convert_f_to_c(temp_f):

"""

Convert fahrenheit to celcius

Args:

temp_f: temperature in Fahrenheit

Returns:

Temperature in Celsius as a float

"""

return (temp_f -32) * 5/9

Testing:print(convert_f_to_c(98))

Observed output:36.666666666666664
```

Lesson learned:

- “Args” must match real parameters.
- “Returns” explains the result, not the raw formula.
- The function body should implement the described behavior.

**Example 4: Repeating symbols (your iterations and fixes)**

Prompted function:

```python
def fancy_line(symbol, length):

return symbol * length

Your first docstring (needed clarity and correct return):def fancy_line(symbol, length):

"""

Creates Symbols and extends length

Args:

symbol: the character to repeat

length: how many times to repeat

Returns: A string made by repeating the symbol



"""

return fancy_line

```

Final corrected version:

```python
def fancy_line(symbol, length):

"""

Create a line by repeating a symbol a specified number of times.

Args:

symbol: The character to repeat.

length: How many times to repeat the symbol.

Returns:

A string made by repeating the symbol.

"""

return symbol * length
```

Lesson learned:

- Summary should state the outcome plainly.
- Return must be the computed value, not the function name.
- Keep “Returns:” on its own line, parallel to “Args:”.

**Quick checklist you used (and answered)**

- Starts with a clear verb.
- Blank line after summary.
- Mentions each parameter and the return value.
- Explains purpose (the why), not step-by-step code internals.

You responded: yes, no, yes, yes — then aligned your docstrings to the full pattern.

**Common pitfalls you navigated**

- Forgetting triple quotes or proper indentation.
- Mismatched parameter names in “Args”.
- Describing formulas instead of the result in “Returns”.
- Returning the wrong thing (e.g., returning the function instead of a value).
- Mixing comments with docstrings; they’re different tools.
- Testing variables outside function scope (print the function call instead).

**Cheat sheet: copy/paste-ready pattern**

```python
def function_name(param1, param2):

"""

Verb-first one-sentence summary of the function’s purpose.

Args:

param1: What it represents / expected type or meaning.

param2: What it represents / expected type or meaning.

Returns:

What is returned and in what form (type), stated simply.

"""

# implementation

Keep docstrings focused on intent and usage. Save internal mechanics for the code or comments when necessary.
```