# Automated Sales Data Pipeline (n8n Workflow)

## Overview
An automated data processing pipeline built in **n8n** that extracts raw sales data, cleans and formats JSON attributes, enriches data with dynamic metadata, converts it into a CSV binary report, and sends it via HTTP POST requests to an external verification endpoint.

## Tech Stack & Concepts Applied
- **Tool**: n8n (Open-Source Workflow Automation)
- **Data Handling**: JSON Data Payload, Binary File Handling (CSV), Array Indexing
- **Protocols**: HTTP Request (POST), Query Parameters, Custom Headers
- **Expressions**: JavaScript / n8n Expression Syntax (`$("Node Name").item.json`)

## Troubleshooting & Technical Challenges Overcome
- **Issue**: Received `missing required fields: report_generated, assessment_id` error during API endpoint execution.
- **Root Cause**: Pipeline sequence misconfiguration — converting JSON to a binary CSV before assigning metadata caused the metadata context to be dropped.
- **Resolution**: Re-architected node sequence to `SetReportMetadata -> ConvertToCSV -> SendReport`, ensuring both binary CSV and JSON metadata properties were maintained and correctly mapped in HTTP Query Parameters.

## How to Use / Import
1. Download the `.json` workflow file from this repository.
2. In your n8n instance, click **Workflows** -> **Import from File**.
3. Select the downloaded JSON file and execute.
