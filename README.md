<div align="center">

# Midad

**EdTech Content Data Pipeline.**

</div>

<!-- Optional: add a short demo GIF here, e.g. -->

<!-- <p align="center"><img src="docs/images/demo.gif" width="700" alt="Midad demo"></p> -->

---

## Table of Contents

* [Project Overview](#project-overview)
* [Project Goal](#project-goal)
* [Architecture](#architecture)
* [Selected Sources](#selected-sources)
* [Medallion Layers](#medallion-layers)
* [API Layer](#api-layer)
* [Dashboard & User Interface](#dashboard--user-interface)
* [Technologies & Tools](#technologies--tools)
* [Project Structure](#project-structure)
* [Team](#team)

## Project Overview

This data engineering project includes:

1. **Data Source Selection:** Integration of multiple public educational content sources covering **AI, Data, and Cloud Computing**.
2. **Data Architecture:** Implementation of **Bronze, Silver, and Gold** layers using **Delta Lake** and the Medallion Architecture.
3. **Data Processing:** Data ingestion, cleaning, transformation, and standardization using **PySpark, SQL, Python, and Databricks notebooks**.
4. **Data Quality & Validation:** Validation of row counts, duplicate records, missing values, URLs, dates, and other data quality checks.
5. **Unified Data Model:** Combining educational content from different sources into a standardized Gold dataset for search, filtering, and discovery.
6. **API Integration:** A **FastAPI** backend that provides endpoints for content retrieval, search, filtering, pagination, dashboard statistics, and health checks.
7. **Dashboard & Web Application:** A **Streamlit** interface that provides a dashboard for exploring content distributions and a search interface for retrieving educational resources.
8. **GitHub Integration:** Version-controlling project notebooks, code, and documentation using GitHub.

This repository showcases skills in:

* Databricks & Delta Lake
* PySpark & SQL
* ETL Pipelines
* Data Cleaning & Transformation
* Data Quality & Validation
* Medallion Architecture
* FastAPI & REST APIs
* Streamlit & Data Visualization
* Python
* Git & GitHub

## Project Goal

The goal of this project is to build a **repeatable and structured data pipeline** that collects educational content from multiple public sources and transforms it into a **unified, high-quality dataset**.

The project focuses on content related to **Artificial Intelligence, Data, and Cloud Computing**, making it easier to **search, filter, and discover relevant educational resources** through an API and user interface.

## Architecture
<img width="1518" height="750" alt="Image" src="https://github.com/user-attachments/assets/5f91a493-aef6-4dff-9ed6-7c07f5c67dac" />

| Component | Purpose |
|---|---|
| **Sources** | Coursera, Microsoft Learn, GitHub, YouTube, Blogs, and Newsletters. |
| **Bronze Layer** | Stores raw data collected from APIs and RSS feeds. |
| **Silver Layer** | Cleans, standardizes, validates, tags, and deduplicates data. |
| **Gold Layer** | Unifies and organizes data into a curated dataset. |
| **Delta Lake** | Stores and manages the Bronze, Silver, and Gold layers. |
| **FastAPI** | Provides API endpoints for search, filtering, and data retrieval. |
| **Streamlit** | Provides the dashboard and Midad Explorer interface. |
| **Midad** | EdTech Content Data Pipeline for discovering educational resources. |

The pipeline follows a Medallion Architecture:

**Data Sources → Bronze → Silver → Gold → FastAPI → Streamlit**

## Selected Sources

The project uses several selected public source types:

* **Coursera** — educational courses
* **Microsoft Learn** — learning modules and resources
* **GitHub** — repositories and technical projects
* **YouTube** — educational videos
* **Educational Blogs** — technical articles and tutorials
* **Newsletters** — educational and technical newsletters through RSS feeds

## Medallion Layers

### Bronze Layer

Stores raw data collected from the selected sources with minimal transformation.

### Silver Layer

Cleans and standardizes the data by:

* Removing invalid records
* Handling missing values
* Standardizing topics and fields
* Parsing dates
* Removing duplicates
* Applying data quality rules

### Gold Layer

Combines the cleaned data from all sources into a unified dataset ready for consumption by the API and user interface.

The Gold dataset includes:

* Content ID
* Title
* Description
* Content Type
* Category
* Topic
* Difficulty Level
* Language
* Keywords
* Source
* Published Date
* Last Updated
* URL

## API Layer

The project includes a **FastAPI** backend that provides access to the curated Gold dataset.

Current API functionality includes:

* **Health Check** — verifies that the API is running and shows the number of loaded records.
* **Content Retrieval** — retrieves educational resources with optional filters.
* **Keyword Search** — searches resources using keywords.
* **Content Filtering** — filters by content type, topic, and source.
* **Content by ID** — retrieves a specific resource using its `content_id`.
* **Pagination** — controls the number of returned records and their starting position.
* **Filter Options** — provides available values for content type, topic, and source.
* **Dashboard Statistics** — provides aggregated statistics for sources, content types, topics, and difficulty levels.

The API loads the curated Gold dataset from a **Parquet snapshot** into memory when the application starts.

## Dashboard & User Interface

The project includes a **Streamlit-based web interface** that provides users with a simple way to explore and interact with the curated educational content dataset.

### Dashboard

The dashboard provides a visual overview of the collected educational resources, including:

* **Content by Source:** Distribution of resources across different sources.
* **Content by Type:** Distribution of resources by content type.
* **Topics:** Distribution of resources across different topics.
* **Difficulty Level:** Distribution of resources by difficulty level.

The interface also displays the latest **Data Quality** status.

### Midad Explorer

The Midad Explorer allows users to:

* Search educational resources using keywords.
* Filter resources by **Content Type**, **Topic**, and **Source**.
* Specify the number of results to display.
* View retrieved resources in a structured data table.

The Streamlit application retrieves data and statistics through the **FastAPI REST API**.

## Technologies & Tools

* **Databricks** — Developed and ran the data engineering pipeline.
* **Delta Lake** — Stored the Bronze, Silver, and Gold layers.
* **PySpark** — Processed and transformed the data.
* **SQL** — Created tables, queried data, and performed data validation.
* **Python** — Used for data processing, API development, and application logic.
* **FastAPI** — Built the REST API.
* **Uvicorn** — Ran the FastAPI application locally.
* **Pandas** — Loaded and processed the Gold dataset for the API.
* **PyArrow** — Supported reading the Gold Parquet snapshot.
* **Streamlit** — Built the web interface and dashboard.
* **Requests** — Connected the Streamlit application to the FastAPI.
* **Altair** — Created dashboard visualizations.
* **JSON & CSV** — Used for storing collected raw data.
* **Parquet** — Used for the Gold dataset snapshot consumed by the API.
* **Git & GitHub** — Managed and version-controlled the project.
* **Visual Studio Code** — Used to develop the API and Streamlit application.

## Project Structure

```text
Midad-EdTech-Content-Data-Pipeline/
│
├── images/                              # Project screenshots
│   ├── midad_dashboard.png             # Dashboard screenshot
│   └── midad_explorer.png              # Explorer interface screenshot
│
├── data sources/                        # Data collection sources
│   ├── notebooks/                       # Data collection notebooks
│   │   ├── API's_sources.ipynb          # Collects data from APIs
│   │   └── RSS Feeds.ipynb              # Collects data from RSS feeds
│   │
│   └── raw/                             # Raw collected datasets
│       ├── api_sources_1200.json        # Raw API data
│       └── rss_feeds_600.json           # Raw RSS data
│
├── exploration/                         # Data exploration notebooks
│   ├── 04_data_exploration_bronze.ipynb # Explores Bronze data
│   ├── 07_data_exploration_silver.ipynb # Explores Silver data
│   └── 10_data_exploration_gold.ipynb   # Explores Gold data
│
├── midad data pipeline/                 # Main Databricks pipeline
│   ├── setup/                           # Project setup
│   │   └── 01_create_schema.ipynb       # Creates catalog and schemas
│   │
│   ├── bronze/                          # Bronze layer
│   │   ├── 02_ddl_bronze.ipynb          # Creates Bronze tables
│   │   └── 03_load_bronze.ipynb         # Loads raw data into Bronze
│   │
│   ├── silver/                          # Silver layer
│   │   ├── 05_ddl_silver.ipynb          # Creates Silver tables
│   │   └── 06_load_silver.ipynb         # Cleans and loads Silver data
│   │
│   ├── gold/                            # Gold layer
│   │   └── 09_load_gold.ipynb           # Creates the final Gold dataset
│   │
│   └── data quality/                    # Data quality checks
│       ├── 08_data_quality_silver.ipynb # Validates Silver data
│       └── 11_data_quality_gold.ipynb   # Validates Gold data
│
├── api/                                 # FastAPI backend
│   ├── main.py                          # API endpoints and logic
│   └── requirements.txt                 # API dependencies
│
├── streamlit_app/                       # Streamlit web application
│   ├── app.py                           # Dashboard and Midad Explorer
│   └── requirements.txt                 # Streamlit dependencies
│
├── data/                                # API and application data
│   ├── gold_content_snapshot.parquet    # Gold dataset snapshot
│   └── quality_report.json              # Data quality results
│
├── .gitignore                           # Files excluded from GitHub
├── README.md                            # Project documentation
└── requirements.txt                     # Project dependencies
```

---

## Team

Developed as part of the **SDA Data Engineering Bootcamp**.

* Amal Al Dawsari — [@amal426](https://github.com/amal426)
* Ewan Hamoh — [@iiewan](https://github.com/iiewan)
* Renad Alghamdi — [@renad-ghazi](https://github.com/renad-ghazi)

<div align="center">

If you find this project useful, please consider giving it a star.

</div>
