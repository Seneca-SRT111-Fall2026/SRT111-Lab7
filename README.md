# Lab 7: Pandas, MatplotLib
**Weight:** 2% <br>
**Work Type:** Individual <br>
Environment: GitHub Codespaces
**Submission Format:** Screenshots

----
## Introduction

In this lab, you will work in GitHub Codespaces to create ten Python scripts that explore data manipulation with Pandas and data visualization with Matplotlib. These two libraries are essential tools in data analysis:

- **Pandas** gives you powerful tools to load, clean, filter, group, summarize, and transform datasets using intuitive structures such as Series and DataFrames. You will practice creating these structures, performing aggregations, extracting insights, and working with real CSV data.
- **Matplotlib** enables you to communicate those insights visually. You will learn how to create line plots, bar charts, histograms, scatter plots, and subplots, as well as how to customize titles, labels, grids, legends, and styles to improve clarity and impact.

By completing this lab, you will gain hands‑on experience working with real‑world data, applying Pandas to analyze it, and using Matplotlib to turn your findings into clear and meaningful visualizations.

----

# Lab Objectives
- Understand the role of Pandas in data analysis and its core structures (Series and DataFrames).
- Create Pandas Series and DataFrames from lists, dictionaries, NumPy arrays, and CSV files.
- Perform common operations such as filtering, sorting, grouping, and aggregation.
- Explore datasets using descriptive statistics, summaries, and DataFrame inspection methods.
- Add new columns, work with derived data (e.g., decades), and interpret real‑world datasets.
- Understand the purpose of Matplotlib and its basic plotting functions.
- Create and customize line plots, scatter plots, bar charts, and histograms.
- Add visual elements such as titles, labels, legends, grid lines, and styles to improve readability.
- Use subplots to compare multiple visualizations within a single figure.
- Apply visualization techniques to explore and communicate insights from real datasets.

----

## Before You Begin

Before starting this lab, complete the following steps:

1. Open your GitHub repository and launch GitHub Codespaces.
2.  Inside the repository, create **ten** Python files:
   - `task1.py`
   - `task2.py`
   - `task3.py`
   - `task4.py`
   - `task5.py`
   - `task6.py`
   - `task7.py`
   -  `task8.py`
   -  `task9.py`
   -  `task10.py`

3. At the top of each Python file, include your name and the date in a comment.
4. Import only the libraries required for each task. Common imports you may need include:

```python
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
```

----

# Submission Instructions
For each task:
1. Write the script in Codespaces.  
2. Run the script from the **terminal**.  
3. Take a screenshot that clearly shows:  
   - Your **code** in the editor.  
   - The **terminal output**, including your **username** visible in the terminal.  
4. Insert the screenshot into a Word document under the heading that matches the task name:  
   - Example: **Task 1**, **Task 2**, **Task 3**, etc.  
5. After completing all tasks, convert the Word document to PDF.  Name the PDF file using your `yoursenecausername.pdf`
6. Submit the PDF file as your final lab submission on Blackbaord.

----

## INVESTIGATION 1: CREATING AND USING SERIES AND DATA FRAMES FROM Pandas
Pandas is a Python library used for data manipulation and analysis. It provides two main data structures:
- Series – a one-dimensional labeled array, similar to a column in a spreadsheet or a 1D NumPy array with labels.
- DataFrame – a two-dimensional labeled data structure, like a table with rows and columns.
Why use Pandas:
- Easily handle tabular data.
- Perform filtering, grouping, and aggregation.
- Combine multiple datasets efficiently.

### Task 1 - Creating and Exploring Pandas Series
**Objective:** Learn how to create Pandas Series with values, index labels, and a name, and practice accessing elements using both label-based and position-based indexing

A Pandas Series is a one‑dimensional labeled array. Each value has an index, and a Series can also have a descriptive name (like a column title). You can create Series from lists, NumPy arrays, or dictionaries.

