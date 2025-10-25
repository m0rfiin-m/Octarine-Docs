# Week 1 Review: Cafe Receipt Calculator

**Date:** October 25, 2025  
**Course:** PY101 - Introduction to Python  
**Week:** 1, End of Week Review  
**Status:** ✅ PASSED (+30 Points)

## 🎯 Assignment Requirements

This review tests everything from Lessons 1-15. You must complete this before advancing to Week 2.

**Core Requirements:**
- Exactly **2 items** (not 3!)
- **2 functions required**: one for item total, one for overall total
- Descriptive input prompts for user guidance
- All prices formatted to **2 decimal places**
- Clean, readable code

---

## 📋 The Given Example

```
Item: Apple
Price: 1.50$
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

## ❌ Your First Attempt (The Problems)

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

**Critical Issues:**

1. ❌ **No functions** - Assignment requires 2 functions
2. ❌ **Variable overwriting** - `item1` used for name, price, AND quantity (each overwrites the previous)
3. ❌ **Missing calculations** - Never multiplied price × quantity
4. ❌ **No price formatting** - Prices need `.2f` for currency display
5. ❌ **3 items instead of 2** - Spec calls for exactly 2 items
6. ❌ **Incomplete code** - Items 2 and 3 never calculated or printed
7. ❌ **No proper prompts** - Input prompts missing spacing and clarity

**Key Lesson:** Each variable can only hold ONE value at a time. When you assign a new value, the old one is gone!

---

## ✅ Final Passing Solution

```python
# Mini receipt calculator

def calculate_item_total(price, quantity):
    """Calculate total for a single item"""
    return price * quantity

def calculate_overall_total(item1_total, item2_total):
    """Calculate the overall cart total"""
    return item1_total + item2_total

# Item 1
item1_name = input("Item 1: ")
item1_price = float(input("Price of item 1: $"))
item1_quantity = int(input("Quantity of item 1: "))
item1_total = calculate_item_total(item1_price, item1_quantity)

print(f"Item: {item1_name}")
print(f"Price: {item1_price:.2f}$")
print(f"Quantity: {item1_quantity}")
print(f"Total price: {item1_total:.2f}$")
print("-------------------")

# Item 2
item2_name = input("Item 2: ")
item2_price = float(input("Price of item 2: $"))
item2_quantity = int(input("Quantity of item 2: "))
item2_total = calculate_item_total(item2_price, item2_quantity)

print(f"Item: {item2_name}")
print(f"Price: {item2_price:.2f}$")
print(f"Quantity: {item2_quantity}")
print(f"Total price: {item2_total:.2f}$")

# Calculate overall cart total
total_cart = calculate_overall_total(item1_total, item2_total)

print("########################")
print(f"Total cart price: {total_cart:.2f}$")
print("########################")
```

**What Makes This Pass:**

✅ **Two functions implemented** - `calculate_item_total()` and `calculate_overall_total()`  
✅ **Descriptive prompts** - Users know what to enter  
✅ **Proper formatting** - All prices show 2 decimals with `.2f`  
✅ **Exactly 2 items** - Follows spec requirement  
✅ **Separate variables** - Each data point has its own variable  
✅ **Complete calculations** - Multiplies price × quantity correctly  
✅ **Clean, organized code** - Easy to read and understand

---

## 📚 Concepts Applied (Lessons Referenced)

### From Lesson 1: Printing and Comments
- `print()` for output display
- F-strings for formatted text: `f"Item: {item1_name}"`
- String repetition: `"#" * 24` for separators

### From Lesson 2: Variables, Types, and String Essentials
- Variables for storing data: `item1_name`, `item1_price`, `item1_quantity`
- Different data types: strings (`str`), decimals (`float`), integers (`int`)
- Type checking with `type()` when debugging

### From Lesson 3: Expressions and Operator Precedence
- Mathematical expressions: `price * quantity`
- Operator precedence in calculations

### From Lesson 8: Rounding and Money Format
- Currency formatting: `.2f` displays exactly 2 decimal places
- Difference between `round()` and formatted display

### From Lesson 9: Getting Input from Users
- `input()` function for user interaction
- Type conversion: `float(input())` and `int(input())`
- Descriptive prompts for user guidance

### From Lesson 10: Functions I
- **Function definition:** `def calculate_item_total(price, quantity):`
- **Parameters:** Values passed into functions
- **Return values:** Functions send back calculated results
- **Function calls:** Using functions to avoid code repetition

---

## 🎓 Grader Feedback Analysis

### ✅ Strengths (What You Did Right)
- Uses two clear functions for item and overall totals
- Captures all required inputs and prints every receipt element
- Displays prices and totals with two decimal places
- Code is clean and easy to read

### 💡 Areas for Improvement (For Next Time)
- Align columns more neatly for a professional receipt
- Consider grouping the two item printouts in a reusable function to avoid repetition

**Advanced Improvement Example:**
```python
def print_item_receipt(name, price, quantity, total):
    """Reusable function to print item details"""
    print(f"Item: {name}")
    print(f"Price: {price:.2f}$")
    print(f"Quantity: {quantity}")
    print(f"Total price: {total:.2f}$")
    print("-------------------")

