# Lab 7
In this lab, you will create 6  Python scripts. All scripts must be written in GitHub Codespaces. 
Data visualization is a key skill for understanding and communicating insights from data.
**Matplotlib** is one of the most powerful and widely used Python libraries for creating a wide range of static, animated, and interactive visualizations.
In this lab, you will explore how to turn raw data into meaningful plots, understand the basics of different plot types, and learn how to enhance visualizations for clarity and impact.
By completing these tasks, you will gain hands-on experience in turning raw data into clear and meaningful visualizations that make your findings easier to interpret and communicate.
# Lab Objectives
- Understand the basics of Matplotlib and its plotting functions.
- Generate and customize various plot types such as line, scatter, bar, and histogram.
- Apply visual elements (titles, labels, legends, grid, styles) to improve readability.
- Use subplots to compare multiple visualizations side by side.
- Annotate and highlight key data points in a plot.
- Visualize real-world style data and CSV-based datasets.
- Apply Matplotlib skills to interpret and communicate data effectively.
# Submission Instructions
For each task:
1. **Write the script** in Codespaces.  
2. **Run the script** from the **terminal**.  
3. **Take a screenshot** that clearly shows:  
   - Your **code** in the editor.  
   - The **terminal output**, including your **username** visible in the terminal.  
4. **Insert the screenshot** into a Word document under the heading that matches the task name:  
   - Example: **Lab7a**, **Lab7b**, **Lab7c**, etc.  
5. After completing all tasks, **convert the Word document to PDF**.  Name the PDF file using your **yoursenecausername.pdf**
6. **Submit the PDF file** as your final lab submission on Blackbaord.

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
- Create a new python file called labdc.py.
- Import Matplotlib.
- Create a list of categories and corresponding values. Example:
```Python
  import matplotlib.pyplot as plt
   products = ['Coffee', 'Tea', 'Juice', 'Soda']
   sales = [150, 120, 90, 60]
```
- Plot a bar chart showing sales per product.
- Add a **title**, **x-axis label**, and **y-axis label**.
   - Hint: Use plt.bar() for categorical comparisons.
- Next, create a list of numerical data representing daily sales for all products combined:
```Python
daily_sales = [20, 15, 25, 18, 30, 12, 22, 28, 16, 14, 19, 21]
```
- Plot a histogram to visualize the distribution of daily sales.
- Experiment with the `bins` parameter.
- Add a **title** and **axis** labels.
   - Hint: Use plt.hist() for numeric distributions.
- Run the script using the command: `python ./lab7d.py` and verify the output.
- **Questions for Reflection:**
   - Why is a bar chart appropriate for the product sales data?
   - Why is a histogram appropriate for daily sales?
   - How does changing the number of bins in the histogram affect the visualization?
   - What could you add to improve readability or interpretability of these plots?

## INVESTIGATION 2: ADVANCED VISUALIZATION AND REAL WORLD DATA 

## Lab 6 Sign-Off
- Submit a PDF on Blackboard, named using your Seneca username (e.g., **yoursenecausername.pdf**).
- The PDF must include screenshots of the following scripts and their terminal output, clearly showing your GitHub username.
    - lab6a.py
    - lab6b.py
    - lab6c.py
    - lab6d.py
    - lab6e.py
    - lab6f.py
    - lab6g.py
    - lab6h.py
    - lab6i.py
    - lab6j.py
- Ensure the code and output are clearly readable. Screenshots should be high-resolution (minimum 800x600) and not blurry.
-  Blurry or unreadable submissions will be returned for redo. Resubmissions will only be graded as Satisfactory with a grade of 0, provided the work is satisfactory.
