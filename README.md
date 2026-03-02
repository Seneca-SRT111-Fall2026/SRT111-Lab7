# Lab 7: Pandas, MatplotLib
**Weight:** 2% <br>
**Work Type:** Individual <br>
Environment: GitHub Codespaces
**Submission Format:** Screenshots

----
## Introduction

In this lab, you will create 6  Python scripts. All scripts must be written in GitHub Codespaces. 
Data visualization is a key skill for understanding and communicating insights from data.
**Matplotlib** is one of the most powerful and widely used Python libraries for creating a wide range of static, animated, and interactive visualizations.
In this lab, you will explore how to turn raw data into meaningful plots, understand the basics of different plot types, and learn how to enhance visualizations for clarity and impact.
By completing these tasks, you will gain hands-on experience in turning raw data into clear and meaningful visualizations that make your findings easier to interpret and communicate.

----

# Lab Objectives
- Understand the role of Pandas in data analysis.
- Create and manipulate Pandas Series and DataFrames.
- Perform filtering, grouping, and aggregations in Pandas.
- Apply both libraries to solve data-driven problems.
- Understand the basics of Matplotlib and its plotting functions.
- Generate and customize various plot types such as line, scatter, bar, and histogram.
- Apply visual elements (titles, labels, legends, grid, styles) to improve readability.
- Use subplots to compare multiple visualizations side by side.
- Annotate and highlight key data points in a plot.
- Visualize real-world style data and CSV-based datasets.
- Apply Matplotlib skills to interpret and communicate data effectively.

----

## Before You Begin

Before starting this lab, ensure the following:

1. Open your GitHub repository and launch GitHub Codespaces.
2.  Inside the repository, create six Python files:
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

3. At the top of each Python file, add your name and date in the comment section.
4. Import the numpy, pands or matplotlib library whichever is required:

```python
import numpy as np
import pands as pd
import matplotlib.pyplot as plt
```

----

# Submission Instructions
For each task:
1. **Write the script** in Codespaces.  
2. **Run the script** from the **terminal**.  
3. **Take a screenshot** that clearly shows:  
   - Your **code** in the editor.  
   - The **terminal output**, including your **username** visible in the terminal.  
4. **Insert the screenshot** into a Word document under the heading that matches the task name:  
   - Example: **Task 1**, **Task 2**, **Task 3**, etc.  
5. After completing all tasks, **convert the Word document to PDF**.  Name the PDF file using your **yoursenecausername.pdf**
6. **Submit the PDF file** as your final lab submission on Blackbaord.

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
**Objective:** Learn how to create Pandas Series with values, index labels, and a name, and access elements by position or label.

A Pandas Series is like a single column of data with labels (index) for each element. It can also have a name, similar to a column title in a spreadsheet. Series can be created from lists, NumPy arrays, or dictionaries.
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
- In the file Lab6g.py, create a numeric series from a Python list: [5, 10, 15, 20] and name it `Numbers`.
- Create a numeric series from a NumPy array [2, 4, 6, 8] and name it `Evens`.
- Create a numeric series from a dictionary: {'Alice': 25, 'Bob': 30, 'Charlie': 35} and name it `Ages`.
- Create a string Series for grades and name st `Grades`:
   - Values: ["<50", "50-59", "60-69", "70-79", "80-89", "90-100"]
   - Index labels: ["F", "D", "C", "B", "A", "A+"]
- Print all Series.
- Print the first and last elements of `Numbers`, `Evens`.
- Print the value for "Bob" from series_ages (use label-based indexing)
- Print the values for indices "C" and "A+" from `Grades`.
- Print the value "60-69" directly without the index.
- Run your script with the command: `python ./lab6g.py` and verify the output.
---

### lab6h.py - Introduction to Pandas DataFrames
**Objective:** Learn to create a DataFrame, explore its columns, rows, and attributes, access elements by label or position, and add new columns.

