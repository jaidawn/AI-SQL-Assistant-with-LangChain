\# AI SQL Assistant with LangChain



An AI-powered SQL assistant that converts natural-language questions into SQL queries and executes them against an Amazon sales dataset using Python, LangChain, an LLM running through Ollama, and SQLite.



The project enables users to explore sales performance, product categories, monthly revenue, order statuses, and cancellation rates without manually writing SQL queries.



\# Project Overview



Analyzing large sales datasets often requires knowledge of SQL and database structures. This project simplifies that process by allowing users to ask business questions in plain English.



The assistant generates SQL from the user's question, validates the generated query, executes approved queries against a read-only SQLite connection, and displays the results as a Pandas DataFrame.



\# Key Features



\- Natural Language to SQL: Converts questions written in English into SQL queries using an LLM.

\- Automated Query Execution: Executes generated queries against a SQLite database.

\- Sales Data Analysis: Analyzes order values, product categories, fulfilment methods, order statuses, and monthly sales.

\- SQL Safety Checks: Restricts queries to `SELECT` statements, blocks multiple SQL statements and selected unsafe SQL patterns, and requires the approved amazon\_sales table.

\- Read-Only Database Access: Uses SQLite read-only mode and enables query\_only.

\- Result Size Control: Adds a default `LIMIT 100` when the generated query does not specify a limit.

\- Error Handling: Handles validation errors, database errors, and empty query results.

\- Interactive Analysis: Allows users to ask different business questions without manually writing each SQL query.



\# Tech Stack



\- Programming Language: Python

\- LLM Framework: LangChain

\- Language Model Runtime: Ollama

\- Database:SQLite

\- Data Processing: Pandas

\- Development Environment: Jupyter Notebook

\- Query Language: SQL



\# Dataset



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



\# Example Business Questions



The assistant was tested with questions such as:



\- Which 10 product categories have the highest total order value?

\- What is the total order value for each month?

\- Which product categories have the highest cancellation percentage?

\- What is the cancellation rate for each fulfilment method?

\- How many records exist for each order status?

\- Which states have the highest total recorded order value?



\## Sample Results and Insights



\### 1. Top Product Categories by Order Value



The assistant generated a query using SUM(), GROUP BY, ORDER BY DESC, and LIMIT 10.



| Category      | Total order value |

| ------------- | ----------------: |

| Set           |     39,202,022.03 |

| kurta         |     21,299,013.70 |

| Western Dress |     11,216,072.69 |

| Top           |      5,347,792.30 |

| Ethnic Dress  |        791,217.66 |



Insight: Set and kurta contributed the highest total order values among the product categories in this dataset.



\### 2. Cancellation Rate by Fulfilment Method



The cancellation rate was calculated as:



`Cancellation Rate = Cancelled Records / Total Records × 100`



| Fulfilment method | Total records | Cancelled records | Cancellation rate |

| ----------------- | ------------: | ----------------: | ----------------: |

| Merchant          |        39,277 |             6,861 |            17.47% |

| Amazon            |        89,692 |            11,468 |            12.79% |



Insight: Merchant-fulfilled records had a higher cancellation rate than Amazon-fulfilled records in this dataset. This is an observational result and does not establish the cause of the difference.



\### 3. Monthly Order Value



The assistant generated a monthly aggregation query using SQLite's `strftime()` function.



| Month      | Total order value |

| ---------- | ----------------: |

| March 2022 |        101,683.85 |

| April 2022 |     28,838,708.32 |

| May 2022   |     26,225,004.75 |

| June 2022  |     23,424,646.38 |



Insight: April recorded the highest total order value among the four months represented in the dataset.



\## SQL Safety and Error Handling



The project includes several safeguards designed to reduce the risk of unsafe SQL execution.



\- Allows queries beginning with `SELECT`.

\- Rejects multiple SQL statements.

\- Blocks SQL comments and selected unsafe keywords.

\- Requires queries to reference `amazon\_sales`.

\- Adds a default row limit when one is absent.

\- Opens SQLite in read-only mode.

\- Enables SQLite's `query\_only` setting.

\- Handles invalid-table queries and queries returning no matching records.



Safety tests were performed for `DROP TABLE`, `DELETE`, `UPDATE`, multiple-statement SQL injection attempts, invalid tables, and empty query results.





\*Adjust the filenames and directory structure to match the files actually included in your repository.\*



\## Skills Demonstrated



\- Python programming

\- SQL querying and aggregation

\- SQLite database integration

\- Pandas data handling

\- LangChain and LLM integration

\- Natural-language-to-SQL workflows

\- Prompt engineering

\- SQL validation and defensive programming

\- Error handling and debugging

\- Business analytics and insight generation



\## Future Improvements



\- Build a Streamlit web interface for interactive querying.

\- Add visualizations for sales trends and product performance.

\- Strengthen SQL validation using a dedicated SQL parser.

\- Add automated tests for query correctness and security edge cases.

\- Improve handling of dates, missing values, and ambiguous questions.

\- Add query logging and performance monitoring.



\## Conclusion



This project demonstrates how LLMs can simplify database analysis by translating natural-language questions into SQL. It combines database querying, Python data processing, LLM integration, and basic safety controls in a practical sales analytics use case.



