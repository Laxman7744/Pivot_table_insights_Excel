# Pivot Table Practice Insights

This repository demonstrates how to use pivot tables (and Python analysis) to extract insights from a student test score dataset. The dataset includes student information: Name, Gender, Age, Class, House, Unit Test 1, Unit Test 2, and Final Test scores.

## Dataset
- **Columns:**
  - `Name`: Student's name
  - `Gender`: 'M' for male, 'F' for female
  - `Age`: Age of student
  - `Class`: Class/grade (numeric)
  - `House`: School house (e.g., Agni, Bhoomi, Jal, Vayu)
  - `Unit Test 1`: Score in Unit Test 1
  - `Unit Test 2`: Score in Unit Test 2
  - `Final Test`: Score in Final Test

## Analysis Questions and Answers

1. **Who scored more, boys or girls, in the Final Test?**  
   - **Answer:** Average Final Test score for girls is **90.83**, for boys is **87.70**. **Girls** scored higher on average.

2. **In Bhoomi house, who scored better, girls or boys?**  
   - **Answer:** In Bhoomi house, average Final Test score for girls is **85.0**, for boys is **80.0**. **Girls** scored higher.

3. **What is the average Final Test score by House?**  
   - **Answer:**  
     - Agni: **92.67**  
     - Vayu: **92.29**  
     - Jal: **88.00**  
     - Bhoomi: **81.25**  

4. **How many students are in each House?**  
   - **Answer:**  
     - Vayu: 7 students  
     - Agni: 6 students  
     - Jal: 5 students  
     - Bhoomi: 4 students  

5. **What is the average Unit Test 1 score by Gender?**  
   - **Answer:**  
     - Male (M): **84.20**  
     - Female (F): **81.42**  

6. **Which class has the highest average Final Test score?**  
   - **Answer:** Class **9** has the highest average Final Test score of **95.33**.

7. **Who scored the highest in the Final Test?**  
   - **Answer:** **Vrinda** scored the highest with a score of **98**.

## How to Reproduce (Excel Pivot Tables)

1. **Open** the dataset in Excel. Ensure the columns are correctly labeled: Name, Gender, Age, Class, House, Unit Test 1, Unit Test 2, Final Test.
2. **Select** the data range (including headers).
3. Go to **Insert > PivotTable**.
4. Choose to place the pivot table in a new worksheet or existing one.
5. For each question:
   - **Question 1 (Final Test by Gender):**  
     - Drag `Gender` to Rows.  
     - Drag `Final Test` to Values and set Value Field Settings to Average.  
   - **Question 2 (Final Test in Bhoomi by Gender):**  
     - Add `House` to Filters or Rows, filter/select `Bhoomi`.  
     - Drag `Gender` to Rows and `Final Test` to Values (Average).  
   - **Question 3 (Average Final Test by House):**  
     - Drag `House` to Rows and `Final Test` to Values (Average).  
   - **Question 4 (Count of students by House):**  
     - Drag `House` to Rows and `Name` to Values, set Value Field Settings to Count.  
   - **Question 5 (Average Unit Test 1 by Gender):**  
     - Drag `Gender` to Rows and `Unit Test 1` to Values (Average).  
   - **Question 6 (Average Final Test by Class):**  
     - Drag `Class` to Rows and `Final Test` to Values (Average). Sort descending by average.  
   - **Question 7 (Highest Final Test score):**  
     - Drag `Name` to Rows and `Final Test` to Values (Max). Sort descending or use filter Top 1.

## Python Analysis (Optional)
A Python script using pandas can also compute these metrics. Example snippet:
```python
import pandas as pd
df = pd.read_excel('pivot table practice insights.xlsx', sheet_name='pivot table practice', header=1)
df.columns = ['Name', 'Gender', 'Age', 'Class', 'House', 'Unit Test 1', 'Unit Test 2', 'Final Test']
df = df[df['Name'] != 'Name'].dropna(subset=['Name'])

# Convert numeric columns
df['Class'] = pd.to_numeric(df['Class'], errors='coerce')
df['Unit Test 1'] = pd.to_numeric(df['Unit Test 1'], errors='coerce')
df['Final Test'] = pd.to_numeric(df['Final Test'], errors='coerce')

# Example: Average Final by Gender
print(df.groupby('Gender')['Final Test'].mean())
```
Include this script in the repository if desired.

## Files
- `pivot table practice insights.xlsx`: Original dataset.
- `README.md`: This file with analysis summary and instructions.

---
*Feel free to modify or extend the analysis as needed.*
"# Pivot_table_insights_Excel" 
