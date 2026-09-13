# ECE2112_HULIPAS_PA3
#### EXPERIMENT 2: PYTHON DATA ANALYSIS<br>**Submitted By: Kathleen Hazel L. Hulipas | 2ECE-A**
The content of this repository contains the _**Programming Assignment 3**_ for ECE2112 Advanced Computer Programming course A.Y. 2026 - 2027 which covers python problems from _**Module 3 - PANDAS**_.

Objectives
---
At the end of this laboratory activity, the student should be able to:
  1. load a CSV dataset into a Pandas DataFrame;
  2. select rows and columns using positional and label-based indexing;
  3. filter records using conditions on a DataFrame column; and
  4. extract a well-defined subset of data without changing the source data.

The code below is used to access the Pandas library:
```python
import pandas as pd
```

The code below was used to access the csv file:
```python
cars = pd.read_csv('cars.csv')
```

A.  POSITIONAL AND LABEL-BASED SLICING
---
After loading cars, complete the following operations.
    
    a. Display the shape and complete list of column names of cars.
    b. Using positional slicing, create cars 6 to 10 containing rows 6 through 10 of the dataset, where the first data row is row 1.
    c. From cars 6 to 10, display only the columns Model, mpg, cyl, hp, and gear, in that order.

The following function and methods were used in this problem:
  - `.shape` - used to determine the shape or dimensions of the dataframe.
  - `list()` - used to convert column names into a list.
  - `.iloc[r,c]` - used to select rows and columns from the dataframe by their integer position.
  - `.loc[r, c]` - used to locate the specific rows and columns by their labels.
    
These methods were used to create a single function that displays a ranged dataset and specific columns:
```python
# (a)
print ("Shape:", cars.shape)
print ("List of Column Names:", list(cars))

# (b)
cars_6_to_10 = cars.iloc[5:10]
cars_6_to_10

# (c)
cars_6_to_10.loc[:, ['Model', 'mpg', 'cyl', 'hp', 'gear']]
```

B.  MODEL LOOKUP
---
Use Boolean indexing on the Model column to answer both requests.
  
    a. Display the complete row for Toyota Corolla.
    b. For Pontiac Firebird, display only Model, mpg, hp, and wt.
  
Store the two results in toyota and pontiac, respectively. Do not use a hard-coded row number to locate either model.

The following function and methods were used in this problem:
  - `.loc[r, c]` - used to locate the specific rows and columns by their labels.

These methods were used to create a single function that displays a model and specific columns:
```python
# (a)
toyota = cars.loc[cars['Model']=='Toyota Corolla']
toyota

# (b)
pontiac = cars.loc[(cars['Model']=='Pontiac Firebird'), ['Model', 'mpg', 'hp', 'wt']]
pontiac
```

C.  MULTI-MODEL SUBSETTING
---
Create a DataFrame named selected_cars containing only the records for three models: Datsun 710, Lotus Europa, and Ferrari Dino.

For these records, retain only Model, mpg, cyl, hp, and gear. Select the rows by their model values rather than by row numbers. Display selected cars and its shape.

The following function and methods were used in this problem:
  - `.shape` - used to determine the shape or dimensions of the dataframe.    
  - `|` - or operator
  - `.loc[r, c]` - used to locate the specific rows and columns by their labels.

These methods were used to create a single function that display specific models and columns:
```python
selected_cars = cars.loc[(cars['Model']=='Datsun 710')|(cars['Model']=='Lotus Europa')|(cars['Model']=='Ferrari Dino'), ['Model', 'mpg', 'cyl', 'hp', 'gear']]
print ("Shape:", selected_cars.shape)
selected_cars
```
---
To view the program for PA3: download [ECE2112_PA3](https://github.com/kathleenhazelhulipas-cloud/ECE2112_HULIPAS_PA3/blob/main/PA3.ipynb), open on Jupyter Notebook, and run all cells.

## **README file Version History:**
- September 13, 2026 - Uploaded Readme File, PA3.ipynb, and cars.csv
