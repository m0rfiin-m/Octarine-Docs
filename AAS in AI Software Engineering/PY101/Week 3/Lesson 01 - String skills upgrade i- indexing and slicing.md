
# String skills upgrade i: indexing and slicing

This lesson covers the fundamentals of string indexing and slicing in Python, building up to writing a function that extracts the middle third of a string. Work through the steps below—try out each code example, then challenge yourself with the mini-exercise at the end.

## Letter Positioning: Indexing

- Each character in a Python string has a **position (index)**, starting from 0 on the left.

- Example:
  For the word `"PYTHON"`:

  | **Letter** | **P** | **Y** | **T** | **H** | **O** | **N** |
  | --- | --- | --- | --- | --- | --- | --- |
  | Index | 0 | 1 | 2 | 3 | 4 | 5 |

- To access a specific letter: `text[index]`.

- Example: Print the third letter (index 2) of `"Marco"`:

  ```plaintext
  python
  ```

  `print("Marco"[2]) # Output: r`

## Negative Indexing

- Python allows **negative indices** to access characters from the end of a string.

- `-1` is the last character, `-2` the second-to-last, and so on.

- Example:

  ```plaintext
  python
  ```

  `word = "python" print(word[-1]) # Output: n print(word[-2]) # Output: o`

- Practice: Print the second-to-last letter of `"Dallas"`:

  ```plaintext
  python
  ```

  `word = "Dallas" print(word[-2]) # Output: a`

## Slicing Strings

- **Slicing** lets you extract a chunk (substring) using `text[start:stop]`.

- **Start index is included, stop index is NOT included**.

- Example:

  ```python
  python
  ```

  `phrase = "live code" print(phrase[0:4]) # Output: live print(phrase[5:9]) # Output: code`

- Practice: To grab `"ve c"` from `"live code"`

  - Spans positions 2,3,4,5, so use:

  ```plaintext
  python
  ```

  `print(phrase[2:6]) # Output: ve c`

## Omitting Bounds in Slices

- Leave **start** blank to start at 0.

- Leave **stop** blank to go to the end.

- Example:

  ```plaintext
  python
  ```

  `phrase = "hello world" print(phrase[6:]) # Output: world print(phrase[:5]) # Output: hello`

## Step in Slicing

- Syntax: `text[start:stop:step]`

- **Step** allows you to skip characters (e.g., every 2nd letter).

- Example:

  ```plaintext
  python
  ```

  `secret = "abcdefg" print(secret[::2]) # Output: aceg`

- **To reverse a string:**

  ```plaintext
  python
  ```

  `print(secret[::-1]) # Output: gfedcba`

## Mini-Challenge: Writing `middle_third(text)`

**Goal:** Write a function that returns the middle third of a string whose length is divisible by 3.

**Hints:**

- Use `len(text)` to get the total length.

- Use integer division (`//`) to get one third.

- Use slicing with calculated indices.

**Sample Solution:**

```plaintext
python
```

`def middle_third(text): n = len(text) third = n // 3 return text[third:2*third] result = middle_third("SpaceStation") print(result) # Output: eSta`

**Checklist:**

- Uses `len()` ✔️

- Uses slicing ✔️

- Works when length is a multiple of 3 ✔️

## Key Takeaways

- **Indexing:** `text[n]` for nth character (starts at 0; use negative numbers for counting from end)

- **Slicing:** `text[start:stop]` gets substring from `start` (inclusive) to `stop` (exclusive)

- **Steps** in slicing: `text[start:stop:step]` (step can reverse or skip)

- **Middle third logic:**

  - Start at 1/3 of the string

  - End at 2/3 of the string

  - Remember integer division (`//`) for indices