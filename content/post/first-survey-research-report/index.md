+++
categories = ['projects']
date = '2024-11-24'
description = 'My first introduction to survey data analysis using Excel’s descriptive and inferential tools. I worked with a cleaned survey dataset and applied techniques like frequency distributions, central tendencies, t-tests, ANOVA, Pearson’s R correlation. This was my first time using these methods in a full project.'
image = 'https://file.garden/aSgFhNqucTCqhF8L/Portfolio/Ladder%20Art%20Space/frequency-table-1.png'
metaRobots = 'noindex, nofollow'
slug = 'first-survey-research-report-using-excel-descriptive-and-inferential-tools'
tags = ['Excel', 'data analysis']
title = 'My First Survey Research Report Using Excel Descriptive and Inferential Tools'
url = 'projects/excel-survey-research/:slug'
+++

# My First Survey Research Report Using Excel Descriptive and Inferential Tools

This project marks my introduction to analysing survey data using Excel. Working with a cleaned dataset for a real Melbourne business called [Ladder Art Space](https://maps.app.goo.gl/6ydbhVooYih97jK58), I applied both descriptive and inferential statistical methods to derive actionable insights.

*   **Descriptive statistics** were used to summarise the data through frequency distributions and measures of central tendency (mean).
*   **Inferential statistics** (T-tests, ANOVA, and Pearson’s R Correlation) were used to test hypotheses and verify statistical significance.

The full PDF is available [here](https://file.garden/aSgFhNqucTCqhF8L/Portfolio/Ladder%20Art%20Space/Ladder%20Art%20Space%20Research%20Report.pdf) if you are interested in the full research setup, hypothesis testing, results, and the appendix documenting the tools used.

<hr>

## Context of the Case Study
To demonstrate how these tools work in a business context, I will focus on [Research Question 3.3](https://file.garden/aSgFhNqucTCqhF8L/Portfolio/Ladder%20Art%20Space/Ladder%20Art%20Space%20Research%20Report.pdf#page=28) from the report: *"What is the most preferred communication message for PAS and PYP sessions at LAS?"*

To answer this, I set up the following hypothesis test:
*   **H₀ (Null Hypothesis):** There is no difference in customer interest levels between the types of messaging.
*   **H₁ (Alternative Hypothesis):** There is a meaningful difference in customer interest levels between the types of messaging.

## Descriptive Tools
I used frequency tables not just to count how many people voted for a specific message, but to find the **Mean (Average)**. This allows us to see which message had the highest overall "score" of interest.

![Frequency Table 1](https://file.garden/aSgFhNqucTCqhF8L/Portfolio/Ladder%20Art%20Space/frequency-table-1.png)

*Note: The detailed calculations for the mean and standard deviation can be found on [page 32-33 of the PDF](https://file.garden/aSgFhNqucTCqhF8L/Portfolio/Ladder%20Art%20Space/Ladder%20Art%20Space%20Research%20Report.pdf#page=32).*

To make this easier to understand, I visualized the results in a bar chart. As seen below, "Message 5" appears to be the most popular.

![Result of Frequency Table in Bar Chart](https://file.garden/aSgFhNqucTCqhF8L/Portfolio/Ladder%20Art%20Space/frequency-table-bar-chart.png)

To interpret what these numbers actually mean for the business (e.g., is a score of 3.5 "good"?), I compared the means against a standard [likert scale scoring table](https://www.google.com/url?sa=i&url=https%3A%2F%2Fwww.researchgate.net%2Ffigure%2FScoring-range-of-likert-scale-of-the-survey_tbl1_335752203&psig=AOvVaw3O4j3t2mf_abP1vRhhnyio&ust=1764404054794000&source=images&cd=vfe&opi=89978449&ved=0CBgQjhxqFwoTCPCn4sizlJEDFQAAAAAdAAAAABAa).

| Interpretation | Value | Range |
| --- | --- | --- |
| Not Interested At All | 1 | 1.00 - 1.80 |
| Slightly Interested | 2 | 1.81 - 2.60 |
| Moderately Interested | 3 | 2.61 - 3.40 |
| **Very Interested** | **4** | **3.41 - 4.20** |
| Extremely Interested | 5 | 4.21 - 5.00 |

**Finding:** "Message 5" resulted in a mean score within the **3.41 - 4.20** range. This indicates that the target audience is **"Very Interested"** in this specific message, whereas other messages scored lower.

<br>

## Inferential Tools

### ANOVA
While the descriptive data suggests Message 5 is the winner, I needed to prove this wasn't just a coincidence. I used **ANOVA (Analysis of Variance)** to determine if the difference in preference was statistically significant. ANOVA was chosen specifically because I was comparing **more than two independent variables** (Message 1, Message 2, Message 3, etc.).

![ANOVA](https://file.garden/aSgFhNqucTCqhF8L/Portfolio/Ladder%20Art%20Space/anova.png)

The most important metric here is the **P-value**.
*   A P-value < 0.05 means the data is statistically significant (unlikely to be due to chance).
*   The result here shows a P-value of **< 0.001** (listed as 1.7E-17).

**Conclusion:**
Because the P-value is effectively zero, we reject the null hypothesis and accept the alternative hypothesis. This confirms that there is a **statistically significant difference** in how customers react to the messages. Message 5 is objectively the superior choice for marketing communications for Ladder Art Space.

<hr>

### Other Inferential Tools Used

#### T-Test
I utilized T-Tests for research questions that involved comparing only two variables, such as: <br>
**Research Question 1.4:** ["Does interest toward PAS workshops differ from interest toward PYP Workshops?"](https://file.garden/aSgFhNqucTCqhF8L/Portfolio/Ladder%20Art%20Space/Ladder%20Art%20Space%20Research%20Report.pdf#page=14)

The variables analysed included:

| Demographic Groups Compared | Workshop Interests Measured |
| :--- | :--- |
| **Group A:** People with **No Pets**<br>**Group B:** People with **At Least One Pet** | • Interest in **Paint and Sip (PAS)**<br>• Interest in **Paint Your Pet (PYP)** |

Similarly, I used frequency tables for descriptive analysis to calculate the means first. I then applied the T-Test to obtain the P-value and determine which hypothesis to accept.


![T-Test](https://file.garden/aSgFhNqucTCqhF8L/Portfolio/Ladder%20Art%20Space/paired-sample-t-test.png)

**Note on Methodology:**
In the screenshot above, I originally applied a **Paired Sample T-Test**. However, looking back, an **Independent Sample T-Test** would have been the correct choice. This is because a Paired test is designed for the *same* group of people being measured twice, whereas here I am comparing two completely separate groups (Pet Owners vs. Non-Owners).

<br>

#### Pearson's R Correlation Test
Correlation test was used when examining the relationship between two **continuous variables**, as seen in <br>
**Research Question 1.3:**
[*"Is there any relationship between income and individual interest in PAS classes? How about how far they live from the city and their interests in painting and sip?"*](https://file.garden/aSgFhNqucTCqhF8L/Portfolio/Ladder%20Art%20Space/Ladder%20Art%20Space%20Research%20Report.pdf#page=11)

The continuous variables included:
*   Income ranges (e.g., $0 to >$75,000)
*   Distance (e.g., 0km to >50km)

The goal was to identify the strength of the linear relationship (Correlation), rather than cause-and-effect (Causation). For example, I tested if higher income correlates with higher interest, or if greater distance from the venue correlates with lower interest.

![Correlation Test](https://file.garden/aSgFhNqucTCqhF8L/Portfolio/Ladder%20Art%20Space/correlation-test.png)

Similarly, I used frequency tables for descriptive analysis to calculate the means first. I then applied the Correlation Test to obtain the P-value and determine which hypothesis to accept.

By analysing the P-value and the correlation coefficient (r), I could determine if a significant relationship existed between the demographics (income & distance) and customer interest in PAS.