A DataFrame is like a table or spreadsheet in Python. Each column is a Series, so a DataFrame can store numeric, string, or categorical data. DataFrames have rows and columns, can be labeled, and support row/column selection, addition of new columns, and basic analysis. Pandas DataFrame can be created in multiple ways; you can create them:
- From a dictionary of lists
- From a list of dictionaries
- From a list of lists
- From NumPy arrays
- From external sources (CSV, Excel, SQL, etc.)

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
- In your Lab6h.py write code to create a DataFrame with the following information about library books:
  
| Title                              | Author              | Year | Pages | Genre        |
|------------------------------------|---------------------|------|-------|--------------|
| "The Great Gatsby"                 | F. Scott Fitzgerald | 1925 | 180   | Fiction      |
| "A Brief History of Time"          | Stephen Hawking     | 1988 | 212   | Science      |
| "To Kill a Mockingbird"            | Harper Lee          | 1960 | 281   | Fiction      |
| "The Art of Computer Programming"  | Donald Knuth        | 1968 | 672   | Computer Sci |
| "Sapiens: A Brief History of Humankind" | Yuval Noah Harari | 2011 | 498   | History      |

- Print the entire DataFrame.
- Perform the following operations:
- Print the `"Title"` column.  
- Print the `"Author"` column.  
- Print the first 3 rows using `.head()`.  
- Print the number of rows and columns using `.shape`.  
- Print the data type of each column using `.dtypes`.
- Run your script with the command: `python ./lab6h.py` and verify the output.
---
### lab6i.py - Exploring and Analyzing a DataFrame
**Objective:** Learn how to explore, summarize, and filter data in a DataFrame

**Instructions:**
- In your Lab6i.py file, create a DataFrame of student grades with the following data:
```Python
import pandas as pd

data = {
    "Name": ["Amira", "David", "Sofia", "Liam", "Noah"],
    "Course": ["Math", "Math", "Science", "History", "Science"],
    "Grade": [85, 92, 78, 88, 95],
    "Year": [1, 2, 1, 3, 2]
}

df = pd.DataFrame(data)
print("DataFrame:\n", df)
```
- Write code to do the following:
   - Print the first 3 rows.
   - Get summary statistics for numeric columns.
   - Find all students with grades above 90.
   - Print the names of students enrolled in Science courses.
   - Sort the DataFrame by Grade in descending order.
- **Hint:** Look into Pandas functions like .head(), .describe(), boolean indexing, column selection, and .sort_values() to complete these tasks.
- Run your script with the command: `python ./lab6i.py` and verify the output.
---
### lab6j.py - Analyzing Real-World Movie Data
**Objective:** Practice advanced Pandas operations including summary statistics, filtering, grouping, and basic plotting using a real dataset.

CSV (Comma-Separated Values) files are widely used for storing tabular data. Pandas provides simple functions to read from and write to CSV files. In this task, you will work with a **real-world dataset**: the IMDB Top 250 movies. You will practice reading data from a CSV file, exploring it, performing aggregations, and visualizing results using Pandas and Matplotlib.

To read a CSV file into a DataFrame, you can use the `pd.read_csv` function.
```Python
# Reading data from a CSV file
df_from_csv = pd.read_csv('sample.csv')  # Replace 'sample.csv' with your file path
print("\nDataFrame from CSV:\n", df_from_csv)
```

**Instructions:**
- In your Lab6j.py file, create a new data frame from a csv file located in : https://github.com/itiievskyi/IMDB-Top-250/blob/master/imdb_top_250.csv.
-  **Explore the DataFrame**:  
   - Print a **summary** of the data (`info()` and `describe()`).  
   - Print the **first 10** and **last 10 rows**.
- **Basic analysis**:  
   - Find the **earliest** and **latest** movie year (hint: `min()` and `max()` on the year column).  
   - Print **unique values** in the `"Genre"` column.  
   - Count how many movies are **not made in the USA**.
- **Top-rated movies**: Find the **top 10 highest-rated movies** by the rating column.
-  **Decade analysis**: Find out what the best decade of movies is:
   -  Define a Python function that calculates the **decade** from the year.  
     ```python
     def get_decade(year):
         return (year // 10) * 10
     ```
   - Add a **decade column** to the DataFrame.  
   - Group the data by decade and calculate the **mean rating** per decade.
