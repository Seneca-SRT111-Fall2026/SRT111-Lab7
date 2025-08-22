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

## INVESTIGATION 1: CREATING AND USING ARRAYS IN NumPy

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
- Plot `y` versus `x` using plt.plot().
- Add a title, x-axis label, and y-axis label.
   - Use `plt.xlabel('Your X label')` and `plt.ylabel('Your Y label')` for axes labels.
   - Use `plt.title('Your Title')` to add a title.
- Display the plot using `plt.show()`.
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
