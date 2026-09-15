# ECE2112_HULIPAS_PA3
#### EXPERIMENT 3: PYTHON DATA ANALYSIS<br>**Submitted By: Kathleen Hazel L. Hulipas | 2ECE-A**
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
### OUTCOMES:
(a)
```
Shape: (32, 12)
List of Column Names: ['Model', 'mpg', 'cyl', 'disp', 'hp', 'drat', 'wt', 'qsec', 'vs', 'am', 'gear', 'carb']
```

(b)
|  | Model | mpg | cyl | disp | hp | drat | wt | qsec | vs | am | gear | carb |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 5 | Valiant | 18.1 | 6 | 225.0 | 105 | 2.76 | 3.46 | 20.22 | 1 | 0 | 3 | 1 |
| 6 | Duster 360 | 14.3 | 8 | 360.0 | 245 | 3.21 | 3.57 | 15.84 | 0 | 0 | 3 | 4 |
| 7 | Merc 240D | 24.4 | 4 | 146.7 | 62 | 3.69 | 3.19 | 20.00 | 1 | 0 | 4 | 2 |
| 8 | Merc 230 | 22.8 | 4 | 140.8 | 95 | 3.92 | 3.15 | 22.90 | 1 | 0 | 4 | 2 |
| 9 | Merc 280 | 19.2 | 6 | 167.6 | 123 | 3.92 | 3.44 | 18.30 | 1 | 0 | 4 | 4 |

(c)
|  | Model | mpg | cyl | hp | gear |
|---|---|---|---|---|---|
| 5 | Valiant | 18.1 | 6 | 105 | 3 |
| 6 | Duster 360 | 14.3 | 8 | 245 | 3 |
| 7 | Merc 240D | 24.4 | 4 | 62 | 4 |
| 8 | Merc 230 | 22.8 | 4 | 95 | 4 |
| 9 | Merc 280 | 19.2 | 6 | 123 | 4 |

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

### OUTCOMES:
(a)
| # | Model | mpg | cyl | disp | hp | drat | wt | qsec | vs | am | gear | carb |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 19 | Toyota Corolla | 33.9 | 4 | 71.1 | 65 | 4.22 | 1.835 | 19.9 | 1 | 1 | 4 | 1 |

(b)
| # | Model | mpg | hp | wt |
|---|---|---|---|---|
| 24 | Pontiac Firebird | 19.2 | 175 | 3.845 |

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
### OUTCOMES:
```
Shape: (3, 5)
```
| # | Model | mpg | cyl | hp | gear |
|---|---|---|---|---|---|
| 2 | Datsun 710 | 22.8 | 4 | 93 | 4 |
| 27 | Lotus Europa | 30.4 | 4 | 113 | 5 |
| 29 | Ferrari Dino | 19.7 | 6 | 175 | 5 |

---
To view the program for PA3: download [ECE2112_PA3](https://github.com/kathleenhazelhulipas-cloud/ECE2112_HULIPAS_PA3/blob/main/PA3.ipynb), open on Jupyter Notebook, and run all cells.

## **README file Version History:**
- September 13, 2026 - Uploaded Readme File, PA3.ipynb, and cars.csv
- September 15, 2026 - Updated Readme File Format
