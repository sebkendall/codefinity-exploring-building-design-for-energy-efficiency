# Imports and Datasets
pandas (pd) is used to load and manipulate tabular data.
matplotlib.pyplot (plt) lets you create plots and charts.

pd.read_csv(...) reads the CSV file into a DataFrame named df.
df.head() shows the first five rows so you can verify the data loaded correctly.
df.info() summarizes each column’s data type and non-null count.

# Scatter Plot of Heating Load vs. Relative Compactness
Extracted column X1 (relative compactness) and Y1 (heating load).
plt.scatter(...) draws a scatter plot with black “x” markers of size 50.
Titles and axis labels clarify what’s being plotted.
plt.tight_layout() adjusts spacing so labels/titles aren’t cut off.
plt.show() renders the figure.

# Orientation’s Effect on Heating
df.groupby('X6')['Y1'].mean() computes the mean heating load for each orientation value in X6.
The averages are printed.
.idxmin() finds which orientation yields the lowest average heating load.

# Glazing Area’s Effect on Cooling
Grouped the data in X7 (glazing area) and took the mean of Y2 (cooling load).
These means are printed and then visualized as a bar chart.
Bar width is set to 0.07 for readability.

# Comparing Buildings by Height
Created two subsets based on overall height X5 being 3.5 or 7.
Then computed the mean heating (Y1) and cooling (Y2) loads for each subset.

# Correlation Analysis
df.corr() builds a matrix of Pearson correlation coefficients for all numeric variables.
For Y1 and Y2:
- dropped the self-correlation.
- took absolute values for each correlation coefficient.
- sorted the data in descending order and picked the top three most strongly correlated features.

# Summary
Loaded and inspected the data on energy efficiency.
Visualised and quantified how design features (compactness, orientation, glazing, height) influence heating and cooling loads.
Identified which features are most closely linked to each target variable.

