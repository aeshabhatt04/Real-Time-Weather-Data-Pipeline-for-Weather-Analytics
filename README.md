# Real-Time-Weather-Data-Pipeline-for-Weather-Analytics

This repository contains my AWS Data Engineering Bootcamp Project #3 – a real-time weather data pipeline built using AWS serverless technologies. The pipeline ingests, processes, stores, and visualizes weather data to enable real-time monitoring, forecasting, and interactive analytics.

## Objective

- Build a real-time weather data pipeline leveraging AWS serverless services to:

- Monitor weather conditions in real time

- Perform historical trend analysis for forecasting

- Automate data processing with low latency

- Deliver data-driven insights through interactive dashboards

## Key Outcomes:

- 90% reduction in manual data processing time

- Scalable and cost-efficient architecture using AWS Kinesis, Lambda, Redshift, and QuickSight

# System Architecture

## Prerequisites

- AWS account with access to Kinesis, Lambda, Redshift, S3, and IAM

- Python 3.x for Lambda functions and data simulation

- OpenWeatherMap API key for weather data simulation

- (Optional) Terraform or other IaC tools for automation

### Component Breakdown
1. Data Ingestion – Kinesis

- Kinesis Data Stream: weather-stream (on-demand capacity)

- Python producer script: weather_stream-project-3.py sends weather data every 60 seconds

2. Data Processing – Lambda

- Lambda function: weatherStreamFunction triggered by Kinesis events

- Performs validation, temperature conversion (Kelvin → Celsius), JSON flattening, CSV output

- Stores raw data (Bronze) and cleaned data (Silver) layers in Amazon S3

3. Data Warehouse – Redshift

- Serverless Redshift with VPC and security groups

- Tables to store cleaned weather data for analytics

4. Analytics – QuickSight

- Dashboards and visualizations querying Redshift data

## Data Flow

- Ingestion – Python script streams weather data into Kinesis (weather-stream) & stores raw JSON in S3 Bronze layer

- Processing – Lambda processes Kinesis events, cleans/transforms data, stores CSV files in S3 Silver layer

- Warehousing – Lambda/Glue loads cleaned data into Redshift for analytical queries

- Visualization – QuickSight queries Redshift to generate interactive dashboards

## Security & Compliance

- Encryption: Kinesis streams encrypted with KMS; S3 buckets use SSE-S3

- IAM Roles: Least-privilege roles assigned to Lambda (e.g., LambdaRoleProject3)

- Network Isolation: Redshift deployed within private VPC subnets secured by security groups

## Monitoring & Data Quality

- CloudWatch: Centralized logging and monitoring for Lambda and Kinesis errors

- Data Validation: Lambda checks for empty or invalid JSON records and verifies unit conversions

- Redshift Query Monitoring: Performance tracked via Redshift console

## Results

- Achieved a 90% reduction in manual data processing time

- Delivered real-time dashboards for weather monitoring and trend forecasting

- Built a scalable, automated, and cost-effective data pipeline on AWS

## Connect

Feel free to check out my LinkedIn profile or message me to discuss AWS, data pipelines, or real-time analytics.
