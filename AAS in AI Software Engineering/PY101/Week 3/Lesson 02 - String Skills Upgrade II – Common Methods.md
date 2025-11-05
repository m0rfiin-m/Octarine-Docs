
# String Skills Upgrade II – Common Methods

## Lesson Title

**String skills upgrade ii: common methods**

---

## Key Concepts in This Lesson

## 1. **Raw Strings and Output**

- Print a string to see spaces, newlines, or special characters exactly as they appear.

- Example:

  ```plaintext
  python
  ```

  `raw = ' PyThOn 3.12!!! ' print(raw) `

## 2. **The** `strip()` **Method**

- Removes *spaces* (or any whitespace) from both *ends* of a string.

- `strip()` with no arguments removes whitespace. `strip('abc')` would remove those specific characters from both ends.

- Example:

  ```plaintext
  python
  ```

  `clean = raw.strip()  # Now clean has no spaces at the start or end `

## 3. **The** `lower()` **Method**

- Converts every character to lowercase.

- Does NOT change the original string; it returns a new one.

- Example:

  ```plaintext
  python
  ```

  `name = "MaRCo" print(name.lower())  # prints 'marco' print(name)          # still 'MaRCo' `

## 4. **The** `in` **Keyword**

- Checks whether a string is contained within another string.

- Example:

  ```plaintext
  python
  ```

  `print("rock" in "python rocks")  # prints True `

## 5. **The** `find()` **Method**

- Returns the *index* (position) where a substring first appears, or `-1` if not found.

- Example:

  ```plaintext
  python
  ```

  `pos = "live code".find("ve")  # pos is 2 `

## 6. **The** `replace()` **Method**

- Replaces all occurrences of a substring with another substring.

- Example:

  ```plaintext
  python
  ```

  `msg = "spam spam bacon spam" fixed = msg.replace("spam", "eggs")  # 'eggs eggs bacon eggs' `

- To delete a character, replace it with "":

  ```plaintext
  python
  ```

  `clean = " HeLLo!!! ".strip().lower().replace("!", "")  # 'hello' `

## 7. **Chaining Methods for Powerful Cleaning**

- You can use multiple methods at once:

  ```plaintext
  python
  ```

  `def clean_word(word):     return word.strip().lower().replace('!', '') print(clean_word(" HeLLo!!! "))  # prints 'hello' `

## Lesson Flow Example

1. Print a messy string.

2. Use `.strip()` to remove edge spaces.

3. Use `.lower()` to make everything lowercase.

4. Check for substrings with `in` and find their positions with `.find()`.

5. Replace or remove parts using `.replace()`.

6. Combine steps in a custom function like `clean_word()`.

## Practice Prompts

- What would `clean_word(" PYTHON!!! ")` return?

- Can you use string methods to strip, lowercase, and remove `?` from: `" WhAt? "`?

- What does `msg.replace("-", "/")` do to `"2025-11-05"`?

---

When you’re ready to review or practice, try building similar functions, or ask for more examples on any of these methods.

If you’d like a personalized study experience (more practice or tailored explanations), let me know your course or comfort level!

for number 7 can we also include the basic version clean_word = "   HeLLo!!!   "
clean = clean_word.strip().lower().replace("!", "")
print(clean)

# Study Guide: String Cleaning Methods in Python

## Lesson Title

**String skills upgrade ii: common methods**

## Summary

This lesson showed how to clean, search, and transform strings using Python's standard string methods.

---

## Concepts Covered

## 1. **Printing and Viewing Raw Strings**

- Use `print()` to see exactly what a string contains, including any extra spaces or special characters.

## 2. **The** `strip()` **Method**

- Removes whitespace (spaces, tabs, newlines) from the **start and end** of the string:

  ```plaintext
  python
  ```

  `s = "  Dallas  " clean = s.strip()  # 'Dallas' `

- With an argument, it removes all listed characters from both ends (less common for basic cleaning).

## 3. **The** `lower()` **Method**

- Creates a new string where all letters are lowercase:

  ```plaintext
  python
  ```

  `word = "MaRCo" print(word.lower())  # 'marco' print(word)          # 'MaRCo' (unchanged) `

## 4. **The** `in` **Keyword for Substrings**

- Checks if part of a string exists within another string:

  ```plaintext
  python
  ```

  `"rock" in "python rocks"  # True `

## 5. **The** `find()` **Method**

- Returns the starting index of a substring, or `-1` if not found:

  ```plaintext
  python
  ```

  `pos = "live code".find("ve")  # 2 `

## 6. **The** `replace()` **Method**

- Replaces all occurrences of a substring with another substring:

  ```plaintext
  python
  ```

  `msg = "spam spam bacon spam" msg.replace("spam", "eggs")  # 'eggs eggs bacon eggs' # To delete, replace with "": "hello!!!".replace("!", "")  # 'hello' `

---

## 7. **Chaining Methods for Efficient Cleaning**

- You can combine steps into a single line by chaining string methods:

  ```plaintext
  python
  ```

  `clean_word = "   HeLLo!!!   " clean = clean_word.strip().lower().replace("!", "") print(clean)  # Output: hello `

- **How It Works:**

  1. `.strip()` removes spaces at the start/end

  2. `.lower()` changes all letters to lowercase

  3. `.replace('!', '')` deletes all exclamation marks

---

## Practice & Next Steps

- Try similar exercises: clean up strings with spaces, capitals, or unwanted symbols using these methods.

- **Challenge:** Can you make a one-liner to remove spaces, lower the case, and remove all `?` characters from `" WhAt? "`?