Look at the example given below:
```Python
import pandas as pd
import numpy as np

# Series from a list
series_list = pd.Series([10, 20, 30, 40], name="Scores")
print("Series from list:\n", series_list)

# Series from a NumPy array
arr = np.array([1, 2, 3, 4])
series_array = pd.Series(arr)
print("\nSeries from NumPy array:\n", series_array)
```

**Instructions:**
- In `task1.py`, create a numeric series from a Python list: [5, 10, 15, 20] and name it `Numbers`.
- Create a numeric series from a NumPy array [2, 4, 6, 8] and name it `Evens`.
- Create a numeric series from a dictionary: {'Alice': 25, 'Bob': 30, 'Charlie': 35} and name it `Ages`.
- Create a string Series for grades and name it `Grades`:
   - Values: ["<50", "50-59", "60-69", "70-79", "80-89", "90-100"]
   - Index labels: ["F", "D", "C", "B", "A", "A+"]
- Print all Series.
- **Access and print specific data**
   - Print the first and last elements of `Numbers` and `Evens`. (use `.iloc[0]` and `.iloc[-1]`)
   - Print the value for "Bob" from `Ages` (use label-based indexing `Ages["Bob"]`)
   - Print the values for indices "C" and "A+" from `Grades`.
   - Print the value "60-69" by using positional indexing, not by typing the value directly.
- Run your script with the command: `python ./task1.py` and verify the output.

---

### Task 2 - Introduction to Pandas DataFrames
**Objective:** Learn how to create a Pandas DataFrame, explore its columns and rows, view its attributes, and access elements using label‑based and position‑based selection.

A DataFrame is a two‑dimensional labeled data structure similar to a spreadsheet or a table. Each column is a Pandas Series, and a DataFrame can store mixed data types—numeric, string, categorical, etc.
You can create DataFrames from dictionaries, lists of dictionaries, lists of lists, NumPy arrays, or external files such as CSVs.

Below is an example of creating a dataframe from the dictionary of lists:
```Python
import pandas as pd

# Create a DataFrame from a dictionary that contains student course enrollment data
data = {
    "Student": ["Amira", "David", "Sofia", "Jamal"],
    "Program": ["Computer Science", "Business", "Engineering", "Psychology"],
    "Year": [1, 2, 3, 4],
    "GPA": [3.6, 3.2, 3.9, 3.4]
}

df = pd.DataFrame(data)
print("DataFrame:\n", df)

# Access a column
print("\nColumn 'GPA':\n", df["GPA"])

# Access the first row
print("\nFirst row:\n", df.iloc[0])
```
**Instructions:**
- In task2.py Create a DataFrame with the following information about library books. You need build the data structure first using python dictionary, and then convert the dictionary to a DataFrame.
  
| Title                              | Author              | Year | Pages | Genre        |
|------------------------------------|---------------------|------|-------|--------------|
| "The Great Gatsby"                 | F. Scott Fitzgerald | 1925 | 180   | Fiction      |
| "A Brief History of Time"          | Stephen Hawking     | 1988 | 212   | Science      |
| "To Kill a Mockingbird"            | Harper Lee          | 1960 | 281   | Fiction      |
| "The Art of Computer Programming"  | Donald Knuth        | 1968 | 672   | Computer Sci |
| "Sapiens: A Brief History of Humankind" | Yuval Noah Harari | 2011 | 498   | History      |

- Print the entire DataFrame.
- **Perform the following operations:**
   - Print the `"Title"` column.  
   - Print the `"Author"` column.  
   - Print the first 3 rows using `.head(3)`.  
   - Print the number of rows and columns using `.shape`.  
   - Print the data type of each column using `.dtypes`.
- Run your script with the command: `python ./task2.py` and verify the output.

---

### Task 3 - Exploring and Analyzing a DataFrame
**Objective:** Practice inspecting, filtering, summarizing, and sorting data in a Pandas DataFrame. This task introduces basic analysis techniques used in real‑world data workflows.

