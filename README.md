# 🚢 Titanic Dataset Analysis & Visualization

A beginner-friendly **Data Analysis and Visualization project** based on the Titanic dataset. The project uses Python, Pandas, NumPy, Matplotlib, and Seaborn to clean, analyze, and visualize passenger data and explore factors related to passenger survival.

---

## 📌 Project Overview

This project analyzes the **Titanic passenger dataset** using Python data analysis and visualization libraries.

The dataset contains information about Titanic passengers such as:

* Passenger ID
* Passenger class
* Name
* Sex
* Age
* Number of siblings/spouses aboard
* Number of parents/children aboard
* Ticket
* Fare
* Cabin
* Port of Embarkation
* Survival status

The main goal of this project is to understand the dataset, handle missing values, perform data cleaning, and create visualizations to explore patterns in passenger survival.

---

## 🎯 Objectives

The main objectives of this project are:

* Load Titanic datasets using Pandas.
* Explore the structure of the datasets.
* Remove duplicate records.
* Identify missing values.
* Handle missing values.
* Combine related datasets.
* Perform basic statistical analysis.
* Analyze passenger survival.
* Compare survival across different passenger groups.
* Study age and fare distributions.
* Analyze relationships between numerical variables.
* Create different visualizations using Matplotlib and Seaborn.

---

## 🛠️ Technologies Used

| Technology       | Purpose                             |
| ---------------- | ----------------------------------- |
| Python           | Programming language                |
| Pandas           | Data loading, cleaning and analysis |
| NumPy            | Numerical operations                |
| Matplotlib       | Data visualization                  |
| Seaborn          | Statistical visualization           |
| Jupyter Notebook | Development environment             |
| GitHub           | Project hosting                     |

---

## 📦 Libraries Used

```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
```

---

## 📂 Dataset

The project uses three Titanic dataset files:

```text
train.csv
test.csv
gender_submission.csv
```

### `train.csv`

The training dataset contains passenger information along with the `Survived` column.

### `test.csv`

The test dataset contains passenger information used separately from the training data.

### `gender_submission.csv`

This file contains passenger IDs and survival-related submission data.

---

## 📁 Project Structure

```text
Titanic-Data-Analysis/
│
├── finalpr.ipynb
├── train.csv
├── test.csv
├── gender_submission.csv
└── README.md
```

---

# 🔍 Data Analysis Process

## 1. Load the Training Dataset

The project loads the Titanic training dataset using Pandas:

```python
df1 = pd.read_csv('train.csv')
```

The dataset is then displayed for initial inspection.

---

## 2. Remove Duplicate Records

Duplicate rows are removed from the training dataset using:

```python
df1.drop_duplicates(inplace=True)
```

This helps prevent duplicate records from affecting the analysis.

---

## 3. Check Missing Values

Missing values are checked using:

```python
df1.isnull().sum()
```

This identifies the number of missing values in each column.

---

## 4. Handle Missing Values

Missing values are handled for important columns.

### Age

Missing age values are replaced with the mean age:

```python
df1['Age'] = df1['Age'].fillna(df1['Age'].mean())
```

### Cabin

Missing cabin values are replaced with:

```text
unknown
```

### Embarked

Missing embarkation values are also replaced with:

```text
unknown
```

---

# 🧪 Test Dataset Analysis

The project also loads the test dataset:

```python
df2 = pd.read_csv('test.csv')
```

The `gender_submission.csv` file is loaded separately:

```python
df3 = pd.read_csv('gender_submission.csv')
```

The project then joins the test dataset with the submission dataset.

---

## 🔗 Combining Data

The project demonstrates Pandas DataFrame joining:

```python
fd = df2.join(df3, lsuffix='left', rsuffix='right')
```

The resulting DataFrame is inspected using:

```python
fd.info()
```

Duplicate records are also removed from the combined DataFrame.

---

## 🧹 Additional Data Cleaning

