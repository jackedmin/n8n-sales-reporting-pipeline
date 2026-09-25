# Automated E-Commerce Sales Reporting Pipeline (n8n Workflow)

## Overview
An end-to-end automation pipeline built in **n8n** that extracts raw e-commerce order data, cleans JSON structure, attaches reporting metadata, converts datasets into CSV binary format, and transmits the report via HTTP requests with URL parameters.

## Workflow Architecture
1. **Manual Trigger**: Simulates incoming raw order events.
2. **UpdateFieldNames**: Formats JSON attributes and extracts payment status via array indexing (`tags[0]`).
3. **SetReportMetadata**: Appends system timestamps (`$now`) and total batch sizes (`$input.all().length`).
4. **ConvertToCSV**: Flattens JSON items into a structured CSV file binary object.
5. **SendReport**: Dispatches the binary report to a webhook endpoint using Query Parameters (`generated_at`, `total_orders`) with `.first().json` context references.

## Technical Concepts Mastered
- **Data Transformation**: JSON restructuring & Array Indexing.
- **Binary Conversion**: Converting JSON datasets into CSV binary objects.
- **n8n Expression Syntax**: Resolving item mapping errors with `.first().json` context references.
- **API Integration**: HTTP POST requests with Binary Body payloads & Query Parameters.

## How to Import
1. Download `ecommerce_sales_pipeline.json` from this repository.
2. Open your n8n instance and select **Import from File**.
3. Load the file and click **Execute Workflow**.
