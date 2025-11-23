# BigQuery Advanced SQL and Analytics Demo

This repository contains a comprehensive demonstration of advanced SQL and analytics capabilities within Google BigQuery. The included Jupyter Notebook (`advanced_sql_demo.ipynb`) guides you through a practical workflow, showcasing how to leverage BigQuery for data ingestion, discovery, real-time aggregation, complex business logic, and AI-driven analytics.

## Overview

This demo is designed for data engineers, analysts, and data scientists who want to explore the full potential of BigQuery beyond traditional data warehousing. It covers the following key areas:

* **Schema-on-Read & JSON Handling:** Learn how to ingest and query raw, semi-structured JSON data without a predefined schema.
* **Search & Vector Search:** Implement hybrid search capabilities combining keyword matching and semantic vector search.
* **Real-Time Aggregation:** Use advanced functions like HyperLogLog++ (HLL) sketches for high-speed, approximate distinct counting.
* **Complex Pattern Matching:** Analyze sequences of events using `MATCH_RECOGNIZE` for use cases like funnel analysis.
* **AI Integration:** Apply generative AI models directly within SQL queries to generate content, analyze sentiment, and categorize unstructured text.
* **Data Governance & Reuse:** Create reusable logic with User-Defined Functions (UDFs), User-Defined Aggregate Functions (UDAFs), and Table-Valued Functions (TVFs).
* **Change Data Capture (CDC):** Monitor and query data changes in real-time using BigQuery's native CDC capabilities.

## Prerequisites

To run this notebook, you will need:

* A Google Cloud Platform (GCP) project with billing enabled.
* The BigQuery API enabled.
* The Vertex AI API enabled (for AI functions).
* Appropriate IAM permissions to create datasets, tables, models, and connections (e.g., BigQuery Admin, Vertex AI User).

## Setup Instructions

1.  **Open the Notebook:** Open `advanced_sql_demo.ipynb` in Google Colab or Vertex AI Workbench.
2.  **Configure Variables:** Update the configuration variables at the top of the notebook (e.g., `PROJECT_ID`, `LOCATION`, `dataset_names`) if necessary. By default, the script attempts to auto-detect your project ID.
3.  **Run Setup Cell:** Execute the first code cell (`setup_environment`) to authenticate, create the BigQuery connection to Vertex AI, and set up the necessary datasets and tables.
    * **Note:** This step creates a remote connection (`bq_vertex_conn`) and grants the necessary IAM roles. Ensure you have the permissions to perform these actions.

## Key Features Demonstrated

### 1. Ingestion & Discovery
* **Schema-on-Read:** Query raw JSON data directly using `JSON_VALUE`, `JSON_QUERY`, and `JSON_KEYS`, demonstrating flexibility without rigid schema enforcement.
* **Search Indexes:** Create search indexes to accelerate point lookups and text searches.
* **Vector Search:** Generate embeddings for product descriptions using a remote Vertex AI model and perform semantic similarity searches.
* **Hybrid Search:** Combine keyword search and vector search to find relevant products that might be missed by keyword matching alone.

### 2. Real-Time Aggregations
* **Approximate Counting:** Compare the performance of exact `COUNT(DISTINCT ...)` versus approximate `APPROX_COUNT_DISTINCT` (using HyperLogLog++) for massive datasets.
* **Data Sketches:** Utilize HLL sketches for scalable, mergeable distinct counting, enabling sub-second analytics on pre-aggregated data.

### 3. Advanced Business Logic
* **Pattern Matching:** Use `MATCH_RECOGNIZE` to identify complex event sequences (e.g., View Product -> Add to Cart -> Purchase) within user sessions.
* **Multi-Dimensional Grouping:** Perform advanced aggregations using `GROUPING SETS`, `ROLLUP`, and `CUBE` to generate subtotals and grand totals in a single query.

### 4. AI Analytics
* **Generative AI:** Use `AI.GENERATE` to create synthetic customer reviews based on product descriptions.
* **AI Filtering:** Use `AI.IF` to filter records based on semantic meaning (e.g., "does this review mention a gift?").
* **Sentiment Analysis:** Use `AI.SCORE` to quantify the sentiment of text data.
* **Classification:** Use `AI.CLASSIFY` to categorize unstructured text into predefined buckets (e.g., Billing, Shipping, Quality).

### 5. Reusable Logic & Governance
* **UDFs (User-Defined Functions):** Encapsulate complex logic (e.g., tax calculations) into reusable SQL functions.
* **UDAFs (User-Defined Aggregate Functions):** Create custom aggregate functions (e.g., Average Order Value) for consistent metric definitions.
* **TVFs (Table-Valued Functions):** Parameterize table views (e.g., Sales by Country and Date) for secure and flexible data access.

### 6. Change Data Capture (CDC)
* **CDC Monitoring:** Enable change history on tables and use the `CHANGES()` function to query the stream of inserts, updates, and deletes for real-time auditing and synchronization.

## Cleanup

A cleanup cell is provided at the end of the notebook to delete the created datasets and resources, preventing unnecessary costs.

## Contact

* [Gmail](mailto:philipchop@google.com)
* [LinkedIn](https://www.linkedin.com/in/pchop/)

---
*This demo is for educational purposes and showcases the capabilities of Google Cloud's data analytics platform.*