# Then call it for each item:
print_item_receipt(item1_name, item1_price, item1_quantity, item1_total)
print_item_receipt(item2_name, item2_price, item2_quantity, item2_total)
```

---

## 🔧 Additional Practice Problems

Practice the same concepts with different scenarios. Each problem includes:
- Clear requirements
- Lesson hints to guide you
- Example output
- Complete solution (try first before looking!)

### Practice 1: Restaurant Bill with Functions

**Problem:**  
Calculate a restaurant bill with tax and tip using functions.

**📖 Lesson Hints:**
- **Lesson 10:** Use functions to calculate tax and tip separately
- **Lesson 8:** Format all currency to 2 decimals
- **Lesson 3:** Remember operator precedence for calculations

**Requirements:**
- Create a function `calculate_tax(amount, rate)` that returns tax
- Create a function `calculate_tip(amount, rate)` that returns tip
- Get meal cost from user
- Calculate 8.5% tax
- Calculate 18% tip (on original amount, before tax)
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
<summary>💡 Solution</summary>

```python
# Restaurant Bill Calculator with Functions

def calculate_tax(amount, rate):
    """Calculate tax based on amount and rate"""
    return amount * rate

def calculate_tip(amount, rate):
    """Calculate tip based on amount and rate"""
    return amount * rate

# Get input
meal_cost = float(input("Enter meal cost: $"))

# Define rates
tax_rate = 0.085
tip_rate = 0.18

# Calculate using functions
tax = calculate_tax(meal_cost, tax_rate)
tip = calculate_tip(meal_cost, tip_rate)
total = meal_cost + tax + tip

# Display receipt
print("-------------------")
print(f"Subtotal: ${meal_cost:.2f}")
print(f"Tax (8.5%): ${tax:.2f}")
print(f"Tip (18%): ${tip:.2f}")
print("-------------------")
print(f"Total: ${total:.2f}")
```

</details>

---

### Practice 2: Shipping Calculator with Functions

**Problem:**  
Calculate shipping cost with multiple components using functions.

**📖 Lesson Hints:**
- **Lesson 10:** Break calculations into separate functions
- **Lesson 3:** Use expressions to combine base rate + charges
- **Lesson 1:** Use string repetition for visual separators

**Requirements:**
- Create `calculate_weight_charge(weight, rate)` function
- Create `calculate_distance_charge(distance, rate)` function
- Base rate: $5.00 (constant)
- Per pound: $0.50
- Per mile: $0.10
- Get weight and distance from user
- Display all components and total

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
<summary>💡 Solution</summary>

```python
# Shipping Cost Calculator with Functions

def calculate_weight_charge(weight, rate):
    """Calculate charge based on weight"""
    return weight * rate

def calculate_distance_charge(distance, rate):
    """Calculate charge based on distance"""
    return distance * rate

# Get input
weight = float(input("Package weight (lbs): "))
distance = float(input("Shipping distance (miles): "))

# Define rates
base_rate = 5.00
per_pound = 0.50
per_mile = 0.10

# Calculate using functions
weight_charge = calculate_weight_charge(weight, per_pound)
distance_charge = calculate_distance_charge(distance, per_mile)
total = base_rate + weight_charge + distance_charge

