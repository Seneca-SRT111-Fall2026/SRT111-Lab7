<h1 align="center">SRT111 Lab 7 - Fall 2026</h1>

<p align="center">
<b>Prepared by:</b> Tiayyba Riaz<br>
<b>Total Marks:</b> 10<br>
<b>Percentage Towards Final Grade:</b> 2%
</p>

In Lab 6, you used NumPy arrays to do fast maths on numbers. Real data rarely arrives as a plain grid of numbers, though. It comes as a table: IP addresses next to ports and timestamps, student names next to courses and grades. In the first part of this lab, you will work with **Pandas**, the Python library for tabular data. Pandas is built on top of NumPy and gives you two structures: the **Series** (one labelled column) and the **DataFrame** (a whole table). You will create them, inspect them, and then filter, sort and group them to answer questions about the data.

In the second part, you will act as a **security analyst**. You will load a small **firewall log** from a CSV file, use your **student ID** to pick your own sample of events, and answer a few simple questions about it with Pandas. Then you will use **Matplotlib** to turn numbers into pictures: line plots, scatter plots, bar charts and histograms, and finally a figure with two charts of your own firewall data. Every chart is **saved to a PNG file** with an exact file name, so your work can be checked from your GitHub repository without any screenshots.

You will continue to use functions and a `main()` function to organize your programs, as practised in Labs 4 to 6.

The lab is divided into two components:

- **Part A: In-Class Lab** (must be completed during the scheduled lab period and demonstrated to the professor for grading).
- **Part B: Take-Home Lab** (can be completed independently after the scheduled class and is submitted as a link to your GitHub repository).

## Academic Integrity and Use of AI

This lab is intended to assess your individual understanding of Python programming. You may use AI tools (e.g., ChatGPT, Copilot, Gemini) to help explain concepts, syntax, or error messages. However, all submitted code must be your own work, and you must be able to explain your solution if asked by the professor.

Submitting copied, shared, or AI-generated solutions as your own work may result in a grade of zero and may be handled according to the College Academic Integrity Policy.

## Lab Objectives

By the end of this lab, you should be able to:

- Explain the role of Pandas in data analysis and the difference between a Series and a DataFrame.
- Create a Series from a list, a NumPy array and a dictionary, and give it a name.
- Create a DataFrame from a dictionary of lists and read one from a CSV file with `pd.read_csv()`.
- Inspect data with `head()` and `shape`.
- Select data by label with `[]` and `loc`, and by position with `iloc`.
- Filter rows with a condition, sort with `sort_values()`, count with `value_counts()`, and average groups with `groupby()`.
- Load a CSV file with `pd.read_csv()` and answer simple questions about your own sample of it.
- Create line plots, bar charts, scatter plots and histograms with Matplotlib.
- Add titles, axis labels, legends, grid lines, colours, markers and line styles to a plot.
- Arrange several plots in one figure with `plt.subplot()` and save every figure with `plt.savefig()`.

## Required Comment Header

For every script created in this lab include the following comment block at the top of the file/cell.

```python
# Author: Your Name
# Date: YYYY-MM-DD
# Purpose: Brief description of what the program does.
```

## Data Files

| File | Used in | Where it comes from |
|---|---|---|
| `security_log.csv` | Tasks 4 and 7 | Download it from Blackboard (Lab 7 starter files) and save it in your `Lab07` folder. |

`security_log.csv` is a small firewall log: 300 connection attempts to a company network, one event per line. It was made up for this course, so the events are not real. It has 6 columns:

| Column | Meaning | Example |
|---|---|---|
| `EventID` | Event number, from 1 to 300 | `2` |
| `Hour` | Hour of the day, from `0` (midnight) to `23` | `0` |
| `SourceIP` | IP address that tried to connect | `192.0.2.77` |
| `Service` | What it tried to reach: `HTTPS`, `HTTP`, `DNS`, `SSH` or `RDP` | `SSH` |
| `Action` | What the firewall did: `ALLOWED` or `BLOCKED` | `BLOCKED` |
| `Bytes` | Amount of data transferred | `183` |

Do not edit `security_log.csv`.

### Your Own Data: Using Your Student ID

In Tasks 4 and 7, every student works with a **different** sample of 50 events from the log. Your sample is picked using your **9-digit Seneca student ID**, so your numbers and charts will be different from everyone else's.

The starter code for Tasks 4 and 7 already contains everything needed to load the file and pick your sample. You only change **one line**:

```python
STUDENT_ID = 123456789      # replace with your own 9-digit student ID
```

