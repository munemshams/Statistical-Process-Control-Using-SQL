**Statistical Process Control (SPC) Analysis Using SQL Window Functions**

This project applies Statistical Process Control (SPC) techniques to real manufacturing data to identify out-of-control measurements in a production process. SPC helps ensure consistent product quality by detecting when measurements fall outside acceptable ranges based on historical process variation.

Using advanced SQL window functions—including ROW_NUMBER(), AVG() OVER(), and STDDEV() OVER()—this analysis computes dynamic control limits for each machine operator and flags products that require attention.

**Project Goal**

To determine whether the height of each manufactured part is within acceptable control limits, defined as:

$ucl = avg\_height + 3 * \frac{stddev\_height}{\sqrt{5}}$

$lcl = avg\_height - 3 * \frac{stddev\_height}{\sqrt{5}}$

Where:

-Rolling averages and standard deviations are computed over a window of the previous 4 items plus the current item (5 total).

-Any height outside these limits triggers an alert = TRUE.

The data is available in the `manufacturing_parts` table which has the following fields:
- `item_no`: the item number
- `length`: the length of the item made
- `width`: the width of the item made
- `height`: the height of the item made
- `operator`: the operating machine

**Files Included**

-Readme.md → Project Documentation

-notebook.ipynb → Notebook file containing the analysis

- SQL Query.sql → Raw SQL Query

- 2 raw datasets in the "data" folder

- 1 output CSV file in the "output" folder

**SQL Techniques Used**

Window functions

Rolling statistics

Nested subqueries

Custom calculated fields

Condition-based flagging

**Output**

For each manufactured part (starting from the 5th per operator), the query returns:

height

rolling average

rolling standard deviation

calculated UCL / LCL

alert → TRUE if out of bounds
