# Week 1 Review: Cafe Receipt

**Date:** October 25, 2025  
**Course:** PY101 - Introduction to Python  
**Week:** 1, End of Week Review  
**Status:** ⚠️ Must Complete Before Week 2

## Why This Review Matters

This review combines everything you learned in Lessons 1-15: variables, types, user input, expressions, operator precedence, rounding, and formatting. You cannot move to Week 2 until you complete this exercise and the additional practice problems.

---

## The Original Problem

**Given Example:**
```
Item: Apple
Price: 1.5$
Quantity: 4
Total price: 6.00$
-------------------
Item: Cream cheese
Price: 3.45$
Quantity: 3
Total price: 10.35$

########################
Total cart price: 16.35$
########################
```

---

## Your Original Code (With Issues)

```python
# Mini receipt calculator

item1 = input("item1")
item1 = float(input("Price of item 1: $"))
item1 = int(input("Quantity of item 1"))
total = item1
print(total)

item2 = input("item2")
item2 = float(input("Price of item 2: $"))
item2 = int(input("Quantity of item 2"))

item3 = input("item3")
item3 = float(input("Price of item 3: $"))
item3 = int(input("Quantity of item 3"))
```

**Problems Identified:**
1. **Variable overwriting** - You used `item1` for name, price, and quantity, so each assignment deleted the previous value
2. **Missing calculations** - You never multiplied price by quantity
3. **No formatting** - Prices need `.2f` formatting for currency
4. **Incomplete** - Item 2 and 3 never calculated totals or printed output
5. **No final sum** - Never added all items together for cart total

---

## Corrected Solution

```python
# Mini receipt calculator

# Item 1
item1_name = input("Item 1: ")
item1_price = float(input("Price of item 1: $"))
item1_quantity = int(input("Quantity of item 1: "))
item1_total = item1_price * item1_quantity

print(f"Item: {item1_name}")
print(f"Price: {item1_price}$")
print(f"Quantity: {item1_quantity}")
print(f"Total price: {item1_total:.2f}$")
print("-------------------")

# Item 2
item2_name = input("Item 2: ")
item2_price = float(input("Price of item 2: $"))
item2_quantity = int(input("Quantity of item 2: "))
item2_total = item2_price * item2_quantity

print(f"Item: {item2_name}")
print(f"Price: {item2_price}$")
print(f"Quantity: {item2_quantity}")
print(f"Total price: {item2_total:.2f}$")
print("-------------------")

# Item 3
item3_name = input("Item 3: ")
item3_price = float(input("Price of item 3: $"))
item3_quantity = int(input("Quantity of item 3: "))
item3_total = item3_price * item3_quantity

print(f"Item: {item3_name}")
print(f"Price: {item3_price}$")
print(f"Quantity: {item3_quantity}")
print(f"Total price: {item3_total:.2f}$")

# Calculate total cart price
total_cart = item1_total + item2_total + item3_total

print("########################")
print(f"Total cart price: {total_cart:.2f}$")
print("########################")
```

**Key Fixes:**
1. **Separate variables** - Each piece of data gets its own variable name
2. **Calculate totals** - Multiply price by quantity for each item
3. **Format currency** - Use `.2f` to show exactly two decimal places
4. **Complete all sections** - All three items have full input, calculation, and output
5. **Sum the cart** - Add all item totals for final cart price

---

## Concepts Applied

This exercise uses:

✅ **Variables** - Storing different types of data (Lesson 2)  
✅ **Type conversion** - `float()` and `int()` for user input (Lesson 9)  
✅ **User input** - `input()` to get data from user (Lesson 9)  
✅ **Expressions** - `price * quantity` for calculations (Lesson 3)  
✅ **F-strings** - `f"{variable:.2f}"` for formatted output (Lesson 1, 8)  
✅ **Rounding/Formatting** - `.2f` for money display (Lesson 8)  
✅ **String repetition** - `"#" * 24` for visual separators (Lesson 1)

---

## Additional Practice Problems

Test your Week 1 knowledge with these similar exercises. Try to solve them in LazyVim or your IDE without looking at the solutions first.

### Practice 1: Restaurant Bill Calculator

**Problem:**  
Create a program that calculates a restaurant bill with tax and tip.

