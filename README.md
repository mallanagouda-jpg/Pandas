# Pandas
Data Analysis & Preprocessing with Pandas

A structured reference guide for exploratory data analysis (EDA), dataset inspection, and data cleaning workflows using the Pandas library on an IPL matches dataset.

Table of Contents

Overview

Installation

Data Loading & Initial Inspection

Data Cleaning Workflow

1. Checking and Removing Duplicates

2. Handling Missing Values

3. Dropping Unnecessary Columns

Data Indexing & Subsetting

Descriptive Statistics

Overview

Pandas is an open-source data analysis and manipulation library for Python. It provides high-performance data structures—such as DataFrame and Series—that simplify loading, filtering, cleaning, and analyzing structured data.

This project demonstrates practical data engineering techniques using an IPL (Indian Premier League) match dataset.

Installation

Install Pandas via pip:

pip install pandas


Import Pandas in your script or notebook:

import pandas as pd


Data Loading & Initial Inspection

Load tabular datasets directly into a Pandas DataFrame using file readers like read_csv():

# Load CSV dataset into a DataFrame
df = pd.read_csv("matches.csv")

# Preview the first 5 rows
df.head()

# Preview the last 5 or N rows
df.tail(10)

# Retrieve basic structural properties
print("Columns:", df.columns)
print("Shape (rows, columns):", df.shape)
print("Total rows:", len(df))

# Detailed metadata summary (data types, memory usage, non-null counts)
df.info()


Data Cleaning Workflow

Data preprocessing involves inspecting missing values, removing duplicates, and trimming uninformative features.

1. Checking and Removing Duplicates

Identify identical rows to maintain data integrity:

# Count duplicate rows
duplicate_count = df.duplicated().sum()
print(f"Total Duplicate Rows: {duplicate_count}")

# Remove duplicate rows in-place
df.drop_duplicates(inplace=True)


2. Handling Missing Values

Locate null or missing values across features and apply appropriate handling strategies:

# Count missing values per column
print(df.isnull().sum())

# Drop all rows containing missing values
df.dropna(inplace=True)

# Verify null removal
print(df.isnull().sum())


3. Dropping Unnecessary Columns

Remove redundant or high-null columns to streamline analysis:

# Drop specific column from DataFrame
df.drop(columns="method", inplace=True)


Data Indexing & Subsetting

Access specific subsets, target columns, or individual records using string names or integer locations (iloc):

# Access a single column (returns a Series)
method_series = df["method"]

# Select a subset of columns (returns a DataFrame)
subset_df = df[['toss_decision', 'winner', 'city']]

# Access a single row by index position using .iloc
first_row = df.iloc[0]
print(first_row)


Descriptive Statistics

Compute key summary statistics for numerical features (count, mean, standard deviation, quartiles, min/max values):

# Summary statistics for numeric features
df.describe()
