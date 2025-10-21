# When Solving Expressions Rules

Multiplication * and Division / are handled before Addition + and Subtraction - in Python.

Example: print(7 + 6 * 3) would give 25 because Multiplication is handled first
then Addition.

When you have operators at the same priority—like + and - together—the
calculation goes left to right. But * and / will always win over + and -.

How you can control the order using parentheses Example: total = (price + tax) *
qty If instead you write total = price + tax* qty, you get a different total.

Example: price = 3, tax = 2, qty = 4
print((3 + 2) *4) = 20

print(3 + 2* 4) = 11

Example: print("ha" * 2 + "!") = haha! print("ha" + 2) Error: Traceback (most
recent call last): TypeError: can only concatenate str (not "int") to str

Example: print("ha" * "ha") Results in Error: Traceback (most recent call last):
TypeError: can't multiply sequence by non-int of type 'str'

Rule: is you can only multiply a string by an integer, not by another string. If
not will result in error.

So with strings:

+ joins strings
+ repeats strings, but only with integers