- `load_log()` (given) reads the CSV file into a DataFrame. If the file is missing, it prints an error and returns `None`.
- `select_my_events()` (given) uses `sample()` to pick 50 random rows. The `random_state` number decides **which** rows are picked: the same number always gives the same rows, so your student ID always gives you the same 50 events.
- **First**, run your task with the example ID `123456789` and compare your output with the expected output in this README. When it matches, your code is correct.
- **Then** change `123456789` to your own student ID (the same in both files), run the script again, and push that version. Work submitted with the example ID, or with an ID that is not yours, receives **zero** for the task.

## Installing Pandas and Matplotlib

In the VS Code terminal (or a Jupyter Lab terminal), run:

```text
python -m pip install pandas matplotlib
```

On a Mac, use `python3` instead of `python` if `python` is not found. NumPy is installed automatically with Pandas.

> **Note:** The expected outputs were produced with Pandas 3. If you have Pandas 2, text columns are shown as `object` instead of `str` (for example `dtype: object`). That is fine.

---

## Part A - In-Class Lab [30% of Lab Marks]

Complete all assigned in-class tasks during your scheduled lab.

**Part A Marking (3 marks):**

| Task | Marks |
|---|---|
| Task 1 - Creating and Exploring Pandas Series | 1.0 |
| Task 2 - Creating and Exploring a DataFrame | 1.0 |
| Task 3 - Filtering, Sorting and Grouping a DataFrame | 1.0 |
| **Total** | **3** |

- This part can be completed in Jupyter Lab or VS Code. You have a choice. I recommend using Jupyter Lab.
  - If you are using Jupyter Lab, then please create a single notebook file called `Lab7.ipynb` and complete each task in a unique cell.
  - If you are using VS Code, then just follow the instructions for each task and create `.py` files.
- Demonstrate your completed work to the professor before leaving the lab.
- The professor may ask you to explain portions of your code.
- No submission is required for Part A unless otherwise instructed.

<details markdown="1">

<summary><b>Quick Reference: Pandas Series</b></summary>

<br>

**Import Pandas once, at the top of the script.** By convention it is given the short name `pd`:

```python
import pandas as pd
import numpy as np      # only needed if you create arrays
```

A **Series** is a one-dimensional array of values where every value has a **label** (its index). A Series can also have a **name**, like a column heading.

| Code | What it creates |
|---|---|
| `pd.Series([10, 20, 30], name="Scores")` | From a list. The labels are `0, 1, 2`. |
| `pd.Series(np.array([1, 2, 3]))` | From a NumPy array. |
| `pd.Series({"Ann": 20, "Ben": 22})` | From a dictionary. The **keys** become the labels. |

**Accessing values**

| Code | Meaning |
|---|---|
| `s["Ann"]` | The value with the **label** `"Ann"` |
| `s.iloc[0]` | The value at **position** 0 (the first value) |
| `s.iloc[-1]` | The value at the last position |
| `s * 2` | A new Series with every value doubled (vectorized, like NumPy) |
| `s.tolist()` | The values as a plain Python list |

When you `print()` a Series, Pandas shows the labels on the left, the values on the right, and a last line with the name and the data type, such as `Name: Scores, dtype: int64`.

</details>

### Task 1 - Creating and Exploring Pandas Series

**Objective:** Practice creating Series from a list, a NumPy array and a dictionary, and accessing values by position and by label.

**Instructions:**

- Create a file named `task1.py` and add the required comment header.
- Copy the following starter code into your file, below the comment header. The `Numbers` Series and the first value are done for you as examples:

  ```python
  import numpy as np
  import pandas as pd


  def create_series():
      numbers = pd.Series([5, 10, 15, 20], name="Numbers")    # done for you
      print("Numbers (from a list):")
      print(numbers)
      print()

      # 1. Create a Series named Evens from the NumPy array np.array([2, 4, 6, 8]),
      #    store it in the variable evens, and print it like Numbers above
      # 2. Create a Series named Ages from the dictionary {"Alice": 25, "Bob": 30, "Charlie": 35},
      #    store it in the variable ages, and print it like Numbers above

      return numbers, evens, ages


  def access_values(numbers, ages):
      print("=== Accessing values ===")
      print("First value of Numbers:", numbers.iloc[0])      # done for you
      # 3. Print the last value of Numbers (use .iloc[-1])
      # 4. Print the age of Bob (use the label "Bob")
      # 5. Print Numbers multiplied by 2, as a list (use .tolist())


  def main():
      numbers, evens, ages = create_series()
      access_values(numbers, ages)


  main()
  ```

- Complete the two functions by following the numbered comments. Use the labels shown in the expected output. Do not change `main()`.
- Run your script with `python task1.py` and verify the output.

**Expected Output:**

```text
Numbers (from a list):
0     5
1    10
2    15
3    20
Name: Numbers, dtype: int64

Evens (from a NumPy array):
0    2
1    4
2    6
3    8
Name: Evens, dtype: int64

Ages (from a dictionary):
Alice      25
Bob        30
Charlie    35
Name: Ages, dtype: int64

=== Accessing values ===
First value of Numbers: 5
Last value of Numbers: 20
Age of Bob: 30
Numbers doubled: [10, 20, 30, 40]
```