# Display breakdown
print("=" * 24)
print(f"Base rate: ${base_rate:.2f}")
print(f"Weight charge: ${weight_charge:.2f}")
print(f"Distance charge: ${distance_charge:.2f}")
print("=" * 24)
print(f"Total shipping: ${total:.2f}")
```

</details>

---

### Practice 3: Movie Ticket Sales with Functions

**Problem:**  
Calculate ticket sales for different customer types using functions.

**📖 Lesson Hints:**
- **Lesson 10:** One function can be reused for different ticket types
- **Lesson 2:** Use descriptive variable names for each ticket type
- **Lesson 8:** Format all currency consistently

**Requirements:**
- Create `calculate_ticket_revenue(quantity, price)` function
- Create `calculate_total_revenue(adult_rev, child_rev, senior_rev)` function
- Adult tickets: $25.00 each
- Child tickets: $15.00 each
- Senior tickets: $20.00 each
- Get quantities sold for each type
- Display breakdown and grand total

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
<summary>💡 Solution</summary>

```python
# Movie Ticket Sales Calculator with Functions

def calculate_ticket_revenue(quantity, price):
    """Calculate revenue for one ticket type"""
    return quantity * price

def calculate_total_revenue(adult_rev, child_rev, senior_rev):
    """Calculate total revenue from all ticket types"""
    return adult_rev + child_rev + senior_rev

# Get input
adult_qty = int(input("Adult tickets sold: "))
child_qty = int(input("Child tickets sold: "))
senior_qty = int(input("Senior tickets sold: "))

# Define prices
adult_price = 25.00
child_price = 15.00
senior_price = 20.00

# Calculate using functions
adult_revenue = calculate_ticket_revenue(adult_qty, adult_price)
child_revenue = calculate_ticket_revenue(child_qty, child_price)
senior_revenue = calculate_ticket_revenue(senior_qty, senior_price)
total_revenue = calculate_total_revenue(adult_revenue, child_revenue, senior_revenue)

# Display results
print("=" * 24)
print(f"Adult tickets: {adult_qty} x ${adult_price:.2f} = ${adult_revenue:.2f}")
print(f"Child tickets: {child_qty} x ${child_price:.2f} = ${child_revenue:.2f}")
print(f"Senior tickets: {senior_qty} x ${senior_price:.2f} = ${senior_revenue:.2f}")
print("=" * 24)
print(f"Total revenue: ${total_revenue:.2f}")
```

</details>

---

### Practice 4: Grade Calculator with Functions

**Problem:**  
Calculate average grade from multiple assignments using functions.

**📖 Lesson Hints:**
- **Lesson 10:** Create a function that accepts multiple scores
- **Lesson 3:** Division for average calculation
- **Lesson 8:** Round average to 2 decimal places

**Requirements:**
- Create `calculate_average(score1, score2, score3)` function
- Get 3 assignment scores from user
- Calculate and display average
- Show all individual scores and the computed average

**Note:** Letter grades will come in Week 2 when you learn conditionals!

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
<summary>💡 Solution</summary>

```python
# Grade Calculator with Functions

def calculate_average(score1, score2, score3):
    """Calculate average of three scores"""
    return (score1 + score2 + score3) / 3

# Get input
assignment1 = float(input("Assignment 1 score: "))
assignment2 = float(input("Assignment 2 score: "))
assignment3 = float(input("Assignment 3 score: "))

# Calculate using function
average = calculate_average(assignment1, assignment2, assignment3)

# Display results
print("=" * 24)
print(f"Assignment 1: {assignment1:.0f}")
print(f"Assignment 2: {assignment2:.0f}")
print(f"Assignment 3: {assignment3:.0f}")
print("=" * 24)
print(f"Average: {average:.2f}")
```

</details>

---

### Practice 5: Road Trip Fuel Cost with Functions

**Problem:**  
Calculate fuel cost for a road trip using functions.

**📖 Lesson Hints:**
- **Lesson 10:** Separate functions for gallons needed and total cost
- **Lesson 6:** Division for calculating gallons
- **Lesson 8:** Format fuel cost to 2 decimals

**Requirements:**
- Create `calculate_gallons_needed(distance, mpg)` function
- Create `calculate_fuel_cost(gallons, price_per_gallon)` function
- Get trip distance, car MPG, and gas price from user
- Calculate gallons needed and total cost
- Display all information in organized format

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
<summary>💡 Solution</summary>

```python
# Road Trip Fuel Cost Calculator with Functions

