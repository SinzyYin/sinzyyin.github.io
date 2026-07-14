+++
categories = ['projects']
date = '2025-08-16'
description = 'My first introduction to MySQL Workbench and my first hands-on SQL project. This is a data cleaning exercise following Alex the Analyst’s YouTube tutorial.'
image = 'https://img.youtube.com/vi/4UltKCnnnTA/maxresdefault.jpg'
metaRobots = 'noindex, nofollow'
slug = 'data-cleaning-in-mysql-8.0'
tags = ['SQL', 'data cleaning']
title = 'My First SQL Data Cleaning Project using MySQL 8.0'
+++

##  
Through this **[Alex the Analyst's Data Cleaning in MySQL Tutorial](https://www.youtube.com/embed/4UltKCnnnTA?si=YeRISUkuREp-_OwN)**, 

<div style="padding-left: 50px;"> 
<iframe 
  width="420" 
  height="236" 
  src="https://www.youtube.com/embed/4UltKCnnnTA?si=YeRISUkuREp-_OwN" 
  title="YouTube video player" 
  frameborder="0" 
  allowfullscreen>
</iframe>
</div>


I gained hands-on experience with essential SQL techniques for cleaning and preparing data using **MySQL 8.0.43**. Below is a structured summary of the key concepts and methods I learned. The full workflow is documented here:
**[Data Cleaning in MySQL 8.0 Learning Notes]({{< ref "post/data-cleaning-in-MySQL-8.0-notes/index.md" >}})**


<hr>

## Data Cleaning

### 1. Removing Duplicates

I learned how to identify and eliminate duplicate rows using a combination of SQL functions and techniques:
- **Common Table Expressions (CTE)**: Helped organize and simplify complex queries, improving readability and reusability.
- `ROW_NUMBER()`: Assigned a unique number to each row within a partition, allowing me to detect duplicates.
- `WHERE` **clause**: Used to filter out rows where `ROW_NUMBER()` was greater than 1, indicating duplicates.

```mysql

WITH duplicate_cte AS (
    SELECT *,
        ROW_NUMBER() OVER (
            PARTITION BY column1, column2, column3) AS row_num
    FROM staging
)
SELECT *
FROM duplicate_cte
WHERE row_num > 1;
```
<hr>

### 2. Creating Table using the Create Table Statement

To manage and delete duplicates safely, I created a new staging table with an additional `row_num` column using the `Create Table Statement`:

```mysql
CREATE TABLE `staging2` (
  `column1` text,
  `column2` text,
  `column3` int DEFAULT NULL,
  `row_num` INT /* To Delete The Duplicates in Another Staging */
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci;
```
<hr>

### 3. Standardizing Data
#### 3.1 Trimming Whitespace & Trailing

I used the `TRIM()` function to remove leading and trailing spaces from string values.

```mysql
UPDATE staging SET
column1 = TRIM(column1)
column2 = TRIM(column2)
column3 = TRIM(column3);
```

#### 3.2 Renaming & Updating Inconsistent Data

To standardize inconsistent naming conventions, I used `LIKE` with wildcards (`%`) to filter similar values and then applied `UPDATE` to unify them.

Examples:
- `"Crypto Currency"`, `"Cryptocurrency"` → `"Crypto"`
- `"United States."`, `"United States of America"` → `"United States"`

```mysql
Select *
FROM staging
WHERE column1 LIKE 'Crypto%'
```

#### 3.3 Standardizing Dates

I converted string-based dates into proper date formats using `STR_TO_DATE()` to ensure consistency and enable date-based filtering or sorting.

```mysql
SELECT `date`
FROM staging;

UPDATE staging
SET `date` = STR_TO_DATE(`date`, '%m/%d/%Y)'
```
<hr>

### 4. Filtering for Null and Blank Values

I learned to use the `WHERE` clause to identify rows with missing or blank values using the below query:

```mysql
SELECT *
FROM staging
WHERE column1 IS NULL OR column1 = '';
```
<hr>

### 5. Handling Null and Blank Values

I learned how to identify and address rows with critical missing data (e.g., `total_laid_off`, `percentage_laid_off`) that could impact analysis accuracy.
- I applied a **self-join** technique to intelligently fill in missing values by referencing other rows with matching identifiers and valid data.

| Company Name | Column With Missing Values |
| ------------ | -------------------------- |
| ABC          | Null                       |
| ABC          | Tourism                    |
| BCD          | Null                       |
| BCD          | Financial                  |

```mysql
UPDATE layoffs_staging2 AS t1
JOIN layoffs_staging2 AS t2
	ON t1.column1 = t2.column1
SET t1.column2 = t2.column2
WHERE t1.column2 IS NULL
AND t2.column2 IS NOT NULL;
```


---