**Requirements:**
- Get meal cost from user
- Calculate 8.5% tax
- Calculate 18% tip (on subtotal before tax)
- Display: subtotal, tax, tip, and total

**Example Output:**
```
Enter meal cost: $45.00
-------------------
Subtotal: $45.00
Tax (8.5%): $3.83
Tip (18%): $8.10
-------------------
Total: $56.93
```

<details>
<summary>Solution</summary>

```python
# Restaurant Bill Calculator

meal_cost = float(input("Enter meal cost: $"))

tax_rate = 0.085
tip_rate = 0.18

tax = meal_cost * tax_rate
tip = meal_cost * tip_rate
total = meal_cost + tax + tip

print("-------------------")
print(f"Subtotal: ${meal_cost:.2f}")
print(f"Tax (8.5%): ${tax:.2f}")
print(f"Tip (18%): ${tip:.2f}")
print("-------------------")
print(f"Total: ${total:.2f}")
```

</details>

---

### Practice 2: Shipping Cost Calculator

**Problem:**  
Calculate shipping cost based on package weight and distance.

**Requirements:**
- Get package weight (in lbs) from user
- Get shipping distance (in miles) from user
- Base rate: $5.00
- Per pound: $0.50
- Per mile: $0.10
- Display: base rate, weight charge, distance charge, total

**Example Output:**
```
Package weight (lbs): 12
Shipping distance (miles): 150
========================
Base rate: $5.00
Weight charge: $6.00
Distance charge: $15.00
========================
Total shipping: $26.00
```

<details>
<summary>Solution</summary>

```python
# Shipping Cost Calculator

weight = float(input("Package weight (lbs): "))
distance = float(input("Shipping distance (miles): "))

base_rate = 5.00
per_pound = 0.50
per_mile = 0.10

weight_charge = weight * per_pound
distance_charge = distance * per_mile
total = base_rate + weight_charge + distance_charge

print("=" * 24)
print(f"Base rate: ${base_rate:.2f}")
print(f"Weight charge: ${weight_charge:.2f}")
print(f"Distance charge: ${distance_charge:.2f}")
print("=" * 24)
print(f"Total shipping: ${total:.2f}")
```

</details>

---

### Practice 3: Event Ticket Sales

**Problem:**  
Calculate total revenue from ticket sales for an event with multiple ticket types.

**Requirements:**
- Get number of adult tickets sold (price: $25.00 each)
- Get number of child tickets sold (price: $15.00 each)
- Get number of senior tickets sold (price: $20.00 each)
- Display: each ticket type with quantity and subtotal, then grand total

**Example Output:**
```
Adult tickets sold: 45
Child tickets sold: 20
Senior tickets sold: 15
========================
Adult tickets: 45 x $25.00 = $1125.00
Child tickets: 20 x $15.00 = $300.00
Senior tickets: 15 x $20.00 = $300.00
========================
Total revenue: $1725.00
```

<details>
<summary>Solution</summary>

```python
# Event Ticket Sales Calculator

adult_qty = int(input("Adult tickets sold: "))
child_qty = int(input("Child tickets sold: "))
senior_qty = int(input("Senior tickets sold: "))

adult_price = 25.00
child_price = 15.00
senior_price = 20.00

adult_total = adult_qty * adult_price
child_total = child_qty * child_price
senior_total = senior_qty * senior_price

total_revenue = adult_total + child_total + senior_total

print("=" * 24)
print(f"Adult tickets: {adult_qty} x ${adult_price:.2f} = ${adult_total:.2f}")
print(f"Child tickets: {child_qty} x ${child_price:.2f} = ${child_total:.2f}")
print(f"Senior tickets: {senior_qty} x ${senior_price:.2f} = ${senior_total:.2f}")
print("=" * 24)
print(f"Total revenue: ${total_revenue:.2f}")
```

</details>

---

### Practice 4: Grade Calculator

**Problem:**  
Calculate final grade from multiple assignment scores.

**Requirements:**
- Get scores for 3 assignments (out of 100 points each)
- Calculate average
- Display: each score, average, and letter grade message

**Grading Scale:**
- 90-100: A
- 80-89: B
- 70-79: C
- 60-69: D
- Below 60: F

