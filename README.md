# 🐍 Python Learning Journey

## Preface

This document is a personal learning log and quick-reference guide covering the core building blocks of Python — from the very first concept of storing a value in a variable, all the way to scraping live data off the web. Every topic includes a working code example so the material can be read, understood, and applied immediately without needing to look anything up.

The journey is intentionally linear: each concept builds on the one before it. Variables lead to data types, data types lead to operators, operators lead to conditions, and so on — until everything comes together in real projects like a BMI calculator, a file sorter, and a web scraper.

Use this as a study companion, a revision sheet, or a starting point for your own projects.

---

## 📋 Table of Contents

1. [Variables](#1-variables)
2. [Data Types](#2-data-types)
3. [Comparison, Logical & Membership Operators](#3-comparison-logical--membership-operators)
4. [if-elif-else Statement](#4-if-elif-else-statement)
5. [For Loops and Nested For Loops](#5-for-loops-and-nested-for-loops)
6. [While Loops](#6-while-loops)
7. [Functions](#7-functions)
8. [Converting Data Types](#8-converting-data-types)
9. [BMI Calculator Project](#9-bmi-calculator-project)
10. [Automatic File Sorter](#10-automatic-file-sorter)
11. [BeautifulSoup & Requests](#11-beautifulsoup--requests)
12. [Web Scraping in Python](#12-web-scraping-in-python)

---

## 1. Variables

> A **variable** is a named container that stores a value. You create one simply by writing a name, an `=` sign, and a value. Python figures out the type automatically — no need to declare it upfront.

```python
name = "Alice"
age = 25
height = 1.68
is_student = True

print(name)       # Alice
print(age)        # 25
print(height)     # 1.68
print(is_student) # True
```

**Naming rules:**
- Use lowercase letters and underscores: `my_variable` ✅
- Cannot start with a number: ~~`1name`~~ ❌
- Cannot use reserved words: ~~`if`~~, ~~`for`~~, ~~`class`~~ ❌

---

## 2. Data Types

> Python has several built-in **data types**. Knowing which type you're working with matters because different types support different operations — you can't add a number to a string without converting it first.

```python
# String — text wrapped in quotes
name = "Alice"
print(type(name))        # <class 'str'>

# Integer — whole number, no decimal
age = 25
print(type(age))         # <class 'int'>

# Float — number with a decimal point
height = 1.68
print(type(height))      # <class 'float'>

# Boolean — only True or False
is_student = True
print(type(is_student))  # <class 'bool'>

# List — ordered, changeable collection
fruits = ["apple", "banana", "cherry"]
print(type(fruits))      # <class 'list'>

# Dictionary — stores key-value pairs
person = {"name": "Alice", "age": 25}
print(type(person))      # <class 'dict'>

# Tuple — ordered but unchangeable collection
coordinates = (10.5, 20.3)
print(type(coordinates)) # <class 'tuple'>
```

---

## 3. Comparison, Logical & Membership Operators

> **Operators** let you compare values, combine multiple conditions, and check whether something exists inside a collection. They always return `True` or `False`.

### Comparison Operators
```python
x = 10
y = 5

print(x > y)    # True  — greater than
print(x < y)    # False — less than
print(x == y)   # False — equal to
print(x != y)   # True  — not equal to
print(x >= 10)  # True  — greater than or equal
print(x <= 4)   # False — less than or equal
```

### Logical Operators
```python
age = 20
has_id = True

print(age >= 18 and has_id)  # True  — both conditions must be True
print(age < 18 or has_id)    # True  — at least one must be True
print(not has_id)            # False — flips the boolean value
```

### Membership Operators
```python
fruits = ["apple", "banana", "cherry"]

print("apple" in fruits)      # True  — item exists in the list
print("grape" not in fruits)  # True  — item does not exist

sentence = "Hello World"
print("World" in sentence)    # True  — also works on strings
```

---

## 4. if-elif-else Statement

> **Conditionals** let your program make decisions. Python checks each condition from top to bottom and runs the first block that evaluates to `True`. If none match, the `else` block is the fallback.

```python
score = 75

if score >= 90:
    print("Grade: A")
elif score >= 80:
    print("Grade: B")
elif score >= 70:
    print("Grade: C")
elif score >= 60:
    print("Grade: D")
else:
    print("Grade: F")

# Output: Grade: C
```

```python
# Practical example — login check
username = "admin"
password = "1234"

if username == "admin" and password == "1234":
    print("Access granted.")
else:
    print("Invalid credentials.")
```

---

## 5. For Loops and Nested For Loops

> A **for loop** repeats a block of code once for each item in a sequence. A **nested for loop** is simply a loop placed inside another loop — the inner loop runs to completion on every single step of the outer loop.

### Basic For Loop
```python
fruits = ["apple", "banana", "cherry"]

for fruit in fruits:
    print(fruit)

# apple
# banana
# cherry
```

### For Loop with range()
```python
# range(start, stop) — stop is excluded
for i in range(1, 6):
    print(i)

# 1  2  3  4  5
```

### Nested For Loop
```python
# Multiplication table for 2 and 3
for i in range(2, 4):           # outer loop: 2, 3
    for j in range(1, 6):       # inner loop: 1 through 5
        print(f"{i} x {j} = {i * j}")
    print("---")

# 2 x 1 = 2
# 2 x 2 = 4
# ...
# --- (divider after each outer step)
# 3 x 1 = 3
# ...
```

---

## 6. While Loops

> A **while loop** keeps running as long as its condition stays `True`. Use it when you don't know in advance how many repetitions you need — such as waiting for a user to enter valid input.

```python
count = 1

while count <= 5:
    print(f"Count: {count}")
    count += 1      # increment — this eventually makes the condition False

# Count: 1
# Count: 2
# Count: 3
# Count: 4
# Count: 5
```

```python
# Practical example — keep asking until correct password
password = ""

while password != "secret":
    password = input("Enter password: ")
    if password != "secret":
        print("Wrong. Try again.")

print("Access granted!")
```

> ⚠️ Always make sure the condition can eventually become `False`. If it never does, you create an **infinite loop** that runs forever and freezes your program.

---

## 7. Functions

> A **function** is a reusable block of code you define once with `def` and call as many times as you need. Functions keep your code organized, eliminate repetition, and make programs much easier to read and maintain.

```python
# Define a basic function
def greet(name):
    print(f"Hello, {name}!")

# Call it multiple times with different values
greet("Alice")  # Hello, Alice!
greet("Bob")    # Hello, Bob!
```

```python
# Function that returns a value
def add(a, b):
    return a + b

result = add(3, 7)
print(result)       # 10
```

```python
# Function with a default parameter value
def greet(name, greeting="Hello"):
    print(f"{greeting}, {name}!")

greet("Alice")                 # Hello, Alice!
greet("Bob", "Good morning")   # Good morning, Bob!
```

---

## 8. Converting Data Types

> **Type conversion** (casting) changes a value from one data type to another. This is essential when handling user input (always arrives as a string) or mixing numbers in calculations.

```python
# String → Integer
age = int("25")
print(age + 5)       # 30

# String → Float
price = float("9.99")
print(price * 2)     # 19.98

# Integer → String (needed to concatenate with text)
score = 100
label = "Your score: " + str(score)
print(label)         # Your score: 100

# Float → Integer (truncates — does NOT round)
y = int(9.99)
print(y)             # 9

# String → List (splits into individual characters)
letters = list("hello")
print(letters)       # ['h', 'e', 'l', 'l', 'o']
```

> ⚠️ Trying `int("hello")` will raise a `ValueError`. Always validate or check user input before converting.

---

## 9. BMI Calculator Project

> **Project:** Combine variables, user input, type conversion, functions, and conditionals to build an interactive BMI calculator.

**Formula:** `BMI = weight (kg) ÷ height (m)²`

| BMI Range | Category |
|---|---|
| Below 18.5 | Underweight |
| 18.5 – 24.9 | Normal weight |
| 25.0 – 29.9 | Overweight |
| 30.0 and above | Obese |

```python
def calculate_bmi(weight, height):
    bmi = weight / (height ** 2)
    return round(bmi, 2)

def classify_bmi(bmi):
    if bmi < 18.5:
        return "Underweight"
    elif bmi < 25:
        return "Normal weight"
    elif bmi < 30:
        return "Overweight"
    else:
        return "Obese"

# Get user input and convert from string to float
weight = float(input("Enter your weight in kg: "))
height = float(input("Enter your height in meters: "))

bmi = calculate_bmi(weight, height)
category = classify_bmi(bmi)

print(f"\nYour BMI   : {bmi}")
print(f"Category   : {category}")
```

**Example output:**
```
Enter your weight in kg: 70
Enter your height in meters: 1.75

Your BMI   : 22.86
Category   : Normal weight
```

---

## 10. Automatic File Sorter

> **Project:** Use Python's `os` and `shutil` modules with loops and dictionaries to automatically move files in a folder into organized subfolders by file type.

```python
import os
import shutil

# Folder you want to sort
folder_path = r"C:\Users\YourName\Downloads"

# Map category names to their file extensions
file_types = {
    "Images":    [".jpg", ".jpeg", ".png", ".gif", ".svg", ".webp"],
    "Documents": [".pdf", ".docx", ".doc", ".txt", ".xlsx", ".pptx"],
    "Videos":    [".mp4", ".mov", ".avi", ".mkv"],
    "Audio":     [".mp3", ".wav", ".aac"],
    "Archives":  [".zip", ".rar", ".tar", ".gz"],
    "Code":      [".py", ".js", ".html", ".css", ".json"],
}

for filename in os.listdir(folder_path):
    file_path = os.path.join(folder_path, filename)

    # Skip subfolders — only process files
    if os.path.isdir(file_path):
        continue

    # Extract the file extension (e.g. ".pdf")
    _, ext = os.path.splitext(filename)
    ext = ext.lower()

    # Match extension to a category and move the file
    moved = False
    for folder_name, extensions in file_types.items():
        if ext in extensions:
            dest_folder = os.path.join(folder_path, folder_name)
            os.makedirs(dest_folder, exist_ok=True)   # create if missing
            shutil.move(file_path, dest_folder)
            print(f"Moved: {filename}  →  {folder_name}/")
            moved = True
            break

    # Unrecognized types go to "Others"
    if not moved:
        other_folder = os.path.join(folder_path, "Others")
        os.makedirs(other_folder, exist_ok=True)
        shutil.move(file_path, other_folder)
        print(f"Moved: {filename}  →  Others/")
```

---

## 11. BeautifulSoup & Requests

> `requests` downloads the raw HTML of any webpage. `BeautifulSoup` parses that HTML into a tree you can navigate, search, and extract data from. Together they form the foundation of Python web scraping.

### Installation
```bash
pip install requests beautifulsoup4
```

### HTTP Status Codes
| Code | Meaning |
|---|---|
| `200` | ✅ OK — page returned successfully |
| `204` | ⚠️ No Content — request worked but no data came back |
| `400` | ❌ Bad Request — something wrong with how you asked |
| `404` | ❌ Not Found — server couldn't locate the page |

```python
import requests

response = requests.get("https://example.com")
print(response.status_code)   # 200 = all good
```

### Common HTML Tags
| Tag | What it represents |
|---|---|
| `<html>` | Root element of the entire page |
| `<body>` | All visible page content lives here |
| `<div>` | Generic block container, used for layout sections |
| `<p>` | A paragraph of text |
| `<table>` | A data table |
| `<tr>` | A table row |
| `<th>` | A table header cell |
| `<td>` | A table data cell |
| `href` | Attribute inside `<a>` tags — holds the link URL |
| `class="col-md-12"` | Bootstrap class — often wraps the main page content |

### find() vs find_all()
```python
from bs4 import BeautifulSoup
import requests

page = requests.get("https://example.com")
soup = BeautifulSoup(page.text, 'html.parser')

# find() — returns the FIRST matching element only
first_p = soup.find('p')
print(first_p.text.strip())

# find_all() — returns a LIST of ALL matching elements
all_p = soup.find_all('p')
for p in all_p:
    print(p.text.strip())    # loop first, THEN call .text.strip()
```

> ⚠️ **Do NOT** call `.text` or `.strip()` directly on `find_all()` — it returns a **list**, not a single element. Always loop through the list first, then extract text from each individual item.

```python
# ❌ WRONG — crashes with AttributeError
text = soup.find_all('p').text.strip()

# ✅ CORRECT — loop first, then extract
for item in soup.find_all('p'):
    print(item.text.strip())
```

---

## 12. Web Scraping in Python

> **Web scraping** is automating the extraction of data from websites. The full pipeline combines `requests` to fetch the page, `BeautifulSoup` to find and parse the data, and `pandas` to store and export it as a clean CSV.

### Full Pipeline — Scraping a Wikipedia Table
```python
from bs4 import BeautifulSoup
import requests
import pandas as pd

# Step 1 — Spoof a real browser to avoid being blocked
headers = {
    'User-Agent': 'Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36'
}

# Step 2 — Fetch the page
url = 'https://en.wikipedia.org/wiki/List_of_largest_companies_in_the_United_States_by_revenue'
page = requests.get(url, headers=headers)
soup = BeautifulSoup(page.text, 'html.parser')

# Step 3 — Find the right table (pages can have many)
table = soup.find_all('table')[0]

# Step 4 — Extract column headers from <th> tags
world_titles = table.find_all('th')
world_table_titles = [title.text.strip() for title in world_titles]

# Step 5 — Build an empty DataFrame with those column names
df = pd.DataFrame(columns=world_table_titles)

# Step 6 — Loop through rows <tr>, skip header row at index [0]
column_data = table.find_all('tr')
for row in column_data[1:]:
    row_data = row.find_all('td')
    individual_row_data = [data.text.strip() for data in row_data]
    length = len(df)
    df.loc[length] = individual_row_data

# Step 7 — Preview and export to CSV
print(df.head())
df.to_csv('Companies.csv', index=False)
```

### Scraping by Class or Attribute
```python
# Find a div with a specific CSS class
content = soup.find('div', class_='col-md-12')
print(content.text.strip())

# Extract all hyperlinks (href values) from a page
links = soup.find_all('a')
for link in links:
    print(link.get('href'))
```

### The Scraping Mental Model
```
URL
 ↓  requests.get(url, headers=headers)
Raw HTML string
 ↓  BeautifulSoup(page.text, 'html.parser')
Navigable HTML tree
 ↓  .find() / .find_all()
Target HTML elements
 ↓  .text.strip()  (inside a loop if find_all)
Clean text data
 ↓  pd.DataFrame()  +  df.loc[length] = row
Structured table
 ↓  df.to_csv('file.csv', index=False)
CSV file  ✅
```

---

## 💡 Concepts at a Glance

| # | Topic | Key Takeaway |
|---|---|---|
| 1 | Variables | Named containers — `name = "Alice"` |
| 2 | Data Types | `str`, `int`, `float`, `bool`, `list`, `dict`, `tuple` |
| 3 | Operators | Compare (`==`, `>`), combine (`and`, `or`), check (`in`) |
| 4 | if-elif-else | First `True` block wins; `else` is the fallback |
| 5 | For Loops | Iterate sequences; nest for multi-dimensional data |
| 6 | While Loops | Repeat until a condition becomes `False` |
| 7 | Functions | `def name(): return value` — define once, reuse anywhere |
| 8 | Type Conversion | `int()`, `float()`, `str()`, `list()` |
| 9 | BMI Calculator | Input + casting + functions + conditionals |
| 10 | File Sorter | `os` + `shutil` + loops + dictionaries |
| 11 | BeautifulSoup | `find()` = first match · `find_all()` = list of all matches |
| 12 | Web Scraping | requests → BeautifulSoup → pandas → CSV |

---

> 💬 *Examples are kept short on purpose — a small working snippet beats a large confusing one every time. Once a concept clicks, extend the example with your own data and ideas.*
