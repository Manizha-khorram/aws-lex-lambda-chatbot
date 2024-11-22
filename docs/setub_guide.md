# AWS Lex Chatbot with Lambda - Setup Guide

## Prerequisites

- AWS Account with appropriate permissions
- AWS CLI installed and configured (optional but recommended)
- Basic understanding of Python
- Git installed (for cloning this repository)

## Step 1: Create the Lambda Function

1. **Navigate to AWS Lambda Console**

   - Go to AWS Management Console
   - Search for "Lambda"
   - Click "Create function"

2. **Configure Lambda Function**

   - Choose "Author from scratch"
   - Function name: `BankerBotFunction` (or your preferred name)
   - Runtime: Python 3.9 (or latest version)
   - Architecture: x86_64
   - Click "Create function"

3. **Add Function Code**

   - Copy the `lambda_function.py` code from this repository
   - Paste it into the Lambda function code editor
   - Click "Deploy"

4. **Configure Function Settings**
   - Memory: 128 MB (default is sufficient)
   - Timeout: 30 seconds
   - Click "Save"

## Step 2: Create Amazon Lex Bot

1. **Navigate to Amazon Lex Console**

   - Go to AWS Management Console
   - Search for "Lex"
   - Click "Create bot"

2. **Configure Bot Settings**

   - Creation method: Create a blank bot
   - Bot name: `BankerBot`
   - IAM role: Create a new role
   - COPPA: Choose appropriate option
   - Language: English (US)
   - Click "Next"

3. **Create Intent**

   ```
   Intent name: CheckBalance
   Sample utterances:
   - What's my balance
   - Check my account balance
   - How much money do I have
   ```

4. **Add Slots**
   ```
   Slot name: accountType
   Slot type: AMAZON.BankAccount
   Prompts:
   - Which account would you like to check?
   - For which account?
   ```

## Step 3: Connect Lambda with Lex

1. **Configure TestBotAlias**

   - Go to your Lex bot
   - Click on "Aliases" in the left sidebar
   - Select "TestBotAlias"
   - Click "Languages"
   - Select "English (US)"

2. **Add Lambda Function**

   - Under "Source", select "Lambda function"
   - Choose your Lambda function
   - Version: Latest
   - Click "Save"

3. **Add Code Hooks**
   - Go back to your intent
   - Under "Fulfillment"
   - Select "Use a Lambda function"
   - Choose your Lambda function
   - Click "Save intent"

## Step 4: Testing

1. **Test in Lex Console**

   - Click "Test" in the left sidebar
   - Type: "What's my balance"
   - Verify bot asks for account type
   - Provide account type
   - Verify random balance is returned

2. **Common Test Cases**
   ```
   User: What's my balance?
   Bot: Which account would you like to check?
   User: Checking
   Bot: Thank you. The balance on your checking account is $XXX.XX dollars.
   ```

## Step 5: Deployment (Optional)

1. **Create Channels**

   - Click "Channels" in left sidebar
   - Options available:
     - Web Interface
     - Mobile Apps
     - Facebook Messenger
     - Slack
     - Other platforms

2. **Configure Channel Settings**
   - Follow platform-specific instructions
   - Note down integration credentials

## Troubleshooting

### Common Issues

1. **Lambda Function Not Responding**

   - Check Lambda execution role permissions
   - Verify Lambda function timeout settings
   - Check CloudWatch logs for errors

2. **Lex Not Understanding Inputs**

   - Add more sample utterances
   - Train the bot again
   - Check slot configurations

3. **Integration Issues**
   - Verify IAM roles and permissions
   - Check Lambda function name/ARN
   - Ensure regional compatibility

## Security Considerations

1. **IAM Roles**

   - Use principle of least privilege
   - Regularly review permissions
   - Monitor using AWS CloudTrail

2. **Data Privacy**
   - Don't store sensitive information
   - Implement proper logging
   - Consider data retention policies

## Next Steps

- Add more intents for different banking operations
- Implement actual account balance lookup
- Add user authentication
- Enhance error handling
- Add support for multiple languages

## Additional Resources

- [AWS Lambda Documentation](https://docs.aws.amazon.com/lambda/)
- [Amazon Lex Documentation](https://docs.aws.amazon.com/lex/)
- [AWS IAM Best Practices](https://docs.aws.amazon.com/IAM/latest/UserGuide/best-practices.html)
