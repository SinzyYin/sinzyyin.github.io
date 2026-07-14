+++
categories = ['learning notes']
date = '2025-07-02 12:02:00+0000'
metaRobots = 'noindex, nofollow'
slug = 'how-christine-jiang-changed-my-view-on-data-cleaning-and-analysis-notes'
tags = ['data', 'data cleaning', 'data analysis']
title = 'How Christine Jiang Changed the Way I See Data Cleaning and Analysis - Learning Notes of her Tutorials'
url = 'reviews/:slug'
+++

> 📌 **Disclaimer:**  
> This note is created for personal study purposes based on two YouTube videos by [Christine Jiang](https://www.youtube.com/@christinejiangdata):  
> - [The ONLY Data Cleaning Framework You Need | Playbook Ep. 3](https://youtu.be/y9wFFD2bXQM?si=hqOJv61GPB2KgBdD)
> - [How to NAIL Exploratory Data Analysis | Playbook Ep. 4](https://youtu.be/deS6lETubdU?si=aqku6H_iZjrvE2jk)
>  
> All content belongs to the original creator. This document summarizes and reflects my understanding and is not a transcript or official material.


## Ep. 3 - The ONLY Data Cleaning Framework You Need

### **CLEAN** Framework
- C - *Conceptualize the Data*
  - Identify the Grain
  - Identify the Metrics
  - Identify Dimensions
- L - *Locate Solvable Issues*
  - Inconsistent Types
  - Inconsistent Spelling
  - Nulls & Duplicates
- E - *Evaluate Unsolvable Issues*
  - Missing Values
  - Outliers
  - Business Logic
- A - *Augment the Data*
  - New Dimensions
  - New Metrics
  - New Time Grains
- N - *Note & Document*

### How Christine Jiang Cleans Her Data
1. Duplicate data into a new sheet
2. Turn whole sheet into a table
3. Click on filter & sort to roughly see the issues
4. Document those issues

| Table  | Columns     | Issues                    | Row Count | Solvable? | Resolution |
| ------ | ----------- | ------------------------- | --------- | --------- | ---------- |
| orders | purchase_ts | inconsistent data formats | 10        | Y         |   ...         |
| orders | purchase_ts | missing dates| 1 | N         |  ...         |

5. Copy & Paste those issues into another sheet, then clean it
6. Clean the issues column by inserting the empty column to clean the data
| Product_Name | Product_Name_Cleaned |
| --- | --- |
   - also uses *formulas* like ```=IF(A1 = " ", ABC, A1)```

7. Choose to ***Impute*** (or Not)
   - Data analysts seldom use imputation on the job. Their job is to surface the truth of what the data says - when using imputation, there is a risk of introducing bias
   - You should only impute data if:
     - You have a reliable source of truth
     - You have clear business logic to infer the value confidently
     - You can fill it in with a representative sample
8. ***Augment*** the Data
   - Slice & Dice by other Time Grains
   - Add more Dimensions for Exploration
   - Calculate New Metrics
9.  Note & Document



| Table  | Columns     | Issues                    | Row Count | Magnitude | Solvable? | Resolution                                          |
| ------ | ----------- | ------------------------- | --------- | --------- | --------- | --------------------------------------------------- |
| orders | purchase_ts | inconsistent data formats | 10        | Y         | Y         | used DATE functions to reformat the dates correctly |
| orders | purchase_ts | missing dates             | 1         | N         | N         | **LEFT AS IS** - low magnitude & no way to infer    |

<br>

---

## Ep. 4 - How to NAIL Exploratory Data Analysis

### **READY** Framework
- R - *Representative Data*
- E - *Exec-Driven Questions*
- A - *Analytical Frameworks (SCAN)*
- D - *Data Best Practices*
- Y - *Your Insights, Your Impact*

### How Christine Jiang Analyse Her Data
1. ##### **Requirement Gathering**
   - Narrow the Scope & Get Intentional about What the Deliverable Should Actually be (see below on how vague if it's not clarified, it can mean many things)
   - Goal:
      -  Understand What's in the Data & Spot any Obvious Trends/Patterns/Anomalies
      - See Whether or Not the Data Can Answer Stakeholder Questions
      -  To Reduce Analysis Paralysis


| Type                    | Big Question                                                                   | Transformed into Finance Metrics                        | Transformed into Marketing Metrics                                                            |
| ----------------------- | ------------------------------------------------------------------------------ | ------------------------------------------------------- | --------------------------------------------------------------------------------------------- |
| Overall Trends          | What are the overall trends in sales?                                          | What are the overall trends in REVENUE?                 | What are the overall trends in CAMPAIGN ROI?                                                  |
| Growth Rates            | What were our monthly & yearly growth rates?                                   | What were our monthly & yearly in REVENUE?              | What were our monthly & yearly in CAMPAIGN ROI?                                               |
| Performance Measurement | How is the program/product feature performing                                  | How is the RETENTION PROGRAM performing?                | How is the LOYALTY PROGRAM performing?                                                        |
| KPI Reporting           | What were the refund rates/average order value (AOV) over the last few months? | What were the REVENUE/PROFITS over the last few months? | What were the LIFETIME VALUE (LTV)/ CUSTOMER ACQUISITION COST (CAC) over the last few months? |


- --> **Clarify the Metrics**
  - Are we looking at SALES REVENUE, AOV, or ORDER COUNT?
- --> **Clarify the Dimensions**
  - Time? Geographic/Regional? Product? Other Demographic?
- --> **Clarify the Deliverable**
  - Who is the Audience? 
  - What is the Business Context?
  - Deliverable Format?


| Before Requirement Gathering                | After Requirement Gathering                                                                                                                    |
| ------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------- |
| How did sales look over the Covid-19 years? | How did total sales revenue perform across products from 2019 to 2022? Conduct initial analysis for managers in marketing, product and finance |


1. **Analytical Framework (SCAN)**
  - S - Stakeholder Goals
    - What KPI's & Dimensions Matter the Most?
  - C - Columns & Coverage
    - What Data is Available & How Can We Use It?
  - A - Aggregates & Anomalies
    - The High Level Metrics, Outliers, Unexpected Patterns
  - N - Notable Segments
    - Slice by Category, Time, and other key dimension to Surface Early Insights


| SCAN Framework         | -                                                                              | Initial Analysis                                                                                                     |
| ---------------------- | ------------------------------------------------------------------------------ | -------------------------------------------------------------------------------------------------------------------- |
| Stakeholder Goals      | What KPI's & Dimensions Matter the Most?                                       | no direct decision made yet - focus on high-level trends & patterns, most important dimension is usd price (revenue) |
| Columns & Coverage     | What Data is Available & How Can We Use It?                                    | we'll use usd_price, product_name, purchase_time                                                                     |
| Aggregates & Anomalies | The High Level Metrics, Outliers, Unexpected Patterns                          | look at the total usd_price across months, products, averages. identify minimum, maximum, and outliers               |
| Notable Segments       | Slice by Category, Time, and other key dimension to Surface Early Insights<br> | can also slice by region, and other user demographic like marketing_channel, account_creation_method                 |

- Use **Pivot Table** & **Conditional Formating** to Conduct Initial Analysis
 - ex: view product_name, sales, by month (purchase_time)
    - can make some initial observations about sales trends (by month, seasons, years), sales ranges (min - max)



| Month       | Product A | Product B | Product C |
| ----------- | --------- | --------- | --------- |
| 1           | 100       | 50        | 120       |
| 2           | 200       | 80        | 100       |
| 3           | 150       | 60        | 90        |
| 4           | 180       | 70        | 110       |
| ... 12      | 250       | 50        | 100       |
| Grand Total | 1000      | 560       | 890       |
- Add a Sparkline Underneath the Pivot Table
  - = easy way to get a sense for initial trends of a metric without needing to create a full graph
<br>

    -  ![spark lines in excel](https://chandoo.org/img/2010/sparklines-in-pivot-tables.png)
3. Document in Observation Log

| tab           | metric/dimension | finding                                                                                                                                                           | relevant team    |
| ------------- | ---------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------- |
| pivot_table_1 | usd_price/month  | Total Sales across 2019-2022 is $6.1M, monthly sales ranges from $80K to $500K                                                                                    | finance          |
| pivot_table_1 | usd_price/month  | Best Performing is Product A ($1000K), Worst Performing is Product B ($560K), might be missing data, need to check with team                                      | finance, product |
| pivot_table_1 | usd_price/month  | Worst Perfoming Product is Product B, which are responsible for less than 2% of sales                                                                             | product          |
| pivot_table_1 | usd_price/month  | December 2022 saw a large spike in sales, seems like fall & winter months before the new year perform best. May be related to holiday or promotions at that time. | marketing        |



> **Here is My Review of This Tutorial:**  
> - [How Christine Jiang Changed the Way I See Data Cleaning and Analysis – Review of her Tutorials]({{< ref "post/christine-jiang/christine-jiang-0.md">}})
>   
> This review captures my personal reflections and key takeaways from the tutorial. It is written for **self-study** and the **ideas belong to the original creator**.
