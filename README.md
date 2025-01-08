# python-programming-questions
Questions by Shaileshwar


Summary of Questions

1.Extract and Combine Strings

Type: Function type, Data types

Description: Concatenate the first element of each non-empty list from a dictionary's values into a single string separated by spaces.

Example: combine_strings({"name": ["Alice"], "city": ["Paris"]}) returns "Alice Paris".


2.Calculate Total Expenditure

Type: Function type, Data Processing

Description: Compute total expenditure by multiplying corresponding prices and quantities, summing the result.

Example: calculate_expenditure([2.5, 4.0], [2, 3]) returns 15.5.


3.Filter and Format Student Records

Type: Input-output based, Data Processing I/O

Description: Read student records from input, output names and grades for students scoring above 60.

Example: Input "Alice 75\nBob 60\nCharlie 85", output "Alice 75\nCharlie 85".


4.Detect Valid Hexadecimal Colors

Type: Input-output based, Problem-solving

Description: Identify and print unique valid hexadecimal color codes from input lines in the order of appearance.

Example: Input "Colors: #abc, #123456. Invalid: #12345g", output "#abc\n#123456".


---
title: Extract and Combine Strings
---

# Problem Statement

Implement a function `combine_strings(data: dict) -> str` that takes a dictionary where keys are strings and values are lists of strings. The function should return a single string formed by concatenating the first element of each list corresponding to the keys, separated by a space. If any list is empty, skip that key.

**Example**
```py3
combine_strings({"name": ["Alice", "Bob"], "city": ["Paris", "Berlin"], "country": ["France"]})  # "Alice Paris France"
combine_strings({"fruit": [], "color": ["Red"]})  # "Red"
```

# Solution

```py3 test.py -r 'python test.py'
<prefix>
# some prefix
</prefix>
<template>
def combine_strings(data: dict) -> str:
    '''
    Concatenate first elements of lists from the dictionary.

    Arguments:
    data: dict - dictionary with strings as keys and lists of strings as values.

    Return: str - concatenated string.
    '''
    <los>...</los>
    <sol>return ' '.join(data[key][0] for key in data if data[key])</sol>
    test = <los>...</los><sol>'test'</sol>
</template>
<suffix>
# some suffix
</suffix>
<suffix_invisible>
{% include '../function_type_and_modify_check_suffix.py.jinja' %}
</suffix_invisible>
```

# Public Test Cases

## Input 1

```
is_equal(
    combine_strings({"animal": ["Cat"], "bird": ["Eagle"]}),
    "Cat Eagle"
)
```

## Output 1

```
"Cat Eagle"
```

## Input 2

```
is_equal(
    combine_strings({"fruit": ["Apple"], "empty": []}),
    "Apple"
)
```

## Output 2

```
"Apple"
```

---

title: Calculate Total Expenditure
---

# Problem Statement

Write a function `calculate_expenditure(prices: list[float], quantities: list[int]) -> float` that calculates the total expenditure by multiplying corresponding prices and quantities, then summing them. If the lists are of unequal length, consider only the minimum length.

**Example**
```py3
calculate_expenditure([2.5, 4.0, 1.0], [3, 2, 5])  # 15.5
calculate_expenditure([10.0], [5, 2])  # 50.0
```

# Solution

```py3 test.py -r 'python test.py'
<prefix>
# some prefix
</prefix>
<template>
def calculate_expenditure(prices: list[float], quantities: list[int]) -> float:
    '''
    Calculate total expenditure.

    Arguments:
    prices: list[float] - list of item prices.
    quantities: list[int] - list of quantities for each item.

    Return: float - total expenditure.
    '''
    <los>...</los>
    <sol>return sum(p * q for p, q in zip(prices, quantities))</sol>
    test = <los>...</los><sol>'test'</sol>
</template>
<suffix>
# some suffix
</suffix>
<suffix_invisible>
{% include '../function_type_and_modify_check_suffix.py.jinja' %}
</suffix_invisible>
```

# Public Test Cases

## Input 1

```
is_equal(
    calculate_expenditure([5.0, 3.0], [2, 4]),
    22.0
)
```

## Output 1

```
22.0
```

## Input 2

```
is_equal(
    calculate_expenditure([1.5, 2.5], [4, 3]),
    12.0
)
```

## Output 2

```
12.0
```

---

title: Filter and Format Student Records
---

# Problem Statement

Implement a program that reads student records from standard input and prints students with a grade above 60. Each input line represents a record as `"name grade"`. Output each valid record on a new line.

**Example**

Input:
```
Alice 75
Bob 60
Charlie 85
```

Output:
```
Alice 75
Charlie 85
```

# Solution

```py3 test.py -r 'python test.py'
<prefix>
# some prefix
</prefix>
<template>
import sys

def filter_students() -> None:
    '''
    Read student records and print those with grade > 60.
    '''
    for line in sys.stdin:
        name, grade = line.rsplit(' ', 1)
        if int(grade) > 60:
            print(line.strip())
</template>
<suffix>
# some suffix
</suffix>
<suffix_invisible>
{% include '../input_output_suffix.py.jinja' %}
</suffix_invisible>
```

# Public Test Cases

Input:
```
John 50
Jane 70
```

Output:
```
Jane 70
```

---

title: Detect Valid Hexadecimal Colors
---

# Problem Statement

Write a program that takes multiple lines of input and prints all valid hexadecimal color codes found in each line. A valid color code starts with a `#` followed by exactly 3 or 6 hexadecimal characters (`0-9`, `a-f`, `A-F`). Print each unique valid color code in the order of appearance.

**Example**

Input:
```
Background color: #AABBCC, text color: #000.
Invalid: #12345g, valid: #1a1.
```

Output:
```
#AABBCC
#000
#1a1
```

# Solution

```py3 test.py -r 'python test.py'
<prefix>
# some prefix
</prefix>
<template>
import re
import sys

def find_hex_colors() -> None:
    '''
    Print unique valid hexadecimal color codes.
    '''
    pattern = re.compile(r'#(?:[0-9a-fA-F]{3}|[0-9a-fA-F]{6})\b')
    seen = set()
    for line in sys.stdin:
        for match in pattern.findall(line):
            if match not in seen:
                print(match)
                seen.add(match)
</template>
<suffix>
# some suffix
</suffix>
<suffix_invisible>
{% include '../input_output_suffix.py.jinja' %}
</suffix_invisible>
```

# Public Test Cases

Input:
```
Colors: #abc, #123456.
Invalid colors: #ggg, #fffff.
```

Output:
```
#abc
#123456
```