**Instructions:**
- Copy the following code task3.py. This code create a DataFrame of student grades.
```Python
data = {
    "Name": ["Amira", "David", "Sofia", "Liam", "Noah"],
    "Course": ["Math", "Math", "Science", "History", "Science"],
    "Grade": [85, 92, 78, 88, 95],
    "Year": [1, 2, 1, 3, 2]
}

df = pd.DataFrame(data)
print("DataFrame:\n", df)
```
- Perform the following analyses
   - Print the first 3 rows. Use `.head(3)` to preview the beginning of the dataset.
   - Use .describe() to view mean, min, max, etc.
   - Use boolean filtering on the Grade column to find all students with grades above 90.
   - Filter rows where Course == "Science" and select only the "Name" column.
   - Sort the DataFrame by Grade in descending order. Use `.sort_values()` with `ascending=False`.
- Run your script with the command: `python ./task3.py` and verify the output.

---

### Task 4 - Analyzing Real-World Movie Data
**Objective:** Practice reading CSV files, exploring DataFrame structure, filtering, summarizing data, grouping values, and performing basic visual analysis with Pandas.

CSV (Comma-Separated Values) files are widely used for storing tabular data. Pandas provides simple functions to read from and write to CSV files. In this task, you will work with a **real-world dataset**: the IMDB Top 250 movies. You will practice reading data from a CSV file, exploring it, performing aggregations, and visualizing results using Pandas and Matplotlib.

To read a CSV file into a DataFrame, you can use the `pd.read_csv` function.
```Python
# Reading data from a CSV file
df_from_csv = pd.read_csv('sample.csv')  # Replace 'sample.csv' with your file path
print("\nDataFrame from CSV:\n", df_from_csv)
```

**Instructions:**
- Copy the following code in task4.py to read the dataset from the raw CSV link.
  ```python
  url = "https://raw.githubusercontent.com/itiievskyi/IMDB-Top-250/master/imdb_top_250.csv"
  df = pd.read_csv(url)
  ```
-  **Explore the DataFrame**:  
   - print `df.info()` — data types, non‑null counts.
   - print `df.describe()` — summary statistics for numeric columns
   - Print the first 10 and last 10 rows.
- **Basic analysis**:  
   - Find the **earliest** and **latest** movie year (hint: `min()` and `max()` on the year column).  
   - Print **unique values** in the `"Genre"` column.  Use `df["Genre"].unique()` 
   - Count how many movies are not from the USA.
     ```python
     non_usa_df = df[df["Country"] != "USA"]
     non_usa_count = non_usa_df.shape[0]
     ```
- **Top-rated movies**: Find the top 10 highest-rated movies by the rating column. Use `.sort_values()`.
- Run your script with the command: `python ./task4.py` and verify the output.
----
## INVESTIGATION 2: BASIC PLOTS AND CUSTOMIZATION

### Task 5 - Your First Line Plot
**Objective:** Learn how to create a simple line plot using Matplotlib and add essential visual elements such as a title, axis labels, and a displayed figure.

A line plot is useful for showing trends, patterns, or changes over a sequence of values.

**Instructions:**
- Add the following code in the file `task5.py`. This defines the x‑values and corresponding y‑values you will plot.
```Python
import matplotlib.pyplot as plt
x = [1, 2, 3, 4, 5]
y = [2, 4, 6, 8, 10]
```
- Plot `y` versus `x` using `plt.plot()`.
  ```python
  plt.plot(x, y)
  ```
- Provide meaningful axis labels and a descriptive title:
   - Use `plt.xlabel('Your X label')` and `plt.ylabel('Your Y label')` for axes labels.
   - Use `plt.title('Your Title')` to add a title.
- Display the plot using `plt.show()`.
- Run the script using the command: `python ./task5.py` and verify the output.
---

### Task 6- Plotting Multiple Lines
**Objective:** Learn how to plot multiple lines on the same graph, customize their appearance (color, style), and add a legend and grid to improve readability.

