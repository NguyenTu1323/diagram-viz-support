# Data Engineering Pipeline Architecture

This diagram shows a modern data pipeline with medallion architecture (Bronze/Silver/Gold layers), visualization, and reverse ETL.

```mermaid
graph LR
    %% Data Sources
    subgraph sources["Data Sources"]
        API[APIs]
        DB[(Databases)]
        Files[Files/CSV]
        Stream[Event Streams]
    end

    %% Ingestion Layer
    subgraph ingestion["Data Ingestion"]
        ETL[ETL Tools<br/>Airbyte/Fivetran]
        CDC[CDC<br/>Change Data Capture]
    end

    %% Data Warehouse - Medallion Architecture
    subgraph warehouse["Data Warehouse"]
        subgraph bronze["🥉 Bronze Layer"]
            Raw[Raw Data<br/>No Transformations]
        end

        subgraph silver["🥈 Silver Layer"]
            Clean[Cleaned Data<br/>Validated & Deduplicated]
        end

        subgraph gold["🥇 Gold Layer"]
            Agg[Aggregated Data<br/>Business Metrics]
        end
    end

    %% Consumption Layer
    subgraph consumption["Data Consumption"]
        BI[BI Tools<br/>Tableau/Power BI]
        Analytics[Analytics<br/>Jupyter/Databricks]
        ML[ML Models<br/>Training & Inference]
    end

    %% Reverse ETL
    subgraph reverse["Reverse ETL"]
        RevETL[Reverse ETL<br/>Hightouch/Census]
    end

    %% Operational Systems
    subgraph operational["Operational Systems"]
        CRM[CRM<br/>Salesforce]
        Marketing[Marketing<br/>HubSpot]
        Support[Support<br/>Zendesk]
    end

    %% Flow
    API --> ETL
    DB --> CDC
    Files --> ETL
    Stream --> ETL

    ETL --> Raw
    CDC --> Raw

    Raw --> Clean
    Clean --> Agg

    Agg --> BI
    Agg --> Analytics
    Agg --> ML

    Agg --> RevETL
    RevETL --> CRM
    RevETL --> Marketing
    RevETL --> Support

    %% Styling
    style sources fill:#e1f5e1
    style ingestion fill:#e1e5ff
    style warehouse fill:#fff4e1
    style bronze fill:#cd7f32,color:#fff
    style silver fill:#c0c0c0,color:#000
    style gold fill:#ffd700,color:#000
    style consumption fill:#ffe1f5
    style reverse fill:#e1ffe1
    style operational fill:#ffe1e1
```

## Pipeline Stages

### 1. **Data Sources**
- APIs, databases, files, event streams
- Raw operational data from various systems

### 2. **Data Ingestion**
- ETL/ELT tools (Airbyte, Fivetran, dbt)
- Change Data Capture (CDC) for real-time updates

### 3. **Data Warehouse - Medallion Architecture**

#### 🥉 Bronze Layer (Raw)
- Raw, unprocessed data
- Exact copy from sources
- Immutable historical record

#### 🥈 Silver Layer (Cleaned)
- Cleaned and validated data
- Deduplicated records
- Type conversions applied
- Basic business rules enforced

#### 🥇 Gold Layer (Business)
- Aggregated, business-ready data
- Calculated metrics and KPIs
- Optimized for reporting
- Star/snowflake schema

### 4. **Data Consumption**
- BI dashboards and reports
- Ad-hoc analytics and exploration
- Machine learning model training

### 5. **Reverse ETL**
- Push enriched data back to operational systems
- Close the data loop
- Enable data-driven workflows in business tools

## Technologies

**Data Warehouse:** Snowflake, BigQuery, Databricks, Redshift
**ETL/ELT:** Airbyte, Fivetran, dbt, Apache Airflow
**Reverse ETL:** Hightouch, Census, Grouparoo
**BI Tools:** Tableau, Power BI, Looker, Metabase

## How to View

Press `Cmd+Shift+V` in VS Code to preview this diagram.