> **Think about it:** `ages["Bob"]` and `ages.iloc[1]` both give `30`. What is the difference between the two, and which one would still give Bob's age if the Series were sorted by age in descending order?

<details markdown="1">

<summary><b>Quick Reference: Pandas DataFrames</b></summary>

<br>

A **DataFrame** is a table: rows and named columns. Each column is a Series. The usual way to build one is from a **dictionary of lists**, where each key is a column name and each list holds that column's values (all lists must be the same length):

```python
data = {
    "Student": ["Amira", "David", "Sofia"],
    "GPA": [3.6, 3.2, 3.9],
}
df = pd.DataFrame(data)
```

**Inspecting a DataFrame**

| Code | Result |
|---|---|
| `df.head(3)` / `df.tail(3)` | The first / last 3 rows |
| `df.shape` | `(rows, columns)` as a tuple, an attribute (no brackets) |

**Selecting data**

| Code | Result |
|---|---|
| `df["GPA"]` | One column, as a Series |
| `df.loc[1, "Student"]` | The value in the row with **label** 1 and the column `"Student"` |

</details>

### Task 2 - Creating and Exploring a DataFrame

**Objective:** Practice building a DataFrame from a dictionary and looking at its columns, rows and size.

**Instructions:**

- Create a file named `task2.py` and add the required comment header.
- Copy the following starter code into your file, below the comment header. The data is already typed in for you:

  ```python
  import pandas as pd


  def build_books():
      data = {
          "Title": ["The Great Gatsby", "A Brief History of Time", "To Kill a Mockingbird",
                    "The Art of Computer Programming", "Sapiens"],
          "Author": ["F. Scott Fitzgerald", "Stephen Hawking", "Harper Lee",
                     "Donald Knuth", "Yuval Noah Harari"],
          "Year": [1925, 1988, 1960, 1968, 2011],
          "Pages": [180, 212, 281, 672, 498],
      }
      # 1. Convert data to a DataFrame with pd.DataFrame(), store it in books, and return books


  def explore_books(books):
      print("All books:")
      print(books)                 # done for you
      print()
      # 2. Print the Title column
      # 3. Print the first 3 rows (use .head(3))
      # 4. Print the number of rows and columns (use .shape)
      # 5. Print the author of the book in row 2 (use .loc[2, "Author"])


  def main():
      books = build_books()
      explore_books(books)


  main()
  ```

- Complete the two functions by following the numbered comments. Use the labels and empty lines shown in the expected output. Do not change `main()`.
- Run your script with `python task2.py` and verify the output.

**Expected Output:**

```text
All books:
                             Title               Author  Year  Pages
0                 The Great Gatsby  F. Scott Fitzgerald  1925    180
1          A Brief History of Time      Stephen Hawking  1988    212
2            To Kill a Mockingbird           Harper Lee  1960    281
3  The Art of Computer Programming         Donald Knuth  1968    672
4                          Sapiens    Yuval Noah Harari  2011    498

Title column:
0                   The Great Gatsby
1            A Brief History of Time
2              To Kill a Mockingbird
3    The Art of Computer Programming
4                            Sapiens
Name: Title, dtype: str

First 3 rows:
                     Title               Author  Year  Pages
0         The Great Gatsby  F. Scott Fitzgerald  1925    180
1  A Brief History of Time      Stephen Hawking  1988    212
2    To Kill a Mockingbird           Harper Lee  1960    281

Rows and columns: (5, 4)
Author of the book in row 2: Harper Lee
```

> **Note:** Each column of a DataFrame is a Series. That is why printing the `Title` column ends with `Name: Title, dtype: str`, just like the Series in Task 1.

<details markdown="1">

<summary><b>Quick Reference: Filtering, Sorting and Grouping</b></summary>

<br>

**Filtering with a Boolean condition** works like Boolean indexing in NumPy. The condition gives one `True`/`False` per row, and the square brackets keep only the `True` rows:

```python
df[df["GPA"] > 3.5]                        # rows where GPA is above 3.5
df[df["Program"] == "Business"]["Student"]  # filter, then keep one column
```

**Sorting**

```python
df.sort_values("GPA")                      # lowest first
df.sort_values("GPA", ascending=False)     # highest first
```

Sorting does not change `df`. It returns a new, sorted DataFrame. The original index labels move with their rows.

**Grouping.** `groupby()` splits the rows into groups that share a value, then summarises each group:

```python
df.groupby("Program")["GPA"].mean()        # average GPA for each program
```

The result is a Series whose labels are the group names, sorted alphabetically.

</details>

