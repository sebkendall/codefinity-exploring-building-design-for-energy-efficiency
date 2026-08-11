-e This file is a merged representation of the entire codebase, combined into a single document

## Purpose
This file contains a packed representation of the entire repository's contents.
It is designed to be easily consumable by AI systems for analysis, code review,
or other automated processes.

## File Format
The content is organized as follows:
1. This summary section
2. Repository information
3. Directory structure
4. Multiple file entries, each consisting of:
  a. A header with the file path (## File: path/to/file)
  b. The full contents of the file in a code block or first three lines for files with .csv extensions

## Usage Guidelines
- This file should be treated as read-only. Any changes should be made to the
  original repository files, not this packed version.
- When processing this file, use the file path to distinguish
  between different files in the repository.
- Be aware that this file may contain sensitive information. Handle it with
  the same level of security as you would the original repository.

## Notes
- This file includes only .ipynb and .csv file contents in full or partial form
- All other file types are represented only through the directory structure
- Binary files are not included in this packed representation. Please refer to the Repository Structure section for a complete list of file paths, including binary files

# Directory Structure

````
./
energy_efficiency.csv
fs_report.md
main.py
````
-e 
# Files
-e 
## File: energy_efficiency.csv
````
,X1,X2,X3,X4,X5,X6,X7,X8,Y1,Y2
0,0.98,514.5,294.0,110.25,7.0,2.0,0.0,0.0,15.55,21.33
1,0.98,514.5,294.0,110.25,7.0,3.0,0.0,0.0,15.55,21.33
````
-e 
## File: main.py
````
import pandas as pd
import matplotlib.pyplot as plt

# Load the dataset
df = pd.read_csv("energy_efficiency.csv")

# Task 1
compactness = df['X1']
heating_load = df['Y1']

plt.scatter(compactness, heating_load, marker='x', s=50, color='black')
plt.title('Heating Load vs Relative Compactness')
plt.xlabel('Relative Compactness')
plt.ylabel('Heating Load')
plt.tight_layout()
plt.show()

# Task 2
avg_hl = df.groupby('X6')['Y1'].mean()
print(f'\nThe average Heating Load per Orientation is: \n{avg_hl}\n')

best_orientation = avg_hl.idxmin()
print(f'The best orientation effect on heating is: {best_orientation}\n')

# Task 3
avg_cl = df.groupby('X7')['Y2'].mean()
print(f'The average Cooling Load per Glazing Area is: \n{avg_cl}\n')

plt.bar(avg_cl.index, avg_cl.values, width=0.07)
plt.title('Mean Cooling Load per Glazing Area')
plt.xlabel('Glazing Area')
plt.ylabel('Mean Cooling Load')
plt.tight_layout()
plt.show()

# Task 4
subset_3_5 = df[df['X5'] == 3.5]
subset_7 = df[df['X5'] == 7]

x5_mean_3_5 = {'Y1_mean_3.5' : subset_3_5['Y1'].mean(), 'Y2_mean_3.5' : subset_3_5['Y2'].mean()}

x5_mean_7 = {'Y1_mean_7' : subset_7['Y1'].mean(), 'Y2_mean_7' : subset_7['Y2'].mean()}

print(f'\nMean Y1 and Y2 for X5 = 3.5: {x5_mean_3_5}')
print(f'Mean Y1 and Y2 for X5 = 7: {x5_mean_7}')

# Task 5
corr_matrix = df.corr()

top3_Y1 = corr_matrix['Y1'].drop('Y1').abs().sort_values(ascending=False).head(3)
print(f'\nThe top 3 values most correlated with Y1 are: \n{top3_Y1}')

top3_Y2 = corr_matrix['Y2'].drop('Y2').abs().sort_values(ascending=False).head(3)
print(f'\nThe top 3 values most correlated with Y2 are: \n{top3_Y2}')


````