def calculate_gallons_needed(distance, mpg):
    """Calculate gallons needed for trip"""
    return distance / mpg

def calculate_fuel_cost(gallons, price_per_gallon):
    """Calculate total fuel cost"""
    return gallons * price_per_gallon

# Get input
distance = float(input("Trip distance (miles): "))
mpg = float(input("Fuel efficiency (MPG): "))
gas_price = float(input("Gas price per gallon: $"))

# Calculate using functions
gallons_needed = calculate_gallons_needed(distance, mpg)
total_cost = calculate_fuel_cost(gallons_needed, gas_price)

# Display results
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

## 🎯 Self-Assessment Checklist

Before moving to Week 2, verify you can:

**Functions (Lesson 10):**
- [ ] Define functions with `def function_name(parameters):`
- [ ] Use `return` to send values back from functions
- [ ] Call functions and use their returned values
- [ ] Create functions that accept multiple parameters

**Variables & Types (Lesson 2):**
- [ ] Create variables with meaningful, descriptive names
- [ ] Understand the three core types: `int`, `float`, `str`
- [ ] Avoid variable name reuse/overwriting

**User Input (Lesson 9):**
- [ ] Use `input()` with descriptive prompts
- [ ] Convert strings to numbers with `int()` and `float()`
- [ ] Handle different data types appropriately

**Calculations (Lesson 3):**
- [ ] Write expressions with correct operator precedence
- [ ] Use parentheses to control evaluation order
- [ ] Multiply, divide, add, and subtract correctly

**Formatting (Lessons 1, 8):**
- [ ] Format currency with `.2f` in f-strings
- [ ] Use f-strings for variable interpolation: `f"text {variable}"`
- [ ] Create visual separators with string repetition

**Debugging:**
- [ ] Identify and fix variable overwriting issues
- [ ] Recognize type conversion errors
- [ ] Debug missing calculations or incomplete code

---

## ⚠️ Common Mistakes Reference

### Mistake 1: Variable Overwriting
```python
# ❌ Bad: Each assignment erases the previous value
item = input("Item name: ")
item = float(input("Price: "))  # Lost the name!
item = int(input("Quantity: "))  # Lost the price!

# ✅ Good: Separate variables for each piece of data
item_name = input("Item name: ")
item_price = float(input("Price: "))
item_quantity = int(input("Quantity: "))
```

### Mistake 2: Missing Type Conversion
```python
# ❌ Bad: Input is always a string
price = input("Price: ")
total = price * 2  # TypeError or wrong result!

# ✅ Good: Convert to appropriate numeric type
price = float(input("Price: "))
total = price * 2
```

### Mistake 3: No Functions When Required
```python
# ❌ Bad: Inline calculations (when spec requires functions)
item1_total = item1_price * item1_quantity
total_cart = item1_total + item2_total

# ✅ Good: Use functions as required
def calculate_item_total(price, quantity):
    return price * quantity

item1_total = calculate_item_total(item1_price, item1_quantity)
```

### Mistake 4: Missing Currency Formatting
```python
# ❌ Bad: Inconsistent decimal places
print(f"Price: {price}$")  # Might show: 1.5$ or 1.333333$

# ✅ Good: Always 2 decimals for currency
print(f"Price: {price:.2f}$")  # Shows: 1.50$ or 1.33$
```

### Mistake 5: Wrong Number of Items
```python
# ❌ Bad: 3 items when spec says 2
# (Processing item1, item2, AND item3)

# ✅ Good: Follow spec exactly
# (Only process item1 and item2)
```

---

## 🚀 Next Steps

**You've completed Week 1!** Here's what to do next:

1. ✅ **Review your passing solution** - Make sure you understand every line
2. 📝 **Complete at least 3 practice problems** - Build muscle memory
3. 🔄 **Try variations** - What if there were 4 items? Different calculations?
4. 🎓 **Reflect on feedback** - Consider the "areas for improvement" suggestions
5. ➡️ **Move to Week 2** - You're ready for the next challenge!

**Pro Tip:** The concepts you learned this week (variables, functions, input, formatting) are the foundation of EVERYTHING in programming. Time spent mastering them now saves hours of confusion later.

---

**Grade:** PASSED ✅ (+30 points)  
**Last Updated:** October 25, 2025
