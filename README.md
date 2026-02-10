# Capstone Project – Python Fundamentals

This repository contains my solution to the **Capstone Project: Python Fundamentals** assigned by SkilloVilla. It focuses on working with dataframes in Python using **NumPy** and **Pandas**, and performing a series of tasks on project, employee, and seniority data.

---

## Project Description

The project simulates a small project-management dataset with three main tables:

- **Employee** – basic details of project heads (ID, name, gender, city, age).
- **Seniority Level** – designation level for each employee.
- **Project** – projects handled by each employee, with project cost and status.

Using these datasets, the notebook performs data cleaning, transformation, and analysis tasks such as handling missing values, splitting columns, joining tables, updating designation levels, and aggregating project costs.

---

## Files in this Repository

- `Capstone.ipynb` – Jupyter notebook containing all code and outputs for Tasks 1–10 (every line commented).
- `Employee.csv` – Employee dataframe saved to CSV (Task 1).
- `Seniority.csv` – Seniority/Designation dataframe saved to CSV (Task 1).
- `Project.csv` – Project dataframe saved to CSV (Task 1).
- `TotalProjCost.csv` – Output dataframe containing total project cost per employee (Task 9).
- `README.md` – This documentation file.

> Note: From Task 2 onwards, all operations are performed by reading these CSV files using `pandas.read_csv`, as required in the assignment.

---

## Tasks Implemented

The notebook follows the exact task sequence from the assignment.

1. **Create DataFrames and Save as CSV**  
   - Build three dataframes: Employee, Seniority Level, and Project.  
   - Save them as `Employee.csv`, `Seniority.csv`, and `Project.csv`.

2. **Handle Missing Project Cost (Running Average)**  
   - Read `Project.csv`.  
   - Replace missing `Cost` values using a **running average** of previous non-missing costs, implemented with a `for` loop.

3. **Split Employee Name into First and Last Name**  
   - Read `Employee.csv`.  
   - Split `Name` into `First Name` and `LastName`.  
   - Drop the original `Name` column.

4. **Join All Three DataFrames into `Final`**  
   - Merge Employee and Seniority on `ID`.  
   - Merge the result with Project on `ID` to create a unified **`Final`** dataframe.

5. **Add Bonus Column for Finished Projects**  
   - Add a `Bonus` column to `Final`.  
   - For rows where `Status == "Finished"`, set `Bonus` to 5% of `Cost`.

6. **Demote Designation for Failed Projects and Filter**  
   - For rows with `Status == "Failed"`, demote the designation level by 1 (numerically increase, since 1 is highest). 
   - Remove all records where `Designation Level` becomes greater than 4 (ineligible to head projects).

7. **Add “Mr.” / “Mrs.” to First Name and Drop Gender**  
   - Prefix `First Name` with `Mr.` for males and `Mrs.` for females based on `Gender`.  
   - Drop the `Gender` column from `Final`.

8. **Promote Designation Based on Age**  
   - If `Age > 29`, promote designation level by 1 (numerically decrease, with a lower bound of 1).

9. **Calculate Total Project Cost per Employee**  
   - Group `Final` by `ID` and `First Name`.  
   - Sum `Cost` to compute total project cost handled by each employee.  
   - Save results to **`TotalProjCost`** dataframe and export as `TotalProjCost.csv`.

10. **Filter Employees by City Name Containing “o”**  
    - From `Final`, print all employee records where `City` contains the letter “o” (case-insensitive).

---

## Tech Stack

- **Language:** Python 3  
- **Libraries:**  
  - `pandas` – dataframes, merging, grouping, CSV I/O  
  - `numpy` – numerical operations, handling `NaN`
