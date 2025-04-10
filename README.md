![image](https://github.com/user-attachments/assets/4ff409e2-0fa4-4469-9f70-e7f93c090bd8)

# Videogames-Sales-SQL
Analysis of Trends, Audience Preferences, and Market Demand Across 40 Years of the Gaming Industry

## Summary
This dataset contains info on video game sales, downloads, and user engagement across platforms. It includes details such as game title, genre, platform, release date, total sales (physical & digital), regional distribution, revenue, ratings, and in-game purchases.

### Dataset Overview:
| *Column* | *Type* |
| ----------- | ----------- |
| rank | INTEGER |
| name | TIMESTAMP |
| platform | STRING |
| year | STRING |
| genre | STRING |
| publisher | STRING |
| NA_sales | FLOAT |
| EU_sales | FLOAT |
| JP_sales | FLOAT |
| other_sales | FLOAT |
| global_sales | FLOAT |

Where:
- **rank** - position in sales ranking;
- **name** - game title;
- **platform** - console/PC system;
- **year** - release year;
- **genre** - type of game (Action, RPG, etc.);
- **publisher** - company that released the game;
- **NA_sales** - north America sales (in millions);
- **EU_sales** - europe sales (in millions);
- **JP_sales** - japan sales (in millions);
- **other_sales** - sales in other regions (in millions);
- **global_sales** - total worldwide sales (in millions).

### Sample Data Preview:
<img width="1375" alt="Screenshot 2025-04-11 at 00 05 55" src="https://github.com/user-attachments/assets/d159a2a1-d8b7-4974-8bda-d4e1f851a6e7" />

## Data Exploration
Given this dataset, the following questions were explored:
1. Who are the top 5 publishers that released the most successful video games?
2. Which video games were relatively popular and had similar sales across North America, Europe, and Japan?
3. What is the longest time gap between two consecutive releases by the same publisher?
4. Which game genres were the most popular in each decade from 1980 to 2020?
5. What platform was the most popular in each of the three major regions?
6. Which game genres are historically preferred in each region?
7. What genre does each publisher tend to specialize in?

## Key Techniques and Approaches
1. Aggregation and filtering to identify top publishers (`COUNT()`, `SUM()`, `GROUP BY`);
2. Sales similarity check across regions using absolute difference (`ABS(NA_sales - EU_sales) <= 0.5`);
3. Window functions for calculating time gaps between releases (`LEAD() OVER(PARTITION BY ...)`);
4. Common table expressions (CTEs) for structuring complex logic (`WITH years AS (...)`);
5. Data type casting to enable numeric calculations (`CAST(year AS INT)`);
6. Use of WHERE clause filters to exclude irrelevant or incomplete records (`year <> 'N/A'`, `publisher <> 'Unknown'`);
7. Sorting to highlight significant results, such as highest global sales or largest gaps in release years (`ORDER BY global_sales DESC`, `ORDER BY year_diff DESC`);
8. Multi-condition filtering to enforce strict comparison rules (e.g., similar sales values across regions);
9. Optional use of `QUALIFY` vs. subqueries for filtering rows based on window functions, improving clarity and reducing nesting in platforms like BigQuery.

## Technologies Used
- BigQuery SQL;
- Google Cloud Platform (BigQuery);
- Jupyter Notebooks (via VS Code);
- GitHub for version control.

The complete set of SQL queries for each insight (with commentary) can be found in [this notebook](Videogames.ipynb).