- **Hint:** Use Pandas functions such as .info(), .describe(), .head(), .tail(), .unique(), .groupby(), .mean(), .sort_values().
- Run your script with the command: `python ./lab6j.py` and verify the output.
----
## INVESTIGATION 1: BASIC PLOTS AND CUSTOMIZATION

### lab7a.py - Your First Line Plot
**Objective:** Learn how to create a simple line plot and label its axes and title.
A line plot is one of the simplest and most commonly used visualizations. It is ideal for showing trends or changes over a sequence, such as time or numerical progression.

**Instructions:**
- Create a new python file called lab7a.py.
- Import Matplotlib and create two lists:
```Python
import matplotlib.pyplot as plt
x = [1, 2, 3, 4, 5]
y = [2, 4, 6, 8, 10]
```
- Plot `y` versus `x` using `plt.plot()`.
- Add a **title**, **x-axis label**, and **y-axis label**.
   - Use `plt.xlabel('Your X label')` and `plt.ylabel('Your Y label')` for axes labels.
   - Use `plt.title('Your Title')` to add a title.
- Display the plot using `plt.show()`.
- Run the script using the command: `python ./lab7a.py` and verify the output.
---

### lab7b.py - Plotting Multiple Lines
**Objective:** Learn how to plot multiple lines on the same figure and customize their appearance with colors, line styles, and legends.

Often, we want to compare two or more datasets on the same graph.  
Plotting multiple lines together allows us to see relationships or differences between the datasets clearly.

**Instructions:**
- Create a new python file called lab7b.py.
- Import Matplotlib and create two lists:
   - a list of `x` values as shown below.
   - two lists of `y` values as shown below.
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
- Run the script using the command: `python ./lab7b.py` and verify the output.
---
### lab7c.py - Scatter Plots
**Objective:** Learn how to create a scatter plot and customize point appearance, including color, size, and transparency.

A **scatter plot** is used to visualize the relationship between two variables.  
Each point represents an observation, making it easier to identify trends, clusters, or outliers.

**Instructions:**
- Create a new python file called lab7c.py.
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
- Run the script using the command: `python ./lab7c.py` and verify the output.
---
### lab7d.py - Bar Charts and Histograms
**Objective:** Learn how to create bar charts and histograms, and understand their differences and uses.

- A **bar chart** is used to compare quantities across different categories.  
- A **histogram** shows the distribution of numerical data by grouping it into bins.  
These plots help visualize categorical and frequency-based data effectively.

**Instructions:**
- Create a new python file called lab7d.py.
- Import Matplotlib and create a list of categories and corresponding values. Example:
```Python
import matplotlib.pyplot as plt
products = ['Coffee', 'Tea', 'Juice', 'Soda']
sales = [150, 120, 90, 60]
```
- Plot a bar chart showing sales per product.
- Add a **title**, **x-axis label**, and **y-axis label**.
   - Hint: Use `plt.bar()` for categorical comparisons.
- Next, create a list of numerical data representing daily sales for all products combined:
```Python
daily_sales = [20, 15, 25, 18, 30, 12, 22, 28, 16, 14, 19, 21]
```
- Plot a histogram to visualize the distribution of daily sales.
- Experiment with the `bins` parameter.
- Add a **title** and **axis** labels.
   - Hint: Use `plt.hist()` for numeric distributions.
- Run the script using the command: `python ./lab7d.py` and verify the output.
- **Questions for Reflection:**
   - Why is a bar chart appropriate for the product sales data?
   - Why is a histogram appropriate for daily sales?
   - How does changing the number of bins in the histogram affect the visualization?
   - What could you add to improve readability or interpretability of these plots?

## INVESTIGATION 2: ADVANCED VISUALIZATION AND REAL WORLD DATA 

### lab7e.py - Subplots
**Objective:** Learn to create multiple plots in a single figure using `plt.subplot()` and customize each subplot.

Sometimes, you want to **display multiple plots in a single figure** for easy comparison.  
Matplotlib’s **subplots** allow you to arrange multiple plots in rows and columns within the same figure.
For example: A **2×2 subplot layout** means:
- 2 rows and 2 columns → 4 plots in total  
- Each plot has an **index** to specify its position:  
  - 1 → Top-left  
  - 2 → Top-right  
  - 3 → Bottom-left  
  - 4 → Bottom-right  

