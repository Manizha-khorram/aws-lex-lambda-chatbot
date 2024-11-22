# aws-lex-lambda-chatbot# AWS Lex Chatbot with Lambda Integration

## Project Overview

This project demonstrates how to create a conversational chatbot using Amazon Lex and AWS Lambda, specifically designed to simulate a bank account balance inquiry system.

## Technologies Used

- Amazon Lex
- AWS Lambda
- Serverless Computing

## Prerequisites

- AWS Account
- Basic understanding of:
  - Cloud computing
  - Serverless architecture
  - Python (for Lambda function)

## Project Components

### 1. Amazon Lex Bot

- **Purpose**: Create a conversational interface for account balance inquiries
- **Key Features**:
  - Natural language processing
  - User intent recognition
  - Multi-turn conversation support

### 2. AWS Lambda Function

- **Purpose**: Generate dynamic responses for account balance queries
- **Functionality**:
  - Generates a random account balance
  - Serves as a code hook for intent fulfillment

### 3. Chatbot Alias

- **Purpose**: Provide a stable reference point between Lex bot and Lambda function
- **Configuration**:
  - Points to the latest Lambda function version
  - Enables easy version management and updates

## Implementation Steps

1. **Create Lambda Function**

   - Write a Python script to generate random account balance
   - Configure function to return simulated balance

2. **Configure Amazon Lex Bot**

   - Define intents (e.g., account balance inquiry)
   - Set up user verification flow
   - Configure code hooks

3. **Connect Lambda with Lex**
   - Use TestBotAlias to link Lambda function
   - Select "Latest" version for dynamic updates

## Code Hook Configuration

- Located in intent's fulfillment settings
- Select Lambda as the source
- Configure function to handle specific intent logic

## Project Highlights

- Serverless architecture
- Dynamic response generation
- Secure intent fulfillment
- Scalable design

## Potential Improvements

- Implement actual bank account integration
- Add more robust user verification
- Enhance error handling
- Implement more complex conversational flows

## Time to Complete

Approximately 1 hour

## Learning Outcomes

- Understand serverless computing principles
- Learn AWS Lex and Lambda integration
- Practice creating conversational AI interfaces

## Author

Manizha Khorram
