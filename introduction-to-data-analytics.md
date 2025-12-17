---
title: Introduction to Data Analytics
---

# Introduction to Data Analytics



# Introduction to Data Analytics

## What is Data Analytics?

In today's digital world, data is being generated at an unprecedented rate. Every click, purchase, sensor reading, and social media interaction creates data points that, when properly analyzed, can reveal powerful insights. **Data Analytics** is the science of examining raw data to draw conclusions, identify patterns, and support decision-making.

```{glossary}
Data Analytics
  The process of examining, cleaning, transforming, and modeling data to discover useful information, draw conclusions, and support decision-making.

Data
  Raw facts, figures, and observations that have been collected but not yet processed or analyzed.

Information
  Data that has been processed, organized, and structured to provide context and meaning.

Insight
  A deep understanding or revelation derived from analyzing information, often leading to actionable recommendations.
```

:::{important}
Data Analytics is not just about working with numbers—it's about telling stories with data and transforming raw information into actionable insights that drive real-world decisions.
:::

## The Data Analytics Landscape

### Types of Data Analytics

Data analytics can be categorized into four main types, each serving a different purpose and answering different questions:

```{mermaid}
flowchart LR
    A[Descriptive] --> B[Diagnostic]
    B --> C[Predictive]
    C --> D[Prescriptive]
    
    A1["What happened?"] --> A
    B1["Why did it happen?"] --> B
    C1["What will happen?"] --> C
    D1["What should we do?"] --> D
```

| Type | Question Answered | Example | Complexity |
|------|------------------|---------|------------|
| Descriptive | What happened? | Monthly sales reports | Low |
| Diagnostic | Why did it happen? | Root cause analysis of sales decline | Medium |
| Predictive | What will happen? | Forecasting next quarter's revenue | High |
| Prescriptive | What should we do? | Recommending optimal pricing strategy | Very High |

```{card} The Four Types Explained
:header: Understanding Analytics Maturity
:footer: Most organizations progress through these types sequentially

**Descriptive Analytics** summarizes historical data to understand what has occurred. This includes basic statistics, reports, and dashboards.

**Diagnostic Analytics** digs deeper to understand *why* something happened, using techniques like drill-down analysis, data discovery, and correlations.

**Predictive Analytics** uses statistical models and machine learning to forecast future outcomes based on historical patterns.

**Prescriptive Analytics** recommends specific actions by simulating various scenarios and optimizing for desired outcomes.
```

### The Data Analytics Process

A systematic approach to data analytics follows a well-defined lifecycle:

```{mermaid}
flowchart TD
    A[1. Define the Problem] --> B[2. Collect Data]
    B --> C[3. Clean & Prepare Data]
    C --> D[4. Explore & Analyze]
    D --> E[5. Model & Visualize]
    E --> F[6. Communicate Insights]
    F --> G[7. Make Decisions]
    G --> A
```

:::{tip}
The data analytics process is iterative, not linear. You'll often cycle back to earlier stages as you discover new questions or data quality issues.
:::

## Getting Started with Python for Data Analytics

Python has become the lingua franca of data analytics due to its simplicity, extensive libraries, and strong community support. In this course, we'll primarily use **Python**, **Pandas**, and **Google Colab**.

### Why Python?

- **Readable syntax**: Python code is easy to read and write
- **Rich ecosystem**: Libraries like Pandas, NumPy, Matplotlib, and Scikit-learn
- **Community support**: Extensive documentation and community resources
- **Versatility**: From data wrangling to machine learning to web applications

### Setting Up Google Colab

Google Colab provides a free, cloud-based Jupyter notebook environment that requires no setup.

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/googlecolab/colabtools/blob/main/notebooks/colab-github-demo.ipynb)

:::{dropdown} How to Create Your First Colab Notebook
1. Go to [colab.research.google.com](https://colab.research.google.com)
2. Sign in with your Google account
3. Click "New Notebook"
4. Start coding in the first cell!

Colab provides free access to GPUs and TPUs, making it perfect for data analytics and machine learning projects.
:::

### Your First Data Analytics Code

Let's write our first Python code to understand the basics:

```{code-cell} python
:tags: [pyodide]

# Welcome to Data Analytics!
# This is a simple Python program

# Define a message
message = "Welcome to Data Analytics!"
print(message)

# Basic arithmetic
total_students = 30
passing_students = 24
passing_rate = (passing_students / total_students) * 100

print(f"Class passing rate: {passing_rate:.1f}%")
```

### Introduction to Pandas

**Pandas** is the most important library for data analytics in Python. It provides powerful data structures and tools for data manipulation.

```{code-cell} python
:tags: [pyodide]

import pandas as pd

# Creating a simple DataFrame
data = {
    'Student': ['Alice', 'Bob', 'Charlie', 'Diana', 'Eve'],
    'Math_Score': [85, 92, 78, 95, 88],
    'Science_Score': [90, 85, 82, 91, 87],
    'Study_Hours': [10, 15, 8, 18, 12]
}

df = pd.DataFrame(data)
print("Student Performance Data:")
print(df)
```

```{code-cell} python
:tags: [pyodide]

# Basic statistics with Pandas
print("\n--- Descriptive Statistics ---")
print(df.describe())
```

:::{note}
The `.describe()` method provides a quick statistical summary including count, mean, standard deviation, minimum, quartiles, and maximum values for numerical columns.
:::

## Core Concepts in Data Analytics

### Variables and Data Types

Understanding data types is fundamental to data analytics. Data can be classified in several ways:

```{mermaid}
flowchart TD
    A[Data Types] --> B[Quantitative]
    A --> C[Qualitative]
    B --> D[Discrete]
    B --> E[Continuous]
    C --> F[Nominal]
    C --> G[Ordinal]
```

| Category | Type | Description | Example |
|----------|------|-------------|---------|
| Quantitative | Discrete | Countable, whole numbers | Number of students |
| Quantitative | Continuous | Measurable, any value in range | Temperature, weight |
| Qualitative | Nominal | Categories with no order | Colors, gender |
| Qualitative | Ordinal | Categories with meaningful order | Education level, satisfaction rating |

```{code-cell} python
:tags: [pyodide]

import pandas as pd

# Demonstrating different data types
data = {
    'Name': ['Alice', 'Bob', 'Charlie'],           # Nominal (categorical)
    'Age': [22, 25, 23],                           # Discrete (quantitative)
    'GPA': [3.75, 3.42, 3.89],                     # Continuous (quantitative)
    'Year': ['Junior', 'Senior', 'Junior'],        # Ordinal (categorical)
    'Major': ['CS', 'Math', 'CS']                  # Nominal (categorical)
}

df = pd.DataFrame(data)
print("DataFrame with mixed data types:")
print(df)
print("\n--- Data Types ---")
print(df.dtypes)
```

### Central Tendency and Spread

The foundation of {term}`Data Analytics` begins with understanding how to summarize data:

```{code-cell} python
:tags: [pyodide]

import pandas as pd
import numpy as np

# Sample dataset: Daily website visitors
visitors = pd.Series([120, 135, 98, 142, 156, 128, 145, 130, 167
