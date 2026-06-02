# DATA CONTRACT

data_product: Corporate_Data_Lakehouse_Pipeline
domain: company_raw_data_ingestion
description: This data product provides raw corporate, financial, and stock market data collected from Companies House and yFinance. It includes company overview, filing history, people information, balance sheet, cash flow, income statement, historical stock price, and company statistics data for downstream analytics, reporting, and financial performance analysis.

# DATA OWNERSHIP

technical_owner: Data Engineering Team
steward: Data Governance Team

# SOURCE SYSTEM DETAILS

source_system:
  - name: Companies House
    type: external company registry data source
    file_format: csv
    ingestion_method: batch
    source_location: Companies House API,yFinance API 


#SOURCE TABLE DETAILS
      - comp_house_overview (main table)
      - comp_house_filing_history
      - comp_house_people

      - yf_balance_sheet
      - yf_cash_flow
      - yf_history
      - yf_income_statement
      - yf_stats

# Data Architecture Layers

  [i] Bronze Layer
        - The Bronze layer stores raw data collected from source systems such as Companies House and yFinance.

  [ii] Silver Layer
        - The Silver layer stores cleaned, standardised, and validated data from the Bronze layer.

  [iii] Gold layer
        - bussiness standerd data in kimble architecture.

# Data Model Design


# Data Pipeline Design


    Companies House API / Files
          |
          v
yFinance API 
          |
          v
Raw Data Ingestion
          |
          v
**Bronze Layer**
Raw company and financial data
          |
          v
**Silver Layer**
Cleaned, standardised, validated data
          |
          v
**Gold Layer**
Business-ready star schema and analytics tables
          |
          v
Dashboards / Reports / Financial Analysis


# Data Quality Rules
    company_number must not be null  
    ticker must not be null  
    company_name must not be empty  
    duplicate company records must be removed  
    filing_date must be a valid date  
    stock_history_date must be a valid date  
    financial values must be valid numeric fields  
    stock prices must be valid numeric fields  
    stock volume must be >= 0  
    all foreign keys must exist in dimension tables  
    source_system must not be null  
    ingestion_timestamp must not be null  

# Data Refresh Strategy
    - Frequency: Daily batch processing  
      Latency: T+1, data available the next day  
      Pipeline Orchestration: Databricks Workflows / Azure Data Factory  

# Security & Governance

#BI & Consumption Layer

  Tools: Power BI, Tableau, Databricks SQL Analytics, and SQL reporting tools.

  Use Cases:
    Investment dashboards
    Risk analysis reports
    Company performance tracking
    Industry benchmarking

# Final Outcome

# Summary

    The Corporate Data Lakehouse Pipeline combines Companies House and yFinance data into a structured lakehouse platform. Raw data is stored in the Bronze layer, cleaned and validated data is stored in the Silver layer, and business-ready analytics data is stored in the Gold layer. This data contract defines the ownership, schema, quality rules, refresh strategy, security controls, and BI consumption approach needed to make the data reliable for company comparison, financial analysis, stock performance tracking, and reporting.