The project removes an unnecessary passenger ID column and works with the remaining data.

Missing values in the test-related dataset are checked using:

```python
fd.isnull().sum()
```

Missing values are handled for:

* Fare
* Age
* Cabin

Numerical missing values are filled using the column mean, while missing cabin values are replaced with `"unknown"`.

---

# 📊 Data Visualization

The project uses **Seaborn** and **Matplotlib** to create multiple visualizations.

---

## 1. Boxen Plots

Boxen plots are created for numerical columns:

```python
for col in df1.select_dtypes(include='number').columns:
    sns.boxenplot(x=df1[col])
```

These plots help visualize the distribution of numerical variables and identify unusual values.

---

## 2. Survival by Sex

A bar plot is created to examine survival according to passenger sex.

```text
Sex → Survived
```

This visualization helps compare survival rates between male and female passengers.

**Chart:** `Survived by sex`

---

## 3. Survival by Passenger Class

A bar plot is used to analyze survival across passenger classes, with sex included as a category.

```text
Passenger Class → Survival
Sex → Category
```

**Chart:** `Survived by Class`

---

## 4. Age Distribution

A histogram is used to visualize the distribution of passenger ages.

```python
sns.histplot(x='Age', data=df1, bins=20)
```

**Chart:** `Age distribution of passengers`

---

## 5. Fare Distribution

A histogram is used to visualize the distribution of passenger fares.

```python
sns.histplot(x='Fare', data=df1, bins=6)
```

**Chart:** `Fare distribution`

---

## 6. Age vs Fare

A scatter plot is used to examine the relationship between passenger age and fare.

```text
Age → X-axis
Fare → Y-axis
Sex → Category
```

**Chart:** `Age vs Fare`

---

## 7. Correlation Heatmap

The project calculates correlations between numerical columns:

```python
corr = df1.select_dtypes(include='number').corr()
```

A Seaborn heatmap is then used to visualize the correlation matrix.

```python
sns.heatmap(corr, annot=True, cmap='inferno')
```

The heatmap helps identify the strength and direction of relationships between numerical variables.

---

## 8. Survival Rate by Embarkation Port

A bar plot is created to compare survival across different embarkation ports.

```text
Embarked → Survived
```

**Chart:** `Survival Rate by Embarkation Port`

---

## 9. Fare by Passenger Class

A line plot is used to visualize the relationship between passenger class and fare.

```python
sns.lineplot(x='Pclass', y='Fare', data=df1)
```

**Chart:** `Fare by Passenger class`

---

## 10. Passenger Survival Distribution

The project calculates survival counts using:

```python
x = df1['Survived'].value_counts()
```

A pie chart is then created to visualize the proportion of passengers who survived and did not survive.

**Chart:** `Passenger Survival Distribution`

The chart contains:

* Not survived
* Survived

---

# 📈 Analysis Areas

The project explores several important areas of the Titanic dataset:

### Passenger Demographics

* Age
* Sex
* Passenger class

### Travel Information

* Fare
* Cabin
* Embarkation port

### Survival

* Overall survival distribution
* Survival by sex
* Survival by passenger class
* Survival by embarkation port

### Relationships

* Age vs Fare
* Passenger class vs Fare
* Correlation between numerical variables

---

# 🧹 Data Cleaning Techniques Used

The project demonstrates the following data-cleaning techniques:

```text
✔ Removing duplicate rows
✔ Checking missing values
✔ Filling numerical missing values with mean
✔ Filling categorical missing values with "unknown"
✔ Removing unnecessary columns
✔ Joining DataFrames
✔ Inspecting DataFrame information
```

---

# 📚 Pandas Concepts Used

This project demonstrates:

```text
read_csv()
drop_duplicates()
isnull()
sum()
fillna()
mean()
join()
drop()
rename()
info()
select_dtypes()
value_counts()
corr()
```

---

# 📊 Visualization Concepts Used

The project demonstrates:

