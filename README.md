1. AI SQL ASSISTANT WITH LANGCHAIN



An AI-powered SQL assistant that converts natural-language questions into SQL queries and executes them against an Amazon sales dataset using Python, LangChain, an LLM running through Ollama, and SQLite.



The project enables users to explore sales performance, product categories, monthly revenue, order statuses, and cancellation rates without manually writing SQL queries.



2. PROJECT OVERVIEW



Analyzing large sales datasets often requires knowledge of SQL and database structures. This project simplifies that process by allowing users to ask business questions in plain English.



The assistant generates SQL from the user's question, validates the generated query, executes approved queries against a read-only SQLite connection, and displays the results as a Pandas DataFrame.



KEY FEATURES



1. Natural Language to SQL: Converts questions written in English into SQL queries using an LLM.

2. Automated Query Execution: Executes generated queries against a SQLite database.

3. Sales Data Analysis: Analyzes order values, product categories, fulfilment methods, order statuses, and monthly sales.

4. SQL Safety Checks: Restricts queries to `SELECT` statements, blocks multiple SQL statements and selected unsafe SQL patterns, and requires the approved amazon\_sales table.

5. Read-Only Database Access: Uses SQLite read-only mode and enables query\_only.

6. Result Size Control: Adds a default `LIMIT 100` when the generated query does not specify a limit.

7. Error Handling: Handles validation errors, database errors, and empty query results.

8. Interactive Analysis: Allows users to ask different business questions without manually writing each SQL query.



TECH STACK



1. Programming Language: Python

2. LLM Framework: LangChain

3. Language Model Runtime: Ollama

4. Database:SQLite

5. Data Processing: Pandas

6. Development Environment: Jupyter Notebook

7. Query Language: SQL



DATASET



Dataset: Amazon Sale Report



The dataset contains order-level sales information used to explore product performance, fulfilment, order status, shipping details, and order value.



| Attribute       | Details          |

| --------------- | ---------------- |

| Total records   | 128,969          |

| Total columns   | 22               |

| Database table  | amazon\_sales     |

| Database engine | SQLite           |

| Query results   | Pandas DataFrame |



The dataset covers records from March 31, 2022, to June 29, 2022.



 EXAMPLE BUSINESS QUESTIONS

The assistant was tested with questions such as:


1. Which 5 product categories have the highest total order value?

2. What is the total order value for each month?

3. Which product categories have the highest cancellation percentage?

4. What is the cancellation rate for each fulfilment method?

5. How many records exist for each order status?

6. Which states have the highest total recorded order value?



SAMPLE RESULTS AND INSIGHTS



1. Top Product Categories by Order Value



The assistant generated a query using SUM(), GROUP BY, ORDER BY DESC, and LIMIT 10.



| Category      | Total order value |

| ------------- | ----------------: |

| Set           |     39,202,022.03 |

| kurta         |     21,299,013.70 |

| Western Dress |     11,216,072.69 |

| Top           |      5,347,792.30 |

| Ethnic Dress  |        791,217.66 |



Insight: Set and kurta contributed the highest total order values among the product categories in this dataset.



2. Cancellation Rate by Fulfilment Method


The cancellation rate was calculated as: `Cancellation Rate = Cancelled Records / Total Records × 100`



| Fulfilment method | Total records | Cancelled records | Cancellation rate |

| ----------------- | ------------: | ----------------: | ----------------: |

| Merchant          |        39,277 |             6,861 |            17.47% |

| Amazon            |        89,692 |            11,468 |            12.79% |



Insight: Merchant-fulfilled records had a higher cancellation rate than Amazon-fulfilled records in this dataset. This is an observational result and does not establish the cause of the difference.



3. Monthly Order Value


The assistant generated a monthly aggregation query using SQLite's `strftime()` function.



| Month      | Total order value |

| ---------- | ----------------: |

| March 2022 |        101,683.85 |

| April 2022 |     28,838,708.32 |

| May 2022   |     26,225,004.75 |

| June 2022  |     23,424,646.38 |



Insight: April recorded the highest total order value among the four months represented in the dataset.



SQL SAFETY AND ERROR HANDLING


1. Allows queries beginning with `SELECT`.

2. Rejects multiple SQL statements.

3. Blocks SQL comments and selected unsafe keywords.

4. Requires queries to reference `amazon\_sales`.

5. Adds a default row limit when one is absent.

6. Opens SQLite in read-only mode.

7. Enables SQLite's `query\_only` setting.

8. Handles invalid-table queries and queries returning no matching records.



Safety tests were performed for `DROP TABLE`, `DELETE`, `UPDATE`, multiple-statement SQL injection attempts, invalid tables, and empty query results.



SKILLS DEMONSTRATED



1. Python programming

2. SQL querying and aggregation

3. SQLite database integration

4. Pandas data handling

5. LangChain and LLM integration

6. Natural-language-to-SQL workflows

7. Prompt engineering

8. SQL validation and defensive programming

9. Error handling and debugging

10. Business analytics and insight generation


CONCLUSION

This project demonstrates how LLMs can simplify database analysis by translating natural-language questions into SQL. It combines database querying, Python data processing, LLM integration, and basic safety controls in a practical sales analytics use case.



