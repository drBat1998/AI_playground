1. Row and column names:
	Use the first row as column headers (or column names). Generally, columns represent variables.
	Use the first column as row names. Generally rows represent observations.
	Each row name should be unique, so remove duplicated names.
2. Naming conventions:
	1. Avoid names with blank spaces. Good column names: Long_jump or Long.jump
	2. Avoid names with special symbols: ?, $, *, +, #, (, ), -, /, }, {, |, >, < etc. Only underscore can be used.
	3. Avoid beginning variable names with a number. Use letter instead. Good column names: sport_100m or x100m. Bad column name: 100m
	4. Column names must be unique. Duplicated names are not allowed.
	5. R is case sensitive. This means that Name is different from Name or NAME.
	6. Avoid blank rows in your data
	7. Delete any comments in your file
	8. Replace missing values by NA (for not available)
	9. If you have a column containing date, use the four digit format. Good format: 01/01/2016. Bad format: 01/01/16