**Note:** For this week, just display the average. We'll add letter grade logic in future weeks when we learn conditionals.

**Example Output:**
```
Assignment 1 score: 85
Assignment 2 score: 92
Assignment 3 score: 88
========================
Assignment 1: 85
Assignment 2: 92
Assignment 3: 88
========================
Average: 88.33
```

<details>
<summary>Solution</summary>

```python
# Grade Calculator

assignment1 = float(input("Assignment 1 score: "))
assignment2 = float(input("Assignment 2 score: "))
assignment3 = float(input("Assignment 3 score: "))

average = (assignment1 + assignment2 + assignment3) / 3

print("=" * 24)
print(f"Assignment 1: {assignment1:.0f}")
print(f"Assignment 2: {assignment2:.0f}")
print(f"Assignment 3: {assignment3:.0f}")
print("=" * 24)
print(f"Average: {average:.2f}")
```

</details>

---

### Practice 5: Fuel Cost Calculator

**Problem:**  
Calculate the cost of a road trip based on distance, fuel efficiency, and gas price.

**Requirements:**
- Get trip distance (miles) from user
- Get car's fuel efficiency (miles per gallon) from user
- Get current gas price (per gallon) from user
- Calculate gallons needed
- Calculate total fuel cost
- Display: distance, MPG, gallons needed, cost per gallon, total cost

**Example Output:**
```
Trip distance (miles): 450
Fuel efficiency (MPG): 28
Gas price per gallon: $3.75
========================
Trip distance: 450 miles
Fuel efficiency: 28 MPG
Gallons needed: 16.07
Cost per gallon: $3.75
========================
Total fuel cost: $60.27
```

<details>
<summary>Solution</summary>

```python
# Fuel Cost Calculator

distance = float(input("Trip distance (miles): "))
mpg = float(input("Fuel efficiency (MPG): "))
gas_price = float(input("Gas price per gallon: $"))

gallons_needed = distance / mpg
total_cost = gallons_needed * gas_price

print("=" * 24)
print(f"Trip distance: {distance:.0f} miles")
print(f"Fuel efficiency: {mpg:.0f} MPG")
print(f"Gallons needed: {gallons_needed:.2f}")
print(f"Cost per gallon: ${gas_price:.2f}")
print("=" * 24)
print(f"Total fuel cost: ${total_cost:.2f}")
```

</details>

---

## Testing Your Understanding

Before moving to Week 2, make sure you can:

- [ ] Create variables with meaningful names for different data types
- [ ] Use `input()` to get data from users
- [ ] Convert input strings to numbers with `int()` and `float()`
- [ ] Perform calculations using expressions with correct operator precedence
- [ ] Format currency output with `.2f` in f-strings
- [ ] Print organized output with visual separators
- [ ] Debug common errors like variable overwriting and type mismatches

**Challenge:** Can you modify the cafe receipt to handle 5 items instead of 3? Try it without looking at the solution!

---

## Common Mistakes to Avoid

**Mistake 1: Reusing Variable Names**
```python
# Bad
item = input("Item name: ")
item = float(input("Price: "))  # Lost the name!

# Good
item_name = input("Item name: ")
item_price = float(input("Price: "))
```

**Mistake 2: Forgetting to Convert Input**
```python
# Bad
price = input("Price: ")  # This is a string!
total = price * 2  # TypeError or wrong result

# Good
price = float(input("Price: "))  # Convert to number
total = price * 2
```

**Mistake 3: Incorrect Operator Precedence**
```python
# Bad
total = price + tax * quantity  # Tax applied to quantity only

# Good
total = (price + tax) * quantity  # Tax added to price first
```

**Mistake 4: Missing Currency Formatting**
```python
# Bad
print(f"Total: ${total}")  # Might show: Total: $16.3333333

# Good
print(f"Total: ${total:.2f}")  # Shows: Total: $16.33
```

---

## What's Next?

Once you complete the cafe receipt and at least 3 of the practice problems:

1. Test each program multiple times with different inputs
2. Make sure output formatting matches the examples
3. Save your working solutions
4. Move on to Week 2 with confidence

**Remember:** These fundamentals are the building blocks for everything else in Python. Take time to master them now!

---

**Last Updated:** October 25, 2025