Plotting multiple lines allows you to compare datasets visually on the same axes.

**Instructions:**
- Add the following code in the file `task6.py`.  Note that we have two lists of `y` values as shown below. We will plot both of them in separate colors.

```Python
import matplotlib.pyplot as plt
x = [1, 2, 3, 4, 5]
y1 = [2, 4, 6, 8, 10]   # first line
y2 = [1, 4, 9, 16, 25]  # second line
```
- Plot both lines on the same figure:
```Python
plt.plot(x, y1, color='blue', linestyle='-', label='y = 2x')
plt.plot(x, y2, color='red', linestyle='--', label='y = x^2')
```
- Add a **title**, **x-axis label**, and **y-axis label**.
- Add a **legend** to distinguish the lines.
- Add **grid lines** for better readability. Use `plt.grid(True)` to show grid lines.
- Display the plot using `plt.show()`.
- Run the script using the command: `python ./task6.py` and verify the output.
  
---

### Task 7- Scatter Plots
**Objective:** Learn how to create a scatter plot using Matplotlib and customize point color, size, and transparency.

Scatter plots are useful for visualizing relationships or patterns between two numerical variables.

**Instructions:**
- Add the following code in the file `task7.py`
- Import Matplotlib and create two lists representing data points:
```Python
import matplotlib.pyplot as plt
x = [5, 7, 8, 7, 6, 9, 5, 6]
y = [99, 86, 87, 88, 100, 86, 103, 87]
```
- Create a scatter plot using plt.scatter().
- Customize the points:
   - Change color (e.g., c='green')
   - Change size (e.g., s=100)
   - Adjust transparency (e.g., alpha=0.6)
   - **Hint:** Use plt.scatter(x, y, c='color', s=size, alpha=transparency) to customize points. 
- Add a **title**, **x-axis label**, and **y-axis label**.
- Display the plot using plt.show().
- Run the script using the command: `python ./task7.py` and verify the output.

---

### Task 8 - Bar Charts and Histograms
**Objective:** Learn how to create bar charts and histograms, and understand their differences and uses.

- A **bar chart** compares quantities across categories.
- A **histogram** shows how often numerical values fall within specific ranges (bins).
These plots help visualize categorical and frequency-based data effectively.

**Instructions:**
- Add the following code in the file `task8.py`

```Python
import matplotlib.pyplot as plt
products = ['Coffee', 'Tea', 'Juice', 'Soda']
sales = [150, 120, 90, 60]
```
- Create a bar chart showing sales per product
```python
plt.figure()  # Create a new figure
plt.bar(products, sales)
plt.xlabel("Product")
plt.ylabel("Sales (Units)")
plt.title("Product Sales Comparison")
plt.show()
```
- The bar chart compares sales across four categories.
- Next, create a list of daily sales values:
```Python
daily_sales = [20, 15, 25, 18, 30, 12, 22, 28, 16, 14, 19, 21]
```
- Create a histogram showing the distribution of daily sales.
```python
plt.figure()  # Start a new figure for the histogram
plt.hist(daily_sales, bins=5)  # You can change the number of bins
plt.xlabel("Daily Sales")
plt.ylabel("Frequency")
plt.title("Distribution of Daily Sales")
plt.show()
```
- bins=5 groups the numbers into 5 ranges.
- Try changing it to bins=3 or bins=8 to see how it affects the shape of the graph.
- Run the script using the command: `python ./task8.py` and verify the output.
  
- **Questions for Reflection:**
   - Why is a bar chart appropriate for the product sales data?
   - Why is a histogram appropriate for daily sales?
   - How does changing the number of bins in the histogram affect the visualization?
   - What could you add to improve readability or interpretability of these plots?

## INVESTIGATION 3: ADVANCED VISUALIZATION AND REAL WORLD DATA 