### Task 3 - Filtering, Sorting and Grouping a DataFrame

**Objective:** Practice filtering rows with a condition, sorting, and grouping.

**Instructions:**

- Create a file named `task3.py` and add the required comment header.
- Copy the following starter code into your file, below the comment header:

  ```python
  import pandas as pd


  def build_grades():
      data = {
          "Name": ["Amira", "David", "Sofia", "Liam", "Noah", "Maya"],
          "Course": ["Math", "Math", "Science", "History", "Science", "History"],
          "Grade": [85, 92, 78, 88, 95, 71],
      }
      return pd.DataFrame(data)


  def analyse_grades(df):
      # 1. Print the students with a grade above 90 (use df[df["Grade"] > 90])
      # 2. Print the DataFrame sorted by grade, highest first (use sort_values with ascending=False)
      # 3. Print the average grade for each course (use groupby("Course")["Grade"].mean())
      pass


  def main():
      df = build_grades()
      print("Student grades:")
      print(df)
      print()
      analyse_grades(df)


  main()
  ```

- Complete `analyse_grades()` by following the numbered comments (remove `pass`). Use the labels and empty lines shown in the expected output. Do not change the other functions.
- Run your script with `python task3.py` and verify the output.

**Expected Output:**

```text
Student grades:
    Name   Course  Grade
0  Amira     Math     85
1  David     Math     92
2  Sofia  Science     78
3   Liam  History     88
4   Noah  Science     95
5   Maya  History     71

Grades above 90:
    Name   Course  Grade
1  David     Math     92
4   Noah  Science     95

Sorted by grade (highest first):
    Name   Course  Grade
4   Noah  Science     95
1  David     Math     92
3   Liam  History     88
0  Amira     Math     85
2  Sofia  Science     78
5   Maya  History     71

Average grade per course:
Course
History    79.5
Math       88.5
Science    86.5
Name: Grade, dtype: float64
```

> **Think about it:** In the sorted table, the index labels on the left are no longer `0, 1, 2, ...`. Why did Pandas keep the original labels?

---

## Part B - Take-Home Lab [70% of Lab Marks]

Complete the following tasks independently after the scheduled lab using VS Code.

**Part B Marking (7 marks):**

| Task | Marks |
|---|---|
| Task 4 - Analysing a Firewall Log with Pandas | 1.5 |
| Task 5 - Plotting Two Lines | 1.5 |
| Task 6 - Bar Charts, Scatter Plots and Histograms | 2.0 |
| Task 7 - Firewall Charts with Subplots | 2.0 |
| Submission requirements (exact repo, folder and file names, comment headers, generated files, code pushed to GitHub) | up to 100% deduction may apply |
| **Total** | **7** |

> Marks are awarded only when the required functions and methods are used as instructed. Correct output alone is not enough. Your charts are checked by the **file name**, **titles**, **axis labels**, **legend**, **colours** and **data** they contain, so use the exact text given in each task.

**Before You Begin:**

