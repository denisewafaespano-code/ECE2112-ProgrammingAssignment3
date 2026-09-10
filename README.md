# EXPERIMENT 3: PYTHON DATA ANALYSIS (PANDAS)
**Made by**: Denise Wafa B. Españo
<div style="border-bottom: 2px solid gray; margin-bottom: 10px;"></div>

The content of this repository contains Programming Assignment 3 for our course. This project covers three Python data analysis problems pertaining to Experiment 3: Python Data Analysis (Pandas). 

**Objectives**

By the end of this laboratory activity, the goal is be able to load a CSV dataset into a Pandas DataFrame, select specific rows and columns, using both positional and label-based indexing, and filter records based on column conditions in order to successfully extract a well-defined subset of information without altering the original source data.


Before starting the problems, the required library must be imported and the dataset must be loaded into memory. The original values in the 'cars' dataframe must not be modified throughout the experiment.

```python
import pandas as pd

cars = pd.read_csv('cars.csv') #Loading the datset into a DataFrame named 'cars'
```

## A. POSITIONAL AND LABEL-BASED SLICING
The goal in this first programming problem is to extract specific rows using their numerical position in the table and specific columns using their text labels

```python
print("Shape of cars dataset:", cars.shape)
```

The `.shape ` returns a tuple representing the dimensionality of the DataFrame.
The output `Shape: (32,12)` indicates there are 32 rows and 12 columns in the original dataset, which is important for verifying that the dataset loaded correctly before slicing it.


It is also required to extract rows 6 through 10, assuming the very first data row is considered row 1. 
```python
cars_6_to_10 = cars.iloc[5:10] 
cars_6_to_10
```
The `.iloc` function is used for index-based selection. Because Python utilizes 0-based indexing, row 1 corresponds to index 0. Therefore, row 6 is to index 5, and row 10 is to index 9. The slice `[5:10]` starts exactly at index 5 and stops right before index 10 (inclusive of 5, exclusive of 10).



From the created row subset, only the columns `Model`, `mpg`, `cyl`, `hp`, and `gear` must be extracted in that exact sequence.

```python
cars_6_to_10.loc[:, ['Model', 'mpg', 'cyl', 'hp', 'gear']]
```
The `.loc` function is used for label-based indexing, meaning elements are selected by their actual names rather than numerical position. Then, this follows a `[rows, columns]` format. The `:` placed before the comma means to select all rows present in that current subset. The list of strings following the comma selects only the explicitly requested columns.  

| | Model | mpg | cyl | hp | gear |
| :--- | ---: | ---: | ---: | ---: | ---: |
| **5** | Valiant | 18.1 | 6 | 105 | 3 |
| **6** | Duster 360 | 14.3 | 8 | 245 | 3 |
| **7** | Merc 240D | 24.4 | 4 | 62 | 4 |
| **8** | Merc 230 | 22.8 | 4 | 95 | 4 |
| **9** | Merc 280 | 19.2 | 6 | 123 | 4 |


## B. Model Lookup
<div style="border-bottom: 2px solid gray; margin-bottom: 10px;"></div>

The goal for this programming problem is to use Boolean indexing to locate a specific car model without hard-coding row numbers.

```python
toyota = cars.loc[(cars['Model'] == 'Toyota Corolla'),:]
toyota
```
Boolean indexing acts as a data filter. By writing `cars['Model'] == 'Toyota Corolla'`, the code checks every row in the Model column and isolates only the row that evaluates to true. 

| | Model | mpg | cyl | disp | hp | drat | wt | qsec | vs | am | gear | carb |
| :--- | ---: | ---: | ---: | ---: | ---: | ---: | ---: | ---: | ---: | ---: | ---: | ---: |
| **19** | Toyota Corolla | 33.9 | 4 | 71.1 | 65 | 4.22 | 1.835 | 19.9 | 1 | 1 | 4 | 1 |


Locating the 'Pontiac Firebird' will be similar to the previous step. However, instead of a colon `:` for the columns, a specific list of column names to extract only `Model`, `mpg`, `hp`, and `wt`. 

```python
pontiac = cars.loc[(cars['Model'] == 'Pontiac Firebird'), ['Model', 'mpg', 'hp', 'wt']]
pontiac
```

| | Model | mpg | hp | wt |
| :--- | ---: | ---: | ---: | ---: |
| **24** | Pontiac Firebird | 19.2 | 175 | 3.845 |

## C. Multi-Model Subsetting
<div style="border-bottom: 2px solid gray; margin-bottom: 10px;"></div>
The goal for this last programming problemm is to create a subset for three specific column, and verify its dimensions.

```python
selected_cars = cars.loc[(cars['Model'] == 'Datsun 710') | (cars['Model'] == 'Lotus Europa') | (cars['Model'] == 'Ferrari Dino'), ['Model', 'mpg', 'cyl', 'hp', 'gear']]
selected_cars
```

The OR  operator `|` is used to combine multiple Boolean conditions. This tells Pandas to select a row if the Model is Datsun 710 OR Lotus Europa OR Ferrari Dino. It simultaneously filters the columns down to the five requested variables.

| | Model | mpg | cyl | hp | gear |
| :--- | ---: | ---: | ---: | ---: | ---: |
| **2** | Datsun 710 | 22.8 | 4 | 93 | 4 |
| **27** | Lotus Europa | 30.4 | 4 | 113 | 5 |
| **29** | Ferrari Dino | 19.7 | 6 | 175 | 5 |

Lastly, verify the output dimensions
```python
print("Shape:", selected_cars.shape)
```
As required by the programming assignment, checking the shape confirms the final DataFrame contains exactly three rows and five columns (3,5).

<div style="border-bottom: 1px solid gray; margin-bottom: 5px;"></div>

Thank you for reading!

To see the main Python program for Programming Assignment 3, click this https://github.com/denisewafaespano-code/ECE2112-ProgrammingAssignment3.git and download. Open on Jupyter Notebook, then run all cells. 

**READ ME file Version History:**

September 4, 2026 - Initial README output uploaded.













