# Serverless AI Image Editing on AWS

This repository contains a full-stack, serverless image editing web application built on AWS. The backend runs as an AWS Lambda function, and the frontend is a static web app deployed with AWS Amplify.

## Repository Structure

- `Code files/`
  - `lambda_function.py` – AWS Lambda function that receives requests from API Gateway, calls Amazon Bedrock (e.g., Titan Image Generator) for image generation/editing, and writes logs/metadata to other AWS services as configured.
- `AWS-Amplify-Code/`
  - Frontend web application (HTML, CSS, JavaScript or framework-based) that lets users provide prompts, upload images, and view AI-edited results.

## High-Level Architecture

The typical deployment uses the following AWS services:[file:1]

- Amazon Cognito for user authentication.
- Amazon API Gateway as the HTTP entry point to the Lambda backend.
- AWS Lambda for serverless business logic (`lambda_function.py`).
- Amazon DynamoDB for storing image metadata, prompts, and results.
- Amazon Bedrock (Titan Image Generator) for AI image generation and editing.
- AWS Amplify for hosting the frontend web application.

## Prerequisites

- An AWS account with permissions to create and configure:
  - Cognito User Pools
  - API Gateway REST APIs
  - Lambda functions
  - DynamoDB tables
  - Bedrock access and foundation models
  - Amplify apps and hosting.
- Python 3.x for local Lambda development.
- Node.js and a package manager (if the frontend uses a JS build toolchain).

## Setup (High Level)

1. Configure and deploy the Lambda function:
   - Update environment variables and IAM role for Bedrock, DynamoDB, etc.
   - Package and deploy `lambda_function.py` to AWS Lambda.

2. Create an API Gateway REST API:
   - Create a POST method that integrates with the Lambda function.
   - Optionally secure it with a Cognito authorizer.

3. Deploy the frontend:
   - Update API endpoint, Cognito details, and any config values in `AWS-Amplify-Code`.
   - Deploy the frontend directory as an AWS Amplify app.

4. Test end-to-end:
   - Open the Amplify-hosted URL.
   - Authenticate (if enabled), submit prompts, and verify generated images and metadata.

## License

Add your chosen license here (e.g., MIT, Apache 2.0) before publishing.