- Open your local Git repository `SRT111F2026` on your computer.
- Create a new folder named `Lab07` inside the repository (capital `L`, then a zero: `Lab07`).
- Download `security_log.csv` from Blackboard and save it in the `Lab07` folder.
- Open the `Lab07` folder in VS Code.
- Create all Part B files inside the `Lab07` folder. Use these names **exactly**, all in lower case: `task4.py`, `task5.py`, `task6.py`, `task7.py`.
- Make sure Pandas and Matplotlib are installed (see [Installing Pandas and Matplotlib](#installing-pandas-and-matplotlib)).

**For each task:**

- Run the script from the `Lab07` folder using the VS Code terminal and compare your output with the expected output.
- Your scripts **create PNG images** in the `Lab07` folder. Open each PNG in VS Code to check it, then commit and push it with your code.
- Some tasks ask you to answer a question in a **comment** at the bottom of your script. These answers are marked, so do not skip them.
- No screenshots or PDF are required for this lab. Your code and the files it creates in GitHub are your submission.

<details markdown="1">

<summary><b>Quick Reference: Reading a CSV File and Answering Questions</b></summary>

<br>

**Reading a CSV file.** A CSV (Comma-Separated Values) file is a table saved as text: the first line holds the column names, and each following line is one row. `pd.read_csv("security_log.csv")` turns it into a DataFrame. (This is done for you in `load_log()`.)

**Answering questions about a DataFrame `df`** (you already used most of these in Part A):

| Question | Code |
|---|---|
| What do the first rows look like? | `df.head(5)` |
| How many rows and columns? | `df.shape` |
| Which rows match a condition? | `df[df["Action"] == "BLOCKED"]` |
| How many rows match? | `df[df["Action"] == "BLOCKED"].shape[0]` |
| How many times does each value appear? | `df["Service"].value_counts()` |
| What is the average for each group? | `df.groupby("Service")["Bytes"].mean()` |
| Which rows have the largest values? | `df.sort_values("Bytes", ascending=False).head(3)` |

`value_counts()` lists the most common value first. `.round(1)` rounds the results to 1 decimal place.

</details>

### Task 4 - Analysing a Firewall Log with Pandas

**Objective:** Practice reading a CSV file and answering simple questions about your own sample of data with `head()`, `shape`, filtering, `value_counts()`, `groupby()` and `sort_values()`.

**Instructions:**

- Make sure `security_log.csv` is in your `Lab07` folder.
- Create the file `task4.py` and add the required comment header.
- Copy the following starter code into your file, below the comment header. Loading the file, picking your sample and the first output are done for you:

  ```python
  import pandas as pd

  STUDENT_ID = 123456789      # replace with your own 9-digit student ID
  SAMPLE_SIZE = 50


  # ---------- Provided code: copy as is ----------
  def load_log(filename):
      try:
          log = pd.read_csv(filename)
          print("Loaded", filename, "with", log.shape[0], "events")
          return log
      except FileNotFoundError:
          print("Error: the file", filename, "was not found.")
          return None


  def select_my_events(log, student_id, size):
      my_log = log.sample(n=size, random_state=student_id)
      my_log = my_log.sort_values("EventID").reset_index(drop=True)
      print("Student ID:", student_id)
      print("Events selected:", my_log.shape[0])
      print()
      return my_log
  # ---------- End of provided code ----------


  def analyse_events(my_log):
      print("First 5 events:")
      print(my_log.head(5))                      # done for you
      print()
      # 1. Print the number of rows and columns (use .shape)
      # 2. Count the blocked events: keep the rows where my_log["Action"] == "BLOCKED",
      #    store them in blocked, and print blocked.shape[0]. Then print an empty line.
      # 3. Print the number of events per service (use my_log["Service"].value_counts())
      # 4. Print the average Bytes per service, rounded to 1 decimal place
      #    (use my_log.groupby("Service")["Bytes"].mean().round(1))
      # 5. Print the 3 largest transfers
      #    (use my_log.sort_values("Bytes", ascending=False).head(3))


  def main():
      log = load_log("security_log.csv")
      if log is None:
          return
      my_log = select_my_events(log, STUDENT_ID, SAMPLE_SIZE)
      analyse_events(my_log)


  main()
  ```

- Complete `analyse_events()` by following the numbered comments. Use the labels and empty lines shown in the expected output. Do not change the given code (except `STUDENT_ID`, later).
- Run your script with `python task4.py` and compare the output with the expected output below. Then change `STUDENT_ID` to your own ID and run it again.

**Expected Output (with the example ID `123456789`):**

```text
Loaded security_log.csv with 300 events
Student ID: 123456789
Events selected: 50

First 5 events:
   EventID  Hour       SourceIP Service   Action  Bytes
0        3     0  198.51.100.11     RDP  BLOCKED    120
1        6     0   203.0.113.38     SSH  ALLOWED   4381
2       23     1   203.0.113.33     RDP  BLOCKED    153
3       36     2   203.0.113.25     RDP  BLOCKED     99
4       50     3      10.0.0.24     SSH  BLOCKED    176

Rows and columns: (50, 6)
Blocked events: 16

Events per service:
Service
HTTPS    21
SSH       9
RDP       7
HTTP      7
DNS       6
Name: count, dtype: int64

Average bytes per service:
Service
DNS        664.2
HTTP     21888.9
HTTPS    61450.4
RDP        140.1
SSH        828.9
Name: Bytes, dtype: float64

3 largest transfers:
    EventID  Hour       SourceIP Service   Action   Bytes
40      250    17   198.51.100.1   HTTPS  ALLOWED  207360
7        60     4  198.51.100.32   HTTPS  ALLOWED  127379
11       82     6   203.0.113.11   HTTPS  ALLOWED  108894
```

> **Think about it:** Look at the average bytes per service in **your** output. Why are `SSH` and `RDP` so small compared with `HTTPS`? (Hint: look at the `Action` column of those events.)

<details markdown="1">

<summary><b>Quick Reference: Matplotlib Basics and Saving a Plot</b></summary>

<br>

**Import the plotting module once, at the top of the script.** By convention it is given the short name `plt`:

```python
import matplotlib.pyplot as plt
```

**The steps for every chart in this lab**

```python
plt.figure()                  # 1. start a new, empty figure
plt.plot(x, y)                # 2. draw the data
plt.title("My Title")         # 3. add a title and axis labels
plt.xlabel("X label")
plt.ylabel("Y label")
plt.savefig("my_plot.png")    # 4. save the figure to a PNG file in the current folder
plt.close()                   # 5. close the figure, so the next chart starts clean
```

- In this lab you **save** every chart with `plt.savefig()` instead of showing it with `plt.show()`. The file is your proof that the chart works, and it is checked from GitHub. Open the PNG in VS Code to look at it.
- Call `plt.savefig()` **before** `plt.close()`. Saving a closed figure gives an empty image.
- Forgetting `plt.figure()` or `plt.close()` makes the next chart draw on top of the previous one.

**Customizing lines**

```python
plt.plot(x, y, color="blue", linestyle="-", marker="o", label="Series A")
```

| Argument | Examples | Meaning |
|---|---|---|
| `color` | `"blue"`, `"red"`, `"green"` | Line colour |
| `linestyle` | `"-"` solid, `"--"` dashed, `":"` dotted | Line style |
| `marker` | `"o"` circle, `"s"` square, `"^"` triangle | Symbol drawn at each data point |
| `label` | `"y = 2x"` | Text shown for this line in the legend |

- `plt.legend()` draws the legend, using the `label` of each line. Call it **after** the lines are drawn.
- `plt.grid(True)` adds grid lines.

</details>

### Task 5 - Plotting Two Lines

**Objective:** Practice drawing lines on a chart, changing their colour, style and markers, and adding axis labels, a legend and grid lines.

**Instructions:**

- Create the file `task5.py` and add the required comment header.
- Copy the following starter code into your file, below the comment header. The first line and the title are done for you:

  ```python
  import matplotlib.pyplot as plt


  def plot_two_lines(x, y1, y2, filename):
      plt.figure()
      plt.plot(x, y1, color="blue", linestyle="-", marker="o", label="y = 2x")   # done for you
      plt.title("Linear vs Quadratic Growth")                                     # done for you
      # 1. Plot y2 against x: red, dashed line ("--"), square markers ("s"), label "y = x^2"
      # 2. Set the x-axis label to "x" and the y-axis label to "y"
      # 3. Add a legend and grid lines
      plt.savefig(filename)
      plt.close()
      print("Saved", filename)


  def main():
      x = [1, 2, 3, 4, 5]
      y1 = [2, 4, 6, 8, 10]
      y2 = [1, 4, 9, 16, 25]
      plot_two_lines(x, y1, y2, "two_lines.png")


  main()
  ```

- Complete `plot_two_lines()` by following the numbered comments. Do not change the other lines.
- Run your script with `python task5.py`, then open `two_lines.png` in VS Code.

**Expected Output:**

```text
Saved two_lines.png
```

**Expected File:** `two_lines.png`, with a blue solid line, a red dashed curve, a legend in the top-left corner, and grid lines.

> **Think about it:** At which value of `x` do the two lines cross, and what happens to the gap between them after that point?

<details markdown="1">

<summary><b>Quick Reference: Scatter Plots, Bar Charts and Histograms</b></summary>

<br>

| Chart | Function | Use it to show |
|---|---|---|
| Bar chart | `plt.bar(categories, values)` | One value per **category** (products, services, countries) |
| Scatter plot | `plt.scatter(x, y)` | The relationship between two numeric variables, one dot per pair |
| Histogram | `plt.hist(data, bins=5)` | How often the values of **one** numeric variable fall into ranges (bins) |

**Customizing**

```python
plt.bar(categories, values, color="orange")          # bar colour
plt.scatter(x, y, c="green", s=100, alpha=0.6)       # dot colour, dot size, transparency (0 to 1)
plt.hist(data, bins=5, edgecolor="black")            # number of bins, outline of each bar
```

With `bins=5`, Matplotlib splits the range from the smallest to the largest value into 5 equal parts and counts how many values fall into each part.

</details>

### Task 6 - Bar Charts, Scatter Plots and Histograms

**Objective:** Practice creating a bar chart, a scatter plot and a histogram, and understanding when to use each one.

**Instructions:**

- Create the file `task6.py` and add the required comment header.
- Copy the following starter code into your file, below the comment header. `plot_bar()` is complete and shows you the pattern to follow:

  ```python
  import matplotlib.pyplot as plt


  def plot_bar(products, sales, filename):        # done for you
      plt.figure()
      plt.bar(products, sales, color="orange")
      plt.title("Product Sales Comparison")
      plt.xlabel("Product")
      plt.ylabel("Sales (units)")
      plt.savefig(filename)
      plt.close()
      print("Saved", filename)


  def plot_scatter(x, y, filename):
      # Follow the same steps as plot_bar(), but:
      # - draw a scatter plot with green dots (c="green"), size 100 (s=100) and alpha=0.6
      # - title "Car Age vs Speed", x-axis label "Car age (years)", y-axis label "Speed (km/h)"
      pass


  def plot_histogram(daily_sales, filename):
      # Follow the same steps as plot_bar(), but:
      # - draw a histogram with 5 bins and black edges (edgecolor="black")
      # - title "Distribution of Daily Sales", x-axis label "Daily sales (units)",
      #   y-axis label "Number of days"
      pass


  def main():
      products = ["Coffee", "Tea", "Juice", "Soda"]
      sales = [150, 120, 90, 60]
      plot_bar(products, sales, "bar_chart.png")

      ages = [5, 7, 8, 7, 6, 9, 5, 6]
      speeds = [99, 86, 87, 88, 100, 86, 103, 87]
      plot_scatter(ages, speeds, "scatter_plot.png")

      daily_sales = [20, 15, 25, 18, 30, 12, 22, 28, 16, 14, 19, 21]
      plot_histogram(daily_sales, "histogram.png")


  main()
  ```

- Complete `plot_scatter()` and `plot_histogram()` by following the comments (remove `pass`). Do not change the other functions.
- At the **bottom** of `task6.py`, answer the following in a comment of 2-3 sentences: *Why is a bar chart the right choice for the product sales, and a histogram the right choice for the daily sales?*
- Run your script with `python task6.py`, then open the three PNG files in VS Code.

**Expected Output:**

```text
Saved bar_chart.png
Saved scatter_plot.png
Saved histogram.png
```

**Expected Files:** `bar_chart.png`, `scatter_plot.png` and `histogram.png`.

> **Think about it:** Change `bins=5` to `bins=3`, run the script and look at `histogram.png`. Then try `bins=8`. How does the number of bins change the picture? Set it back to `5` before you push.

<details markdown="1">

<summary><b>Quick Reference: Subplots</b></summary>

<br>

**Subplots** place several charts in one figure, side by side, so you can compare them.

`plt.subplot(rows, columns, index)` selects the chart that the next plotting commands draw on. For two charts next to each other, use 1 row and 2 columns:

| | Column 1 | Column 2 |
|---|---|---|
| **Row 1** | `plt.subplot(1, 2, 1)` (left) | `plt.subplot(1, 2, 2)` (right) |

```python
plt.figure(figsize=(10, 4))   # width and height in inches: room for 2 charts

plt.subplot(1, 2, 1)          # left chart
plt.bar(names, values)
plt.title("Left chart")       # title and labels apply to the CURRENT chart

plt.subplot(1, 2, 2)          # right chart
plt.hist(data, bins=5)
plt.title("Right chart")

plt.suptitle("One title for the whole figure")
plt.tight_layout()            # adjust spacing so titles and labels do not overlap
plt.savefig("charts.png")
plt.close()
```

**Plotting the result of `value_counts()`.** The result is a Series: the values (such as service names) are its `index`, and the counts are its `values`:

```python
counts = df["Service"].value_counts()
plt.bar(counts.index, counts.values)
```

</details>

### Task 7 - Firewall Charts with Subplots

**Objective:** Bring Pandas and Matplotlib together: count the events in your sample with `value_counts()`, and show your data in one figure with two charts side by side.

**Instructions:**

- Create the file `task7.py` and add the required comment header.
- Copy the following starter code into your file, below the comment header. Use the **same** student ID as in Task 4. The left chart is done for you:

  ```python
  import matplotlib.pyplot as plt
  import pandas as pd

  STUDENT_ID = 123456789      # replace with your own 9-digit student ID
  SAMPLE_SIZE = 50


  # ---------- Provided code: copy as is ----------
  def load_log(filename):
      try:
          log = pd.read_csv(filename)
          print("Loaded", filename, "with", log.shape[0], "events")
          return log
      except FileNotFoundError:
          print("Error: the file", filename, "was not found.")
          return None


  def select_my_events(log, student_id, size):
      my_log = log.sample(n=size, random_state=student_id)
      my_log = my_log.sort_values("EventID").reset_index(drop=True)
      print("Student ID:", student_id)
      print("Events selected:", my_log.shape[0])
      print()
      return my_log
  # ---------- End of provided code ----------


  def build_charts(my_log, student_id, filename):
      service_counts = my_log["Service"].value_counts()
      plt.figure(figsize=(10, 4))

      # Left chart - done for you
      plt.subplot(1, 2, 1)
      plt.bar(service_counts.index, service_counts.values, color="blue")
      plt.title("Events per Service")
      plt.xlabel("Service")
      plt.ylabel("Number of events")

      # Right chart
      # 1. Select the right chart with plt.subplot(1, 2, 2)
      # 2. Draw a red histogram of my_log["Hour"] with 6 bins and black edges
      # 3. Title "Events by Hour", x-axis label "Hour of day", y-axis label "Number of events"

      # 4. Add the figure title: plt.suptitle("Firewall Events - Student " + str(student_id))
      plt.tight_layout()
      plt.savefig(filename)
      plt.close()
      print("Saved", filename)
      # 5. Print the most common service (use service_counts.idxmax())


  def main():
      log = load_log("security_log.csv")
      if log is None:
          return
      my_log = select_my_events(log, STUDENT_ID, SAMPLE_SIZE)
      build_charts(my_log, STUDENT_ID, "security_charts.png")


  main()
  ```

- Complete `build_charts()` by following the numbered comments. Do not change the given code (except `STUDENT_ID`).
- At the **bottom** of `task7.py`, answer the following in a comment of 2-4 sentences, using **your own** charts: *Which service appears most often in your sample? At what time of day are there the most events, and are there any events in the middle of the night?*
- Run your script with the example ID and compare the output below. Then change `STUDENT_ID` to your own ID, run it again, and open `security_charts.png` in VS Code.

**Expected Output (with the example ID `123456789`):**

```text
Loaded security_log.csv with 300 events
Student ID: 123456789
Events selected: 50

Saved security_charts.png
Most common service: HTTPS
```

**Expected File:** `security_charts.png`. With the example ID it looks like the picture described below. With your own ID the bars are different, and the figure title shows your ID.

```text
                 Firewall Events - Student 123456789
+-------------------------------+-------------------------------+
| Events per Service            | Events by Hour                |
| (blue bars: HTTPS, SSH, ...)  | (red histogram, 6 bins)       |
+-------------------------------+-------------------------------+
```

> **Think about it:** A company's employees work during the day. If you saw many `SSH` and `RDP` events at 2 a.m. from addresses outside the company, what might that mean?

## Part B Submission

Part B is graded **directly from your GitHub repository**. The structure below must match **exactly**, including upper and lower case. A file with the wrong name or in the wrong folder is treated as missing.

```text
SRT111F2026/                   <- your repository, with exactly this name
└── Lab07/                     <- capital L, zero, seven
    ├── task4.py               <- with YOUR student ID in STUDENT_ID
    ├── task5.py
    ├── task6.py
    ├── task7.py               <- with the same student ID
    ├── security_log.csv       <- the data file from Blackboard, unchanged
    ├── two_lines.png          <- created by task5.py
    ├── scatter_plot.png       <- created by task6.py
    ├── bar_chart.png          <- created by task6.py
    ├── histogram.png          <- created by task6.py
    └── security_charts.png    <- created by task7.py with your ID
```

- Do **not** rename the repository, and do not put the files in a sub-folder of `Lab07` or at the top level of the repository.
- Run every script from inside the `Lab07` folder, so the PNG files are created there. Do not rename them.
- Run `task7.py` again **after** you put in your own student ID, so the pushed `security_charts.png` shows your ID.
- Part A files (`task1.py` to `task3.py`) are graded in class. You may also push them to `Lab07`; they will not affect your Part B grade.
- Commit and push the `Lab07` folder to GitHub. Open your repository on github.com in a browser and confirm that all ten files are inside `Lab07` and that the PNG images open.
- On Blackboard, submit **only the link** to your repository, for example: `https://github.com/yourgithubusername/SRT111F2026`
- No screenshots and no PDF are required.

### Part B Grading Checklist

Your repository will be checked against the following list. Your scripts are also run again by the grader, and the charts they save are checked automatically. For Tasks 4 and 7, the grader works out the expected results from **your** student ID. Use this list to check your own work before you submit.

| # | Check |
|---|---|
| 1 | The repository is named `SRT111F2026` and contains a folder named `Lab07`. |
| 2 | `Lab07` contains the four scripts, `security_log.csv` and the five PNG files, with the exact names shown above. |
| 3 | Every `.py` file starts with the required comment header (Author, Date, Purpose). |
| 4 | Every script defines the required functions with the required names, has a `main()` function, and calls `main()`. |
| 5 | Each script runs from the `Lab07` folder without errors and prints the expected output (for Tasks 4 and 7, the expected output for your ID). |
| 6 | `task4.py` and `task7.py` set `STUDENT_ID` to **your own** 9-digit student ID (the same in both), not the example ID. |
| 7 | Task 4 uses `head()`, `shape`, a filter on `Action`, `value_counts()`, `groupby()` and `sort_values()`. |
| 8 | Task 5 saves `two_lines.png` with the required title, axis labels, line colours, line styles, markers, legend and grid. |
| 9 | Task 6 saves `bar_chart.png`, `scatter_plot.png` and `histogram.png` with the required titles, axis labels, colours, size, transparency and bins, and has the reflection comment at the bottom. |
| 10 | Task 7 saves `security_charts.png` with two subplots (a bar chart and a histogram) holding the required titles, labels, colours and figure title with your ID, and has a reflection comment at the bottom about your own charts. |
| 11 | The repository link was submitted on Blackboard. |
