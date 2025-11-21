
# Sketching Flow

Date: Thursday, November 20, 2025, 3 PM PST
Course: CS101 – AAS in AI Software Engineering
Week: 2, Lesson 5

---

## Key Idea

**Sketching flow** means writing out every possible decision and outcome in a simple table—before you ever touch code. By mapping out all the logic this way, you reduce bugs and make your if/elif/else code much easier to write.

---

## Flow Table Example

This technique uses a table to match each situation to an action:

| light_color | action |
| --- | --- |
| red | brake hard |
| yellow | slow |
| green | zoom |

- *Tip*: Copy this as a comment in your editor to guide your code.

---

## Steps to Sketch Flow

1. **Write the table as a Python comment**

   ```python
   # flow description: 
   # | light_color | action   |
   # |-------------|----------| 
   # | red         | brake hard| 
   # | yellow      | slow     |
   # | green       | zoom     | 
   ```

2. **Translate the logic into code**

   ```python
   light_color = "red"  # Try "yellow" or "green"  
   if light_color == "red":     
       print("brake hard") 
   elif light_color == "yellow":     
       print("slow") 
   else:     
       print("zoom")
   ```

---

## Expanding to Multiple Conditions

You can use two or more variables by making a wider table:

| distance | speed | warning |
| --- | --- | --- |
| close | fast | high |
| close | slow | low |
| far | fast | medium |
| far | slow | low |

*Turn each row into an if/elif/else condition:*

```python
distance = "close" speed = "fast"  
if distance == "close" and speed == "fast":     
    print("high") 
elif distance == "close" and speed == "slow":     
    print("low") 
elif distance == "far" and speed == "fast":     
    print("medium") 
else:     
    print("low") 
```

---

## Testing Multiple Scenarios

To check lots of cases quickly, use a loop:

```python
distance = "close" 
speeds = ["fast", "slow"]  
for speed in speeds:     
    print("speed:", speed)     
if distance == "close" and speed == "fast":         
    print("high")     
else:         
    print("low") 
```

---

## Membership Example

Test if a keyword is present:

```python
zone = "school zone" 
if "school" in zone:     
print("extra caution") 
```

---

## Review/Practice

- Use tables to plan out logic before you write code.

- Practice turning each situation in your table into a clear if/elif/else.

- Try extending your tables and code to more variables.

**Key takeaway:** Organizing your decision-making in tables makes your final code much more reliable and easy to read.