```text
Seaborn
├── boxenplot()
├── barplot()
├── histplot()
├── scatterplot()
├── heatmap()
└── lineplot()

Matplotlib
└── pie()
```

---

# 🧠 NumPy

NumPy is imported in the project for numerical/data-analysis work:

```python
import numpy as np
```

The current notebook primarily uses Pandas and Seaborn/Matplotlib for the implemented analysis.

---

# 🔄 Project Workflow

```text
Load Titanic Dataset
        ↓
Explore Dataset
        ↓
Check Duplicate Records
        ↓
Check Missing Values
        ↓
Clean Missing Values
        ↓
Load Test Dataset
        ↓
Load Submission Dataset
        ↓
Join Related Data
        ↓
Perform Data Analysis
        ↓
Create Visualizations
        ↓
Analyze Survival Patterns
```

---

# 📊 Visualizations Included

The notebook currently includes visualizations for:

```text
1. Numerical column boxen plots
2. Survival by sex
3. Survival by passenger class and sex
4. Age distribution
5. Fare distribution
6. Age vs Fare
7. Numerical correlation heatmap
8. Survival rate by embarkation port
9. Fare by passenger class
10. Passenger survival distribution
```

---

# 🎓 Learning Outcomes

Through this project, the following practical skills are demonstrated:

* Reading CSV files using Pandas.
* Understanding DataFrames.
* Inspecting dataset information.
* Detecting missing values.
* Handling missing values.
* Removing duplicate records.
* Joining DataFrames.
* Selecting numerical columns.
* Calculating correlations.
* Counting categorical values.
* Creating statistical visualizations.
* Using Seaborn for data visualization.
* Using Matplotlib for charts.
* Performing exploratory data analysis (EDA).

---

# 💡 Key Questions Explored

The analysis helps explore questions such as:

* What is the distribution of passenger ages?
* How are fares distributed?
* How does survival vary by sex?
* How does survival vary across passenger classes?
* How does survival vary by embarkation port?
* What is the relationship between age and fare?
* What relationships exist between numerical variables?
* What proportion of passengers survived?

---

# ⚠️ Project Limitations

This project is primarily an **Exploratory Data Analysis (EDA) and visualization project**.

It does not currently implement:

* Machine learning prediction
* Model training
* Model evaluation
* Feature engineering for machine learning
* Automated reporting
* Interactive dashboard
* Deployment

These can be added in future versions.

---

# 🚀 Future Improvements

Possible improvements include:

* Add more detailed statistical analysis.
* Perform feature engineering.
* Analyze survival using additional passenger features.
* Create more advanced visualizations.
* Build an interactive dashboard.
* Add machine-learning models for survival prediction.
* Compare different classification algorithms.
* Add model evaluation metrics.
* Export cleaned datasets.
* Improve notebook organization and documentation.

---

# ▶️ How to Run the Project

### 1. Clone the repository

```bash
git clone https://github.com/your-username/Titanic-Data-Analysis.git
```

### 2. Open the project

Open the project folder in:

* VS Code
* Jupyter Notebook
* JupyterLab

### 3. Install required libraries

```bash
pip install pandas numpy matplotlib seaborn
```

### 4. Make sure the dataset files are available

Keep the following files in the project directory:

```text
train.csv
test.csv
gender_submission.csv
```

### 5. Open the notebook

Open:

```text
finalpr.ipynb
```

Run the notebook cells from top to bottom.

---

# 📌 Project Status

**Status:** Completed EDA / Beginner Data Analysis Project

This project demonstrates the practical use of Python libraries for cleaning, analyzing, and visualizing the Titanic dataset.

---

# 👨‍💻 Author

**Your Name**



---

# ⭐ Acknowledgement

This project was created as a learning project to practice:

**Python + Pandas + NumPy + Matplotlib + Seaborn + Exploratory Data Analysis**

---

## 📜 License

This project is intended for educational and learning purposes.
