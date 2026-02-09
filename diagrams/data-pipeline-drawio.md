# Data Engineering Pipeline (Draw.io Compatible)

This is a Draw.io-compatible version without styling. Copy the code below and paste into Draw.io → Insert → Mermaid.

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
        ETL[ETL Tools - Airbyte/Fivetran]
        CDC[CDC - Change Data Capture]
    end

    %% Data Warehouse - Medallion Architecture
    subgraph warehouse["Data Warehouse"]
        subgraph bronze["Bronze Layer - Raw"]
            Raw[Raw Data - No Transformations]
        end

        subgraph silver["Silver Layer - Cleaned"]
            Clean[Cleaned Data - Validated & Deduplicated]
        end

        subgraph gold["Gold Layer - Business"]
            Agg[Aggregated Data - Business Metrics]
        end
    end

    %% Consumption Layer
    subgraph consumption["Data Consumption"]
        BI[BI Tools - Tableau/Power BI]
        Analytics[Analytics - Jupyter/Databricks]
        ML[ML Models - Training & Inference]
    end

    %% Reverse ETL
    subgraph reverse["Reverse ETL"]
        RevETL[Reverse ETL - Hightouch/Census]
    end

    %% Operational Systems
    subgraph operational["Operational Systems"]
        CRM[CRM - Salesforce]
        Marketing[Marketing - HubSpot]
        Support[Support - Zendesk]
    end

    %% Flow Connections
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
```

## Changes for Draw.io Compatibility

- ✅ Removed all `style` statements
- ✅ Removed emoji icons (🥉🥈🥇)
- ✅ Simplified `<br/>` tags to single words
- ✅ Kept all connections and flow logic

## To Use in Draw.io

1. Copy the mermaid code above (between the ```mermaid markers)
2. Open Draw.io → **Arrange → Insert → Advanced → Mermaid**
3. Paste the code
4. Click **Insert**
5. **Manually add colors** in Draw.io after insertion

## Manual Styling in Draw.io

After inserting, you can manually style in Draw.io:
- Right-click shapes → **Edit Style**
- Change fill colors, borders, fonts
- This gives you full visual control!