### Task 9 - Subplots
**Objective:** Learn how to display multiple plots in a single figure using Matplotlib’s subplot() function. Subplots allow you to compare different datasets side‑by‑side in a single window.
Sometimes, you want to **display multiple plots in a single figure** for easy comparison.  
Matplotlib’s **subplots** allow you to arrange multiple plots in rows and columns within the same figure.
For example: A **2×2 subplot layout** means:
- 2 rows
- 2 columns
- 4 total plots  
- Each subplot is selected by its index:
  - 1 → top-left  
  - 2 → top-right  
  - 3 → bottom-left  
  - 4 → bottom-right  

**Instructions:**
- Add the following code in the file `task9.py`
```Python
import matplotlib.pyplot as plt
x = [1, 2, 3, 4, 5]
y1 = [2, 4, 6, 8, 10]
y2 = [1, 3, 5, 7, 9]
y3 = [5, 3, 6, 2, 7]
y4 = [10, 8, 6, 4, 2]
```
- Create a 2×2 grid of subplots: (the first plot is done for you, extend the idea to complete the remaining 3 plots)
   - Top-left: Line plot of y1 vs x
     ```python
     plt.subplot(2, 2, 1) # The first 2 = number of rows, the second 2 = number of columns, the third 1 = index of this subplot (top-left).
     plt.plot(x, y1)
     plt.title("Plot 1: y1 vs x")
     ```
   - Top-right: Line plot of y2 vs x 
   - Bottom-left: Line plot of y3 vs x
   - Bottom-right: Line plot of y4 vs x
- Adjust spacing so that titles and labels do not overlap (hint: `plt.tight_layout()`).
- Run the script using the command: `python ./lab7e.py` and verify the output.
  
- **Questions for Reflection:**
   - How does using subplots help compare multiple datasets?
   - Why is a histogram appropriate for daily sales?
   - Could you combine different types of plots (line, scatter, bar) in the same figure? How?
     
---

### Task 10 - Plotting Real-World Data from CSV
**Objective:** Learn to read a CSV file, process data with Pandas, and create multiple plots using Matplotlib.

In this task, you will use **real-world movie data** to practice creating plots.  
You will combine **line, bar, scatter, and histogram plots** to explore trends and relationships in the dataset.

**Instructions:**
- Add the following code in the file `task10.py`
- Import the necessary libraries:
```python
import pandas as pd
import matplotlib.pyplot as plt
```
- Read the CSV file from the following link:
```Python
url = "https://github.com/itiievskyi/IMDB-Top-250/blob/master/imdb_top_250.csv"
df = pd.read_csv(url)
```
- Explore the dataset using df.head() and df.info().
- Perform essential data processing:
   - Copy the Year column into a new series.
   - Sort the years in ascending order.
   - Count the number of movies for each year (use value_counts() or a similar method).
- Using Matplotlib, create at least three plots:
   - Line plot: Show the trend of movie ratings over the years.
   - Bar plot: Show the number of movies per genre (df['Genre'].value_counts()).
   - Histogram: X-axis = years, bar height = count of movies per year. If there are many unique years, display the histogram for the first 10 years.
- Add **titles**, **axis labels**, and **legends** to all plots.
- Optionally, arrange the plots in a subplot layout.
- Adjust spacing with `plt.tight_layout()`.
- Run your script with python ./task10.py and verify the output.
---

  
## Lab 7 Sign-Off
- Submit a PDF on Blackboard, named using your Seneca username (e.g., **yoursenecausername.pdf**).
- The PDF must include screenshots of the following scripts and their terminal output, clearly showing your GitHub username.
    - task1.py
    - task2.py
    - task3.py
    - task4.py
    - task5.py
    - task6.py
    - task7.py
    - task8.py
    - task9.py
    - task10.py
- Ensure the code and output are clearly readable. Screenshots should be high-resolution (minimum 800x600) and not blurry.
- Blurry or unreadable submissions will be returned for redo. Resubmissions will only be graded as Satisfactory with a grade of 0, provided the work is satisfactory.