**Instructions:**
- Create a new python file called lab7e.py.
- Import Matplotlib and prepare the data. Example:
```Python
import matplotlib.pyplot as plt
x = [1, 2, 3, 4, 5]
y1 = [2, 4, 6, 8, 10]
y2 = [1, 3, 5, 7, 9]
y3 = [5, 3, 6, 2, 7]
y4 = [10, 8, 6, 4, 2]
```
- Create a 2×2 subplot layout:
   - Top-left: Line plot of y1 vs x
   - Top-right: Line plot of y2 vs x
   - Bottom-left: Line plot of y3 vs x
   - Bottom-right: Line plot of y4 vs x

**Example to start with:**
```Python
plt.subplot(2, 2, 1)  # Selects the top-left plot in a 2x2 grid
plt.plot(x, y1)
plt.title("Plot 1")
```
- The first 2 = number of rows, the second 2 = number of columns, the third 1 = index of this subplot (top-left).
- Extend this idea to plot `y2`, `y3`, and `y4` in the remaining subplots.
- Adjust spacing so that titles and labels do not overlap (hint: `plt.tight_layout()`).
- Run the script using the command: `python ./lab7e.py` and verify the output.
- **Questions for Reflection:**
   - How does using subplots help compare multiple datasets?
   - Why is a histogram appropriate for daily sales?
   - Could you combine different types of plots (line, scatter, bar) in the same figure? How?
---
### lab7f.py - Plotting Real-World Data from CSV
**Objective:** Learn to read a CSV file, process data with Pandas, and create multiple plots using Matplotlib.

In this task, you will use **real-world movie data** to practice creating plots.  
You will combine **line, bar, scatter, and histogram plots** to explore trends and relationships in the dataset.

**Instructions:**
- Create a new python file called lab7f.py.
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
- Run your script with python ./lab7f.py and verify the output.
---
### lab7g.py - Annotating and Saving Plots
**Objective:** Learn to annotate plots, highlight key points, and save figures using Matplotlib.

In this task, you will **highlight important insights** in your plots using annotations and markers.  
You will also learn how to **save your visualizations** to image files, which is useful for reports and presentations.

**Instructions:**
- Create a new python file called lab7g.py.
- Import Matplotlib and Pandas (you can reuse the movie dataset from lab7f.py):
```python
import pandas as pd
import matplotlib.pyplot as plt

url = "https://github.com/itiievskyi/IMDB-Top-250/blob/master/imdb_top_250.csv"
df = pd.read_csv(url)
```
- Using the dataset, create a line plot of movie ratings over the years.
- **Highlight key points:**
   - Mark the movie(s) with the highest rating using a different color or marker.
   - Annotate these points with the movie title using plt.annotate().
- **Further enhancements:**
   - Highlight the earliest and latest movie in the dataset.
   - Change colors, line styles, or marker types for better visualization.
   - Hint
      - plt.scatter() can be used to mark specific points on a line plot.
      - plt.annotate("Text", xy=(x, y), xytext=(x_offset, y_offset), arrowprops=dict(...)) allows text with an arrow.
- Save the figure to a file:
```Python
plt.savefig("movie_ratings_plot.png")
```
- Run your script using python ./lab7g.py and verify the output.
  
## Lab 7 Sign-Off
- Submit a PDF on Blackboard, named using your Seneca username (e.g., **yoursenecausername.pdf**).
- The PDF must include screenshots of the following scripts and their terminal output, clearly showing your GitHub username.
    - lab7a.py
    - lab7b.py
    - lab7c.py
    - lab7d.py
    - lab7e.py
    - lab7f.py
    - lab7g.py
- Ensure the code and output are clearly readable. Screenshots should be high-resolution (minimum 800x600) and not blurry.
- Blurry or unreadable submissions will be returned for redo. Resubmissions will only be graded as Satisfactory with a grade of 0, provided the work is satisfactory.
