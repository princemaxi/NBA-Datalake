# NBA Data Lake

This repository contains setup_nba_data_lake.py, a Python script that automates the creation of a data lake for NBA analytics using AWS services. The setup leverages Amazon S3, AWS Glue, and Amazon Athena to store, query, and analyze NBA-related data efficiently.

## Overview

The setup_nba_data_lake.py script performs the following tasks:

- Creates an Amazon S3 bucket to store raw and processed NBA data.
- Uploads sample NBA data (in JSON format) to the S3 bucket.
- Sets up an AWS Glue database and an external table for querying the data.
- Configures Amazon Athena for querying the data stored in the S3 bucket.
- This project demonstrates how to build a cloud-native data lake integrated with external APIs for analytics and reporting.

## Prerequisites

Before running the script, ensure you have the following:

1. API Key from SportsData.io
- Sign up at SportsData.io and create a free account.
- Navigate to Developers → API Resources and select NBA for your trial.
- Under "Standings," locate the Query String Parameters section to find your API key.
- Copy the API key for later use.

2. AWS Account
Set up an AWS account with basic knowledge of the following services:

- Amazon S3: For data storage.
- AWS Glue: For data cataloging.
- Amazon Athena: For querying the data.

3. IAM Permissions
Ensure the IAM role or user executing the script has the following permissions:

- S3: s3:CreateBucket, s3:PutObject, s3:DeleteBucket, s3:ListBucket
- Glue: glue:CreateDatabase, glue:CreateTable, glue:DeleteDatabase, glue:DeleteTable
- Athena:  athena:StartQueryExecution, athena:GetQueryResults

## Setup Instructions

1. Open AWS CloudShell
- Log in to AWS Management Console.
- Click the CloudShell icon ( >_ ) next to the search bar to open the CloudShell environment.
 
2. Create the setup_nba_data_lake.py Script
- In CloudShell, run the following command to create the script: nano setup_nba_data_lake.py
- Copy the content of the setup_nba_data_lake.py script from this repository and paste it into the editor.
- Replace the placeholder in the script with your SportsData.io API key under the # Sportsdata.io configurations section.
- Save and exit: Press Ctrl+X, then Y, and hit Enter.

3. Create a .env File
- Run the following command to create an .env file: nano .env
- Add the following content, replacing the placeholder with your actual API key:
   - SPORTS_DATA_API_KEY=your_sportsdata_api_key
   - NBA_ENDPOINT=https://api.sportsdata.io/v3/nba/scores/json/Players
- Save and exit: Press Ctrl+X, then Y, and hit Enter.

4. Run the Script
- Execute the script by running: python3 setup_nba_data_lake.py
- You should see logs confirming successful resource creation and data upload.

5. Verify Resources

Amazon S3:
- Go to S3 in the AWS Console.
- Verify the creation of a bucket named sports-analytics-data-lake containing:
- A folder raw-data with nba_player_data.json.

Amazon Athena:
- Run this sample query to check the data:
sql
SELECT FirstName, LastName, Position, Team
FROM nba_players
WHERE Position = 'PG';

## What You’ll Learn
- Securing AWS services with least privilege IAM policies.
- Automating the creation of cloud resources using Python scripts.
- Integrating external APIs into cloud-based workflows.

## Future Enhancements
- Automated Data Ingestion: Use AWS Lambda to fetch and update data dynamically.
- Data Transformation: Implement ETL pipelines with AWS Glue.
- Advanced Analytics: Add dashboards and visualizations using AWS QuickSight.
- Real-Time Updates: Integrate AWS Kinesis for real-time data streaming.

