
## Why Do You Need User Input?

- Some programs, like calculators and order forms, need to **react to what the user types**.
    
- Input allows a program to become interactive.
    

---

## Step 1: Getting Simple Input (Strings)

**Problem:**  
Get the user's name and greet them.

**How-To:**

1. Use the `input()` function to show a prompt and wait for the user to type.
    
2. Store what's typed in a variable.
    
3. Print results using the variable.
    

**Code:**
```python
name = input("your name: ") print(f"hi, {name}!")
```

---

## Step 2: Checking the Type

**Problem:**  
See what type of value `input()` gives you.

**How-To:**

1. Get input with `input()`.
    
2. Use `type()` to check.
    

**Code:**
```python 
response = input("Type anything: ") print(type(response)) # Always str

``` 

---

## Step 3: Getting Numbers and Using Them

**Problem:**  
Ask for the user's age and tell them how old they’ll be next year.

**How-To:**

1. Remember: input always gives you a string!
    
2. Convert the string to a number with `int()`.
    

**Code:**
``` python
age_text = input("age in years: ") # Gets a string
age =int(age text) 
# Converts to integer print("next year:", age + 1)
print("next year:" , age + 1)

```
---

## Step 4: Input With Decimals (Floats)

**Problem:**  
Ask the user for the price of coffee and calculate the cost for two.

**How-To:**

1. Get input as a string.
    
2. Convert to float.
    
3. Multiply for cost.
    
4. Format output to two decimals.
    

**Code:**
``` python
price_text = input("coffee price $: ")
price = float(price_text)
print(f"double order: ${price * 2:.2f}")

```

---

## Step 5: Common Errors With Variables

**Problem:**  
What happens if variable names are misspelled?

**How-To:**

- Python variables must be spelled exactly the same everywhere.
    
- A typo will cause a `NameError`.
    

**Code:**
``` python
coffee = 10
print(cofee)    # Spelling error!


```
---

# Word Problems & Examples

## 1. Age Calculator

**Word Problem:**  
Ask the user for their birth year. Calculate their age in 2025.

**Step By Step:**

1. Get birth year as input.
    
2. Convert it to an integer.
    
3. Subtract from 2025.
    
4. Print result.
    

**Code:**
``` python
width = float(input("Enter the width (m): "))
height = float(input("Enter the height (m): "))
area = width * height
print(f"The area is {area} square meters.")

```

---

## 2. Rectangle Area

**Word Problem:**  
Ask for width and height (in meters). Calculate the area.

**Step By Step:**

1. Get width and height as decimal numbers.
    
2. Multiply together for area.
    
3. Print result.
    

**Code:**
```python
width = float(input("Enter the width (m): "))
height = float(input("Enter the height (m): "))
area = width * height
print(f"The area is {area} square meters.")

```
---

## 3. Shopping Cart Total

**Word Problem:**  
Get the price of three items and add up the total.

**Step By Step:**

1. Get price for each item.
    
2. Convert each to a decimal (with float).
    
3. Add all three together.
    
4. Print cost.
    

**Code:**

```python
item1 = float(input("Price of item 1: $"))
item2 = float(input("Price of item 2: $"))
item3 = float(input("Price of item 3: $"))
total = item1 + item2 + item3
print(f"Your total is ${total:.2f}")

```


---

## 4. Celsius to Fahrenheit

**Word Problem:**  
Ask for Celsius temperature and convert to Fahrenheit.

**Step By Step:**

1. Get Celsius input.
    
2. Convert with formula: F = C * 9/5 + 32.
    
3. Print result.
    

**Code:**

```python
celsius = float(input("Temperature in Celsius: "))
fahrenheit = celsius * 9 / 5 + 32
print(f"{celsius}°C is {fahrenheit:.1f}°F")

```
---

## 5. Weekly Pay Calculator

**Word Problem:**  
Ask for hours worked and hourly wage. Calculate weekly pay.

**Step By Step:**

1. Get hours and wage as decimal input.
    
2. Multiply hours by wage.
    
3. Print result.
    

**Code:**
 ```python
 hours = float(input("Hours worked: "))
wage = float(input("Hourly wage: $"))
pay = hours * wage
print(f"Your pay is ${pay:.2f}")

 ```

---

## 6. Grade Percentage

**Word Problem:**  
Ask for points earned and points possible. Calculate grade percentage.

**Step By Step:**

1. Get two decimal numbers as input.
    
2. Divide earned by possible and multiply by 100.
    
3. Print percentage.
    

**Code:**

```python
earned = float(input("Points earned: "))
possible = float(input("Points possible: "))
percentage = (earned / possible) * 100
print(f"Your grade is {percentage:.1f}%")

```

---

## 7. Tip Calculator

**Word Problem:**  
Ask for bill total and tip percentage. Print tip and total bill.

**Step By Step:**

1. Get bill and tip percent.
    
2. Convert both to decimals.
    
3. Calculate tip and total.
    
4. Print both.
    

**Code:**

```python
bill = float(input("Restaurant bill: $"))
tip_percent = float(input("Tip percentage: "))
tip = bill * tip_percent / 100
total = bill + tip
print(f"Tip: ${tip:.2f}")
print(f"Total bill: ${total:.2f}")


```

---

# Study Tips

- Try writing the code for each problem from scratch before looking at the answer.
    
- Change variable names or numbers to create your own practice questions.
    
- Always convert inputs to numbers before doing math!